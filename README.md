# workshop-flisol2016MGA
Workshop de AngularJS no Flisol MGA 2016 - www.flisolm.ga

## Sobre angularJs
AngularJS é um framework baseado no modelo MVC mantido pela Google. Famoso por suas diretivas que aumentam as possibilidades no HTML e aplicações **"Single Page"** em conjunto com **API'S REST**  usando , assim dando mais poder ao **client-side**.

## Instalação 

>npm install angular

ou

>bower install angular

Importe o script em seu index  
```<script src="/node_modules/angular/angular.js"></script>```

Usando bower  
```<script src="/bower_components/angular/angular.js"></script>```


## Primeiro app

Ao iniciarmos nosso primeiro app, criaremos um ```index.hml``` como de costume e então usaremos o atributo ```ng-app``` para declararmos nosso primeiro e principal modulo da aplicação. O atributo ```ng-app``` pode ser utlizado em qualquer elemento da pagina, nesse exemplo usaremos na tag ```<body>```

```
<html lang="pt-br">
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>ui-router-example</title>
  </head>
  <body data-ng-app="flisolApp">
  </body>
  
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.5/angular.min.js"></script>
  <script>
    angular
    .module('flisolApp', [])
    .controller('IndexController', IndexController);
    ​
    function IndexController(){
    	
    };
  </script>
</html>
``` 