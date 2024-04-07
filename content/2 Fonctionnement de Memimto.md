Memimto comporte un Client Web pour l'utilisateur qui communique avec le côté Serveur
![[Pasted image 20240405144855.png]]
# Front end

# Back end

## Base de données

![[Pasted image 20240405144908.png]]

## Processing des images
![[Pasted image 20240405144927.png]]

L'album photo va d'abord être décompressé puis on va appliquer à chaque image une [[Détection et encodage]] des visages et ils vont être stockés dans la base de données.
Ensuite, un processus de [[Clustering]] va être appliqué sur les visages, et les visages appartenant à une même personne vont être regroupés.

# Environnement Docker

Pour que le projet puisse être déployé sur n'importe quelle plateforme (Windows, Linux, ...), le backend est enveloppé dans un container [[Docker]].