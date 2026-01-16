# Exercice 4 (Repo 1): SonarQube: Static Analysis & Quick Fixes

1. Voici 3 `issues` importantes :

| Issues                                                   | Fichier et ligne                                 | Explications                                                                                                                                                                                                        |
| -------------------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Cognitive Complexity of methods should not be too high` | `BankAccountApp.java` et à partir de la ligne 20 | La méthode `main` est beaucoup trop grande. Ceci affecte grandement la maintenabilité du projet. On doit donc la refactorisé afin de la rendre plus lisible                                                         |
| `Try-with-resources should be used`                      | `BankAccount.java` à partir de la ligne 160      | Nous avons une lecture de texte dans un `try` avec une boucle itérative `while`, nous pouvons ajouter en paramètre du `try` la ressource du texte pour que le processus se ferme à la fin du `try` automatiquement. |
| `Sections of code should not be commented out`           | `Bank.java` à partir de la ligne 27              | Une ligne de code est commenté et doit être supprimé pour amélioré la lisibilité et la maintenabilité.                                                                                                              |

2. Je vais `fix` 2 Issues :

 - Dans la classe `Bank.java` nous avons l'issues `make this final field static too` à la ligne 20. On nous demande donc de rendre le variable `static` :

```
private static final int initialSize = 1000;
```

- Une fois cette erreur corriger, une nouvelle erreur se lève nous demandant de corriger le nom de notre variable pour respecter la casse d'une constante (`Constant names should comply with a naming convention`) :

```
private static final int INITIAL_SIZE = 1000;
```

Ceci nous permet donc de corriger 2 erreurs `SonarQube`. Les erreurs ont bien disparu des issues `SonarQube`.

2. Comme nous l'avons vu dans les questions précédentes, les classes `BankAccount` et `Person` ont le `WMC` / `CBO` le plus grand. Cependant, ce ne sont pas les classes avec le plus d'erreur `SonarQube`. Il y a 12 erreurs pour `BankAccount.java` là ou il y en a 19 pour `Bank.java` et 46 pour  `BankAccountApp.java`. Il n'y a donc pas de corrélation entre `WMC` / `CBO` et erreurs `SonarQube`.
