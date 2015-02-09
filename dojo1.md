#dojo1

* Sailjs : http://sailsjs.org/
* Heroku app : https://www.heroku.com/

#Pre-requis :
* nodejs + npm cf : http://sailsjs.org/#/getStarted

#déroulement du dojo :

1 - Generation mood REST API with sailsjs
* add sails dependencie  : npm install sails -g
* create sails app :  sails generate new sails-api
* go in the app directory : cd sails-api
* update project dependencies : npm install
* create the mood api : sails generate api mood
* add fields in mood model : api/models/Mood.js

2 - Deploiement de notre API sur heroku app
* follow the guide : https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction

