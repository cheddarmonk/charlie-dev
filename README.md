# Dev Lab CHARLIE/486 Story Card 

## User Story (Story Points = med👕) 

## Table of Contents

1. Goals
2. Critera
3. Angular
   

**As a** user of your hello-node app

**I want** to interact with the app: type and respond. 

**So That** my app does something a little more

## Comments/Discussion
- use node.js + express.js + angular.js

## Test/Acceptance Criteria/Rubric (how do you know when you are done) 

- [x] navigate to a URL: _______ (heroku): 0 | 5 | 10
- [x] app has a  link back to ghyt repo w/target: 0 | 5 | 10
- [x] file directory and naming, ghyt link to heroku: 0 | 5 | 10 
- [x] readme: explain some about angular...how user types in input and where that data goes from there, use code hightlight syntax in markdown: 0 | 5 | 10 
- [x] code quality: logical, readable, functional: functional = loads user json data, changes input data; updates a file on the server0 | 5 | 10  

## Angular
This segment is focused on the home page where we typed in our name. We can see in the index file that the base request from the server is handled by dishing out angular.html. Its here we can begin to trace the data that we recieve on the browser end. 

Looking under the `<head> </head>` threads we can see other than the title a bunch of src links that lead to angular, jquery, and bootstrap for sources. 

`<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>`

This line pulls in Angular for us to use in our HTML. 

Under the body tag we see this `<body ng-app="hi-angular">` This Names program that we see down on lines 33-42 

 ```
    <script>
        window.app = angular.module('hi-angular', []);
        app.controller('MainController', function($scope, $http) {
            $scope.user = null;

            $http.get('/user')
                .then(response => {
                    console.log(response.data);
                    $scope.user = response.data;
                });

        });
    </script>
```
 
This script then pulls data from the `('/user')` response. If we look in the index.js we see that it will return the user.json file and also read the data within. 

```
{
    "name": "Han Solo",
    "car": "Millennium Falcon"
}
```

Now back to our angular.html file, if we look at lines 26 and 27 we will see these lines

```
 <h3 id="user-greeting">Hello There, {{ user.name }}!!</h3>
    <p id="user-car">Is this the {{ user.car }}? I did Kessell run in under 12 Parsecs in this!</p>
```
Notice the  `{{user.name}}` & `{{user.car}}` and notice in our .json file the header info is `"name"` and `"car"`. Angular takes the data (Han Solo) and turns it into an attribute value of an object, that object being **User** and its attributes **name** and **car**.

It gets displayed on the page for us to see. Well how do we interact with it??

Notice in line 25 of the angular.html we get this niftly little bit of code:

`<input ng-model="user.name">`

This creats the text area we see, allows us to type in it and activly change what the JSON program is reading and will asyncronously update the data live as we type!