# CSS (Cascading Style Sheets)

CSS (Cascading Style Sheets) est un langage de feuilles de style utilisé pour définir la présentation visuelle des documents HTML. Il permet de contrôler l'apparence et la mise en page des éléments HTML sur une page web.

## Cascade Style

La "Cascading" dans CSS fait référence à la cascade des styles qui se produit lorsqu'un élément sur une page web est ciblé par plusieurs règles de style différentes. Les règles de style sont appliquées dans un certain ordre et peuvent être écrasées ou surchargées par des règles plus spécifiques ou plus récentes.

La cascade des styles suit un ordre de priorité basé sur l'origine de la règle, la spécificité du sélecteur, et l'ordre de déclaration dans le fichier CSS. Les styles inline (définis directement sur les éléments HTML), les styles définis dans les balises `<style>` dans le `<head>` du document, et les styles définis dans des fichiers CSS externes sont appliqués dans cet ordre.

## Sélecteurs

Les sélecteurs CSS sont des motifs utilisés pour cibler les éléments HTML et leur appliquer des styles. Ils déterminent quels éléments seront stylisés par une règle CSS donnée.

### Sélecteurs de Base :
- Sélecteurs d'éléments : ciblent tous les éléments d'un type donné (par exemple, `p` cible tous les paragraphes).
- Sélecteurs de classe : ciblent tous les éléments qui ont une classe spécifique (par exemple, `.ma-classe` cible tous les éléments avec la classe "ma-classe").
- Sélecteurs d'identifiant : ciblent un élément spécifique avec un identifiant unique (par exemple, `#mon-id` cible l'élément avec l'ID "mon-id").

### Sélecteurs Combinés :
- Sélecteurs de descendant : ciblent un élément qui est descendant d'un autre élément (par exemple, `div p` cible tous les paragraphes qui sont descendants de div).

## Encapsulation

L'encapsulation en CSS fait référence à la pratique de regrouper des styles associés dans des blocs distincts et les appliquer sélectivement à des parties spécifiques de la page web. Cela aide à organiser et à maintenir le code CSS de manière efficace, en le rendant plus modulaire et réutilisable.

Les méthodes courantes d'encapsulation incluent l'utilisation de classes et d'identifiants pour cibler des éléments spécifiques, ainsi que la définition de règles de style dans des fichiers CSS distincts pour différents composants ou sections de la page.

## Marges et Rembourrages

### Modèle de boites : 
![[Pasted image 20240404175259.png]]


Les marges (`margin`) et les rembourrages (`padding`) sont des propriétés CSS qui contrôlent l'espace autour et à l'intérieur des éléments HTML, respectivement.

- Les marges définissent l'espace entre les bordures des éléments voisins.
- Les rembourrages définissent l'espace entre le bord de l'élément et son contenu interne.

```css
.ma-classe {
    margin: 10px; /* Applique une marge de 10 pixels autour de l'élément */
    padding: 5px; /* Applique un rembourrage de 5 pixels à l'intérieur de l'élément */
}
```


## **3.Les styles courant** 



### Police personnalisée

Vous pouvez spécifier une police personnalisée pour votre texte en utilisant la propriété CSS `font-family`. Voici un exemple avec une police Google Fonts appelée "Roboto" :

```html
<p style="font-family: 'Roboto', sans-serif;">Ceci est un texte en police Roboto.</p>
<p style="font-size: 18px;">Ceci est un texte avec une taille de police de 18 pixels.</p>
```
### Taille de police


La taille de police est spécifiée en pixels, ems, ou en pourcentage. Voici un exemple avec une taille de police de 18 pixels :
```html
<p style="font-size: 18px;">Ceci est un texte avec une taille de police de 18 pixels.</p>
```


### Gras et italique

Pour mettre en évidence du texte, vous pouvez utiliser les styles gras et italique. Voici un exemple avec du texte en gras et en italique :

```html
<p style="font-weight: bold; font-style: italic;">Ceci est un texte en gras et italique.</p>

```
## Modèles de couleur

Dans cette section, nous explorerons différents modèles de couleur couramment utilisés dans la conception graphique et le développement web.

### Modèle RVB (RGB)

Le modèle RVB (rouge, vert, bleu) est un modèle additif dans lequel les couleurs sont générées en mélangeant différentes quantités de rouge, de vert et de bleu. Voici un exemple de spécification de couleur RVB :

```css
color: rgb(255, 0, 0); /* Rouge pur */
```

### Modèle HEX (Hexadécimal)

Le modèle HEX utilise des valeurs hexadécimales pour représenter les couleurs. Chaque composante (rouge, vert, bleu) est représentée par une paire de chiffres hexadécimaux allant de 00 à FF. Voici un exemple de spécification de couleur HEX :



```html
color: #ff0000; /* Rouge pur */
```

Bref dautres modèles de description de couleur existe: Cf Cours AADA Traitement d'images par Pandore

