# Java Crash Course

## What is Programming


Computers understand 0s and 1s. Humans understand "natural" language, with words, sentences and paragraphs. "Programming" is the process of telling computers what we want them to do. 

Examples of programming: 

* When you tell your oven to pre-heat at a certain temperature, you're "programming" it

* When you tell your DVR to record a certain show at a certain time on a certain channel, you're "programming" it

* When you tell your smartphone to wake you up at 6:30 a.m., you're programming it

## What's a Programming Language

When we tell our appliances to do something, we're using a very limited set of instructions. You can only pre-heat your oven based on specific conditions. You cannot, for example, start pre-heating your oven at 350F on Tuesday night if the weather is a specific temperate outside. 

A Programming Language, such as Java, gives you a full array of "instructions" so that you can control just about any aspect of a computer. If it has a sensor, you can access the sensor, if it has storage, you can access the files on it, if it has a speaker, you can play sound on it, etc...

## Object Oriented Programming

Java is an Object Oriented Programming Language - what does that mean? 

* The "real" world is made up of objects

* Objects have "properties", things that you know about them

* Object can "do things", take action

Example of objects: 

* Your car is an object. It has properties: wheels (4 of them), an engine (1), a brake pedal (1), etc...

* Your car can also do things: start, accelerate, brake, ... 

That's what *your* car can do. How about my car? Same thing? How do I know? Because it's a ... "car". I have expectations of what an object is and what it can do if you tell me it's a car ... 

In Java, that's what "classes" are for. They describe the properties and methods (actions) of an object. So that every object of that class (instance of that class) will follow these rules. 

The class is the blueprint - the object is the actual "thing" that follows that blueprint. 

## Cool - I want to create a blueprint! 

Ok - we'll do that in a minute, but first let's get some building blocks together. 

### Getting something that understands Java

We'll write an actual class and compile it and run it through the command line later, but for now ... 

[Go to Java REPL](http://www.javarepl.com/console.html) 

### Variables

A"variable" is a container for a value. Let's say your car has a name: 

```java
String carName = "Caroline"; 
```

Variables:

* Have a type, such as int (whole numbers), String (text) or double (decimal numbers)
* Have a name (can start with any letter, underscore or $ and can have as many characters as desired)
* Can be assigned a value with the "=" operator

### Methods

Methods are how we act on variables and actually do things. For example, we can ask Java to print out (i.e. display on the console) the name of our car: 

```java
System.out.println(carName); 
```

The code above is calling the `println()` method on the `out` variable in the `System` class. 

It seems complicated, but it's really about containers, and mirrors our daily lives. Think of ... a postcard in the mail, for example: 

* When the mail person delivers it to your house, it's delivered to your mailbox: that's container 1 for our discussion. 
* The postcard is in an envelope: that's container 2 for our discussion. 
* And then you have the postcard itself with an image and some text on it

If we were to use the "dot" notation to access this postcard's image, we'd use something like: 

`mailbox.postcardEnvelope.postcard.image`

We're telling Java that we want something in the mailbox called `postcardEnvelope`. Moreover, within that, we want something called postcard. Moreover, within that, we want something called image. 

The sentence above is too long and too convoluted, so the simple "programming language" way of saying that is: 

`mailbox.postcardEnvelope.postcard.image`

### Classes

Classes are how we group methods and variables together to define the blueprint for a specific type of object. For example, the String class from Oracle has some built-in methods that we can use on our carName variable of type String: 

```java
System.out.println(carName.toUpperCase()); 
System.out.println(carName + " is " + carName.length() + " characters long"); 
```

## Why Java

* Lots of libraries
* Lots of support
* Lots of demand
* Lots of fun!!!

## Let's play

Let's build a simple game ... 

* Open a terminal window or command prompt and run these two commands: 

```
java -version
javac -version
```

If they both run, congratulations! You can now create a Java class, compile it and run it! 

### Basic class

One of the main principles of programming is to do things step by step and to always have a working baseline to go back to, in case things break and stop working - which they will! So ... before we start working our our actual functionality, we're going to write a simple class and make sure we can compile it and run it - this will be our *baseline*. 

* First, create a folder for this project (name it whatever you want)
* In that folder, create a file and name it GuessMyNumber.java and open it 

(In Java, the name of a class must match the name of the file it is stored in)

* Now, let's actually write our base class: 

```java
public class GuessMyNumber { 
    public static void main(String[] args) { 
        System.out.println("GuessMyNumber is running!"); 
    }
}
```

### I have a class - now what? 

Compile it: this means turning the code that we, humans, can read into code that the computer can read more easily understand and run. We use the `javac` command for that: 

```
javac GuessMyNumber.java
```

Now we have a "class" file named GuessMyNumber.class, which we can actually run with the `java` command: 

```
java GuessMyNumber
```

You should see output similar to this: 

```
C:\data\sandbox\theironyard\crash-courses>java GuessMyNumber
GuessMyNumber is running!

C:\data\sandbox\theironyard\crash-courses>
```

### Standing on the shoulders of giants

The power of programming is that we can use code that we didn't write ourselves. Oracle gives me many classes we can use with the Java Developer Kit (JDK), and there are many other libraries and frameworks we can leverage in the Java universe. 

For this game, we're going to use two new Java classes: 

* Math: this will let us generate a random number
* Scanner: this will let us get some input from the user from the console

### Requirements

Here are the requirements for our game: 

* The system must ask the user for an integer number between 0 and 10
* The system must generate a random number between 0 and 10
* If the user's number is greater than the system generated number, then the user wins
* Otherwise, the system wins
* The system must tell the user who won

Let's go ahead and modify our class to implement this functionality (then we'll walk through what every line of code does: 

```java
import java.util.Scanner; 

public class GuessMyNumber { 
	public static void main(String[] args) { 
		System.out.println("GuessMyNumber is running!"); 

		// Ask the user for their number 
		// and store it in an int variable
		System.out.println("Please enter a number between 0 and 10"); 
		Scanner inputScanner = new Scanner(System.in); 
		int userNumber = inputScanner.nextInt(); 
		System.out.println("You entered: " + userNumber); 

		// Generate a random number between 0 and 10
		// and store it in another int variable
		int computerNumber = (int) (Math.random() * 10); 
		System.out.println("Computer generated: " + computerNumber); 

		// Compare the two and display who won
		if (userNumber > computerNumber) { 
			System.out.println("You win!"); 
		} else { 
			System.out.println("I win!"); 
		}

		System.out.println("Thank you for playing!"); 
	}
}
```

Now that you have a new baseline, you can play with it to make it do other things, such as: 

* Play the game x number of times before stopping (with a for loop)
* Play the game forever until the user chooses to stop (with a while loop, and if statement and a break instruction)
* Display a "You won" animatation when the user wins



