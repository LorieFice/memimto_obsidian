##   Vue.js : Le Framework JavaScript Progressif

Vue.js est un framework JavaScript progressif utilisé pour construire des interfaces utilisateur modernes et réactives. Il se concentre sur la simplicité et la flexibilité, offrant des fonctionnalités puissantes pour le développement d'applications web front-end tout en étant facile à apprendre et à utiliser.

Pour lancer un projet Vue:
```bash
npm create vue@latest
```
### Principales caractéristiques de Vue.js

### Syntaxe déclarative

Vue.js utilise une syntaxe déclarative simple et intuitive pour définir l'interface utilisateur de votre application. Avec des concepts tels que les directives, les composants et la liaison de données, vous pouvez facilement créer des interfaces utilisateur réactives en décrivant simplement le comportement souhaité.

### Composants réutilisables

Vue.js encourage la composition d'interfaces utilisateur à l'aide de composants réutilisables. Les composants Vue sont des blocs autonomes de code qui encapsulent la logique et la présentation d'une partie de l'interface utilisateur. Ils peuvent être facilement réutilisés et combinés pour construire des interfaces complexes.

### Réactivité

Vue.js offre une liaison de données bidirectionnelle qui permet de synchroniser automatiquement les données du modèle avec l'interface utilisateur. Cela signifie que toute modification apportée aux données est immédiatement reflétée dans l'interface utilisateur, et vice versa, sans nécessiter de code boilerplate.

### Vue CLI

Vue CLI est l'interface en ligne de commande officielle pour le développement d'applications Vue.js. Il simplifie le processus de création et de configuration de nouveaux projets Vue, tout en offrant des fonctionnalités avancées telles que la gestion de l'état de l'application, la génération de composants et la construction de projets pour la production.

## Composants Vue.js

Les composants sont une partie essentielle de l'architecture de Vue.js. Ils permettent de diviser l'interface utilisateur en petits blocs autonomes et réutilisables, appelés composants, ce qui facilite la gestion et la maintenance des applications Vue.js. Les composants Vue.js sont des instances Vue avec des options spécifiques qui définissent la structure, le comportement et le style d'une partie de l'interface utilisateur.

### Création d'un composant Vue.js

Pour créer un composant Vue.js, vous pouvez utiliser l'option `components` dans une instance Vue ou enregistrer le composant globalement à l'aide de `Vue.component()`. Chaque composant peut avoir ses propres données, méthodes, hooks de cycle de vie et options de configuration.

Exemple de création d'un composant Vue.js :

```js
// Définition du composant
Vue.component('mon-composant', {
  template: '<div>{{ message }}</div>',
  data() {
    return {
      message: 'Bonjour depuis mon composant !'
    };
  }
});

```

Dans cet exemple, nous avons créé un composant Vue.js appelé `mon-composant`. Il contient une propriété `template` qui définit la structure HTML du composant et une propriété `data` qui définit les données initiales du composant.

### Utilisation d'un composant Vue.js

Une fois qu'un composant Vue.js est défini, vous pouvez l'utiliser dans d'autres parties de votre application en l'insérant dans le template d'une instance Vue ou d'un autre composant.

Exemple d'utilisation d'un composant Vue.js dans une instance Vue :
```js
var app = new Vue({
  el: '#app',
  template: '<mon-composant></mon-composant>'
});
```


Dans cet exemple, nous avons utilisé le composant `mon-composant` à l'intérieur de l'élément avec l'ID `#app`.

### Communication entre les composants

Les composants Vue.js peuvent communiquer entre eux en utilisant les props, les événements, et le système de gestion de l'état centralisé (comme Vuex). Les props permettent de passer des données d'un composant parent à un composant enfant, tandis que les événements permettent à un composant enfant d'émettre des signaux à un composant parent.

Exemple de passage de données via les props :

```js
// ParentComponent.vue
<template>
  <child-component :message="parentMessage"></child-component>
</template>
<script>
export default {
  data() {
    return {
      parentMessage: 'Message du parent'
    };
  }
};
</script>

// ChildComponent.vue
<template>
  <div>{{ message }}</div>
</template>
<script>
export default {
  props: ['message']
};
</script>

```
### Avantages des composants Vue.js

- **Réutilisabilité**: Les composants Vue.js permettent de réutiliser du code, ce qui favorise la modularité et la maintenance de l'application.
- **Isolation**: Chaque composant possède son propre état et sa propre logique, ce qui favorise l'isolation et la gestion indépendante.
- **Composabilité**: Les composants peuvent être combinés pour former des interfaces utilisateur complexes, offrant ainsi une grande flexibilité dans la construction de l'application.

En conclusion, les composants Vue.js sont des blocs de construction essentiels dans le développement d'applications Vue.js. Ils permettent de diviser l'interface utilisateur en petits blocs réutilisables, facilitant ainsi la construction, la gestion et la maintenance des applications front-end. En comprenant comment créer et utiliser des composants Vue.js, vous pouvez construire des applications web robustes, modulaires et réactives.


## Cycle de vie
![[Pasted image 20240405134355.png]]

On peut donc avoir pleins d'autres type de Methodes comme els Mounted les Update ou les Computeds




## Vue Router

VueRouter est un routeur officiellement pris en charge par Vue.js, conçu pour la navigation dans les applications Vue.js à page unique (SPA). Il permet de gérer la navigation entre différentes vues (ou composants) de manière fluide et réactive, en synchronisant l'état de l'URL avec le contenu affiché à l'écran. VueRouter offre une intégration transparente avec Vue.js, permettant aux développeurs de définir facilement des routes et de naviguer entre elles sans rechargement de page. Il offre également des fonctionnalités avancées telles que la gestion des paramètres d'URL, les routes imbriquées, les transitions d'animation et la navigation programmatique. Grâce à VueRouter, les développeurs peuvent créer des applications web complexes avec une navigation dynamique et une expérience utilisateur fluide.

![[Pasted image 20240405135627.png]]

On indique dans le main.js que l'on va utilisé Router

VueRouter fournie 
 outils principales qui sont **RouterLink** et **RouterView**

## Organisation d'un projet vue

![[Pasted image 20240405135939.png]]

- Dossier public pour les assets public
1. Dossier src pour l'appli:
	1.  Dossier asset: Pour les logos et le style : On a base.css pour les couleurs de bases et les couleurs définit qu'on choisit
		- Main.css qui permet de rajouter des couches de styles css correspondant aux parties de nos codes
	 2. Components: Contient tout les composants Vue en l'occurrence les views
	 3. Router qui contient un fichier js pour parametrer nos routes et les associés aux components
	 4. Le main.js
	  ![[Pasted image 20240405140527.png]]
		Il permet de monter l'app et la crée et de définir ce qu'on lui injecte nottament ici une api et des couleurs on lui précise aussi les librairies qu'il uttilise ici router et WaveUI principalement!




## Globalement un code vue ca ressemble à ca:

![[Pasted image 20240405140738.png]]
Une partie **template** avec les éléments 

Une partie **script** ou **script setup** selon la version de vue:

On y importe les composants qu'on a déja crée (Ici Toolbar)
Et on définit ce qu'on veut export c'est à dire les parties du composant qu'on crée 
Ici c'est donc des datas relatifs à cette vue soit stream,width etc, on y trouve aussi les méthods et les computes etc c'est gllobalement ici que se trouve toutes les fonctions et tout les données de notre objet
On y trouve aussi les props
![[Pasted image 20240405140935.png]]


