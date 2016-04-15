# workshop-flisol2016MGA
Workshop de AngularJS no Flisol MGA 2016 - www.flisolm.ga

## Sobre angularJs
AngularJS é um framework baseado no modelo MVC mantido pela Google. Famoso por suas diretivas que aumentam as possibilidades no HTML e aplicações **"Single Page"** em conjunto com **API'S REST** assim dando mais poder ao **client-side**.

## Instalação 

>npm install angular

ou

>bower install angular

_Importe o script em seu index_  

NPM
```<script src="/node_modules/angular/angular.js"></script>```

bower  
```<script src="/bower_components/angular/angular.js"></script>```

## Primeiro app

Ao iniciarmos nosso primeiro app, criaremos um ```index.hml``` como de costume e então usaremos o atributo ```ng-app``` para declararmos nosso primeiro e principal modulo da aplicação. O atributo ```ng-app``` pode ser utlizado em qualquer elemento da pagina, nesse exemplo usaremos na tag ```<html>```.  
Como comentado na introdução o angular é baseado no padrão **MCV** (model, view, controller) porém com o seu **two way data binding** o angular ganhou a denominação de **MODEL VIEW WHATEVER (MVW ou MV*)**.  
Two way data binding cria uma ligação direta bidirecional entre o **model** e **controller** (que?), resumindo as alterações feitas no model pela **view** são vistas pelo **controller** e vise versa, isso ficará mais claro no nosso primeiro exemplo.  
```
<html lang="pt-br" data-ng-app="flisolApp"> <!-- declaração do modulo -->
<!-- exemplo01.html 01 -->
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>ui-router-example</title>
  </head>
  <body data-ng-controller="IndexController"> <!-- declaração do controller -->
    
    <h1>{{helloWord}}</h1> <!-- exibindo valor de um (model use {{}}) -->
    <input type="text" data-ng-model="helloWord">
 
  </body>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.5/angular.min.js"></script>
  <script>
    angular
    .module('flisolApp', [])
    .controller('IndexController', IndexController);
    
    IndexController.$inject = ['$scope']; 
    function IndexController($scope){
      $scope.helloWord = 'Flisol 2016';
    };
  </script>
</html>
``` 
No nosso primeiro exemplo podemos notar a criação do modulo usando a sintaxe ```angular.module('nomeString', [])``` e em seguida por meio de encadeamendo o controller ```.controller('nomeDoControllerString', funcaoQueRepresentaOcontroller)```.   
Na função que representa o controller podemos ver o ```$scope``` sendo usado por meio de injeção de dependencias, ```$scope``` é objeto que contem o valor do model. Uma instancia desse objeto e disponibilizado para a **view**, cada contoller ou diretiva (chegaremos nisso)  possui seu ```$scope```.