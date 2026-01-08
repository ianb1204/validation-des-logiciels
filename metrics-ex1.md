# Validation des logigicels - exercice 1

### Exercice 1

1 : Bank.class :

```bash
bankAccountApp.Bank 14 1 0 4 41 0 0 4 12 0,8333 393 1,0000 0 0,0000 0,3286 0 0 26,6429
 ~ public double getMinimumBalance(): 4
 ~ public boolean transferAmount(int arg0, int arg1, int arg2, int arg3, float arg4): 1
 ~ public double getMaximumBalance(): 3
 ~ public String convertToText(): 2
 ~ protected int getAccountsLoaded(): 1
 ~ public java.util.ArrayList getAccounts(): 1
 ~ public void deleteAccount(int arg0): 3
 ~ public void saveAccounts(bankAccountApp.Bank arg0): 8
 ~ public bankAccountApp.BankAccount findAccount(int arg0): 4
 ~ public int addAccount(bankAccountApp.BankAccount arg0, int arg1): 4
 ~ protected void setAccountsLoaded(int arg0): 1
 ~ public double getAverageBalance(): 2
 ~ public boolean registerAccount(int arg0, int arg1, int arg2, int arg3): 1
 ~ public void <init>(): 1
```

2 : BankAccount :

```bash
bankAccountApp.BankAccount 20 1 0 3 39 44 0 3 18 0,6908 405 1,0000 0 0,0000 0,2917 0 0 18,8500
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
 ~ public boolean withdrawMoney(double arg0): 5
 ~ public void <init>(): 1
```

3 : BankAccountApp :

```bash
bankAccountApp.BankAccountApp 2 1 0 4 33 1 0 4 2 2,0000 447 0,0000 0 0,0000 0,5000 0 0 222,5000
 ~ public static void main(String[] arg0): 40
 ~ public void <init>(): 1
```

4 : Person :

```bash
bankAccountApp.Person 23 1 0 1 35 79 0 1 21 0,7626 294 0,8889 0 0,0000 0,3565 0 0 11,3913
 ~ private boolean validateGender(char arg0): 5
 ~ public void setEmail(String arg0): 1
 ~ public void setHeight(float arg0): 1
 ~ public float getWeight(): 1
 ~ public void <init>(String arg0): 3
 ~ public String getEyeColor(): 1
 ~ public void <init>(String arg0, char arg1, int arg2, float arg3, float arg4, String arg5, String arg6, String arg7): 1
 ~ public String getName(): 1
 ~ private void validate(): 1
 ~ public void setHairColor(String arg0): 5
 ~ public String getEmail(): 1
 ~ public void setEyeColor(String arg0): 1
 ~ public void setAge(int arg0): 2
 ~ public String getHairColor(): 1
 ~ public String toString(): 1
 ~ public int getAge(): 1
 ~ public void setWeight(float arg0): 1
 ~ public void setGender(char arg0): 2
 ~ public void <init>(String arg0, char arg1, int arg2, float arg3): 1
 ~ public char getGender(): 1
 ~ public void <init>(): 1
 ~ public float getHeight(): 1
 ~ public void setName(String arg0): 1
```

---

#### ANSWERS :

| Class | LOC | NOM | Short description | 
| :----- | :----- | :----- | :----- |
| Bank | 393 | 14 | Manages bank accounts by providing operations such as account registration, deletion, transfers, balance statistics, persistence, and account lookup. |
| BankAccount | 405 | 20 | Represents a bank account with balance management, deposit and withdrawal logic, serialization to text, and account-related constraints. |
| BankAccountApp | 447 | 2 | Application entry point responsible for launching the banking system through the main method. |
| Person | 294 | 23 | Models a person associated with a bank account, storing personal information and ensuring basic data validation. |

_Do you feel its size roughly matches its responsibility?_

Answer:
* Bank: Yes. Its size is justified by its central role in managing multiple accounts, performing business logic, and handling persistence-related operations.
* BankAccount: Slightly oversized. While it represents a single account, it contains many responsibilities (state management, validation, serialization), which could be partially delegated.
* BankAccountApp: No. The class has very few responsibilities (only main) but a very high LOC, suggesting poor separation of concerns or excessive logic inside main.
* Person: Mostly yes. The size is acceptable given the number of attributes and validation logic, though some setters include more logic than expected.
Overall, most classes have a reasonable size relative to their responsibilities, except BankAccountApp, which appears disproportionately large for an entry-point class and would benefit from refactoring.