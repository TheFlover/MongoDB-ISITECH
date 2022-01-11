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
Des documents de moins de 16 MB peuvent être stocker directement à l'aide de GridFS en utilisant le type de données BinData. (voir doc : https://docs.mongodb.com/manual/core/gridfs/)<br/>
Pour des images très petites encodés en Base64, nous pouvons les stocker directement en base en enregistrant la chaine dans la BDD. (https://www.mongodb.com/developer/how-to/storing-large-objects-and-files/)<br/>
Sinon pour les fichiers volumineux nous pouvons les stockers sur un serveur et enregistrer son chemin en BDD afin de pouvoir retrouver le document.<br/>


- Quelle est la différence entre la "clé primaire" de mongodb et du language sql ?

- Quel domaine se spécialise dans la gestion d'énormes quantités de données ? MongoDB fait-il parti des SGBDs adaptés ? Citez une alternative et présentez la brièvement.

# Projet

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
