## JavaScript

JavaScript est un langage de programmation de haut niveau utilisé principalement dans le développement web pour rendre les pages interactives et dynamiques. Il est souvent utilisé en conjonction avec HTML et CSS pour ajouter des fonctionnalités aux sites web, telles que des animations, des formulaires interactifs, des mises à jour de contenu en temps réel et bien plus encore.

### Qu'est-ce que JavaScript ?

JavaScript est un langage de script polyvalent qui peut être utilisé à la fois côté client (dans le navigateur web) et côté serveur (avec des environnements tels que Node.js). Il a été initialement développé pour ajouter des fonctionnalités interactives aux pages web, mais il est maintenant utilisé dans une grande variété d'applications, y compris les applications web, les applications mobiles et même les applications de bureau.

### À quoi sert JavaScript ?

JavaScript peut être utilisé pour réaliser de nombreuses tâches différentes dans le développement web :

- Manipulation du DOM : JavaScript peut être utilisé pour manipuler dynamiquement le contenu et le style des pages web en modifiant le Document Object Model (DOM).

- Gestion des événements : JavaScript permet de détecter et de réagir aux actions des utilisateurs, telles que les clics de souris, les pressions de touches et les soumissions de formulaires.

- Communication avec le serveur : JavaScript peut être utilisé pour envoyer et recevoir des données depuis le serveur sans avoir à recharger toute la page, grâce à des techniques telles que AJAX (Asynchronous JavaScript and XML).

- Animation et effets visuels : JavaScript peut être utilisé pour créer des animations et des effets visuels dynamiques sur les pages web, tels que des transitions en douceur, des effets de défilement et des animations d'éléments.

### Exemple d'utilisation de JavaScript :

Voici un exemple simple d'utilisation de JavaScript pour afficher un message d'alerte lorsque l'utilisateur clique sur un bouton :

```js
<button onclick="alert('Bonjour !')">Cliquez-moi</button>
```

## Variables en JavaScript

Les variables en JavaScript sont des conteneurs pour stocker des données. Elles permettent de nommer et de référencer des valeurs pouvant être utilisées dans votre programme. Voici quelques points importants à connaître sur les variables en JavaScript :

### Déclaration de variables

En JavaScript, vous pouvez déclarer une variable en utilisant les mots-clés `var`, `let`, ou `const`.

- **`var` :** Il s'agit de la façon classique de déclarer une variable. Cependant, `var` a une portée de fonction et peut être redéclarée.
- **`let` :** Il permet de déclarer une variable dont la portée est limitée au bloc, à l'instruction, ou à l'expression où elle est utilisée.
- **`const` :** Il permet de déclarer une variable dont la valeur est constante et ne peut pas être réassignée.

### Exemples de déclaration de variables :

```js
var x = 10; // Déclaration de variable avec var
let y = 20; // Déclaration de variable avec let
const z = 30; // Déclaration de variable constante avec const
```

### Portée des variables

La portée d'une variable en JavaScript détermine dans quelles parties du code cette variable peut être utilisée.

- Les variables déclarées avec `var` sont globales lorsqu'elles sont déclarées en dehors de toute fonction, sinon elles ont une portée locale à la fonction.
- Les variables déclarées avec `let` ou `const` ont une portée de bloc, limitée au bloc dans lequel elles sont déclarées.
### Exemple de portée des variables :
```js
var a = 1;
let b = 2;

function testScope() {
    var a = 3;
    let b = 4;

    console.log(a); // Affiche 3
    console.log(b); // Affiche 4
}

console.log(a); // Affiche 1
console.log(b); // Affiche 2

testScope();
```

## Globalement le fonctionnement est simillaire à tout les autres languages pour les fonctions, class etc....
# JavaScript côté navigateur
## Fonction Fetch en JavaScript

La fonction Fetch est une fonction native de JavaScript qui permet de faire des requêtes HTTP asynchrones vers des ressources distantes, telles que des API Web. Elle est utilisée pour récupérer des données depuis un serveur et gérer les réponses de manière efficace et flexible.

### Utilisation basique

La fonction Fetch prend comme argument l'URL de la ressource à récupérer et retourne une promesse qui résout en un objet Response représentant la réponse à la requête.

