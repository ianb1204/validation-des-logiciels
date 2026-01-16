# SonarQube: Static Analysis & Quick Fixes

## Problèmes

#### Problème 1 :
* Règle : ```java:S1192 ``` — Define a constant instead of duplicating this literal "Account dosen't exist" 4 times. [+4 locations]
* Fichier / ligne : BankAccountApp.java:139
* Explication : La chaîne ```Account doesn't exist``` apparaît à quatre reprises dans le code, ce qui complique sa maintenance et augmente le risque d’incohérences. En la remplaçant par une constante, le message serait centralisé et plus facile à gérer.

#### Problème 2 :
* Règle : ```java:S135``` — Reduce the total number of break and continue statements in this loop to use at most one.
* Fichier / ligne : BankAccountApp.java:43
* Explication : Cette erreur signifie que la boucle contient trop de break ou continue, ce qui rend le déroulement du programme difficile à suivre. Quand il y a plusieurs sorties possibles dans une même boucle, le code devient plus compliqué à comprendre et à maintenir. SonarLint recommande donc de contrôler la boucle avec une condition claire plutôt qu’avec plusieurs interruptions.

#### Problème 3 : 
* Règle : ```java:S117``` - Rename this local variable to match the regular expression ```^[a-z][a-zA-Z0-9]*$```
* Fichier / ligne : BankAccount.java:52
* Explication : Cette erreur indique que le nom de la variable ne respecte pas les conventions de nommage Java. Ici, la variable locale commence par une majuscule et porte le même nom que la classe, ce qui peut prêter à confusion. Utiliser un nom en minuscules (par exemple person) améliore la lisibilité et évite les ambiguïtés.

## Correction

#### Problème 1 : 

Le message ```Account doesn't exis``` a été remplacé par la constante ```ACCOUNT_NOT_FOUND_MSG``` afin de centraliser sa gestion et améliorer la maintenabilité du code.

#### Problème 3 : 

On renomme simplement la variable ```Person``` en ```person``` pour ne plus avoir l'erreur.

## Vérification

En relançant SornarCube, on constate bien que les erreurs ont disparus bien qu'il en reste encore beaucoup à résoudre.

## Corrélation avec WMC / CBO

Les classes ayant des WMC élevés, comme ```BankAccountApp``` et ```Person```, contiennent effectivement davantage d’issues détectées par SonarLint. Cela montre que les métriques CK (WMC, CBO, LCOM) constituent de bons indicateurs de la dette technique. À l’inverse, les classes plus simples, comme ```ACHService```, présentent peu ou pas de problèmes. On observe donc un lien clair entre la complexité d’une classe et le nombre d’issues détectées par l’analyse statique.