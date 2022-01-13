# <u>Table des matières </u>
**[1. Projet](#projet)**
  * [1.1. Sujet](#sujet)
  * [1.2. Introduction](#introduction)
  * [1.3. Technologies](#technologies)
  * [1.4. Utilisation de MongoDB dans notre projet](#utilisation-de-mongodb-dans-notre-projet)
  * [1.5. Mise en place de MongoDB](#mise-en-place-de-mongodb)
  * [1.6. Fonctionnalités avancées](#fonctionnalités-avancées)
      * [1.6.1. MongoDB plutot que SQL](#mongodb-plutot-que-sql)
      * [1.6.2. BigData](#bigdata)
      * [1.6.3. Stockage de fichiers dans notre projet](#stockage-de-fichiers-dans-notre-projet)
      * [1.6.4. Utilisation des requêtes Géospaciales](#utilisation-des-requêtes-géospaciales-httpsdocsmongodbcommanualgeospatial-queries)
      * [1.6.5. Utilisation de l'aggrégation](#utilisation-de-laggrégation)
**[2. TP - Requêtes](#tp---requêtes)**

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

Pour ce projet, nous avons décidé de faire une application qui sera installé dans les bornes des restaurants.<br/>
Elle permettra aux clients de se connecter grace à leur numéro de téléphone.<br/>
Avec ce système nous pourrons demander des informations de plus en plus ciblés en fonction du nombre de venu des clients dans les restaurants.<br/>
Chaque information ajouté leur créditera des points ainsi que chacune de leurs connections (Limité à une toute les 5h pour éviter les abus).<br/>
Ces points de fidélité permettront aux clients de recevoir des promotions. <br/><br/>

## Technologies

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/node.png?raw=true" alt="NodeJS" width="100"/>

Pour la partie developpement nous alors utiliser NodeJS pour la création de l'API Backend car notre groupe est familier avec cette technologie.

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/React.png?raw=true" alt="React" width="100"/>

Concernant le front, nous utiliserons Réact car tout comme pour le backend, nous sommes familier avec ce language et qu'il convient à notre volonté d'application pour des bornes.


## Utilisation de MongoDB dans notre projet

MongoDB est un SGBD non relationnel orienté document.

Nous avons décidé de l'utiliser pour ce projet car il correspond parfaitement à nos besoins.

MongoDB associe simplicité d'utilisation lors du développement, facilité de mise a l'échelle lors de l'évolution de notre application et performance pour la gestion de BigData ce qui le rend parfait pour notre projet. (voir : https://docs.mongodb.com/manual/)


Nous avons décidé d'utiliser Atlas pour stocker la bdd et Compass pour gérer la base car nous sommes tout les trois sur Windows et que nous l'avons déjà utilisé.



Pour la sécurité, nous avons mis en place une whitelist avec nos IPs pour sécuriser la connection à la base.

Nous avons du créer un utilisateur par personne pour se connecter à la BDD car nous ne pouvions pas nous connecter a plusieurs en simultané avec le même user.

## Mise en place de MongoDB

Tout d'abord, nous avons utilisé la comande :<br/>
> show dbs

qui nous a listé les différentes BDD.<br/>

Nous nous sommes ensuite connecté a la base avec :<br/>
> use Restaurants

Puis nous avons créé deux collections, une Restaurants et une Clients.


Creation d'une collection Restaurants :

![projetCreateCollectionRestaurant](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionRestaurant.png?raw=true)

Voici ensuite le retour de mongoDB une fois les données des restaurants insérés :

![CreateCollectionRestaurantResponse](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionRestaurantResponse.png?raw=true)


Nous avons donc également créé une collection Clients :

![projetCreateCollectionClient](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionClient.png?raw=true)

Cette commande permet d'inserer plusieurs clients dans la collection Clients et créé la collection si elle n'existe pas.

Cela nous a retourné :

![projetCreateCollectionClientResponse](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionClientResponse.png?raw=true)


Nous avons par la suite manipulé la base de donnée avec les commandes suivantes pour nous familiariser avec MongoDB :


- Voir la base complète ou une partie

> db.Restaurants.find({ condition })

- Limiter le nombre de retour

> .limit()

- Avoir différentes informations sur la requete dont le temps d'execution

> .explain()

- Affiche le résultat bien formaté 

> .pretty()

- Inserer un/des enregistrements

> .insertOne({document})

> .insertMany([{document1},{document2},{ document3}….{ documentn}])

- Modifier un enregistrement

> .update()

- Supprimer un enregistrement

> .deleteOne()


Il existe énormement d'autres commandes que nous avons pu utiliser ainsi que des variantes tel que le .deleteMany() pour supprimer plusieurs enregistrement. Le site https://geekflare.com/fr/mongodb-queries-examples/ répertorie les commandes essentiels.

### Fonctionnalités avancées

Les fonctionnalités avancées de MongoDB seront un avantage car elles vont permettre d'effectuer des analyses très poussés des données sur les restaurants et clients.

Elles permettront de faire du ciblage ainsi que des modifications dans les restaurants afin d'augmenter le nombre de clients et de développer les restaurants.

#### MongoDB plutot que SQL

Contrairement à SQL, MongoDB n'est pas un système relationnel. Cela veut dire que les données sont stoqués dans des documents et ne respecte pas les contraintes d'unicité des données.

Une même donnée peut être stocké à de multiples reprises.

Dans la Base SQL les Clé primaires et secondaires permettent de créer des liens entre les différentes tables et donc de s'assurer que les données sont uniques. (https://sql.sh/cours/create-table/primary-key)

En MongoDB, les données possèdes également une clé unique ("_id" : ObjectId("5197c6b453cce2ec3a743811")) mais elle ne sert pas à contruire des relations comme en SQL. Elle permet d'identifier de manière unique les données. (https://askcodez.com/lid-de-la-collection-de-longueur-dans-mongodb.html)


La gestion des données dans des documents en format BSON vas nous être très pratique car cela nous permettra d'ajouter des informations supplémentaires sur les clients sans avoir à modifier les structures de la base comme il faudrait le faire en SQL.

Nous pourrons donc ajouter des données supplémentaires concernant les clients en fonction de nos besoins très facilement.

#### BigData

Enormément de domaines se sont spécialisés dans la gestion d'énormes quantitées de données (BigData) tel que la recherche scientifique, la politique, la communication, la médecine, la météorologie, l'écologie, la finance, le commerce, etc. (https://www.futura-sciences.com/tech/definitions/informatique-big-data-15028/)

Les données sont des richesses qui servent dans tout les domaines et surtout en marqueting pour le ciblage des clients potentiels. 

MongoDB fait parti des SGBD adaptés à la gestion d'énormes quantités de données car il implémente un système de stockage considéré comme plus performant que le SQL pour l'analyse de données en masse. Ce qui le rend très intéréssant pour l'utilisation principale des BigData qui correspond à l'analyse des données.

Une alternative qui est beaucoup revenu lors de mes recherches est Hadoop. 

Hadoop est une solution opensource faisant parti du projet Apache. Il offre un espace de stockage massif prenant en charge tous les types de données. Il possède une immense puissance de traitement et également permet de s'occuper d'une quantité de taches virtuellement illimité cependant nous avons décidé d'utiliser MongoDB. (https://www.lebigdata.fr/hadoop)


Cela est parfait car notre projet vise à stocker des quantitées de données énormes sur les clients a des but de statistiques.

Nous aurons également besoin de traiter très rapidement les informations des clients lors de leurs connexion (à l'aide de leur numéro de téléphone).

C'est pourquoi, afin d'accélérer les requetes, nous allons utiliser les l'indexage. Et utiliser la commande .explain() afin d'améliorer la vitesse d'execution de nos requêtes.

Concretement l'indexage correspond a créer un tableau trié avec uniquement des informations voulues qui pointent vers des documents de la BDD.

Grâce à ça, au lieu de parcourir tout les documents un a un, nous pourrons alors parcourir directement le tableau contenant les téléphones des clients afin de retrouver le documents contenant toutes les informations du client. Cela fera un gain de performance énorme pour nos requetes.

<img src="https://cdn.sanity.io/images/kjg6yd05/production/d6bdb08bc7645392d99b3a26a8cd0ad84efdcdc6-750x500.jpg?w=3840&fit=clip" alt="Tableau index" width="550"/>

#### Stockage de fichiers dans notre projet

Il existe différentes façons de stocker des documents dans une bdd mongoDB.

Selon le type de documents, les façons de les stocker diffèrent également.

Des documents de plus de 16 MB peuvent être stocker à l'aide de GridFS. (voir doc : https://docs.mongodb.com/manual/core/gridfs/)
Concrètement gridFS permet de stocker les données d'un fichier volumineux dans plusieurs documents MongoDB.

Pour des images très petites encodés en Base64 ou documents de moins de 16 MB, nous pouvons les stocker directement en base en enregistrant la chaine dans la BDD en utilisant le type de données BinData. (https://www.mongodb.com/developer/how-to/storing-large-objects-and-files/)

Sinon pour les fichiers volumineux nous pouvons également les stockers sur un serveur et enregistrer leur chemin en BDD afin de pouvoir retrouver le document.

Notre application permettra de prendre une photo des clients fidèles. C'est pourquoi nous devrons utiliser du stockage d'images à l'aide de GridFS par la suite.

#### Utilisation des requêtes Géospaciales (https://docs.mongodb.com/manual/geospatial-queries/)

Les requêtes Géospaciales permettent de faire des analyses sur la locatisation géographique.

La structure des données GeoJson est très simple et permet de stocker très facilement des point Géographiques ou autres types de données.


Structure :

> champ: { type: GeoJSON type , coordinates: coordonnées }


A l'aide de mongoDB Chart, nous pouvons par exemple créer différents graphiques afin d'analyser nos données et de les visualiser.

Cela permet par la suite de faire différentes études par zone géographique par exemple. (https://docs.mongodb.com/charts/)

Nous pourons également utiliser les requetes Géospaciales afin d'étudier des intersections de surfaces.

Les requêtes Géospaciales peuvent être très poussées et permettent de faire une infinité de choses en utilisant des données Géographique.

Cela va nous servir à savoir si un restaurant est manquant dans une zone géographique pour par la suite cibler les endroit où il faudrait ouvrir des restaurants.
Nous pourrons également utiliser ces données afin de comparer les restaurants et comprendre pourquoi dans une même zone géographique un restaurant à beaucoup de clients par rapport aux autres.
Cela permet également de faire des statistiques graphiques pour faire des bilans annuels et ainsi visualiser le développement de la société dans le temps.

Pour montrer un exemple concret, nous allons effectuer une requète qui nous donnera tout les restaurants se situants dans une surface sphérique donné.

Avant tout nous devons utiliser un index de type "2dsphere" sur le champs "localisation" de notre collection restaurant.

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateIndex2dsphere.png?raw=true" alt="Index2dsphere"/>

Nous pouvons alors visualiser cet index sur atlas :

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateIndex2dsphere2.png?raw=true" alt="Index2dsphereAtlas"/>

Désormais, nous allons faire une requête qui vas nous retourner les restaurants se trouvants dans un rayons de 10km autour d'un opéra.
Pour cela nous devons créer un point géométrique avec les coordonnées de l'opéra.

Puis nous recherchons avec un .find() les restaurants qui se trouvent dans la sphère de centre "opera" et de rayon 10000m.
Nous voulons alors que cette requête nous retourne l'id du restaurant et son nom.

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetNearSphereResult1.png?raw=true" alt="requeteSphere1"/>

Nous pouvons donc voir que le restaurant "Lyon Restaurant" se trouve dans cette surface.

Nous allons désormais refaire cette même requête avec un rayons de 1000 km.

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetNearSphereResult2.png?raw=true" alt="requeteSphere2"/>

Nous pouvons voir que cette requête nous retourne quand à elle deux restaurants, Le restaurant de Roanne et celui de Lyon.

#### Utilisation de l'aggrégation

L'aggrégation est une opération qui permet de grouper les données de plusieurs documents afin de retourner un résultat.

L'aggregation peut être faite avec un enchainement de plusieurs étapes. MongoDB appelle ça la pipeline d'aggregation.

Dans notre projet, nous utiliserons l'aggrégation afin de regrouper toutes les données des clients par restaurants.

Nous pourons alors faire des études en ciblant précisement des restaurants.

Cela pourra même être utilisé avec les requêtes Géospaciales pour combiner les analyses Géographiques des restaurants et les données des clients.

Nous allons donc utiliser des requêtes comme celle-ci : 

![projetAggregateRequestWithResponse](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetAggregateRequestWithResponse.PNG?raw=true)

Cette requête nous permet donc de récupérer les noms et prénoms des clients étants allés dans le restaurant avec L'Id 1.
Comme nous pouvons le voir, cette requête nous retourne donc en résultat les noms et prénoms des clients concernés.

Désormais, nous allons combiner l'aggrégation avec les requêtes géospaciales.

![projectCombineGeoSWithAggregation](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projectCombineGeoSWithAggregation.png?raw=true)

Cette requête nous permet de récupérer la distance entre l'opéra et les restaurants grâce au paramètre 'distanceField:"distance.estimation"' dans la requête géospaciale.
Puis dans la pipeline, nous filtrons sur les restaurants la ville de Lyon préalablement filtré dans la requête géospaciale.

Nous executons alors l'aggrégation avec db.Restaurants.agrregate(pipeline) ce qui nous donne en résultat toutes les informations des restaurants de Lyon ainsi que leur distance avec l'opéra.

# TP - Requêtes


1. Ecrivez une requête MongoDB pour afficher tous les documents dans les restaurants de la collection 
 
![TP1](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP1.png?raw=true)

2. Ecrivez une requête MongoDB pour afficher les champs restaurant_id, name, borough et cuisine pour tous les documents de la collection restaurant.
 	
![TP2](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP2.png?raw=true)

3. Ecrivez une requête MongoDB pour afficher les champs restaurant_id, name, borough et cuisine, mais exclure le champ _id pour tous les documents de la collection restaurant. 
 
![TP3](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP3.png?raw=true)
 
4. Ecrivez une requête MongoDB pour afficher les champs restaurant_id, nom, arrondissement et code postal, mais excluez le champ _id pour tous les documents de la collection restaurant.
 
![TP4](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP4.png?raw=true)
 
5. Ecrivez une requête MongoDB pour afficher tous les restaurants qui sont dans l'arrondissement du Bronx. 
 
![TP5](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP5.png?raw=true)
 
6. Ecrivez une requête MongoDB pour afficher les 5 premiers restaurants qui se trouvent dans le quartier du Bronx. 
 
![TP6](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP6.png?raw=true)
 
7. Ecrivez une requête MongoDB pour afficher les 5 restaurants suivants après avoir sauté les 5 premiers qui sont dans le quartier du Bronx.
 
![TP7](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP7.png?raw=true)
 
8. Ecrivez une requête MongoDB pour trouver les restaurants qui ont obtenu un score supérieur à 90. 
 
![TP8](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP8.png?raw=true)
 
9. Ecrivez une requête MongoDB pour trouver les restaurants qui ont obtenu un score supérieur à 80 mais inférieur à 100. 
 
![TP9](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP9.png?raw=true)

10. Ecrivez une requête MongoDB pour trouver les restaurants qui se situent dans une latitude inférieure à -95,754168.

![TP10](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP10.png?raw=true)

11. Ecrivez une requête MongoDB pour trouver les restaurants qui ne préparent pas de cuisine américaine et dont la note est supérieure à 70 et la latitude inférieure à -65.754168

![TP11](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP11.png?raw=true)

12. Ecrivez une requête MongoDB pour trouver les restaurants qui ne préparent pas de cuisine américaine, qui ont obtenu une note supérieure à 70 et qui sont situés à une longitude inférieure à -65.754168.

Note : Faites cette requête sans utiliser l'opérateur $and. 
 
![TP12](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP12.png?raw=true)

13. Ecrivez une requête MongoDB pour trouver les restaurants qui ne préparent pas de cuisine 'américaine' et ont obtenu une note 'A' et qui n'appartiennent pas à l'arrondissement de Brooklyn. Le document doit être affiché en fonction de la cuisine par ordre décroissant. 
 
 ![TP13](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP13.png?raw=true)
 
14. Écrivez une requête MongoDB pour trouver l'identifiant du restaurant, le nom, l'arrondissement et la cuisine pour les restaurants qui contiennent 'Wil' dans les trois premières lettres de leur nom. 
 
 ![TP14](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP14.png?raw=true)

15. Écrivez une requête MongoDB pour trouver l'identifiant, le nom, l'arrondissement et la cuisine des restaurants dont le nom contient trois lettres 'ces'. 
 
 ![TP15](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP15.png?raw=true)

16. Ecrivez une requête MongoDB pour trouver l'Id, le nom, l'arrondissement et la cuisine des restaurants qui contiennent "Reg" comme trois lettres dans leur nom.
 
 ![TP16](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP16.png?raw=true)

17. Ecrivez une requête MongoDB pour trouver les restaurants qui appartiennent à l'arrondissement du Bronx et qui préparent des plats américains ou chinois.
  
 ![TP17](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP17.png?raw=true)

18. Ecrivez une requête MongoDB pour trouver l'Id, le nom, l'arrondissement et la cuisine des restaurants qui appartiennent à l'arrondissement de Staten Island ou Queens ou Bronx ou Brooklyn.
 
 ![TP18](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP18.png?raw=true)

19. Ecrivez une requête MongoDB pour trouver l'Id, le nom, l'arrondissement et la cuisine des restaurants qui n'appartiennent pas à l'arrondissement de Staten Island ou Queens ou Bronx ou Brooklyn.
 
 ![TP19](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP19.png?raw=true)

20. Ecrivez une requête MongoDB pour trouver l'Id, le nom, l'arrondissement et la cuisine des restaurants qui ont obtenu un score inférieur à 10.
 
 ![TP20](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP20.png?raw=true)

21. Ecrivez une requête MongoDB pour trouver l'identifiant, le nom, l'arrondissement et la cuisine des restaurants qui ont préparé des plats autres que "américains" et "chinois" ou dont le nom commence par la lettre "Wil". 
 
 ![TP21](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP21.png?raw=true)

22. Ecrivez une requête MongoDB pour trouver l'Id du restaurant, le nom et les notes pour les restaurants qui ont obtenu la note "A" et un score de 11 sur la date : ISODate "2014-08-11T00:00:00Z" parmi de nombreuses dates d'enquête... 
  
 ![TP22](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP22.png?raw=true)

23. Ecrivez une requête MongoDB pour trouver l'Id du restaurant, le nom et les notes pour les restaurants dont le 2ème élément du tableau des notes contient la note "A" et le score 9 à la date ISOD "2014-08-11T00:00:00Z". 
 
 ![TP23](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP23.png?raw=true)

24. Ecrivez une requête MongoDB pour trouver l'identifiant du restaurant, le nom, l'adresse et l'emplacement géographique des restaurants pour lesquels le deuxième élément du tableau coord contient une valeur supérieure à 42 et inférieure à 52... 
 
 ![TP24](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP24.png?raw=true)

25. Ecrivez une requête MongoDB pour classer le nom des restaurants dans l'ordre croissant avec toutes les colonnes.
 
 ![TP25](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP25.png?raw=true)

26. Ecrivez une requête MongoDB pour classer le nom des restaurants en ordre décroissant avec toutes les colonnes. 
 
 ![TP26](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP26.png?raw=true)

27. Ecrivez une requête MongoDB pour classer le nom de la cuisine par ordre croissant et pour cette même cuisine, l'arrondissement doit être classé par ordre décroissant. 
 
 ![TP27](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP27.png?raw=true)

28. Ecrivez une requête MongoDB pour savoir si toutes les adresses contiennent la rue ou pas.

 
29. Ecrivez une requête MongoDB qui sélectionnera tous les documents de la collection restaurants où la valeur du champ coord est Double. 
 
 ![TP29](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP29.png?raw=true)

30. Ecrivez une requête MongoDB qui sélectionnera l'Id, le nom et les notes des restaurants qui renvoient 0 comme reste après avoir divisé le score par 7. 
  
 ![TP30](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP30.png?raw=true)

31. Écrivez une requête MongoDB pour trouver le nom du restaurant, l'arrondissement, la longitude, l'attitude et la cuisine pour les restaurants dont le nom contient trois lettres 'mon'. 
 
![TP31](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP31.png?raw=true)

32. Écrivez une requête MongoDB pour trouver le nom du restaurant, le quartier, la longitude, la latitude et la cuisine des restaurants dont le nom contient trois lettres "Mad". 
 
![TP32](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/TP32.png?raw=true)