```js
fetch('https://api.exemple.com/donnees')
    .then(response => {
        if (!response.ok) {
            throw new Error('Erreur HTTP : ' + response.status);
        }
        return response.json();
    })
    .then(data => {
        console.log(data); // Données récupérées depuis l'API
    })
    .catch(error => {
        console.error('Erreur Fetch :', error);
    });
```

Dans cet exemple, nous faisons une requête GET à l'URL spécifiée, puis nous utilisons les méthodes `then()` et `catch()` pour gérer la réponse de la requête et éventuellement les erreurs.

### Gestion des méthodes HTTP et des options

La fonction Fetch prend un deuxième argument facultatif, un objet d'options, qui vous permet de personnaliser la requête, y compris les méthodes HTTP, les en-têtes, les données à envoyer, etc.
```js
fetch('https://api.exemple.com/ajout', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ nom: 'Alice', age: 30 })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Erreur Fetch :', error));
```
Dans cet exemple, nous utilisons la méthode POST pour envoyer des données JSON à l'API en spécifiant le type de contenu dans les en-têtes et en utilisant `JSON.stringify()` pour convertir les données en chaîne JSON.

### Gestion des réponses

La fonction Fetch renvoie un objet Response qui représente la réponse à la requête. Vous pouvez utiliser différentes méthodes et propriétés de cet objet pour accéder aux données de la réponse, aux en-têtes, au statut HTTP, etc.
```js
fetch('https://api.exemple.com/donnees')
    .then(response => {
        console.log(response.status); // Statut HTTP de la réponse
        console.log(response.headers.get('Content-Type')); // Type de contenu de la réponse
        return response.json(); // Convertit la réponse en JSON
    })
    .then(data => console.log(data)) // Données récupérées depuis l'API
    .catch(error => console.error('Erreur Fetch :', error));
    ```


La fonction Fetch est un outil puissant pour effectuer des requêtes HTTP asynchrones en JavaScript. Elle est largement utilisée dans le développement web moderne pour communiquer avec les serveurs et récupérer des données en temps réel.

## Fonctions Asynchrones et Synchrones en JavaScript

JavaScript prend en charge à la fois les fonctions synchrones et asynchrones, ce qui permet de gérer les opérations bloquantes et non bloquantes de manière efficace dans les programmes.

### Fonctions synchrones

Les fonctions synchrones sont des fonctions qui s'exécutent de manière séquentielle, bloquant l'exécution du code suivant jusqu'à ce qu'elles soient terminées. Les opérations longues dans les fonctions synchrones peuvent rendre l'interface utilisateur non réactive.

```js
function fonctionSynchrones() {
    console.log("Début de la fonction synchrones");
    // Opérations longues ou bloquantes
    console.log("Fin de la fonction synchrones");
}

fonctionSynchrones();
console.log("Après l'appel de la fonction synchrones");
```
Dans cet exemple, la fonction `fonctionSynchrones` s'exécute de manière synchrone, et le message "Après l'appel de la fonction synchrones" n'est affiché qu'après la fin de l'exécution de cette fonction.

### Fonctions asynchrones

Les fonctions asynchrones sont des fonctions qui s'exécutent de manière non bloquante, permettant à d'autres opérations de se poursuivre pendant leur exécution. Elles sont couramment utilisées pour les opérations réseau, les E/S de fichiers et les animations.
```js
function fonctionAsynchrones() {
    console.log("Début de la fonction asynchrones");
    setTimeout(() => {
        console.log("Traitement asynchrone terminé");
    }, 2000);
    console.log("Fin de la fonction asynchrones");
}

fonctionAsynchrones();
console.log("Après l'appel de la fonction asynchrones");
```
Dans cet exemple, la fonction `fonctionAsynchrones` s'exécute de manière asynchrone grâce à `setTimeout`, et le message "Après l'appel de la fonction asynchrones" est affiché immédiatement après son appel, sans attendre la fin du traitement asynchrone.

Les fonctions asynchrones sont utiles pour améliorer la réactivité des applications et gérer efficacement les opérations longues ou bloquantes sans bloquer l'exécution du code.

On les déclare comme ca
```js
async function maFonctionAsynchrone() {
    // Corps de la fonction asynchrone
}
```


