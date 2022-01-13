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

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/node.png?raw=true" alt="NodeJS" width="200"/>

Pour la partie developpement nous alors utiliser NodeJS pour la création de l'API Backend car notre groupe est familier avec cette technologie.

<img src="https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/React.png?raw=true" alt="React" width="200"/>

Concernant le front, nous utiliserons Réact car tout comme pour le backend, nous sommes familier avec ce language et qu'il convient à notre volonté d'application pour des bornes.


## Utilisation de MongoDB dans notre projet

Nous avons décidé d'utiliser MongoDB pour ce projet car il correspond parfaitement à nos besoins.<br/>
MongoDB associe simplicité d'utilisation lors du développement, facilité de mise a l'échelle lors de l'évolution de notre application et performance pour la gestion de BigData ce qui le rend parfait pour notre projet. (voir : https://docs.mongodb.com/manual/)<br/><br/>

Nous avons décidé d'utiliser Atlas pour stocker la bdd et Compass pour gérer la base car nous sommes tout les trois sur Windows et que nous l'avons déjà utilisé.<br/>
<br/>
Pour la sécurité, nous avons mis en place une whitelist avec nos IPs pour sécuriser la connection à la base.<br/>
Nous avons du créer un utilisateur par personne pour se connecter à la BDD car nous ne pouvions pas nous connecter a plusieurs en simultané avec le même user.<br/>

### Mise en place de MongoDB

Tout d'abord, nous avons utilisé la comande :<br/>
> show dbs

qui nous a listé les différentes BDD.<br/>

Nous nous sommes ensuite connecté a la base avec :<br/>
> use Restaurants

Puis nous avons créé deux collections.<br/>

Une collection Restaurants :<br/>
![projetCreateCollectionRestaurant](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionRestaurant.png?raw=true)<br/>
Qui nous a renvoyé :<br/>
![CreateCollectionRestaurantResponse](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionRestaurantResponse.png?raw=true)<br/>
<br/>
Et une collection Clients<br/>
![projetCreateCollectionClient](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionClient.png?raw=true)<br/>
Qui nous a renvoyé :<br/>
![projetCreateCollectionClientResponse](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetCreateCollectionClientResponse.png?raw=true)<br/>
<br/>

Nous avons par la suite manipulé la base de donnée avec les commandes suivantes pour nous familiariser avec MongoDB :<br/>

- Voir la base complète ou une partie<br/>
db.Restaurants.find({ condition })<br/>
- Limiter le nombre de retour<br/>
.limit()<br/>
- Avoir différentes informations sur la requete dont le temps d'execution<br/>
.explain()<br/>
- Affiche le résultat bien formaté <br/>
.pretty()<br/>
- Inserer un/des enregistrements<br/>
.insertOne({document})<br/>
.insertMany([{document1},{document2},{ document3}….{ documentn}])<br/>
- Modifier un enregistrement<br/>
.update()<br/>
- Supprimer un enregistrement<br/>
.deleteOne()<br/>

Il existe énormement d'autres commandes que nous avons pu utiliser ainsi que des variantes tel que le .deleteMany() pour supprimer plusieurs enregistrement. Le site https://geekflare.com/fr/mongodb-queries-examples/ répertorie les commandes essentiels.

### Fonctionnalités avancées

Les fonctionnalités avancées de MongoDB seront un avantage car elles vont permettre d'effectuer des analyses très poussés des données sur les restaurants et clients.<br/>
Elles permettront de faire du ciblage ainsi que des modifications dans les restaurants afin d'augmenter le nombre de clients et de développer les restaurants.<br/>

#### MongoDB plutot que SQL

Contrairement à SQL, MongoDB n'est pas un système relationnel. Cela veut dire que les données sont stoqués dans des documents et ne respecte pas les contraintes d'unicité des données.<br/>
Une même donnée peut être stocké à de multiples reprises.<br/>
Dans la Base SQL les Clé primaires et secondaires permettent de créer des liens entre les différentes tables et donc de s'assurer que les données sont uniques. (https://sql.sh/cours/create-table/primary-key)<br/>
En MongoDB, les données possèdes également une clé unique ("_id" : ObjectId("5197c6b453cce2ec3a743811")) mais elle ne sert pas à contruire des relations comme en SQL. Elle permet d'identifier de manière unique les données. (https://askcodez.com/lid-de-la-collection-de-longueur-dans-mongodb.html)<br/><br/>

