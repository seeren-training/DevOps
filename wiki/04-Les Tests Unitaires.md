# Les tests Unitaires

* 🔖 **Environnement**
* 🔖 **Source**
* 🔖 **Test**

___

## 📑 Environnement

Il nous faut un environnement de développement.

* 🔗 [vcode](https://code.visualstudio.com/)

Nous allons écrire un test unitaire en utilisant le langage JavaScript dans sa version 6+. Nous avons besoin d'installer un compiler (Babel), un framework de test et des librairies complémentaires (Mocha, Chai, Sinon) puis un couvreur de test (Coveralls). 

*La mise en place de cette stack technique demande une profonde connaissance de cet écosystème.*

* 🔗 [install](https://docs.npmjs.com/cli/install)

```bash
npm install @babel/cli @babel/core @babel/preset-env @babel/register babel-plugin-istanbul chai coveralls cross-env mocha mocha-lcov-reporter nyc sinon --save-dev
```
La commande install install des package dans le dossier `node_modules` et les inscrits dans le fichier `packag.json`. Si vous récupérez un package.json il possédant des dépandances il est possible de toutes les installer avec npm install sans arguments.

```bash
npm install
```

Certains packages demandent un fichier de configuration à la racine du projet.

**.babelrc**

```js
{
  "presets": [
    "@babel/preset-env"
  ],
  "env": {
    "test": {
      "plugins": [
        "istanbul"
      ]
    }
  }
}
```

**.nycrc**

```js
{
  "require": [
    "@babel/register"
  ],
  "reporter": [
    "lcov",
    "text"
  ],
  "sourceMap": false,
  "instrument": false
}
```

Pour pouvoir exécuter un test il faut renseigner dans les scripts du fichier `package.json` quel outil est utilisé, avec quelles options et le dossier de destination de nos tests.

**package.json**

```json
"scripts": {
  "test": "cross-env NODE_ENV=test mocha --require @babel/register --recursive test/unit"
}
```

Pour pouvoir éxécuter un test il faut éxécuter le script test

```bash
npm test
```

___

👨🏻‍💻 Manipulation

Le Scrum master met en place la stack de test, la pousse et les membres d'équipes synchronisent leur contenu. Attention au **gitignore**! Il est évident que vous ne voulez pas associer à votre projet l'ensemble du code soruce téléchargé.

___

## 📑 Source

 Nous allons écrire une classe qui sera le sujet du test. N'ayant pas encore de base en programmation, prenons ce motif comme une introduction aux prochaines semaines nous permettant de mettre en pratique cette thématique.

**src/calculette.js**

```js
export class Calculette {

    additionne (operande1, operande2) {
        return operande1 + operande2;
    }

}
```

___

👨🏻‍💻 Manipulation

Ecrire une classe dans le dossier `src`.

___


## 📑 Test

Nous allons écrire un premier test pour cette classe

**test/unit/calculette.spec.js**

```js
import { describe, it } from 'mocha';
import { assert } from 'chai';

import { Calculette } from '../../src/calculette';

describe('Calculette', () => {

    const calculette = new Calculette();

    describe('additionne', () => {
        it('Return first argument plus second argument', () => 
            assert.equal(2, calculette.additionne(1,1))
        );
    });

});
```

Exécuter le test

```bash
npm test
```

Pour se rapprocher des tests automatisés nous avons mis en palce un envrionnement, écrit une source et son tests associé.
___

👨🏻‍💻 Manipulation


Ecrire le test associé à une source dans le dossier `test/unit`.

___

## 📑 Couverture

Un test peut ne pas couvrir un code source de manière suffisante, nous allons ajouter une méthode à notre source et observer sa couverture de code.

**src/calculette.js**

```js
//...
soustrait (operande1, operande2) {
    return operande1 - operande2;
}
//...
```

Pour avoir un rapport concernant la couverture de code nous avons les packages suffisant et allons ajouter un script pour l'obtenir.

**package.json**

```json
"scripts": {
  "test": "cross-env NODE_ENV=test mocha --require @babel/register --recursive test/unit",
  "coverage": "cross-env NODE_ENV=test nyc mocha --recursive test/unit"
}
```

La propriété test est un mot clef ayant un traitement particulier, pour lancer un autre script il faut ajouter run avant le nom du script.

Créer un rapport de couverture

```bash
npm run coverage
```

Nous pouvons observer que le code source n'est testé qu'à 50%. La couverture apporte une information importante sur l'efficacité d'un test.

___

👨🏻‍💻 Manipulation

Générer un rapport de couverture.

___

La prochaine étape consiste à automatiser le *passing* des tests en automatisant leur éxécution avec un outil d'intégration continue.