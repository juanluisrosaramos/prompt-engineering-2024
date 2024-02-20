# Interfaces and Abstract Classes

## Lesson Overview :pencil2:

Interfaces and abstract classes are cornerstones of good object-oriented design. This lesson takes a closer look at these two vital concepts.

<br>

## Learning Objectives :notebook:

By the end of this lesson, you will be able to:

- Create an interface
- Implement an interface
- Recognize the syntax for implementing multiple interfaces
- Create and extend abstract classes
- Articulate the difference between interfaces and abstract classes

<br>

## Key Definitions and Examples :key:

### Interfaces

An interface looks like a class but it is not a class. An interface can have methods and variables just like the class but the methods declared in the interface are by default abstract (only method signature, no body, see: Java abstract method). Also, the variables declared in an interface are public, static & final by default.

As mentioned above they are used for full abstraction. Since methods in interfaces do not have a body, they have to be implemented by the class before you can access them. The class that implements an interface must implement all the methods of that interface. Also, the java programming language does not allow you to extend more than one class, however, you can implement more than one interface in your class.

Some real-life examples:

- We are creating a pandora service. On the web android, iPhone and other platforms our play, pause and mute methods may need to be implemented differently. ApplePlayer androidPlayer and WebPlayer could all implement the Playable interface which defines play, pause and mute method signatures. This way all the developers working on our app, know that every player will share the same method signatures. This improves maintainability and application agility and reduces development time.

- The List interface is implemented by ArrayList, Vector, LinkedList and Stack. Assuming we program to the interface, we can change our implementation easily as our application scales and new requirements emerge that make one data structure more efficient than the others.

- Data Access Object interfaces ensure that method signatures stay the same even if we change database and data access implementation. This makes our application less brittle.

<u><i>Example:</i></u>

```java
public interface Playable {
    void play();
    void pause();
    void mute();
    void increaseVolume(double volume);
}
```

```java
public class AndroidPlayer implements Playable {

    private final int MAX_VOLUME = 100;

    private double volume;

    public AndroidPlayer(double volume) {
        this.volume = volume;
    }

    public void play() {
        System.out.println("Playing on Android");
    }

    public void pause() {
        System.out.println("Pausing on Android");
    }

    public void mute() {
        System.out.println("Muting on Android");

    }

    public void increaseVolume(double volume) {
        // This implementation increase the current volume with the value passed by the parameter
       this.volume = this.volume + volume > MAX_VOLUME ? MAX_VOLUME : this.volume + volume;
        System.out.println("Current volume: " + this.volume);
    }

    public double getVolume() {
        return volume;
    }
}
```

```java
public class ApplePlayer implements Playable {
    private final int MAX_VOLUME = 1;
    private double volume;

    public ApplePlayer(double volume) {
        this.volume = volume;
    }

    public void play() {
        System.out.println("Playing on Iphone");
    }

    public void pause() {
        System.out.println("Pausing on Iphone");
    }

    public void mute() {
        System.out.println("Muting on Iphone");
    }

    public void increaseVolume(double volume) {
        // This implementation replace the current volume with the value passed by the parameter

        if (volume > MAX_VOLUME) {
            this.volume = MAX_VOLUME;
        } else if (volume < 0) {
            this.volume = 0;
        } else {
            this.volume = volume;
        }

        System.out.println("Current volume: " + this.volume);
    }

    public double getVolume() {
        return volume;
    }
}
```

<br>

### Abstract Classes

A class that is declared as abstract is known as an abstract class. It can have abstract and non-abstract methods. It needs to be extended and its method implemented. It cannot be instantiated.

Points to remember:

- An abstract class must be declared with an abstract keyword.
- It can have abstract and non-abstract methods.
- It cannot be instantiated.
- It can have constructors and static methods also.
- It can have final methods which will force the subclass not to change the body of the method.

Abstract classes are similar to interfaces. You cannot instantiate them and they may contain a mix of methods declared with or without an implementation.

However, with abstract classes, you can declare fields that are not static and final and define public, protected and private concrete methods. With interfaces, all fields are automatically public, static and final and all methods that you declare or define (as default methods) are public. In addition, you can extend only one class, whether or not it is abstract, whereas you can implement any number of interfaces.

Since Java 8, default method implementations are allowed in Interfaces. The differences between abstract classes and interfaces are a bit less now, but there is still an important difference in that abstract classes can have states and can implement non-public methods.

<u><i>Example:</i></u>

In the example below, there is an abstract class `Account` that represents a bank account. You can't have just an `Account` at a bank, you have to have either a `CheckingAccount`, `SavingsAccount`, `RetirementAccount` or some other type of `Account`. Since `Account` should not be instantiated, it should be an abstract class.

```java
abstract class Account {

  private long accountNumber;
  private String owner;
  private double balance;

  //constructor, getters and setters omitted for brevity

  abstract void processPayment(double paymentAmount);
  abstract void processDebit(double purchaseAmount);

}
```

```java
class SavingsAccount extends Account{
  private double interestRate;

  //constructor, getters and setters omitted for brevity

  public void processPayment(double paymentAmount){
    setBalance(getBalance() - paymentAmount);
  }

  public void processDebit(double purchaseAmount){
    setBalance(getBalance() + purchaseAmount);
  }
}
```

<br>

## Additional Resources :clipboard:

If you would like to study these concepts before the class or would benefit from some remedial studying, please utilize the resources below:

- [Official Documentation - Interface](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html)
- [Java Interfaces by Beginners Book](https://beginnersbook.com/2013/05/java-interface/)
- [Official Documentation - Abstract Classes](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)
- [Abstract Classes by JavaTpoint](https://www.javatpoint.com/abstract-class-in-java)
- [Multiple Inheritance by Journal Dev](https://www.journaldev.com/1775/multiple-inheritance-in-java)
