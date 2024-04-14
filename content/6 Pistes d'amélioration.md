Cf [[3 Notre contribution au projet]]

L'appli est pour l'instant un Produit : C'est à dire il est utilisable par une personne en local s'il veut le télécharger et l'utiliser pour lui

Le but final serait de le rendre accessible en tant que service (Et moins cher que le vrai Memento): Pour cela il faut encore améliorer le front et implémenter d'autres choses dans le back mais globalement:
- il y'a un gros travail à fournir sur le Front pour crée un site de qualité d'entreprise. 
- Un travail sur le back et notamment sur la structure de base de donnée
- Un travail en termes de Sécurité surement 
# Front 

Le front est encore largement améliorable et voici les pistes d'améliorations :

- Changer les couleurs des autres Vues et le thème, faire des tests de jeux de couleurs meilleurs que celui-ci

- Implémenter les Vue per Slides pour faire le modèle de Carousel disponible dans la balise 
**overlay** du fichier AlbumView.vue

- Implémenter un ajout de photo depuis galerie, la seul façon pour l'instant c'est avec une prise de selfie mais cela peut grandement fausser l'association à un cluster si la personne change ou si la qualité webcam est insuffisante.
De + la possibilité d'implémenter l'ajout depuis galerie permettrait d'avoir toute les photos à partir d'une photo du jour J

- Changer le design des différentes vues: Le faire en créant des objets vue pour design plus simplement pour vous entrainez!

## Back

SQL:
Rajouter à la base de donnée un systeme d'user avec des rankings(Abonnement par exemple Gold Platine Etccccc) et de possessions d'albums (25 albums max pour user gold par exemple)

Pour l'accélération du GPU par Docker, il faudrait peut être build `Tensorflow` à partir de la source.

Utiliser les `box` qui localisent les visages détectés pour qu'on puisse cliquer dessus et passer sur le cluster qui correspond à cette personne .