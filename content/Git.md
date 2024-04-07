# Git permet de track nos codes

On suit un projet avec git en tapant : 

```bash
git init ##Initie le Git dans le dossier à suivre
```

Ensuite 
```bash
git status ## Permet de récuperer les informations sur les fichiers non traquer et permet de donner les commandes à faire
git add NOMDUFICHIER ##Permet d'ajouter les fichiers git add. permet d'ajouter le fichier au fichier suivi, il les enleve du gitignore??
git commit -m "MESSAGE" ##Permet de valider une étape de notre code et de sauvegarder les changements qu'on a fait sur le code. Crée un backup 
git config --global ## Il peut demander qui on est
git push ##Envoie au repertoire GitHub
	```

## Les commandes classiques pour initialiser son git:

```bash
git init
git add .
git commit -m "premier commit"
git branch -M main
git remote add origin https://github.com/LorieFice/Cours.git
git push --set-upstream origin main
```

### Partager un projet

On se met en collaborateur sur un repertoire github (Lien commun)

```bash
git push ##On partage nos modifs
git pull ## on recupere les modifs que l'autre a commit
```

Gestion de branche: 

```bash
git branch##Te montre quelle branche il y'a
git branch NOMBRANCHE ## Créé une branche
git switch NOMBRANCHE ##permet de switch de branches en branche
git push va alors push la branch sur laquelle il est	
```


### Faire un README Github

Il fait un bon tuto: Sachant que le ReadMe c'est aussi un fichier markdown et que on est entrain de faire du markdown

Il montre qlq trucs cool notament les gifs cmd qui peuvent être cool
https://github.com/Sarvandani/Beautiful_github_profile?tab=readme-ov-file