## Unités de mesure

Dans cette section, nous examinerons différentes unités de mesure utilisées dans la conception web pour définir les dimensions, les marges, les paddings et d'autres propriétés CSS.

### Unités de longueur

Les unités de longueur sont utilisées pour définir la taille des éléments sur une page web.

- **Pixels (px)** : Une unité de mesure basée sur l'écran. Un pixel correspond généralement à un point sur l'écran.
- **Pourcentage (%)** : Une unité de mesure relative à une valeur parente. Par exemple, une largeur de 50% signifie que l'élément occupe la moitié de la largeur de son conteneur parent.
- **Em (em)** : Une unité de mesure relative à la taille de la police de l'élément. Un em correspond à la taille de la police de l'élément en cours.
- **Rem (rem)** : Une unité de mesure relative à la taille de la police de la racine (`<html>`) de la page. Cela rend les rem utiles pour maintenir une cohérence de taille sur toute la page.

### Unités de texte

Les unités de texte sont utilisées pour définir la taille de la police et d'autres propriétés de texte.

- **Pixels (px)** : Comme mentionné précédemment, un pixel est une unité de mesure basée sur l'écran.
- **Points (pt)** : Une unité de mesure utilisée principalement pour les impressions. Un point équivaut à 1/72e de pouce.
- **Pourcentage (%)** : Une fois de plus, les pourcentages peuvent être utilisés pour définir la taille de la police par rapport à la taille de la police de l'élément parent.
- **Em (em) et Rem (rem)** : Ces unités peuvent également être utilisées pour définir la taille de la police.

### Unités de couleur

Pour spécifier les couleurs dans le langage CSS, plusieurs formats sont disponibles :

- **Nom de couleur** : Les noms de couleur prédéfinis comme "red", "green", etc.
- **HEX** : Utilisation de valeurs hexadécimales pour représenter les couleurs.
- **RGB** : Utilisation des valeurs Rouge, Vert, Bleu pour définir une couleur.
- **HSL** : Utilisation de teinte, saturation, luminosité pour définir une couleur.

### Exemple d'utilisation

Voici un exemple d'utilisation de différentes unités de mesure dans du code CSS :

```css
.container {
    width: 100%;
    font-size: 16px;
    padding: 1em;
    margin-bottom: 20px;
    color: #333;
    background-color: rgba(255, 255, 255, 0.8);
}
```

## Positionnement des éléments

Dans cette section, nous examinerons les différentes techniques de positionnement des éléments sur une page web à l'aide de CSS.

### Position statique

Par défaut, les éléments HTML sont positionnés statiquement, ce qui signifie qu'ils sont affichés dans l'ordre dans lequel ils apparaissent dans le flux du document.

```css
.element {
    position: static;
}
```

### Position absolue

Avec un positionnement absolu, un élément est retiré du flux normal du document et positionné par rapport à son premier ancêtre positionné. Cela signifie que ses coordonnées sont par rapport à son parent positionné le plus proche.

```css
.element {
    position: absolute;
    top: 0;
    left: 0;
}
```


### Position fixe

Un élément avec un positionnement fixe est positionné par rapport à la fenêtre du navigateur, ce qui signifie qu'il reste fixe même lorsque l'utilisateur fait défiler la page.
```css
.element {
    position: fixed;
    top: 10px;
    right: 10px;
}

```

### Position collante

Lorsque vous utilisez un positionnement collant, un élément reste dans sa position dans le flux normal du document jusqu'à ce qu'il atteigne un certain point lors du défilement, puis il devient fixe.
```css
.element {
    position: sticky;
    top: 0;
}
```
### Z-index

La propriété `z-index` contrôle la pile de positionnement des éléments qui se chevauchent. Un élément avec un `z-index` plus élevé sera placé au-dessus des éléments avec un `z-index` inférieur.
```css

.element {
    position: relative;
    z-index: 10;
}
```


## Éléments flottants (float)

Les éléments flottants sont une technique de mise en page CSS couramment utilisée pour aligner les éléments côte à côte dans un conteneur.

### Flottement vers la gauche

Lorsque vous flottez un élément vers la gauche, il sera poussé vers la gauche du conteneur aussi loin que possible.

```css
.element {
    float: left;
}
```

**Effet sur le flux du document :** Lorsqu'un élément est flottant, les éléments suivants peuvent remonter à côté de lui, à condition qu'il y ait de la place disponible. Cela peut provoquer des problèmes de mise en page si les dimensions de l'élément flottant sont trop grandes ou si les éléments suivants ne sont pas correctement gérés.

**Clearing (`clear: both`) :** Pour éviter que les éléments suivants ne soient affectés par les éléments flottants précédents, il est souvent nécessaire d'utiliser la propriété `clear` pour les effacer. Par exemple, en ajoutant un élément avec `clear: both` après les éléments flottants, vous pouvez forcer le contenu à revenir en dessous des éléments flottants.

