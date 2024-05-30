# TDD Sandbox

Le TDD (Test Driven Development) a pour but d'écrire les tests avant d'écrire la fonction testée, et d'enrichir à la fois les tests et la fonction au fur et à mesure, en faisant bien attention que tous les tests écrits continuent à fonctionner lorsqu'on modifie la fonction.

Vidéo qui illustre très bien le TDD : https://grafikart.fr/tutoriels/tdd-pratique-javascript-1205


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

a. Dans le fichier `test_geometrie.js`, dupliquer le `describe` renommer le nouveau `describe` obtenu en `Géométrie cube class`. Puis importer la classe `Cube` avec `const Cube = require(' path to cube.js ').Cube;`

b. Modifier les différents tests dans ce nouveau `describe` pour utiliser la classe `Cube` et les méthodes de calcul (au lieu des fonctions de `geometrie.js`).

c. Exécuter les tests, le contenu du premier `describe` doit continuer à fonctionner et le contenu du second doit retourner une erreur.

d. Créer un nouveau fichier `cube.js` et adapter le code du fichier `geometrie.js` pour le transformer en POO.
Il faut donc une classe `Cube`, avec un attribut `lgCote` et des méthodes `perimetre`, `aireFace`, `surface` et `volume`.

e. Exécuter les tests et vérifier qu'ils passent tous.





## Exercice 2 : Prêts pour le décollage ?

Le but de cet exercice est de calculer la quantité de carburant nécessaire au vol d'un avion, en fonction de son chargement. 


______________
Voici quelques données pour un Boeing 747-400 : 
- poids à vide (OEW - empty weight) : 183040 kg
- poids max sans carburant (MZFW - max zero fuel weight) : 246070 kg
- poids max au décollage (MTOW - max takeoff weight) : 396893 kg
- poids max à l'atterrissage (MLW - max landing weight) : 265350 kg 
- capacité de carburant maximale : 173997 kg

Données supplémentaires : 
- Nombre de passagers max sur un B747-400 : 400 environ.
- On compte environ 100kg par passager (bagage de soute compris).
- Il consomme en moyenne environ 3,1L/100km/passager.
- Attention, la densité du kérosène est de 810Kg/m3 au lieu de 1000 pour l'eau (donc 1L de kérosène ne pèse pas 1kg, mais bien 0,81 kg ;) ) !

Quelques règles : 
- Un avion à vide a un poids minimum, donc il faut un minimum de carburant pour le faire voler
- En fonction du nombre de passagers, il faut ajouter du carburant pour les transporter, ainsi que leurs bagages.
- Attention, un avion chargé a un poids maximum, carburant compris, à ne pas dépasser.


Par simplification, on ne prend pas en compte les réserves, la météo, les différentes phases de vol, etc, dans nos calculs.
______________




### Etape 1 :

Créer un dossier `avion` à la racine du projet, et un fichier `calculs.js` dans ce dossier.
Dans le dossier `test`, créer un autre dossier `avion`, et un fichier `test_calculs.js` dans ce dossier.


### Etape 2 : 
Dans le fichier `test_calculs.js`, utiliser le squelette suivant : 

```
const calculs = require(' _path_to_calculs.js_ '); // require the file you want to test
const expect = require('chai').expect; // import other elements of Chai if needed, for example `assert`

describe('Calculs avion', function () {
	it('should to something', function() { // change the name accordingly to what you want to test
		let response = ...; // call the function you want to test, with the params
		expect(...); // what did you expect?
		// or use assert.equal() for example
	});
});

```

a. Créer un premier test permettant de vérifier la capacité de vol de l'avion en appelant une fonction `flyable`.
La fonction `flyable` doit prendre en paramètres les différents paramètres indiqués ci-dessus, ainsi que le nombre de passagers : 

Pour qu'un avion ait la capacité de voler, il faut que : 
- le poids à vide soit inférieur à tous les autres poids,
- le poids chargé soit toujours supérieur au poids à vide,
- le poids soit chargé soit toujours inférieur au poids max de décollage,
- le poids avec les passagers soit inférieur au poids max sans carburant et au poids max à l'atterrissage,
- le poids équivalent du carburant des passagers soit inférieur à la capacité de carburant maximale,
- le poids avec les passagers et leur carburant soit inférieur au poids max de décollage,
- le nombre max de passagers doit être respecté.

Veiller à mettre des messages de tests descriptifs, qui indiquent clairement la nature du problème.


b. Exécuter le test, il doit sortir une erreur (la fonction testée n'existe pas).


### Etape 3 : 

Dans le fichier `calculs.js`, créer la fonction `flyable` avec les paramètres et la logique adéquats.

Exécuter le test, tous les points doivent passer. Corriger au besoin.






## Sources : 
- Mocha (bibliothèque de test) : https://mochajs.org/#getting-started
- Chai (ajoute des fonctionnalités à Mocha, ex : assert, expect, should, etc.) : https://www.chaijs.com/
- Testing your React App with Mocha, Chai and other beverages… https://medium.com/@tatismolin/testing-your-react-app-with-mocha-chai-and-other-beverages-e9a16ca7b9bb

__Sources aviation :__
- https://www.travelguys.fr/2021/08/24/combien-de-carburant-consomme-un-avion/
- https://www.flightsim-corner.com/aller-plus-loin/navigation/navigation-calcul-carburant/

