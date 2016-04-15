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

### Exemplo 01 

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
Na função que representa o controller podemos ver o ```$scope``` sendo usado por meio de injeção de dependencias, ```$scope``` é objeto que contem o valor do model. Uma instancia desse objeto é disponibilizado para a **view**, cada contoller ou diretiva (chegaremos nisso)  possui seu ```$scope```.

### Exemplo 02 

Para treinarmos um pouco mais oque foi visto até agora, faremos validaremos um ```<form>``` com angular usando [boostrap](http://getbootstrap.com/) para deixar com um estilo melhor.  
Para iniciamos uma estrutura básica como usamos até agora, a única diferença é o import do boostrap.
```
<html lang="pt-br" data-ng-app="flisolApp"> 
<!-- exemplo02.html 02 -->
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>ui-router-example</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
  </head>
  <body data-ng-controller="IndexController"> 

  </body>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.5/angular.min.js"></script>
  <script>
    angular
    .module('flisolApp', [])
    .controller('IndexController', IndexController);
    
    IndexController.$inject = ['$scope']; 
    function IndexController($scope){

    };
  </script>
</html>
```
Em seguida dentro da tag ```body``` iniciaremos um form (simulando um cadastro de usúario), nesse momento é importante nos atentarmos ao nome declarado no form porque será importante nas próximas validações. 

```
<form name="formUsuario" data-ng-submit="salvarUsuario()" novalidate>
</form>
```
O atributo ```novalidate``` define que as validações padrões do HTML serão ignoradas.  
A diretiva de atributo ```ng-submit``` [(dococumentação oficial)](https://docs.angularjs.org/api/ng/directive/ngSubmit) espera uma função, essa função é executada quando acontece um ```submit``` dentro do form.   
Nesse momento podemos criar essa função no controller também.
```
IndexController.$inject = ['$scope']; 
function IndexController($scope){
  $scope.salvarUsuario = salvarUsuario;

  function salvarUsuario(){
  };
};
```  

```
<html lang="pt-br" data-ng-app="flisolApp"> 
<!-- exemplo02.html 02 -->
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>ui-router-example</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">

  </head>
  <body data-ng-controller="IndexController"> 
    <div class="container">
      <h1>Cadastro de usúario</h1>
      <!-- atributo novalidate faz o formulario ignorar as validações padrões do HTML  -->
      <form name="formUsuario" data-ng-submit="salvarUsuario()" novalidate> 
       
        <div class="col-xs-12 col-sm-6 col-md-6 col-lg-6">
          <div class="form-group" data-ng-class="{ 'has-error' : formUsuario.nome.$invalid && !formUsuario.nome.$pristine }">
            <label>Nome</label>
            <input type="text" name="nome" class="form-control" data-ng-model="usuario.nome" required>
            <p data-ng-if="formUsuario.nome.$invalid && !formUsuario.nome.$pristine" class="help-block">
              Seu nome é obrigatório.
            </p>
          </div>
        </div>
       
        <div class="col-xs-12 col-sm-6 col-md-6 col-lg-6">
          <div class="form-group" data-ng-class="{ 'has-error' : formUsuario.usuario.$invalid && !formUsuario.usuario.$pristine }">
            <label>Nome de usuario</label>
            <input type="text" name="usuario" class="form-control" data-ng-model="usuario.nomeUsuario" required>
            <p data-ng-if="formUsuario.usuario.$invalid && !formUsuario.usuario.$pristine" class="help-block">
              Nome de usuario é obrigatório.
            </p>
          </div>
        </div>
       
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 text-right">
          <input type="submit" class="btn btn-success" data-ng-disabled="formUsuario.$invalid" value="salvar">
        </div>
        
      </form>
    </div>
  </body>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.5/angular.min.js"></script>
  <script>
    angular
    .module('flisolApp', [])
    .controller('IndexController', IndexController);
    
    IndexController.$inject = ['$scope']; 
    function IndexController($scope){
      $scope.salvarUsuario = salvarUsuario;

      function salvarUsuario(){
        alert('Usuário: ' + $scope.usuario.nome + ' |  ' + $scope.usuario.nomeUsuario + ' salvo!');
      };
    };
  </script>
</html>
```

