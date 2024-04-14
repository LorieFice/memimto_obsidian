Pour lancer le serveur : `docker compose up --build
Pour lancer le client : `npm run dev`

On se connecte à l'adresse `http://localhost:5173/`

## Page d'accueil

Pour se connecter, cliquer sur l'icone "profil" et entrer l'identifiant et le mot de passe. (Pour l'instant, `Id = admin`, `pwd = whatapassword`)

![[Pasted image 20240414193834.png]]

L'icone "profil" se change en icone "upload"

![[Pasted image 20240414194611.png]]

Pour upload un album, cliquer sur l'icone près du 1

En cliquant sur l'icone près du 2, on revient à la page d'accueil

En cliquand sur l'album (3), on affiche toutes les images

## Upload

![[Pasted image 20240414194835.png]]

Cliquer dans le champ "please select a file" et charger un dossier photo zip puis cliquer sur upload

![[Pasted image 20240414195225.png]]

Quand l'extraction des visages et l'entrainement du classifier sont terminés (voir serveur docker : `Album done`), on peut revenir à la page d'accueil

## Visualiser les images triées

On clique sur l'album choisi depuis l'accueil
![[Pasted image 20240414195402.png]]

Et on change l'adresse en rajoutant /0 pour le premier cluster, /1 pour le deuxième etc.

Un exemple d'adresse devient donc `http://localhost:5173/album/1/0` pour le premier cluster, `http://localhost:5173/album/1/1` pour le deuxième etc.