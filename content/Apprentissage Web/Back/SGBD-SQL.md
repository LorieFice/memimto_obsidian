![[Pasted image 20240405160858.png]]
Voila l'exemple du code, on définit nos base de donnée et les méthodes 
  
SQLAlchemy est une bibliothèque Python populaire qui simplifie l'interaction avec les bases de données relationnelles dans les applications web. Elle offre une couche d'abstraction sur les bases de données SQL, permettant aux développeurs d'écrire du code Python plutôt que du SQL brut pour effectuer des opérations CRUD (Create, Read, Update, Delete) sur les données. SQLAlchemy prend en charge plusieurs dialectes de bases de données, ce qui signifie qu'elle peut être utilisée avec divers types de bases de données relationnelles telles que PostgreSQL, MySQL, SQLite, etc.

Dans l'exemple fourni, SQLAlchemy est utilisée avec Flask dans le cadre de la création d'une application web. La classe `User` est un modèle SQLAlchemy qui représente une table dans la base de données. Les colonnes de la table sont définies comme des attributs de classe dans la classe `User`, ce qui permet à SQLAlchemy de mapper ces colonnes aux attributs de l'objet Python lorsqu'il interagit avec la base de données.

## Les décorateurs python "@"
Les décorateurs Python sont des fonctions qui prennent une autre fonction comme argument et retournent une nouvelle fonction. Dans le contexte de Flask, les décorateurs sont couramment utilisés pour mapper des fonctions de vue aux routes URL de l'application. Par exemple, le décorateur `@app.route('/')` est utilisé pour mapper une fonction de vue à l'URL racine de l'application. Les décorateurs sont également utilisés dans SQLAlchemy pour définir des relations entre les modèles et pour créer des méthodes spéciales de requête comme c'est le cas avec `@classmethod`.
Voila l'exemple du code, on définit nos base de donnée et les méthodes 

  
SQLAlchemy est une bibliothèque Python populaire qui simplifie l'interaction avec les bases de données relationnelles dans les applications web. Elle offre une couche d'abstraction sur les bases de données SQL, permettant aux développeurs d'écrire du code Python plutôt que du SQL brut pour effectuer des opérations CRUD (Create, Read, Update, Delete) sur les données. SQLAlchemy prend en charge plusieurs dialectes de bases de données, ce qui signifie qu'elle peut être utilisée avec divers types de bases de données relationnelles telles que PostgreSQL, MySQL, SQLite, etc.

Dans l'exemple fourni, SQLAlchemy est utilisée avec Flask dans le cadre de la création d'une application web. La classe `User` est un modèle SQLAlchemy qui représente une table dans la base de données. Les colonnes de la table sont définies comme des attributs de classe dans la classe `User`, ce qui permet à SQLAlchemy de mapper ces colonnes aux attributs de l'objet Python lorsqu'il interagit avec la base de données.

## Les décorateurs python "@"
Les décorateurs Python sont des fonctions qui prennent une autre fonction comme argument et retournent une nouvelle fonction. Dans le contexte de Flask, les décorateurs sont couramment utilisés pour mapper des fonctions de vue aux routes URL de l'application. Par exemple, le décorateur `@app.route('/')` est utilisé pour mapper une fonction de vue à l'URL racine de l'application. Les décorateurs sont également utilisés dans SQLAlchemy pour définir des relations entre les modèles et pour créer des méthodes spéciales de requête comme c'est le cas avec `@classmethod`.