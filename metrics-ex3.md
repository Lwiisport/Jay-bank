# Exercice 3 (Repo 1): CK Metrics Across Classes: Who Looks "Smelly"?


1. Nous pouvons analyser les fichiers `Bank`, `BankAccount`, `Person`, `BankAccountApp` :


| Class          | LOC | WMC | CBO | LCOM | Notes                                                                          |
| -------------- | --- | --- | --- | ---- | ------------------------------------------------------------------------------ |
| Bank           | 413 | 14  | 4   | 0    | la classe `Bank` à plus de lien avec d'autre classe.                           |
| BankAccount    | 462 | 20  | 3   | 44   | `BankAccount` est une des plus grande classe avec le plus de fonction interne. |
| Person         | 325 | 23  | 3   | 79   | `Person` est la classe avec le plus de fonctions tout en étant la plus petite. |
| BankAccountApp | 491 | 2   | 3   | 1    | Malgré seulement 2 fonctions, `BankAccountApp` est la classe la plus grande.   |
La classe `Person` a la `Weighted methods per class` la plus grande.
La classe `Bank` a la `Coupling between object classes` la plus grande.
Si on fait la somme `WMC + CBO + LCOM` on voit que la classe `Person` a un score de `105` ce que la rend très peu maintenable.