`await` est un opérateur utilisé dans les fonctions asynchrones en JavaScript pour mettre en pause l'exécution d'une fonction asynchrone jusqu'à ce qu'une opération asynchrone soit terminée et que son résultat soit disponible. Il permet d'attendre la résolution (ou le rejet) d'une promesse et récupère sa valeur résolue.

Voici comment `await` fonctionne en pratique :

1. `await` ne peut être utilisé qu'à l'intérieur de fonctions déclarées comme `async`.
2. Lorsque vous utilisez `await` pour attendre la résolution d'une promesse, l'exécution de la fonction asynchrone est mise en pause jusqu'à ce que la promesse soit résolue. Cela signifie que le code qui suit l'`await` ne sera exécuté que lorsque la promesse sera résolue.
3. Si la promesse est résolue avec succès, `await` retourne la valeur résolue de la promesse.
4. Si la promesse est rejetée (c'est-à-dire qu'une erreur est survenue), `await` lance une exception qui peut être capturée à l'aide d'un bloc `try...catch` ou gérée avec une promesse rejetée.
5. `await` ne bloque pas le thread principal de l'application pendant l'attente de la résolution de la promesse. Au lieu de cela, il permet à d'autres tâches d'être exécutées pendant ce temps.

Voici un exemple d'utilisation de `await` pour attendre la résolution d'une promesse retournée par une fonction asynchrone :
```js
async function exempleAsynchrone() {
    // Attendre la résolution de la promesse
    let resultat = await uneFonctionAsynchrone();
    // Utiliser le résultat
    console.log(resultat);
}
```  
Dans cet exemple, `await` est utilisé pour attendre la résolution de la promesse retournée par `uneFonctionAsynchrone()`. Une fois que la promesse est résolue, la valeur résolue est stockée dans `resultat` et peut être utilisée dans le reste de la fonction.

## Le Document Object Model (DOM) en JavaScript

Le Document Object Model (DOM) est une interface de programmation de haut niveau fournie par les navigateurs web pour représenter et manipuler la structure d'une page HTML ou XML. Le DOM représente chaque élément de la page en tant qu'objet dans une hiérarchie arborescente, ce qui permet aux développeurs d'accéder aux éléments de la page, de les modifier et d'ajouter de nouveaux éléments dynamiquement à l'aide de JavaScript.

### Structure du DOM

Le DOM est une représentation en mémoire de la structure de la page web. Chaque élément HTML de la page, tel que `<div>`, `<p>`, `<h1>`, etc., est représenté par un objet dans le DOM. Ces objets sont organisés dans une hiérarchie arborescente, où chaque élément est un nœud dans l'arbre.

Par exemple, considérons le code HTML suivant :
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="conteneur">
        <h1>Bienvenue sur mon site web</h1>
        <p>Ceci est un paragraphe.</p>
    </div>
</body>
</html>
```
Dans le DOM, chaque balise HTML est représentée par un objet. Par exemple, la balise `<div>` est représentée par un objet de type `HTMLDivElement`, et la balise `<h1>` est représentée par un objet de type `HTMLHeadingElement`. Ces objets sont connectés les uns aux autres selon leur relation parent-enfant, comme illustré ci-dessous :
```
document (HTMLDocument)
└─── <html> (HTMLElement)
    ├─── <head> (HTMLHeadElement)
    │   ├─── <meta>
    │   ├─── <meta>
    │   └─── <title>
    └─── <body> (HTMLBodyElement)
        └─── <div id="conteneur"> (HTMLDivElement)
            ├─── <h1> (HTMLHeadingElement)
            └─── <p> (HTMLParagraphElement)
```

### Manipulation du DOM avec JavaScript

JavaScript permet de manipuler le contenu et la structure de la page en accédant aux éléments du DOM et en modifiant leurs propriétés et leurs attributs. Voici quelques opérations courantes de manipulation du DOM avec JavaScript :

- Sélectionner des éléments du DOM à l'aide de méthodes telles que `document.getElementById()`, `document.querySelector()`, etc.
- Modifier le contenu des éléments en modifiant leurs propriétés `innerHTML`, `textContent`, etc.
- Ajouter, supprimer ou modifier des attributs des éléments avec les méthodes `setAttribute()`, `removeAttribute()`, etc.
- Créer de nouveaux éléments HTML avec `document.createElement()` et les ajouter à la page avec les méthodes `appendChild()`, `insertBefore()`, etc.

Voici un exemple simple de manipulation du DOM avec JavaScript :
```js
// Sélectionner l'élément avec l'ID "conteneur"
let conteneur = document.getElementById('conteneur');

