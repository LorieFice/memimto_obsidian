## Frontend


## Backend

- Bien que `RetinaFace` soit très performant, ce modèle de détection de visages est lent : il prend en moyenne 5 secondes pour analyser une image sur le CPU

- Le [[Clustering]] rencontre un problème de paramétrage : Nous n'avons pas réussi à trouver des paramètres qui arrivent à bien regrouper les visages quelque soit l'album : 
Il faut souvent réadapter les paramètres du clustering pour qu'il colle mieux aux données.

- Malgrés de nombreuses heures à installer de nouvelles distributions Linux, et à tester des paramètres de docker pour que le container utilise le **GPU**, nous n'avons pas réussi à faire en sorte que `Tensorflow` et `DeepFace` (qui dépend de `Tensorflow`) utilisent l'accélération matérielle.

Cependant, voici quelques [[7 Pistes d'amélioration]]