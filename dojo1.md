#dojo1 Sails REST API on heroku app

* Sailjs : http://sailsjs.org/
* Heroku app : https://www.heroku.com/

##Pre-requis :
* nodejs + npm cf : http://sailsjs.org/#/getStarted
* Run this from your terminal:
* Please ensure that you have Ruby installed.
```
wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh
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

