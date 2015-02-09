#Sails REST API on heroku app

Sailjs : http://sailsjs.org/
Heroku app : https://www.heroku.com/

##Pre-requis :
* nodejs + npm cf : http://sailsjs.org/#/getStarted
* Run this from your terminal:
* Please ensure that you have Ruby installed.
```
wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh
```

### Heroku usage
* log to heroku
```
heroku login
```
* heroku help 
```
heroku help || heroku 'command' -h
```
* open an heroku app in the browser (in an heroku app directory) :
```
heroku open
```
* To see logs on heroku
```
heroku logs
```
* To restart dyno
```
heroku restart
``` 

##déroulement du dojo :

1 - Generation mood REST API with sailsjs
* add sails dependencie  : 
```
npm install sails -g
```
* create sails app :  
```
sails generate new barometre-sails-api && cd barometre-sails-api
```
* create Procfile with "web: node app.js"
* Add node version to package.json file :
```javascript
"engines": {
     "node": "0.10.35"
},
```
* create local git repository : 
```
git init && git add . && git commit -m 'Initial commit'
```
* create heroku app : 
```
heroku create purch-barometre
```
* Set the app environment to production: 
```
heroku config:set NODE_ENV=production
```
* Deploy it : 
```
git push heroku master
```
* create the mood api : 
```
sails generate api mood
```
* add fields in mood model : api/models/Mood.js ex :
```
attributes: {
    email: {
      type: 'string'
    },
    mood: {
      type: 'integer'
    }
}
  ```
* set migrate mode in config/models.js 
```
git add . && git commit -m 'Set migrate mode'
```
* deploy :  
```
git push heroku master
```

* open app :
```
heroku open
``` 

## Ajout persistence mongoDB
* Add mongoHQ addon on heroku :
```
heroku addons:add mongohq
```
* Add sails-mongo dependencie :
```
npm install sails-mongo --save
```

* Add heroku mongo connections in config/connections.js
```
productionMongoHqDb: {
     adapter: 'sails-mongo',
     url: process.env.MONGOHQ_URL
}
```

* Define productionMongoHqDb in config/env/production.js file

## Use Redis for the session and socket store
In order to share session data between multiple instances, we have to use some shared data store. Let's use Redis.

* Add the RedisToGo free add-on to the Heroku app: 
```
heroku addons:add redistogo
```

* Install the connect-redis npm module: `npm install connect-redis@1.4.5 --save-`. We specified the version here explicitly because 2.0.0 doesn't seem to work with the current version of Sails.

* Open package.json and change "connect-redis": "^1.4.5", to "connect-redis": "1.4.5" (just remove the ^).

* Run heroku config again and this time we need to pull some information out of the REDISTOGO_URL environment variable. We need to set various other variables on Heroku from pieces of this one.

* The url is structured like this: redis://database-name:long-password-here@url.to.the.database.com:port/

* Use that to set the REDIS_DB, REDIS_PASSWORD, REDIS_HOST and REDIS_PORT with heroku config:set VAR_NAME=value

* Copy the following into both config/sessions.js and config/sockets.js, within the export object.
```
adapter: 'redis',
  host: process.env.REDIS_HOST,
  port: process.env.REDIS_PORT,
  db: process.env.REDIS_DB,
  pass: process.env.REDIS_PASSWORD
```  

* Now so that we can still run our app locally in development, let's make our local environment use the memory store. Paste this into the export object in config/local.js
```
session: {
    adapter: 'memory'
  },

  sockets: {
    adapter: 'memory'
  }
```
* Note: I also had to install sails-disk again manually in order for npm install to work: `npm install sails-disk --save`

Commit this, and deploy to Heroku again. `git add -A . && git commit -m 'Define session storage to redis' && git push heroku master`
 