**Limitations :** Bien que le flottement soit souvent utilisé pour aligner des éléments côte à côte, il peut parfois entraîner des comportements inattendus et des problèmes de mise en page, en particulier dans les mises en page complexes. Pour cette raison, les techniques de mise en page modernes, telles que l'utilisation de flexbox et de CSS Grid, sont de plus en plus préférées pour créer des mises en page complexes et adaptatives.

En résumé, bien que la propriété `float` soit toujours utilisée dans certaines situations, elle est de moins en moins recommandée pour les mises en page complexes en raison de ses limitations et des problèmes qu'elle peut entraîner. Il est important de comprendre son fonctionnement et ses implications lors de son utilisation dans la conception de sites web.


## Flexbox

Les Flexbox, ou boîtes flexibles en français, sont une disposition CSS qui permet de créer des mises en page efficaces et flexibles. Elles offrent un contrôle puissant sur la distribution et l'alignement des éléments à l'intérieur d'un conteneur, ce qui les rend particulièrement utiles pour les interfaces utilisateur modernes et réactives.

### Fonctionnement

Dans un modèle de flexbox, un conteneur flex (ou "flex container") est créé autour des éléments que vous souhaitez organiser. Les enfants directs de ce conteneur deviennent des "éléments flexibles" (ou "flex items"), et peuvent être disposés et alignés selon diverses règles définies par les propriétés CSS.

### Propriétés principales

- **`display: flex;`** : Cette propriété est appliquée au conteneur flex pour activer le modèle de flexbox.

- **`flex-direction`** : Définit la direction principale des éléments flexibles dans le conteneur. Les valeurs courantes sont `row` (de gauche à droite), `row-reverse` (de droite à gauche), `column` (de haut en bas) et `column-reverse` (de bas en haut).

- **`justify-content`** : Contrôle l'alignement des éléments flexibles le long de l'axe principal (horizontalement pour `row` et `row-reverse`, verticalement pour `column` et `column-reverse`).

- **`align-items`** : Contrôle l'alignement des éléments flexibles le long de l'axe transversal (verticalement pour `row` et `row-reverse`, horizontalement pour `column` et `column-reverse`).

- **`flex-wrap`** : Détermine si les éléments flexibles doivent s'enrouler ou non sur plusieurs lignes en cas de manque d'espace dans le conteneur.

### Exemple d'utilisation

Voici un exemple simple de mise en page à l'aide de Flexbox :

```html
<div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
</div>
```
```css
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.item {
    width: 100px;
    height: 100px;
    background-color: #ccc;
}
```

### Justify-content

La propriété `justify-content` est utilisée pour aligner les éléments flexibles le long de l'axe principal du conteneur flex. Elle contrôle la distribution des éléments flexibles lorsqu'il y a de l'espace supplémentaire le long de cet axe. Voici une explication détaillée des différentes valeurs de `justify-content` :

- **`flex-start` (par défaut)** : Les éléments flexibles sont alignés au début de l'axe principal du conteneur.
    
- **`flex-end`** : Les éléments flexibles sont alignés à la fin de l'axe principal du conteneur.
    
- **`center`** : Les éléments flexibles sont centrés le long de l'axe principal du conteneur.
    
- **`space-between`** : Les éléments flexibles sont répartis de manière uniforme le long de l'axe principal du conteneur, avec un espace égal entre eux. Le premier élément est aligné au début du conteneur et le dernier élément est aligné à la fin.
    
- **`space-around`** : Les éléments flexibles sont répartis de manière uniforme le long de l'axe principal du conteneur, avec un espace égal autour d'eux. Cela signifie qu'il y a de l'espace égal à gauche et à droite de chaque élément, ainsi qu'entre eux.
    
- **`space-evenly`** : Les éléments flexibles sont répartis de manière uniforme le long de l'axe principal du conteneur, avec un espace égal autour d'eux, y compris à gauche et à droite du premier et du dernier élément.
### Flex-direction

La propriété `flex-direction` définit la direction principale dans laquelle les éléments flexibles sont disposés à l'intérieur du conteneur flex. Elle contrôle l'axe principal le long duquel les éléments sont alignés. Voici une explication détaillée des différentes valeurs de `flex-direction` :

- **`row` (par défaut)** : Les éléments flexibles sont disposés horizontalement de gauche à droite. Cela signifie que l'axe principal est l'axe horizontal.
    
- **`row-reverse`** : Les éléments flexibles sont disposés horizontalement de droite à gauche. L'ordre des éléments est inversé par rapport à `row`.
    
- **`column`** : Les éléments flexibles sont disposés verticalement de haut en bas. L'axe principal est désormais vertical.
    
- **`column-reverse`** : Les éléments flexibles sont disposés verticalement de bas en haut. L'ordre des éléments est inversé par rapport à `column`.


