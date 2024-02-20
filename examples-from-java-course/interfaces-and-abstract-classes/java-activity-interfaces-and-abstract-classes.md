# CFU: Interfaces and Abstract Classes

## Introduction :pencil2:

This activity will help you practice and assess the knowledge and skills you just learned. During a bootcamp, it's important to spend a lot of time practicing what you've learned. The exercises given to you are just the start. You will get the opportunity to practice more in labs and later, in projects.

We encourage you that once you finish the exercises on the Student Portal platform, try to find more challenges to work on online

**Note:** You are provided with solution to each exercise. The purpose of providing solutions to exercises is to allow you to compare your own work to see if you have a similar or correct approach.

It is not meant to be used as a way to cheat or copy the answers.

It is important to understand the reasoning behind the solution in order to improve your own understanding and problem-solving abilities.

<br>

## Interfaces

### Instructions

In the following exercise you should create a number of classes and interfaces following the below characteristics:

<br>

#### `TransactionList` Interface

The `TransactionList` interface should have the following methods:

- `getLastTransaction()`: returns a `Transaction` object
- `addTransaction(Transaction transaction)`: void method that takes a `Transaction` object as a parameter
- `getTransactionByDate(Date date)`: returns a `Transaction` object that matches the given `Date`
- `getAllTransactions()`: returns an `ArrayList` of `Transaction` objects

<br>

#### `Transaction` Class

The `Transaction` class should have the following properties:

- `sellerAccountNumber`: the account number of the seller
- `buyerAccountNumber`: the account number of the buyer
- `amount`: the amount of the transaction
- `date`: the date of the transaction

<br>

#### `Account` Class

The `Account` class should have the following properties:

- `name`: the name of the account holder
- `address`: the address of the account holder
- `accountNumber`: the account number
- `balance`: the balance of the account

<br>

#### **PaymentList Class**

The `PaymentList` class should implement the `TransactionList` interface and have the following property:

- `transactions`: an `ArrayList` of `Transaction` objects that contains all transactions

The `PaymentList` class should implement all methods from the `TransactionList` interface.

<br>

<details style="font-size: 14px; cursor: pointer; outline: none;">
  <summary> Click for Solution </summary>

```java
import java.util.Date;

public class Transaction {
    private String sellerAccountNumber;
    private String buyerAccountNumber;
    private double amount;
    private Date date;

    //constructor, getters and setters omitted for brevity
}
```

```java
public class Account {
    private String name;
    private String address;
    private double balance;
    private String accountNumber;

    //constructor, getters and setters omitted for brevity
}
```

```java
import java.util.Date;
import java.util.List;

public interface TransactionList {
    Transaction getLastTransaction();
    void addTransaction(Transaction transaction);
    Transaction getTransactionByDate(Date date);
    List<Transaction> getAllTransactions();
}
```

```java
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

public class PaymentList implements TransactionList {
    List<Transaction> transactionList = new ArrayList<>();

    @Override
    public Transaction getLastTransaction() {
        return transactionList.get(transactionList.size() - 1);
    }

    @Override
    public void addTransaction(Transaction transaction) {
        transactionList.add(transaction);
    }

    @Override
    public Transaction getTransactionByDate(Date date) {
        for(Transaction transaction : transactionList) {
            if (transaction.getDate().equals(date)) {
                return transaction;
            }
        }

        return null;
    }

    @Override
    public List<Transaction> getAllTransactions() {
        return transactionList;
    }
}
```

<br>

### Benefits of the TransactionList Interface at Scale

- The `TransactionList` interface provides a standardized set of methods for interacting with transactions, which makes it easier to build and maintain applications that involve transactions.
- The `TransactionList` interface allows different parts of an application to communicate with each other using a common set of methods, which helps to reduce complexity and improve code reuse.
- The `TransactionList` interface makes it easier to test and debug applications, as it clearly defines the expected input and output of each method.
- The `TransactionList` interface makes it easier to extend and modify applications, as new functionality can be added by implementing additional methods in the interface.
- The `TransactionList` interface allows developers to build reusable components that can be easily integrated into different applications, which can save time and effort when building software at scale.

</details>
