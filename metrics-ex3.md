# Validation des logigicels - exercice 2

### Exercice 3

| Class | LOC | WMC | CBO | LCOM | Quick notes | WMC + CBO + LCOM |
| :---- | :---- | :---- | :---- | :---- | :--- | :---- |
| Bank | 393 | 14 | 4 | 0 | | 18 |
| BankAccount | 408 | 20 | 3 | 44 | | 67 |
| Person | 294 | 23 | 3 | 79 | | 105 |

_Which class has the highest WMC ?_ :
* BankAccount est la classe qui possède la plus haute WMC (20)

_Which class has the highest CBO ?_
* Bank est la classe qui possède le plus haut CBO (4)

_Looking at WMC + CBO + LCOM together, which one class would you worry about most for future maintenance, and why ?_


La classe Person est celle qui pose le plus de risques pour la maintenance future.
Elle présente la valeur combinée la plus élevée (WMC + CBO + LCOM = 105), ce qui indique une complexité globale nettement supérieure aux autres classes.
Son WMC élevé (23) montre qu’elle contient de nombreuses méthodes, ce qui augmente la charge de compréhension et de modification.
De plus, un LCOM très élevé (79) révèle une faible cohésion, suggérant que la classe regroupe plusieurs responsabilités distinctes.
Même si son CBO est modéré, la combinaison d’une faible cohésion et d’une complexité interne importante rend cette classe difficile à maintenir et à faire évoluer sur le long terme.