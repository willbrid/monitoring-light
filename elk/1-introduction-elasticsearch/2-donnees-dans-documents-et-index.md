# Données dans : documents et index

**Elasticsearch** est un magasin de documents distribué. Au lieu de stocker des informations sous forme de lignes de données en colonnes, **Elasticsearch** stocke des structures de données complexes qui ont été sérialisées en tant que documents JSON. Lorsque nous avons plusieurs nœuds Elasticsearch dans un cluster, les documents stockés sont distribués dans le cluster et sont accessibles immédiatement depuis n'importe quel nœud.
<br><br>
Lorsqu'un document est stocké, il est indexé et entièrement consultable en temps quasi réel, en 1 seconde. **Elasticsearch** utilise une structure de données appelée *index inversé* qui prend en charge des recherches en texte intégral très rapides. Un index inversé répertorie chaque mot unique qui apparaît dans n'importe quel document et identifie tous les documents dans lesquels chaque mot apparaît.
<br><br>
Un index peut être considéré comme une collection optimisée de documents et chaque document est une collection de champs, qui sont les paires clé-valeur qui contiennent nos données. Par défaut, **Elasticsearch** indexe toutes les données dans chaque champ et chaque champ indexé a une structure de données dédiée et optimisée. Par exemple, les champs de texte sont stockés dans des index inversés, et les champs numériques et géographiques sont stockés dans des arbres BKD. La possibilité d'utiliser les structures de données par champ pour assembler et renvoyer des résultats de recherche est ce qui rend **Elasticsearch** si rapide.
<br><br>
**Elasticsearch** a également la capacité d'être sans schéma, ce qui signifie que les documents peuvent être indexés sans spécifier explicitement comment gérer chacun des différents champs qui peuvent apparaître dans un document. Lorsque le mappage dynamique est activé, Elasticsearch détecte et ajoute automatiquement de nouveaux champs à l'index. Ce comportement par défaut facilite l'indexation et l'exploration de nos données. Commençons simplement à indexer les documents et Elasticsearch détectera et mappera les booléens, les valeurs à virgule flottante et entières, les dates et les chaînes aux types de données Elasticsearch appropriés.
<br><br>
En fin de compte, cependant, nous en savons plus sur vos données et sur la manière dont nous souhaitons les utiliser qu'Elasticsearch. Nous pouvons définir des règles pour contrôler le mappage dynamique et définir explicitement des mappages pour prendre le contrôle total de la façon dont les champs sont stockés et indexés.
<br><br>
Définir nos propres mappages nous permet de :

- Faire la distinction entre les champs de chaîne de texte intégral et les champs de chaîne de valeur exacte
- Effectuer une analyse de texte spécifique à la langue
- Optimiser les champs pour une correspondance partielle
- Utiliser des formats de date personnalisés
- Utiliser des types de données tels que **geo_point** et **geo_shape** qui ne peuvent pas être détectés automatiquement
<br>
Il est souvent utile d'indexer le même champ de différentes manières à des fins différentes. Par exemple, nous souhaiterons peut-être indexer un champ de chaîne à la fois en tant que champ de texte pour la recherche en texte intégral et en tant que champ de mot clé pour trier ou agréger nos données. Ou, nous pouvons choisir d'utiliser plusieurs analyseurs de langage pour traiter le contenu d'un champ de chaîne contenant une entrée utilisateur.
<br>
La chaîne d'analyse appliquée à un champ de texte intégral lors de l'indexation est également utilisée lors de la recherche. Lorsque nous interrogeons un champ de texte intégral, le texte de la requête subit la même analyse avant que les termes ne soient recherchés dans l'index.

<br>

Source : [Elasticsearch Doc](https://www.elastic.co/guide/index.html)