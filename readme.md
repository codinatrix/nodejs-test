## Node.js Hello World på Windows med Heroku

Se mitt exempel här:

https://github.com/codinatrix/nodejs-test

https://laylas-nodejs-test.herokuapp.com/

---


### Ladda ner och installera Node.js
http://nodejs.org/

### Och Heroku Toolbelt
https://toolbelt.heroku.com/windows

### Nu kan vi börja

Öppna en konsol och testa installation
```shell
$ node -v
v0.12.0
```

Skriva `node` för att öppna en Node.js konsol.

```shell
$ node
> console.log('Hello World');
Hello World
undefined
```
Den returnerar "undefined" för att console.log inte returnerar nånting.

Skapa en fil i din repository som heter **hello.js** med innehåll:

```
var express = require('express');
var app = express();

app.set('port', (process.env.PORT || 5000));
app.use(express.static(__dirname + '/public'));

app.get('/', function(request, response) {
  response.send('Hello World!');
});

app.listen(app.get('port'), function() {
  console.log("Node app is running at localhost:" + app.get('port'));
});
```

Skapa en fil som heter **package.json** i samma mapp, med innehåll:

```
{
  "name": "node-js-test",
  "version": "0.1.1",
  "description": "Node.js Hello World",
  "main": "hello.js",
  "scripts": {
    "start": "node hello.js"
  },
  "dependencies": {
    "express": "~4.9.x"
  },
  "engines": {
    "node": "0.10.x"
  }
}
```
Installera alla dependencies som är i **package.json** (i detta fall har vi express-modulen)

```shell
$ npm install
```

och commita till Git.

Starta servern på din dator (Avbryt med Ctrl + C)
```shell
$ node hello.js
```
Besök [http://localhost:5000/]

### Fixa Heroku för deployment
Om du inte har ett Heroku konto, skapa ett här: https://www.heroku.com/

I konsolen:

```shell
$ heroku login
```
och skriver din login och lösenord.

Skapa en Heroku app med
```shell
$ heroku create mitt-app-namn
```
Och en vanlig push för att deploya till Heroku
```shell
$ git push heroku master
```
Öppna appen i din webbläsare
```shell
$ heroku open
```

## Lite om IDE
En bra IDE för Javascript kostar pengar. De här är välrekommenderade:

###Cloud9
https://c9.io/

IDE i webbläsaren som körs i molnet. Ganska smidigt. Det finns en liten gratis plan och sen börjar priserna med $9 USD (75 kr) per månad.

###WebStorm
https://www.jetbrains.com/webstorm/

Från JetBrains, så du vet vad du kan förvänta om du har använt nånting annat från JetBrains. Den är användvänlig med avancerade funktioner, inklusiv automasierad Node.js installation, uppgradering, konfiguration och debugging. Den kostar €49 (467 kr) för personlig licens eller €99 (944 kr) för företagslicens.

###Atom
https://atom.io/

Atom är en text editor skapade av Github. Den är ingen IDE, men väldigt kraftfull med många smidiga funktioner och plugins.
