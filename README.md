# MongoDB-ISITECH

Nous avons décidé d'utiliser Atlas pour stocker la bdd et Compass pour gérer la base car nous sommes tout les trois sur Windows et que nous l'avons déjà utilisé.

## Commandes de bases utiles :

//Voir les bdds de mongoDB :
show dbs
//Connexion a la bdd
use Restaurants
//Voir la base complète :
db.Restaurants.find()
//Limiter le nombre de retour
.limit()
//Avoir différentes informations sur la requete dont le temps d'execution
.explain()
//Affiche le résultat bien formaté 
.pretty()

## Questions cours :

- Pourquoi utiliser MongoDB dans ce projet ?
1. Pour sa simplicité d'utilisation lors du developpement (https://docs.mongodb.com/manual/)
2. Pour sa facilité de mise a l'échelle lors de l'évolution de notre application (https://docs.mongodb.com/manual/)
3. Pour ses performances. 
Nous n'avons pas de conversion de données a faire car MongoDB est une base de fichier Json.

- En quoi les fonctionnalités avancées de MongoDB peuvent-elles être un avantage ?

- Est-il possible de stocker des documents dans la BDD ?

- Quelle est la différence entre la "clé primaire" de mongodb et du language sql ?

- Quel domaine se spécialise dans la gestion d'énormes quantités de données ? MongoDB fait-il parti des SGBDs adaptés ? Citez une alternative et présentez la brièvement.

# Projet

## Notes :

Nous avons utilisé Atlas et mis en place une whitelist avec nos IPs pour sécuriser la connection à la base.
Nous avons du créer un utilisateur par personne pour se connecter à la BDD car nous ne pouvions pas nous connecter a plusieurs en simultané avec le même user.
