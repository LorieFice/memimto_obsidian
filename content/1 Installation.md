# Guide d'utilisation de Memimto(Windows)

<hr>

<span style="font-family:cursive"><strong>Etape 1: Clonage</strong></span>

La première étape consiste à cloner les 2 fichiers suivants:

- MementoClient.V2 (In the VueJS file)
- MementoServer.V2
```bash
git clone https://github.com/N4tsoni/Memento.V2-Frontend.git
```

<hr>

<span style="font-family:cursive"><strong>Etape 2: Installation du backend</strong></span>

La deuxième étape consiste à installer le backend de Mémento. Voici les prérequis nécessaires :

1. **Prérequis :**
    1. [Installer Docker et le rendre compatible avec Nvidia](https://docs.docker.com/desktop/gpu/) Vous aurez besoin de Docker + WSL + CUDA + NvidiaDev Toolkits
2. **Lancement du back:"**
	1. Lancer Docker (Docker Desktop sur Windows)
	2. Lancer un terminal dans le client et taper la commande suivante: 
```bash
docker compose up --build ##-- build pour recompiler l'image
```
	![](https://github.com/N4tsoni/Memento.V2/blob/main/terminal_docker.gif)
<hr>
<span style="font-family:cursive"><strong>Etape 3: Installation du front</strong></span>

1. **Prérequis :**
    - Assurez-vous d'avoir Node.js installé sur votre système. Si ce n'est pas déjà le cas, vous pouvez le télécharger et l'installer à partir du site officiel de [Node.js](https://nodejs.org/).


3. **Installation des dépendances :**
    - Accédez au répertoire cloné (`Memento.V2-Frontend`) à l'aide de la commande suivante :
```bash
cd Memento.V2-Frontend
```
    - Installez les dépendances Node.js en exécutant la commande suivante dans le terminal :
    ```bash
    npm install
    ```
		- Ensuite lancez l'appli:
	  ```
    npm run dev --build
    ```

![](https://github.com/N4tsoni/Memento.V2/blob/main/terminal_npm.gif)
	
Pour plus d'infos : [Le lien du gitHub de la V1](https://github.com/zyioump)
