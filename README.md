# TDD Sandbox

Le TDD (Test Driven Development) a pour but d'écrire les tests avant d'écrire la fonction testée, et d'enrichir à la fois les tests et la fonction au fur et à mesure, en faisant bien attention que tous les tests écrits continuent à fonctionner lorsqu'on modifie la fonction.


_What is it ?_
Test Driven Development (TDD) is a process where you write your unit test first, watch it fail, and then implement the necessary code to the module you're creating until the test passes. That's it!

_How it should be done :_
- Unit tests should be specific and test particular components and algorithms of code you wish to test
- The data used in the testing should be static or variable, not subject to change from external API calls for example. A specific output should be expected
- After writing your unit tests and implementing the code for them; if they all pass, you're done!


## Mise en place de l'environnement

a. Créer un dossier TDDSandbox et l'ouvrir dans VSCode

b. Dans le terminal, initialiser le projet avec `npn init -y` (initialisation par défaut)

c. Installer Mocha, Chai : `npm install --save-dev mocha chai`

d. Dans le fichier `package.json`, vérifier qu'il y a bien `mocha` en script de test, sinon l'ajouter :
```
"scripts": {
  "test": "mocha"
}
```

e. Ignorer `node_modules` dans un `.gitignore`.

f. Créer un dossier `test` dans le dossier du projet.


Rappel : pour lancer les tests `npm test`
Sources : https://mochajs.org/#getting-started




## Exercice 1 : The Cube

Le but de cet exercice est de calculer différentes propriétés d'un cube.

### Etape 1 : 

Créer un dossier `cube` à la racine du projet et un fichier `geometrie.js` dans ce dossier.
Dans le dossier `test`, créer un autre dossier `cube` et un fichier `test_geometrie.js` dans ce dossier.

_C'est une bonne pratique de faire un miroir de l'architecture de l'app dans le dossier de test_


### Etape 2 : 

Dans le fichier `test_geometrie.js`, utiliser le squelette suivant :  

```
const geometrie = require(' _path_to_geometrie.js_ '); // require the file you want to test

describe('Géométrie cube', function () {
	it('should to something', function() { // change the name accordingly to what you want to test
		let response = ...; // call the function you want to test, with the params
		assert.equal(response, result) // what result do you expect?
	});
});

```

a. Et créer un premier test permettant de vérifier le calcul du périmètre d'un cube de côté 3, à l'aide de la fonction `perimetre(3)`.

b. Exécuter le test, il doit sortir une erreur (la fonction testée n'existe pas).


### Etape 3 : 

Dans le fichier `geometrie.js`, créer la fonction `perimetre(lgCote)`, qui prend en variable la longueur d'un côté `lgCote` et retourne le périmètre du cube.


Exécuter le test et vérifier qu'il passe.


### Etape 4 : 

a. Dans le fichier `test_geometrie.js`, créer un second test dans `describe`, qui permet de vérifier le calcul l'aire d'une face du cube de côté 3, à l'aide de la fonction `aireFace(3)`.

b. Exécuter le test, il doit retourner une erreur.

c. Dans le fichier `geometrie.js`, créer la fonction `aireFace(lgCote)`, qui prend en variable la longueur d'un côté `lgCote` et retourne l'aire d'une face du cube.

d. Exécuter le test et vérifier qu'il passe.


### Etape 5 : 

En répétant les mêmes étapes que l'étape 4, créer le test, puis la fonction permettant de calculer la surface d'un cube. Vous pouvez utiliser une fonction précédemment créée.


### Etape 6 : 

En répétant les mêmes étapes que l'étape 4, créer le test, puis la fonction permettant de calculer le volume d'un cube.


### Etape 7 : 

a. Dans le fichier `test_geometrie.js`, dupliquer le `describe` renommer le nouveau `describe` obtenu en `Géométrie cube class`. Puis importer la classe `Cube`.

b. Modifier les différents tests dans ce nouveau `describe` pour utiliser la classe `Cube` et les méthodes de calcul (au lieu des fonctions de `geometrie.js`).

c. Exécuter les tests, le contenu du premier `describe` doit continuer à fonctionner et le contenu du second doit retourner une erreur.

d. Créer un nouveau fichier `cube.js` et adapter le code du fichier `geometrie.js` pour le transformer en POO.
Il faut donc une classe `Cube`, avec un attribut `lgCote` et des méthodes `perimetre`, `aireFace`, `surface` et `volume`.

e. Exécuter les tests et vérifier qu'ils passent tous.
