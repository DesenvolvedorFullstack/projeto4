Bower
===

Em nosso projeto até o momento temos somente a lib do AngularJS, porém podemos chegar a ter várias e várias libs
em um mesmo projeto, como podemos gerenciar isso?
Imagine se todas vez que uma lib sua for atualizada você ter que ir até o site da lib em específico, baixar e depois colocá-la em seu projeto,
seria muito trabalhoso né?
Por isso vamos começar a utilizar o Bower que é um gerenciador de componentes que pode conter HTML, CSS, Javascript, fonts ou arquivos de imagens.
O Bower é uma forma de otimizar o seu front-end, caso o mesmo possua dependência de várias bibliotecas.

Para instalar o bower em seu projeto é muito simples, basta excecutar o seguinte comando:

~~~text
npm install -g bower
~~~

Caso seja Linux utilize o sudo

~~~text
sudo npm install -g bower
~~~

Depois vá até a raiz do seu projeto e excecute:

~~~text
 bower init
~~~

Vão aparecer as seguintes opções:

~~~text
? name projeto4
? description Meu projeto com Bower
? main file main.js
? keywords
? authors Seu Nome
? license MIT
? homepage
? set currently installed components as dependencies? Yes
? add commonly ignored files to ignore list? No
? would you like to mark this package as private which prevents it from being accidentally published to the registry? No

{
  name: 'projeto4',
  description: 'Meu projeto com Bower',
  main: 'main.js',
  authors: [
    'Seu Nome'
  ],
  license: 'MIT',
  homepage: ''
}

? Looks good? Yes

~~~

No arquivo bower.json nós vamos colocar as libs que o bower vai gerenciar.
Como até o momento só estamos utilizando a lib do AngularJS então nosso bower.json
ficará assim:

~~~javascript
//projeto4/bower.json
{
  "name": "projeto4",
  "description": "Meu projeto com Bower",
  "main": "main.js",
  "authors": [
    "Seu Nome"
  ],
  "license": "MIT",
  "homepage": "",
  "dependencies": {
    "angular": "~1.4.0"
  }
}
~~~

Altere também o seu package.json para ficar da seguinte forma:

~~~javascript
//projeto4/package.json
{
  "name": "projeto4",
  "version": "1.0.0",
  "description": "Meu projeto com directive",
  "main": "main.js",
  "devDependencies": {
    "http-server": "^0.6.1",
    "bower": "^1.7.0"
  },
  "scripts": {
    "start": "http-server -a localhost -p 8000 -c-1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/github.com/seunome.git"
  },
  "author": "Seu nome",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/github.com/seunome/issues"
  },
  "homepage": "https://github.com/github.com/seunome#readme"
}

~~~

Agora execute o comando:

~~~text
bower install
~~~

O resultado será mais ou menos esse:

~~~text
bower angular#~1.4.0            cached https://github.com/angular/bower-angular.git#1.4.10
bower angular#~1.4.0          validate 1.4.10 against https://github.com/angular/bower-angular.git#~1.4.0
bower angular#~1.4.0           install angular#1.4.10

angular#1.4.10 bower_components/angular
~~~

Repare que o bower já baixou a biblioteca do AngularJS, ou seja o arquivo angular.min.js agora está dentro da pasta bower_components.
Agora você pode acessar a lib do AngularJS pelo seguinte caminho:

~~~text
projeto4/bower_components/angular/angular.min.js
~~~

Agora você pode apagar a basta lib do seu projeto3 e modificar o arquivo index.html.
O index.html vai ficar da seguinte forma:

~~~html
<!-- projeto4/index.html -->
<!doctype html>
<html ng-app="Projeto4">
    <head>
        <title>Directives</title>
    </head>
    <body ng-controller="MinhaController">
        <pessoa ng-model="pessoa"></pessoa>
        <script src="bower_components/angular/angular.min.js"></script>
        <script src="main.js"></script>
        <script src="directives/pessoa.js"></script>
    </body>
</html>
~~~

Pronto! Agora você vai perceber que o sistema funciona da mesma forma, porém quando você precisar adicionar mais alguma
biblioteca será muito simples! Basta colocar no seu bower.json, algo que vamos ver no próximo exemplo.
Para baixar o exemplo do bower funcionando basta acessar [aqui](https://github.com/DesenvolvedorFullstack/projeto4).
