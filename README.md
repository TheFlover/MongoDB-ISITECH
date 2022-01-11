# MongoDB-ISITECH

## Commandes de bases utiles :

<br/> - Voir les bdds de mongoDB
<br/>show dbs
<br/> - Connexion a la bdd
<br/>use Restaurants
<br/> - Voir la base complète
<br/>db.Restaurants.find()
<br/> - Limiter le nombre de retour
<br/>.limit()
<br/> - Avoir différentes informations sur la requete dont le temps d'execution
<br/>.explain()
<br/> - Affiche le résultat bien formaté 
<br/>.pretty()

## Questions cours :

- Est-il possible de stocker des documents dans la BDD ?

Oui, il existe différentes façons de stocker des documents dans une bdd mongoDB.<br/>
Selon le type de documents, les façons de les stocker diffèrent également.<br/>
Des documents de plus de 16 MB peuvent être stocker à l'aide de GridFS. (voir doc : https://docs.mongodb.com/manual/core/gridfs/)<br/>
Pour des images très petites encodés en Base64 ou documents de moins de 16 MB, nous pouvons les stocker directement en base en enregistrant la chaine dans la BDD en utilisant le type de données BinData. (https://www.mongodb.com/developer/how-to/storing-large-objects-and-files/)<br/>
Sinon pour les fichiers volumineux nous pouvons également les stockers sur un serveur et enregistrer leur chemin en BDD afin de pouvoir retrouver le document.<br/>

- Quelle est la différence entre la "clé primaire" de mongodb et du language sql ?

Contrairement à SQL, MongoDB n'est pas un système relationnel. Cela veut dire que les données sont stoqués dans des documents et ne respecte pas les contraintes d'unicité des données.<br/>
Une même donnée peut être stocké à de multiples reprises.<br/>
Dans la Base SQL les Clé primaires et secondaires permettent de créer des liens entre les différentes tables et donc de s'assurer que les données sont uniques. (https://sql.sh/cours/create-table/primary-key)<br/>
En MongoDB, les données possèdes également une clé unique ("_id" : ObjectId("5197c6b453cce2ec3a743811")) mais elle ne sert pas à contruire des relations comme en SQL. Il permet d'identifier de manière unique les données. (https://askcodez.com/lid-de-la-collection-de-longueur-dans-mongodb.html)<br/>

- Quel domaine se spécialise dans la gestion d'énormes quantités de données ? MongoDB fait-il parti des SGBDs adaptés ? Citez une alternative et présentez la brièvement.

Enormément de domaines se sont spécialisés dans la gestion d'énormes quantitées de données (BigData) tel que la recherche scientifique, la politique, la communication, la médecine, la météorologie, l'écologie, la finance, le commerce, etc. (https://www.futura-sciences.com/tech/definitions/informatique-big-data-15028/)<br/>
Les données sont des richesses qui servent dans tout les domaines et surtout en marqueting pour le ciblage des clients potentiels. <br/>
Oui MongoDB fait parti des SGBD adaptés car il implémente un système de stockage considéré comme plus performant que le SQL pour l'analyse de données en masse. Ce qui le rend très intéréssant pour l'utilisation principale des BigData qui correspond à l'analyse des données.<br/>
Une alternative qui est beaucoup revenu lors de mes recherches est Hadoop. <br/>
Hadoop est une solution opensource faisant parti du projet Apache. Il offre un espace de stockage massif prenant en charge tous les types de données. Il possède une immense puissance de traitement et également permet de s'occuper d'une quantité de taches virtuellement illimité. (https://www.lebigdata.fr/hadoop)

# Projet

Une chaine de restaurant souhaite récupérer des données clients afin de capitaliser
sur un flux de personnes sans cesse grandissant 
(plusieurs dizaine de milliers de clients par semaine dans toute la France).<br/>

Fournissez un projet d'application centré sur un stockage des données avec Mongo DB. <br/>

Le projet dans son ensemble ne sera pas forcément terminé cette semaine,
en revanche toutes les interactions avec la base de données doivent être documentées et 
testées. Et toutes les questions posées devront être traitées.<br/>

## Notes :

Nous avons décidé d'utiliser Atlas pour stocker la bdd et Compass pour gérer la base car nous sommes tout les trois sur Windows et que nous l'avons déjà utilisé.<br/>
<br/>
Nous avons utilisé Atlas et mis en place une whitelist avec nos IPs pour sécuriser la connection à la base.<br/>
Nous avons du créer un utilisateur par personne pour se connecter à la BDD car nous ne pouvions pas nous connecter a plusieurs en simultané avec le même user.<br/>

## Questions projet :

- Pourquoi utiliser MongoDB dans ce projet ?
1. Pour sa simplicité d'utilisation lors du developpement (https://docs.mongodb.com/manual/)
2. Pour sa facilité de mise a l'échelle lors de l'évolution de notre application (https://docs.mongodb.com/manual/)
3. Pour ses performances. 
Nous n'avons pas de conversion de données a faire car MongoDB est une base de fichier Json.

- En quoi les fonctionnalités avancées de MongoDB peuvent-elles être un avantage ?

- Qu'est-ce que l'aggrégation ? Expliquer MongoDB Chart.

## Requêtes Géospaciales (https://docs.mongodb.com/manual/geospatial-queries/) :

- Quelle est l'utilité de telles requetes ? Discutez de la structure des données GeoJson

Les requêtes Géospaciales permettent de faire des analyses sur la locatisation géographique.<br/>
La structure des données GeoJson est très simple et permet de stocker très facilement des point Géographiques ou autres types de données.<br/><br/>

Structure :<br/>
champ: { type: GeoJSON type , coordinates: coordonnées }

- Illustrer avec un exemple (https://docs.mongodb.com/charts/)

A l'aide de mongoDB Chart, nous pouvons par exemplecréer différents graphiques afin d'analyser nos données et de les visualiser.

- Comment ce type de données peut intervenir dans le projet ? (https://docs.mongodb.com/charts/)

Dans notre projet, cela pourra permettre d'analyser les magasins les plus utilisés par les clients en fonction de leur lieu de résidence.<br/>
Cela peut concrètement permettre voir la distance parcouru que les clients font pour venir dans les restaurants.

- Exemple de requêtes Geospaciales pour illustrer (Avec screenshots)

## Aggrégation :

- Expliquer brièvement l'interêt de l'aggrégation

- Prévoir une application dans notre projet

- Tenter d'expliquer les traitements effectués à l'aide d'un schéma fonctionnel

- Requêtes natives :