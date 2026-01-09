# Validation des logigicels - exercice 2

### Exercice 3

| Class | LOC | WMC | CBO | LCOM | Quick notes | WMC + CBO + LCOM |
| :---- | :---- | :---- | :---- | :---- | :--- | :---- |
| Bank | 393 | 0,8333 | 14 | 1,0000 | | 15.8333 |
| BankAccount | 408 | 0,6938 | 21 | 1,0000 | | 22.6938 |
| Person | 294 | 0,7626 | 23 | 0,8889 | | 24,6515 |

_Which class has the highest WMC ?_ :
* Bank est la classe qui possède la plus haute WMC (0.8333)

_Which class has the highest CBO ?_
* Person est la classe qui possède le plus haut CBO (23)

_Looking at WMC + CBO + LCOM together, which one class would you worry about most for future maintenance, and why ?_


La classe Person est celle qui pose le plus de risques pour la maintenance future. Elle présente la valeur combinée la plus élevée (WMC + CBO + LCOM = 24,6515), ce qui indique une complexité globale plus importante que les autres classes. Son CBO élevé (23) montre qu’elle est fortement couplée à d’autres classes, ce qui rend les modifications plus risquées et susceptibles d’avoir des effets de bord. De plus, un LCOM proche de 1 (0,8889) suggère une faible cohésion, indiquant que la classe regroupe probablement plusieurs responsabilités. Ces caractéristiques combinées rendent la classe plus difficile à comprendre, à tester et à faire évoluer sur le long terme.