La gestion des données dans des documents en format BSON vas nous être très pratique car cela nous permettra d'ajouter des informations supplémentaires sur les clients sans avoir à modifier les structures de la base comme il faudrait le faire en SQL.<br/>
Nous pourrons donc ajouter des données supplémentaires concernant les clients en fonction de nos besoins et très facilement.

#### BigData

Enormément de domaines se sont spécialisés dans la gestion d'énormes quantitées de données (BigData) tel que la recherche scientifique, la politique, la communication, la médecine, la météorologie, l'écologie, la finance, le commerce, etc. (https://www.futura-sciences.com/tech/definitions/informatique-big-data-15028/)<br/>
Les données sont des richesses qui servent dans tout les domaines et surtout en marqueting pour le ciblage des clients potentiels. <br/>
MongoDB fait parti des SGBD adaptés à la gestion d'énormes quantités de données car il implémente un système de stockage considéré comme plus performant que le SQL pour l'analyse de données en masse. Ce qui le rend très intéréssant pour l'utilisation principale des BigData qui correspond à l'analyse des données.<br/>
Une alternative qui est beaucoup revenu lors de mes recherches est Hadoop. <br/>
Hadoop est une solution opensource faisant parti du projet Apache. Il offre un espace de stockage massif prenant en charge tous les types de données. Il possède une immense puissance de traitement et également permet de s'occuper d'une quantité de taches virtuellement illimité cependant nous avons décidé d'utiliser MongoDB. (https://www.lebigdata.fr/hadoop)<br/><br/>

Cela est parfait car notre projet vise à stocker des quantitées de données énormes sur les clients a des but de statistiques.<br/>
Nous aurons également besoin de traiter très rapidement les informations des clients lors de leurs connexion (à l'aide de leur numéro de téléphone).<br/>
C'est pourquoi, afin d'accélérer les requetes, nous allons utiliser les l'indexage.<br/>
Concretement cela correspond a créer un tableau trié avec uniquement des informations voulues qui pointent vers des documents de la BDD.<br/>
Grâce à ça, au lieu de parcourir tout les documents un a un, nous pourrons alors parcourir directement le tableau contenant les téléphones des clients afin de retrouver le documents contenant toutes les informations du client. Cela fera un gain de performance énorme pour nos requetes.

![Tableau index](https://cdn.sanity.io/images/kjg6yd05/production/d6bdb08bc7645392d99b3a26a8cd0ad84efdcdc6-750x500.jpg?w=3840&fit=clip)

#### Stockage de fichiers dans notre projet

Il existe différentes façons de stocker des documents dans une bdd mongoDB.<br/>
Selon le type de documents, les façons de les stocker diffèrent également.<br/>
Des documents de plus de 16 MB peuvent être stocker à l'aide de GridFS. (voir doc : https://docs.mongodb.com/manual/core/gridfs/)<br/>
Pour des images très petites encodés en Base64 ou documents de moins de 16 MB, nous pouvons les stocker directement en base en enregistrant la chaine dans la BDD en utilisant le type de données BinData. (https://www.mongodb.com/developer/how-to/storing-large-objects-and-files/)<br/>
Sinon pour les fichiers volumineux nous pouvons également les stockers sur un serveur et enregistrer leur chemin en BDD afin de pouvoir retrouver le document.<br/>

Notre application permettra de prendre une photo des clients fidèles. C'est pourquoi nous devrons utiliser du stockage d'images à l'aide de GridFS.

#### Utilisation des requêtes Géospaciales (https://docs.mongodb.com/manual/geospatial-queries/)

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

#### Utilisation de l'aggrégation

L'aggrégation est une opération qui permet de grouper les données de plusieurs documents afin de retourner un résultat.<br/>

Dans notre projet, nous utiliserons l'aggrégation afin de regrouper toutes les données des clients par restaurants.<br/>
Nous pourons alors faire des études en ciblant précisement des restaurants.<br/>
Cela pourra même être utilisé avec les requêtes Géospaciales pour combiner les analyses Géographiques des restaurants et les données des clients.<br/>

Nous allons donc utiliser des requêtes comme celle-ci : <br/>
![projetAggregateRequestWithResponse](https://github.com/TheFlover/MongoDB-ISITECH/blob/main/Images/projetAggregateRequestWithResponse.PNG?raw=true)<br/>

Cette requête nous permet donc de récupérer les noms et prénoms des clients étants allés dans le restaurant avec L'Id 1.

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