// Modifier le contenu de l'élément
conteneur.innerHTML = '<h2>Nouveau titre</h2>';

// Créer un nouvel élément <p>
let nouveauParagraphe = document.createElement('p');
nouveauParagraphe.textContent = 'Ceci est un nouveau paragraphe.';

// Ajouter le nouvel élément à l'élément avec l'ID "conteneur"
conteneur.appendChild(nouveauParagraphe);

```

En combinant JavaScript avec le DOM, les développeurs peuvent créer des expériences web interactives et dynamiques en manipulant la structure et le contenu de la page en réponse aux actions des utilisateurs ou aux événements de la page.

## Écouteurs d'événements en JavaScript

Les écouteurs d'événements en JavaScript sont des mécanismes permettant de détecter et de réagir à des événements sur les éléments du DOM, tels que les clics de souris, les pressions de touche, les chargements de page, etc. Ils permettent d'ajouter de l'interactivité aux pages web en déclenchant des actions en réponse aux actions des utilisateurs ou aux changements d'état de la page.

### Ajout d'un écouteur d'événement

Pour ajouter un écouteur d'événement à un élément du DOM, vous pouvez utiliser la méthode `addEventListener()`. Cette méthode prend deux arguments : le type d'événement à écouter et une fonction de rappel (ou "callback") à exécuter lorsque l'événement est déclenché.
```js
// Sélectionner l'élément à écouter
let monBouton = document.getElementById('monBouton');

// Ajouter un écouteur d'événement de clic
monBouton.addEventListener('click', function() {
    console.log('Le bouton a été cliqué !');
});
```
Dans cet exemple, lorsque le bouton avec l'ID "monBouton" est cliqué, la fonction de rappel est exécutée, affichant "Le bouton a été cliqué !" dans la console.

### Gestion des événements avec des fonctions nommées

Vous pouvez également utiliser des fonctions nommées comme gestionnaires d'événements à la place des fonctions anonymes. Cela permet de mieux organiser votre code et de réutiliser des fonctions pour différents écouteurs d'événements.
```js
// Définir une fonction de gestion d'événement nommée
function gestionnaireClic() {
    console.log('Le bouton a été cliqué !');
}

// Ajouter un écouteur d'événement de clic avec la fonction nommée
monBouton.addEventListener('click', gestionnaireClic);

```
### Suppression d'un écouteur d'événement

Pour supprimer un écouteur d'événement d'un élément du DOM, vous pouvez utiliser la méthode `removeEventListener()`. Cela peut être utile si vous souhaitez arrêter de surveiller les événements sur un élément après un certain point dans votre application.
```js
// Supprimer l'écouteur d'événement de clic
monBouton.removeEventListener('click', gestionnaireClic);

```

## Cookies en JavaScript

Les cookies sont de petits fichiers texte stockés dans le navigateur web de l'utilisateur. Ils sont utilisés pour stocker des données temporaires ou persistantes associées à un site web. En JavaScript, vous pouvez manipuler les cookies pour lire, écrire et supprimer des données stockées dans ces fichiers.

### Structure d'un cookie

Un cookie est une simple chaîne de caractères contenant des informations qui peuvent être lues par le navigateur lors des visites ultérieures sur un site web. Les cookies sont généralement constitués d'une ou plusieurs paires de clé-valeur, séparées par des points-virgules.

Exemple de structure d'un cookie :
```js
nomUtilisateur=John; expires=Fri, 15 Apr 2022 12:00:00 UTC; path=/
```
Dans cet exemple, le cookie contient une paire clé-valeur "nomUtilisateur=John" indiquant le nom d'utilisateur, ainsi que des options supplémentaires telles que la date d'expiration et le chemin du cookie.

### Manipulation des cookies en JavaScript

En JavaScript, vous pouvez utiliser l'API `document.cookie` pour manipuler les cookies côté client. Cette API vous permet de lire, écrire et supprimer des cookies à partir du navigateur de l'utilisateur.

#### Lecture d'un cookie


Pour lire le contenu d'un cookie, vous pouvez simplement accéder à la propriété `document.cookie`, qui contient une chaîne de caractères contenant tous les cookies associés au domaine et au chemin actuels.

```js
let tousLesCookies = document.cookie;
console.log(tousLesCookies);

