# Évolutivité et résilience : clusters, nœuds et partitions

**Elasticsearch** est conçu pour être toujours disponible et s'adapter à nos besoins. Il le fait en étant distribué par la nature. Nous pouvons ajouter des serveurs (nœuds) à un cluster pour augmenter la capacité et Elasticsearch distribue automatiquement notre charge de données et de requêtes sur tous les nœuds disponibles. Nul besoin de remanier notre application, Elasticsearch sait comment équilibrer les clusters multi-nœuds pour fournir une évolutivité et une haute disponibilité. Plus il y a de nœuds, mieux c'est.
<br><br>
Comment cela marche-t-il? Sous les couvertures, un index Elasticsearch n'est en réalité qu'un regroupement logique d'un ou plusieurs partitions physiques, où chaque partition est en fait un index autonome. En distribuant les documents d'un index sur plusieurs partitions et en répartissant ces partitions sur plusieurs nœuds, Elasticsearch peut assurer la redondance, qui à la fois protège contre les pannes matérielles et augmente la capacité de requête lorsque des nœuds sont ajoutés à un cluster. Au fur et à mesure que le cluster grandit (ou diminue), Elasticsearch migre automatiquement les partitions pour rééquilibrer le cluster.
<br><br>
Il existe deux types de partitions : les primaires et les répliques. Chaque document d'un index appartient à une partition principale. Un partition réplique est une copie d'un partition principal. Les répliques fournissent des copies redondantes de nos données pour nous protéger contre les pannes matérielles et augmenter la capacité de répondre aux demandes de lecture telles que la recherche ou la récupération d'un document.
<br><br>
Le nombre de partitions primaires dans un index est fixé au moment de la création d'un index, mais le nombre de partitions de réplique peut être modifié à tout moment, sans interrompre les opérations d'indexation ou de requête.

## ça dépend...
Il existe un certain nombre de considérations de performances et de compromis en ce qui concerne la taille des partitions et le nombre de partitions principales configurées pour un index. Plus il y a de partitions, plus il y a de frais généraux simplement pour maintenir ces index. Plus la taille de la partition est grande, plus il faut de temps pour déplacer les partitions lorsqu'Elasticsearch doit rééquilibrer un cluster.
<br><br>
L'interrogation d'un grand nombre de petites partitions accélère le traitement par partition, mais plus de requêtes signifie plus de surcharge, donc interroger un plus petit nombre de partitions plus grandes peut être plus rapide. 

Comme point de départ :

- Essayons de maintenir la taille moyenne des partitions entre quelques Go et quelques dizaines de Go. Pour les cas d'utilisation avec des données temporelles, il est courant de voir des partitions dans la plage de 20 Go à 40 Go.
- Évitons le problème des partitions de gazillion. Le nombre de partitions qu'un nœud peut contenir est proportionnel à l'espace de tas disponible. En règle générale, le nombre de partitions par Go d'espace de tas doit être inférieur à 20.
<br><br>
La meilleure façon de déterminer la configuration optimale pour notre cas d'utilisation consiste à effectuer des tests avec nos propres données et requêtes.

## En cas d'incident

Les nœuds d'un cluster ont besoin de bonnes connexions fiables entre eux. Pour fournir de meilleures connexions, nous colocalisons généralement les nœuds dans le même centre de données ou dans des centres de données à proximité. Cependant, pour maintenir une haute disponibilité, nous devons également éviter tout point de défaillance unique. En cas de panne majeure à un endroit, les serveurs d'un autre endroit doivent pouvoir prendre le relais. La réponse? Réplication inter-cluster (CCR : Cross-cluster replication).
<br><br>
CCR fournit un moyen de synchroniser automatiquement les index de notre cluster principal vers un cluster distant secondaire qui peut servir de sauvegarde à chaud. Si le cluster principal tombe en panne, le cluster secondaire peut prendre le relais. Nous pouvons également utiliser la CCR pour créer des clusters secondaires afin de répondre aux demandes de lecture à proximité géographique de nos utilisateurs.
<br><br>
La réplication entre clusters est active-passive. L'index sur le cluster principal est l'index leader actif et gère toutes les demandes d'écriture. Les index répliqués sur des clusters secondaires sont des suiveurs en lecture seule.

## Soins et alimentation
Comme pour tout système d'entreprise, nous avons besoin d'outils pour sécuriser, gérer et surveiller nos clusters Elasticsearch. Les fonctionnalités de sécurité, de surveillance et d'administration intégrées à Elasticsearch nous permettent d'utiliser **Kibana** comme centre de contrôle pour la gestion d'un cluster. Des fonctionnalités telles que les cumuls de données et la gestion du cycle de vie des index nous aident à gérer intelligemment nos données au fil du temps.

<br>

Source : [Elasticsearch Doc](https://www.elastic.co/guide/index.html)