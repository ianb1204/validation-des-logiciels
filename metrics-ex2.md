# Validation des logigicels - exercice 2

### Exercice 2

BanckAccount :
* WMC : 405
* CC : 33

Méthode choisie : withdrawMoney 

##### 1 - 

- _Note its cyclomatic complexity value from the plugin (if shown) :_ **5**

* In the file as comments, mark where each decision point is (each if, else if, switch, loop, etc.) :


```java
	public boolean withdrawMoney(double withdrawAmount) {
		if (
            withdrawAmount >= 0 // decision point 1 : IF
            && balance >= withdrawAmount // decision point 2 : &&
            && withdrawAmount < withdrawLimit // decision point 3 : &&
            && withdrawAmount + amountWithdrawn <= withdrawLimit // decision point 4 : &&
        ) {
			balance = balance - withdrawAmount;
			success = true;
			amountWithdrawn += withdrawAmount;
		} 
		// decision point 5 : ELSE
		else {
			success = false;
		}
		return success;
	}
```

##### 2 - 

On peut tout d'abord isoler le contenu de la condition du IF dans une fonction helpers ```isWithdrawAllowed(double withdrawAmount)```, qui retournera le résultat de la condition. On peut également retirer le else et indiquer que la fonction retourne ```false``` à partir du moment ou la condition n'est pas validée.

##### 3 - 

* _Implement the refactoring (create the helper method, simplify the original method) :_

```java

    public boolean isWithdrawAllowed(double withdrawAmount) {
        return withdrawAmount >= 0 && balance >= withdrawAmount && withdrawAmount < withdrawLimit && withdrawAmount + amountWithdrawn <= withdrawLimit
    }
	
    public boolean withdrawMoney(double withdrawAmount) {
		if (isWithdrawAllowed(withdrawAmount)) {
			balance = balance - withdrawAmount;
			amountWithdrawn += withdrawAmount;
            return true
		} 
		
        return false
	}
```

* _Re-run CK Metrics on that file and check whether the complexity for that method decreased :_

``` bash
bankAccountApp.BankAccount 21 1 0 3 40 46 0 3 19 0,6938 408 1,0000 0 0,0000 0,2937 0 0 18,0476
 ~ public boolean isWithdrawAllowed(double arg0): 5
 ~ public int loadFromText(String arg0): 8
 ~ public void <init>(double arg0, double arg1, String arg2, bankAccountApp.Person arg3): 1
 ~ public String convertToText(bankAccountApp.BankAccount arg0): 1
 ~ public void depositMoney(double arg0): 2
 ~ public double getBalance(): 1
 ~ public int getAccountNumber(): 1
 ~ public void setWithdrawLimit(double arg0): 1
 ~ private void setDateCreated(String arg0): 1
 ~ public void <init>(int arg0, double arg1, double arg2, String arg3, String arg4): 1
 ~ private void setBalance(double arg0): 1
 ~ public String getDateCreated(): 1
 ~ public String toString(): 1
 ~ public double getInitMoneyAmount(): 1
 ~ public double getWithdrawLimit(): 1
 ~ public double getAmountWithdrawn(): 1
 ~ public boolean withdrawMoney(double arg0): 2
 ~ public void <init>(): 1
 ~ public void setAccountNumber(int arg0): 1
 ~ public bankAccountApp.Person getAccountHolder(): 1
 ~ public void setAccountHolder(bankAccountApp.Person arg0): 2
```

On remarque que la complexité de la méthode withdrawMoney est passée de 5 à 2.