```
#### Écriture d'un cookie

Pour écrire un nouveau cookie, vous pouvez définir une nouvelle valeur pour la propriété `document.cookie` dans le format `nom=valeur`. Vous pouvez également spécifier des options supplémentaires telles que la date d'expiration, le domaine et le chemin du cookie.

```js
document.cookie = "nomUtilisateur=John; expires=Fri, 15 Apr 2022 12:00:00 UTC; path=/";

```
En résumé, les cookies sont de simples chaînes de caractères stockées dans le navigateur web de l'utilisateur. Ils sont utilisés pour stocker des données temporaires ou persistantes associées à un site web. En JavaScript, vous pouvez utiliser l'API `document.cookie` pour manipuler les cookies côté client, y compris la lecture, l'écriture et la suppression de cookies.
```js

```



## Vite : Outil de développement rapide pour les applications web

Vite est un outil de développement rapide conçu pour les applications web modernes. Il vise à améliorer considérablement le processus de développement en fournissant des temps de compilation instantanés, une mise à jour à chaud rapide et une expérience de développement fluide.

### Principales caractéristiques de Vite

#### Compilation instantanée

Vite utilise la compilation à la volée (on-the-fly) pour compiler les fichiers sources lorsqu'ils sont demandés par le navigateur. Cela permet d'éliminer les longs temps d'attente de compilation lors du développement, offrant ainsi une réactivité instantanée lors de l'édition du code.

#### Mise à jour à chaud rapide

Vite prend en charge la mise à jour à chaud (hot module replacement) pour recharger automatiquement les modules modifiés dans le navigateur sans nécessiter de rechargement de page. Cela accélère considérablement le processus de développement en permettant de voir instantanément les modifications apportées au code.

#### Intégration transparente avec Vue.js et React

Vite est conçu pour fonctionner de manière transparente avec les frameworks populaires tels que Vue.js et React. Il fournit des configurations prédéfinies optimisées pour ces frameworks, permettant aux développeurs de démarrer rapidement et de se concentrer sur l'écriture de code.

#### Prise en charge native des modules ES modules

Vite prend en charge nativement les modules ECMAScript (ES modules), ce qui signifie que vous pouvez importer des fichiers JavaScript, CSS, JSON, etc. en tant que modules sans avoir besoin de transpiler votre code. Cela simplifie le processus de configuration et améliore les performances de développement.

### Utilisation de Vite

Pour démarrer un projet avec Vite, vous pouvez utiliser l'outil de ligne de commande Vite pour créer un nouveau projet à partir d'un modèle prédéfini. Une fois le projet créé, vous pouvez exécuter la commande de développement pour démarrer un serveur de développement local.

Exemple de création et de démarrage d'un projet avec Vite :

# Créer un nouveau projet Vue.js avec Vite
npm init vite@latest mon-projet
```bash
# Accéder au répertoire du projet
cd mon-projet

# Installer les dépendances
npm install

# Démarrer le serveur de développement
npm run dev

```

Une fois le serveur de développement lancé, vous pouvez accéder à votre application dans le navigateur à l'adresse `http://localhost:3000` par défaut. Toute modification apportée au code sera instantanément reflétée dans le navigateur grâce à la mise à jour à chaud de Vite.

En conclusion, Vite est un outil de développement rapide et efficace pour les applications web modernes. Il offre une expérience de développement fluide avec des temps de compilation instantanés, une mise à jour à chaud rapide et une intégration transparente avec les frameworks populaires tels que Vue.js et React. Si vous recherchez une solution de développement rapide et efficace, Vite est certainement un outil à considére


# JavaScript côté serveur Cf BackEnd

## NodeJs-npm- nvm ( A compléter)

## API REST

## fastify?

