# Exercice 2 (Repo 1): Cyclomatic Complexity on a Key Method

BankAccount : 
WMC = 20
CC = 33

Méthode = `WithdrawMoney`.


1. La complexité cyclomatique pour la méthode `WithdrawMoney(double withdrawAmount)` est de `5`.

```
public boolean withdrawMoney(double withdrawAmount) {

	if (withdrawAmount >= 0 && balance >= withdrawAmount && withdrawAmount <             withdrawLimit && withdrawAmount + amountWithdrawn <= withdrawLimit) 
	{
		balance = balance - withdrawAmount;
		success = true;
		amountWithdrawn += withdrawAmount;
	} 
	else 
	{
		success = false;
	}
return success;
}
```

Il y a 1 point au premier `if`, 1 point pour chaque `&&` dans le `if`. Finalement, 1 point pour le `else`. Ce qui nous fait 5 points (1 `if`, 3 `&&`, 1 `else`).

2. Dans la fonction `withdrawMoney` une des conditions du `if` n'est pas nécessaire, nous pouvons l'enlever.

3. Voici la méthode modifié :

```
public boolean withdrawMoney(double withdrawAmount) 
{
	if (withdrawAmount >= 0 && balance >= withdrawAmount && withdrawAmount + amountWithdrawn <= withdrawLimit;) 
	{
		balance = balance - withdrawAmount;
		success = true;
		amountWithdrawn += withdrawAmount;
		return success;
	}
	return false;
}
```

Une fois que l'on réanalyse le document, la complexité est passé de 5 à 4 pour la fonction `WithdrawMoney`.
