L'objectif est de **détecter** les visages dans une image puis d'**extraire** les caractéristiques de chaque visage pour pouvoir les comparer par la suite. 

Pour effectuer la détection, nous utilisons un **réseau de neurones convolutif** qui a été entrainé pour détecter les visages.

Voici le réseau de neurones RetinaFace :
![[1 DFMLhD-7m5eVXYxyxyNrEQ.png]]

Détection et extraction des visages d'une image :
![[DeepFaceLab_Source_Faceset_Extract-1024x1024.png]]

Chaque visage est ensuite encodée grâce à un autoencodeur qui arrive à extraire les données caractéristiques qui font le visage d'une personne. 

![[autoencoder_800px_web.png]]

Les images d'une même personne sont censées avoir des caractéristiques très similaires.
![[embedding.jpg]]
Ici on voit un visage et son vecteur caractéristique.
Maintenant, nous n'avons plus qu'à comparer les vecteurs caractéristiques des visages pour trouver des similarités. C'est ce que fait la partie [[Clustering]].
## Amélioration

Nous utilisons la librairie [DeepFace](https://github.com/serengil/deepface) basée sur `Tensorflow` pour effectuer la détection des visages ainsi que l'encodage des caractéristiques de chaque visage. [[demo_reconnaissance| Demo Jupyter]]

Nous avons testé de nombreux modèles inclus dans `DeepFace`, et les deux meilleurs (mais aussi les plus lents) sont [RetinaFace](https://github.com/serengil/retinaface) et [MTCNN](https://github.com/ipazc/mtcnn) pour la détection de visage. 

Pour ce qui est du modèle d'auto-encodeur, [Facenet](https://github.com/davidsandberg/facenet) et `Facenet512` (vecteur de 512 en sortie) offrent d'excellents résultats, mieux que `VGG-16` qui pourtant génère un vecteur moins compressé en sortie. 
À noter que Facenet fonctionne mieux lorsque l'on compare les vecteurs avec une [**distance cosinus**](https://youtu.be/i_MOwvhbLdI?feature=shared&t=143).

Ainsi, lorsque l'on utilise la librairie `DeepFace`, on détecte puis encode les visages de cette façon :
```Python
embeddings = DeepFace.represent(
	image_path,
	detector_backend='retinaface', #Détection de visages retinaface
	model_name='Facenet', #Encodage Facenet
	enforce_detection=False #Pour gérer les images sans visages
)
```
## Code

```Python
def extract_face(image_list, album, db_session):
    data_dir = Path(current_app.config["data_dir"])
    faces = []
    for (i, image_name) in enumerate(image_list):
        print(f"Extracting faces from Image: {str(image_name)} ({i + 1}/{len(image_list)})")
        image_path = data_dir / image_name
        try:
            # Get the embeddings for all faces in the image
            # retinaface is the best for detecting faces, and Facenet is good for encoding
            face_data_list = DeepFace.represent(str(image_path), model_name='Facenet', detector_backend='retinaface', enforce_detection=False)
            # Create Image object outside the loop
            image_db = Image(name=image_name, album=album)
            db_session.add(image_db)
            db_session.commit()
            for face_data in face_data_list:
                # Extract the face encoding and box coordinates
                face_encoding = face_data['embedding']
                boxe = (face_data['facial_area']['y'], face_data['facial_area']['x'] + face_data['facial_area']['w'],
                        face_data['facial_area']['y'] + face_data['facial_area']['h'], face_data['facial_area']['x'])
                # Create a Face object and append it to the list
                face_db = Face(image=image_db, encoding=face_encoding, boxe=boxe)
                db_session.add(face_db)
                faces.append(face_db)
            db_session.commit()
        except Exception as e:
            print(f"Error processing {image_name}: {e}")
    return faces
```

Grâce à ce code, nous pouvons renvoyer une liste de vecteurs encodés, ainsi que les sauvegarder dans la base de données, nous pouvons maintenant effectuer le [[Clustering]] des vecteurs encodés.