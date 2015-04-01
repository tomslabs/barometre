#Webapp creation consuming REST API created in dojo1

What we will use in this dojo :
* Nodejs : https://nodejs.org/
* Yeoman (Skeleton generator) : http://yeoman.io/
* Grunt (NodeJS task manager) : http://gruntjs.com/
* Bower (Frontend dependencies manager) : http://bower.io/
* Bootstrap (Twitter frontend framework) : http://getbootstrap.com/
* Sass (css Pre-Processing language) : http://sass-lang.com/
* jQuery (Javascript library) https://jquery.com/

##Pre-requis : 
* nodejs + npm 
* Yeoman : npm install -g yo
* webapp generator : npm install -g generator-webapp

###Generate webapp skeleton
```
yo webapp
```

* More info about webapp-generator from yeoman team : https://github.com/yeoman/generator-webapp

###First browse generate webapp :
```
grunt serve
```

###REST API to consume
https://purch-barometre.herokuapp.com/mood

###Create Mood submission form
```
<form action="https://purch-barometre.herokuapp.com/mood" method="POST">
    <div class="form-group">
        <label for="email-input">Adresse email</label>
        <input name="email" type="email" class="form-control" id="email-input" placeholder="Entre ton email">
    </div>
    <div class="form-group">
        <label for="mood-input">Humeur</label>
        <input name="mood" type="integer" id="mood-input" placeholder="4">
        <p class="help-block">Entre ton humeur de 0 à 5.</p>
    </div>
    <button type="submit" class="btn btn-default" onclick="submitMood">Submit</button>
</form>
```

###Create Mood list table
```
<table class="table table-striped table-responsive">
    <thead>
      <th>Email</th>
      <th>Humeur</th>
      <th>Date</th>
    </thead>
    <tbody>

    </tbody>
</table>
```

###Create JavaScript Code to post and reload mood from API
```
var updateMoods = function () {
    $.ajax({
        url: 'https://purch-barometre.herokuapp.com/mood'
    }).done(function(data) {
        var $table = $('.table tbody');
        $table.empty();
        data.forEach(function(elem) {
            var date = moment(elem.createdAt);
            $table.append('<tr><td>' + elem.email + '</td><td>' + elem.mood + '</td><td>' + date.format('YYYY-MM-DD HH:mm:SS') + '</td></tr>');
        });
    });
};
```
