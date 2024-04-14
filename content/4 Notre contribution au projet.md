# Organisation de notre projet

Voici un ordre d'idée du déroulement du projet :

![[Gantt_Memimto.png]]

Reprendre un projet si important lorsque l'on ne connait pas le front end (pour Sofian) ou le back end (pour Thibault) était un réel défi. 
Nous avons passé une bonne semaine et demie à comprendre le fonctionnement du site, et nous avons ensuite décidé de séparer le travail entre l'amélioration du front (Sofian) et back end (Thibault), qui étaient respectivement nos faiblesses.
Nous remercions Simon Archieri et Emile Thibault pour les nombreuses heures qu'ils nous ont accordées pour nous aider à mener à bien ce projet, nous avons beaucoup appris grâce à nos précieux appels.

# Amélioration du front vers un design plus simple à utiliser comme une appli: 


![[Pasted image 20240405150716.png]]

Toutes les couleurs sont modifiables dans le CSS voir [[VueJS#Organisation d'un projet vue]]

On a le rajout d'une barre de navigation permettant à l'utilisateur de se diriger en permanence vers les pages importantes!

Les boutons on un texte rajouté pour mieux comprendre à quoi ils servent!

L'organisation global de la page d'accueil a été modifié pour permettre un affichage type fenêtre et utilisé à plein potentiel les outils de Vue Router.

![[Pasted image 20240405151435.png]]

Ainsi peut importe dans quelle partie de l'appli on se trouve on peut toujours utilisé la barre de navigation pour se retrouver plus simplement.

![[Pasted image 20240405151539.png]]
L'écran d'accueil est un VuperSlide 3D dans lequel on peut présenter l'appli rapidement.

Il intègre une vidéo et une image de la video dans le fond
Voir [[WAVE-UI#Les Vueper Slides]]

J'ai aussi rajouter une page Qui sommes nous pour nous présenter (Elle est incomplète pour l'instant)

# Amélioration du backend

Lorsque l'on a repris le projet, nous avons remarqué qu'il était possible d'améliorer la détection et le clustering des images, qui étaient mal triées si le nombre de personnes différentes était trop grand.

Le traitement d'un album se décompose en plusieurs étapes successives. Lorsque l'on ajoute un album sur le site, ces étapes s'enchainent :

- Dézippage de l'album
- [[Détection et encodage]] des visages
- [[Clustering]] des vecteurs encodés

## Amélioration de la détection / encodage

Utiliser la librairie DeepFace nous a permis de drastiquement améliorer la précision de la détection des visages, ainsi que l'encodage.

>Sur un jeu de 26 images, j'ai compté 76 images, RetinaFace en trouve aussi 76 (Dlib en trouvait moins et avec des points aberrants) ([[demo_reconnaissance|Demo ici]])
>Exemple : ces objets ont été reconnus comme des visages par Dlib
> ![[Pasted image 20240405132922.png]]
>![[Pasted image 20240405132950.png]]

## Amélioration du clustering

En utilisant DBSCAN plutôt que OPTICS, nous avons réussi à mieux affiner les paramètres de clustering, ce qui fait que lorsque les images sont des visages bien définis, le site trouve le bon nombre de clusters. 

Nous avons aussi choisi d'utiliser un classifieur Tensorflow que l'on entraine sur les données et labels que nous fournit DBSCAN. Pourquoi Tensorflow ?

- Nous avons utilisé Tensorflow en AADA
- Pour utiliser le GPU (malheureusement nous n'avons pas réussi)

# Bonus

## Ajout d'un outil de scrapping

Puisque les modèles précédents ne fonctionnaient pas sur des images "difficiles" à analyser (ex : visage incliné, maquillage, flou de mouvement, photo sombre, ...) nous avons développé un outil de [[Scrapping]] pour récolter les images des bases de données de l'école.