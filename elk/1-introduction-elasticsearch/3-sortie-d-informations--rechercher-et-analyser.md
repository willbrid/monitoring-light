# Sortie d'informations : rechercher et analyser

Bien que nous puissions utiliser **Elasticsearch** comme magasin de documents et récupérer des documents et leurs métadonnées, la véritable puissance réside dans la possibilité d'accéder facilement à la suite complète de fonctionnalités de recherche construites sur la bibliothèque du moteur de recherche **Apache Lucene**.
<br><br>
Elasticsearch fournit une API REST simple et cohérente pour gérer notre cluster, indexer et rechercher nos données. À des fins de test, nous pouvons facilement soumettre des demandes directement depuis la ligne de commande ou via la **Console Developpeur** dans **Kibana**. Depuis nos applications, nous pouvez utiliser le client Elasticsearch pour le langage de votre choix : Java, JavaScript, Go, .NET, PHP, Perl, Python ou Ruby.

## Recherche de nos données

Les API REST d'Elasticsearch prennent en charge les requêtes structurées, les requêtes en texte intégral et les requêtes complexes qui combinent les deux. Les requêtes structurées sont similaires aux types de requêtes que nous pouvons construire en SQL. Par exemple, nous pouvons rechercher les champs *sexe* et *âge* dans notre index des employés et trier les correspondances en fonction du champ *date_embauche*. Les requêtes de texte intégral trouvent tous les documents qui correspondent à la chaîne de requête et les renvoient triés par pertinence, c'est-à-dire leur degré de correspondance avec nos termes de recherche.
<br>
En plus de rechercher des termes individuels, nous pouvons effectuer des recherches d'expressions, des recherches de similarités et des recherches de préfixes, et obtenir des suggestions de saisie semi-automatique.
<br>
Nous avons des données géospatiales ou d'autres données numériques que nous souhaitons rechercher ? Elasticsearch indexe les données non textuelles dans des structures de données optimisées qui prennent en charge les requêtes géographiques et numériques hautes performances.
<br>
Nous pouvons accéder à toutes ces fonctionnalités de recherche à l'aide du langage de requête complet de style JSON d'Elasticsearch (Query DSL). Nous pouvons également créer des requêtes de type SQL pour rechercher et agréger des données de manière native dans Elasticsearch, et les pilotes JDBC et ODBC permettent à un large éventail d'applications tierces d'interagir avec Elasticsearch via SQL.

## Analyse de nos données

Les agrégations Elasticsearch nous permettent de créer des résumés complexes de nos données et d'avoir un aperçu des métriques, modèles et tendances clés. Au lieu de simplement trouver la proverbiale « aiguille dans une botte de foin », les agrégations nous permettent de répondre à des questions telles que :

- Combien y a-t-il d'aiguilles dans la botte de foin ?
- Quelle est la longueur moyenne des aiguilles ?
- Quelle est la longueur médiane des aiguilles, ventilée par fabricant ?
- Combien d'aiguilles ont été ajoutées à la botte de foin au cours de chacun des six derniers mois ?
<br>

Nous pouvons également utiliser des agrégations pour répondre à des questions plus subtiles, telles que :

- Quels sont vos fabricants d'aiguilles les plus populaires ?
- Y a-t-il des amas d'aiguilles inhabituels ou anormaux ?
<br>

Étant donné que les agrégations exploitent les mêmes structures de données que celles utilisées pour la recherche, elles sont également très rapides. Cela nous permet d'analyser et de visualiser nos données en temps réel. Nos rapports et tableaux de bord sont mis à jour à mesure que nos données changent afin que nous puissions prendre des mesures en fonction des dernières informations.
<br>
De plus, les agrégations fonctionnent parallèlement aux demandes de recherche. Nous pouvons rechercher des documents, filtrer les résultats et effectuer des analyses en même temps, sur les mêmes données, dans une seule requête. Et comme les agrégations sont calculées dans le contexte d'une recherche particulière, nous n'affichons pas seulement le nombre de toutes les aiguilles de taille 70, nous affichons également le nombre d'aiguilles de taille 70 qui correspondent aux critères de recherche de nos utilisateurs. Par exemple, toutes les aiguilles à broder antiadhésives de taille 70.

## Encore plus
Nous souhaitons automatiser l'analyse de nos données de séries chronologiques ? Nous pouvons utiliser les fonctionnalités d'apprentissage automatique pour créer des lignes de base précises du comportement normal de nos données et identifier les modèles anormaux. Avec le machine learning, nous pouvons détecter :

- Anomalies liées à des écarts temporels de valeurs, de comptages ou de fréquences
- Rareté statistique
- Comportements inhabituels pour un membre d'une population

Et la meilleure partie ? Nous pouvons le faire sans avoir à spécifier d'algorithmes, de modèles ou d'autres configurations liées à la science des données.

<br>

Source : [Elasticsearch Doc](https://www.elastic.co/guide/index.html)