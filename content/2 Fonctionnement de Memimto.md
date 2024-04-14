Memimto comporte un Client Web pour l'utilisateur qui communique avec le côté Serveur
![[Pasted image 20240405144855.png]]
# Front end

Tout est expliqué dans la partie suivante : [[1.Comment ca marche|Comment ça marche]]

# Back end

## Base de données

![[Pasted image 20240405144908.png]]
- Le models.py c'est la BDD ([[SGBD-SQL]]): C'est une base de donnée SQL 
Ici c'est un fichier python car on utilise la librairies[[SQL Alchemy]]: Librairie qui permet de faire du SQL via Python


- Celery.py :
Permet de configurer celery

- task.py :
Dans ce fichier on aura toute les taches lourdes pour le serveur qui seront faites dans le worker donc les fonctions d'upload de clustering ou d'encodage des visages se font dans le worker:
Toute la partie MachineLearning et modèle préentrainés sont la !

- Flask: Le serveur et l'API Rest

- Le dossier BluePrint
	- Il est le fichier qui permet de gérer les requêtes HTML
	


La bluePrint c'est le fichier en rapport avec Flask et les [[Requettes HTTP]]
## Processing des images
![[Pasted image 20240405144927.png]]

L'album photo va d'abord être décompressé puis on va appliquer à chaque image une [[Détection et encodage]] des visages et ils vont être stockés dans la base de données.
Ensuite, un processus de [[Clustering]] va être appliqué sur les visages, et les visages appartenant à une même personne vont être regroupés.

# Environnement Docker

Pour que le projet puisse être déployé sur n'importe quelle plateforme (Windows, Linux, ...), le backend est enveloppé dans un container [[Docker]].