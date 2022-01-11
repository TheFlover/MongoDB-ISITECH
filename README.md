# MongoDB-ISITECH

## TP - Requêtes


# Projet

## Sujet

Une chaine de restaurants souhaite récupérer des données clients afin de capitaliser
sur un flux de personnes sans cesse grandissant 
(plusieurs dizaine de milliers de clients par semaine dans toute la France).<br/>

Fournissez un projet d'application centré sur un stockage des données avec Mongo DB. <br/>

Le projet dans son ensemble ne sera pas forcément terminé cette semaine,
en revanche toutes les interactions avec la base de données doivent être documentées et 
testées. Et toutes les questions posées devront être traitées.<br/>

## Introduction

Nous avons décidé d'utiliser Atlas pour stocker la bdd et Compass pour gérer la base car nous sommes tout les trois sur Windows et que nous l'avons déjà utilisé.<br/>
<br/>
Pour la sécurité, nous avons mis en place une whitelist avec nos IPs pour sécuriser la connection à la base.<br/>
Nous avons du créer un utilisateur par personne pour se connecter à la BDD car nous ne pouvions pas nous connecter a plusieurs en simultané avec le même user.<br/>

## MongoDB

Nous avons décidé d'utiliser MongoDB pour ce projet car il correspond parfaitement à nos besoins.<br/>
MongoDB associe simplicité d'utilisation lors du développement, facilité de mise a l'échelle lors de l'évolution de notre application et performance pour la gestion de BigData ce qui le rend parfait pour notre projet. (voir : https://docs.mongodb.com/manual/)

### Mise en place de MongoDB

Nous avons utilisé certaines commandes afin de nous connecter a la base et de la manipuler.<br/><br/>

Voici une liste des commandes de base que nous avons utilisé :<br/>

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

### Comparatif SQL/MongoDB

Contrairement à SQL, MongoDB n'est pas un système relationnel. Cela veut dire que les données sont stoqués dans des documents et ne respecte pas les contraintes d'unicité des données.<br/>
Une même donnée peut être stocké à de multiples reprises.<br/>
Dans la Base SQL les Clé primaires et secondaires permettent de créer des liens entre les différentes tables et donc de s'assurer que les données sont uniques. (https://sql.sh/cours/create-table/primary-key)<br/>
En MongoDB, les données possèdes également une clé unique ("_id" : ObjectId("5197c6b453cce2ec3a743811")) mais elle ne sert pas à contruire des relations comme en SQL. Il permet d'identifier de manière unique les données. (https://askcodez.com/lid-de-la-collection-de-longueur-dans-mongodb.html)<br/>

### BigData

Enormément de domaines se sont spécialisés dans la gestion d'énormes quantitées de données (BigData) tel que la recherche scientifique, la politique, la communication, la médecine, la météorologie, l'écologie, la finance, le commerce, etc. (https://www.futura-sciences.com/tech/definitions/informatique-big-data-15028/)<br/>
Les données sont des richesses qui servent dans tout les domaines et surtout en marqueting pour le ciblage des clients potentiels. <br/>
MongoDB fait parti des SGBD adaptés à la gestion d'énormes quantités de données car il implémente un système de stockage considéré comme plus performant que le SQL pour l'analyse de données en masse. Ce qui le rend très intéréssant pour l'utilisation principale des BigData qui correspond à l'analyse des données.<br/>
Une alternative qui est beaucoup revenu lors de mes recherches est Hadoop. <br/>
Hadoop est une solution opensource faisant parti du projet Apache. Il offre un espace de stockage massif prenant en charge tous les types de données. Il possède une immense puissance de traitement et également permet de s'occuper d'une quantité de taches virtuellement illimité cependant nous avons décidé d'utiliser MongoDB. (https://www.lebigdata.fr/hadoop)

### Stockage de fichiers

Il existe différentes façons de stocker des documents dans une bdd mongoDB.<br/>
Selon le type de documents, les façons de les stocker diffèrent également.<br/>
Des documents de plus de 16 MB peuvent être stocker à l'aide de GridFS. (voir doc : https://docs.mongodb.com/manual/core/gridfs/)<br/>
Pour des images très petites encodés en Base64 ou documents de moins de 16 MB, nous pouvons les stocker directement en base en enregistrant la chaine dans la BDD en utilisant le type de données BinData. (https://www.mongodb.com/developer/how-to/storing-large-objects-and-files/)<br/>
Sinon pour les fichiers volumineux nous pouvons également les stockers sur un serveur et enregistrer leur chemin en BDD afin de pouvoir retrouver le document.<br/>

### Fonctionnalités avancées

- En quoi les fonctionnalités avancées de MongoDB peuvent-elles être un avantage ?

### Requêtes Géospaciales (https://docs.mongodb.com/manual/geospatial-queries/) :

Les requêtes Géospaciales permettent de faire des analyses sur la locatisation géographique.<br/>
La structure des données GeoJson est très simple et permet de stocker très facilement des point Géographiques ou autres types de données.<br/>

Structure :<br/>
champ: { type: GeoJSON type , coordinates: coordonnées }<br/><br/>

A l'aide de mongoDB Chart, nous pouvons par exemple créer différents graphiques afin d'analyser nos données et de les visualiser.<br/>
Cela permet par la suite de faire différentes études par zone géographique par exemple. (https://docs.mongodb.com/charts/)<br/><br/>

Cela va nous servir à savoir si un restaurant est manquant dans une zone géographique pour par la suite cibler les endroit où il faudrait ouvrir des restaurants.
Nous pourrons également utiliser ces données afin de comparer les restaurants et comprendre pourquoi dans une même zone géographique un restaurant à beaucoup de clients par rapport aux autres.
Cela permet également de faire des statistiques graphiques pour faire des bilans annuels et ainsi visualiser le développement de la société dans le temps.

Exemple de requêtes Geospaciales pour illustrer (Avec screenshots)

### Aggrégation :

L'aggrégation est une opération qui permet de grouper les données de plusieurs documents afin de retourner un résultat.<br/><br/>

Dans notre projet, nous utiliserons l'aggrégation afin de regrouper toutes les données des clients par restaurants.<br/>
Nous pourons alors faire des études en ciblant précisement des restaurants.<br/>
Cela pourra même être utilisé avec les requêtes Géospaciales pour combiner les analyses Géographiques des restaurants et les données des clients.

- Tenter d'expliquer les traitements effectués à l'aide d'un schéma fonctionnel



- Requêtes natives :