# HTML (HyperText Markup Language)

HTML est l'acronyme de HyperText Markup Language. C'est le langage de balisage standard utilisé pour créer et structurer le contenu des pages web. HTML définit la structure de base d'une page web en utilisant des éléments balisés.

# **1.Principes Fondamentaux**

- **Balises et Éléments** : HTML utilise des balises pour délimiter différentes parties du contenu d'une page web. Les balises sont généralement composées d'un élément ouvert `<balise>` et d'un élément fermé `</balise>`. Par exemple, `<p>` est une balise ouvrante pour un paragraphe, et `</p>` est la balise de fermeture correspondante.

- **Structure de la Page** : Une page HTML typique est structurée en plusieurs sections telles que `<head>`, `<body>`, et `<footer>`. La section `<head>` contient des métadonnées sur la page, tandis que la section `<body>` contient le contenu principal visible pour les utilisateurs.

# **2.Balise `<head>` et Balises Classiques**

La balise `<head>` est une section de l'en-tête d'une page HTML qui contient des métadonnées sur le document, telles que des informations sur son titre, son encodage, et des instructions pour les navigateurs web.

1. **`<meta>` : Métadonnées de la Page**
   - Utilisée pour spécifier des métadonnées qui ne sont pas affichées directement sur la page, mais qui fournissent des informations supplémentaires à des fins de référencement, de compatibilité ou de personnalisation. Par exemple :
     - `<meta charset="UTF-8">` : Définit l'encodage des caractères de la page.
     - `<meta name="description" content="Description de la page">` : Fournit une description de la page pour les moteurs de recherche.
     - `<meta name="keywords" content="mots-clés, pour, la, recherche">` : Spécifie des mots-clés pour les moteurs de recherche.

2. **`<title>` : Titre de la Page**
   - Définit le titre de la page qui s'affiche dans l'onglet du navigateur ou dans les résultats de recherche. Chaque page web devrait avoir une balise `<title>` unique. Par exemple :
     - `<title>Titre de la Page</title>`

3. **`<link>` : Lier des Ressources Externes**
   - Utilisée pour lier des ressources externes telles que des feuilles de style CSS, des polices de caractères, des icônes de site, ou d'autres fichiers. Par exemple :
     - `<link rel="stylesheet" href="styles.css">` : Lie une feuille de style CSS externe à la page.

4. **`<script>` : Inclure des Scripts JavaScript**
   - Utilisée pour inclure des scripts JavaScript dans une page HTML. Par exemple :
     - `<script src="script.js"></script>` : Inclut un script externe à partir d'un fichier JavaScript.

5. **`<style>` : Définir des Styles CSS Intégrés**
   - Utilisée pour définir des styles CSS directement dans le document HTML. Par exemple :
     - `<style>
         body {
           font-family: Arial, sans-serif;
         }
       </style>` : Définit la police de caractères pour tout le corps de la page.

D'autres balises couramment trouvées dans la balise `<head>` incluent `<base>` pour spécifier l'URL de base pour les liens de la page et `<script>` pour inclure des scripts JavaScript.

# **3.Balise `<body>` et Balises Classiques**

La balise `<body>` est utilisée pour définir le contenu principal d'une page HTML, visible par les utilisateurs dans leur navigateur.

1. **`<div>` : Divisions de Contenu**
   - Utilisée comme conteneur générique pour regrouper des éléments et appliquer des styles CSS. Par exemple :
     ```html
     <div>
         Contenu ici
     </div>
     ```

2. **`<p>` : Paragraphes**
   - Définit un paragraphe de texte. Par exemple :
     ```html
     <p>Ceci est un paragraphe.</p>
     ```

3. **`<h1>`, `<h2>`, `<h3>`, etc. : Titres**
   - Définissent des titres de différents niveaux de hiérarchie. Par exemple :
     ```html
     <h1>Titre Principal</h1>
     <h2>Titre Secondaire</h2>
     ```

4. **`<ul>`, `<ol>`, `<li>` : Listes**
   - `<ul>` définit une liste non ordonnée, `<ol>` définit une liste ordonnée, et `<li>` définit un élément de liste. Par exemple :
     ```html
     <ul>
         <li>Élément 1</li>
         <li>Élément 2</li>
     </ul>
     ```

5. **`<a>` : Liens Hypertextes**
   - Définit un lien hypertexte vers une autre page web ou une ressource. Par exemple :
     ```html
     <a href="https://www.example.com">Lien vers Example</a>
     ```

6. **`<img>` : Images**
   - Utilisée pour afficher une image sur la page. Par exemple :
     ```html
     <img src="image.jpg" alt="Description de l'image">
     ```

7. **`<form>` : Formulaires**
   - Utilisée pour créer un formulaire interactif. Par exemple :
     ```html
     <form action="/submit" method="post">
         <!-- éléments du formulaire ici -->
     </form>
     ```

8. **`<input>` : Entrées de Formulaire**
   - Utilisée pour créer différents types d'entrées dans un formulaire. Par exemple :
     ```html
     <input type="text" name="nom" placeholder="Votre Nom">
     ```

D'autres balises couramment utilisées dans la balise `<body>` incluent `<table>` pour les tableaux et `<span>` pour les éléments en ligne.





## Exemple de Code HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Titre de la Page</title>
</head>
<body>
    <header>
        <h1>Titre Principal de la Page</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#accueil">Accueil</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    <main>
        <section id="accueil">
            <h2>Section Accueil</h2>
            <p>Bienvenue sur notre site web !</p>
        </section>
        <section id="services">
            <h2>Nos Services</h2>
            <ul>
                <li>Service 1</li>
                <li>Service 2</li>
                <li>Service 3</li>
            </ul>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Nom de l'Entreprise</p>
    </footer>
</body>
</html>


<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ma Page Web</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }
        nav ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
            background-color: #444;
            text-align: center;
        }
        nav ul li {
            display: inline;
        }
        nav ul li a {
            display: inline-block;
            padding: 10px 20px;
            color: #fff;
            text-decoration: none;
        }
        nav ul li a:hover {
            background-color: #666;
        }
        .container {
            width: 80%;
            margin: 20px auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px 0;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>
    <header>
        <h1>Mon Site Web</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#">Accueil</a></li>
            <li><a href="#">Services</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
    <div class="container">
        <h2>Contenu Principal</h2>
        <p>Ceci est le contenu principal de ma page web.</p>
    </div>
    <footer>
        <p>&copy; 2024 Mon Site Web</p>
    </footer>
</body>
</html>
