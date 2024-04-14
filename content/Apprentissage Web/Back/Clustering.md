Maintenant que nous avons extrait les features des visages détectés, nous voulons associer les visages similaires aux mêmes groupes.

![[graphic.webp]]
Les algorithmes de clustering créent des regroupements entre des vecteurs en fonction de différents critères comme la distance entre ces points par exemple. 

![[144739072-353912d2-0fc5-4180-a7ab-5355302a80a5.png]]
Un algorithme pour faire ça est `DBSCAN`, qui, contrairement à `K-Means`, détermine automatiquement le nombre de clusters selon les paramètres.

Une fois que l'on a déterminé les clusters et labels, on **entraine un réseau de neurones** à déterminer lui même ces clusters, pour pouvoir d'une part **sauvegarder ce modèle**, et d'autre part garder une capacité de généralisation.

## Atouts et limites de DBSCAN

`DBSCAN` a l'avantage d'être un outil très puissant pour faire des clusters de **proche en proche**. Il peut s'adapter à de nombreuses formes de données comme on peut le voir ci-dessous. Il nous intéresse beaucoup car nous **n'avons pas** à définir le **nombre de clusters**. 
Nous avons juste à définir le nombre de voisins pour que le point soit un point central, et le rayon max. (Comme vu dans [[Détection et encodage]], on utilise la similarité cosinus comme distance)
![[Pasted image 20240405193834.png]]
Cependant, un grand défaut qui limite notre clustering est le cas particulier que l'on voit à droite. Lorsque beaucoup de points sont similaires, alors ils sont juste affectés au même cluster. C'est un cas qui n'est pas si rare, et qui survient lorsque l'on a trop de visages à classer. Résultat :
- Si la distance est trop sélective, alors beaucoup de visages sont considérés comme du bruit, que `DBSCAN` va ignorer
- Si la distance n'est pas assez sélective, alors il y aura plus de visages que de clusters

C'est une des [[6 Limites]] de notre projet : nous n'arrivons pas à trouver des paramètres de `DBSCAN` qui satisfont tous les types d'albums.
## Code
```Python
def cluster(album_db, faces_db, db_session):
    encodings = np.array([face.encoding for face in faces_db])
    # Perform clustering using DBSCAN
    dbscan = DBSCAN(eps=0.15, min_samples=3, metric='cosine') # This is the trickiest part to adjust
    labels = dbscan.fit_predict(encodings)
    num_faces = len(labels)  # Total number of faces found
    num_clusters = len(np.unique(labels)) - 1  # Number of clusters detected (excluding noise)
    print(f"{num_faces} faces detected in {num_clusters} clusters.")
    for i, label in enumerate(labels):
        faces_db[i].cluster = label
    db_session.commit()
    num_classes = len(np.unique(labels))
    encoder = LabelEncoder()
    labels_encoded = encoder.fit_transform(labels)

    model = Sequential([
        Dense(128, activation='relu', input_shape=(encodings.shape[1],)),
        Dropout(0.5),
        Dense(128, activation='relu'),
        Dropout(0.5),
        Dense(64, activation='relu'),
        Dropout(0.5),
        Dense(num_classes, activation='softmax')
    ])

    model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
    early_stopping = EarlyStopping(patience=5, restore_best_weights=True)
    model.fit(encodings, labels_encoded, epochs=100, batch_size=16, callbacks=[early_stopping])

    # Save the trained model

    classifier_name = str(uuid4()) + ".h5"
    album_db.classifier = classifier_name
    model.save(current_app.config["data_dir"] / classifier_name)

    db_session.commit()

    print("Classifier saved successfully.")
    print(f"{num_faces} faces detected in {num_clusters} clusters.")
```
