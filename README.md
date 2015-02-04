# barometre de l'humeur d'équipe
Fil rouge qui donnera lieu à plusieurs dojo autour de ce dernier

#Idées de features
* Chaque utilisateurs peut voter une fois par jour
* Limiter ou non le nombre de vote par jour et par personne
* Gestion multigroupe
* Représenter l'humeur du jour sous la forme d'un thermomètre
* Avoir une vue calendrier (type niko calendar)
* Le vote se fait sur une échelle d'image (Smiley, Soleil, Panda)
* Avoir un système de notification qui nous invite à donneur notre humeur
* Une appli mobile
* Anonymisation des votes
* Envoi d'un message associé à son humeur si on a envi d'alerter nos collègues
* Stocker d'autres métriques afin de les comparer avec l'humeur (météo, traffic routier, etc)
* Pouvoir faire plusieurs votes dans la journée en fonction des évènements dans notre travail (coupler avec l'ide, la ligne de commande, etc)
* Faire un vote matin et soir afin d'avoir un chiffre plus représentatif
* Avoir un vrai nom de projet et un logo associé

#Technologie
* Séparation backend / frontend
* Approche Microservices (cela permet de multiplier les technos, exemple : service d'acquisition en nodejs, service de de récupération en java
* API REST
* Stockage des données dans mongodb
* Hébergement sur herokuapp
* Appli web en responsive design

#Définition d'un premier livrable
* Une page pour voter 1 fois / jour sur une echelle de valeur à définir
* 1 page pour visualiser l'humeur globale et un historique de l'humeur sous forme d'un tableau (les votes étant anonyme)
* Pas de système d'authentification, l'utilisateur dois uniqument indiquer son adresse email lors du vote

#Planning des dojos
1 - Déployer un simple service d'acquisition écrit en node js sur herokuapp
ou
Dojo 1 : Présentation d'un hello world sur herokuapp
Dojo 2 : Faire un service d'acquisition

#Idées de noms du projet
* HappinessTherapy
* ThermoBonheur
* TeamMetrics
