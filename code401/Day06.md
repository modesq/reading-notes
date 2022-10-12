# class 06

## What are Design Patterns

A design pattern is only a description or template for how to solve a problem! that can be used in many different situations. So every design pattern provide a solution to commonly occurring software design problems. Patterns are formalized best practices that the Software Developer can use to solve common problems when designing an application.

In the case of object-oriented programming paradigm, design patterns are generally aimed at solving the problems of object generation and communication, rather than the larger scale problems of overall software architecture. Note: Patterns that imply object-orientation or more generally mutable state, are not as applicable in functional programming languages.

There is 3 major types of design patterns:

1. Creational Patterns:
Creational patterns provide ways to instantiate single or groups of objects. Making it easier to create objects in a way that suits the situation.

    Some Creational Patterns:

    1. Factory Method. The factory pattern is used to replace class constructors, abstracting the process of object generation so that the type of the object instantiated can be determined at run-time.
    2. Singleton. The singleton pattern ensures that only one object of a particular class is ever created. All further references to objects of the singleton class refer to the same underlying instance.
    3. Abstract Factory. The abstract factory pattern is used to provide a client with a set of related or dependent objects. The “family” of objects created by the factory are determined at run-time.
2. Structural Patterns:
Structural patterns provide a manner to define relationships between classes or objects. Making it easier for these entities to work together.

    Some Structural Patterns:

    1. Facade. The facade pattern is used to define a simplified interface to a more complex subsystem.
    2. Adapter. The adapter pattern is used to provide a link between two otherwise incompatible types by wrapping the “adaptee” with a class that supports the interface required by the client.
    3. Decorator. The decorator pattern is used to extend or alter the functionality of objects at run-time by wrapping them in an object of a decorator class. This provides a flexible alternative to using inheritance to modify behavior.
3. Behavioral Patterns:
Behavioral patterns define manners of communication between classes and objects. Making it easier and more flexible for these entities to communicate.

    Some Behavioral Patterns:

    1. Observer. The observer pattern is used to allow an object to publish changes to its state. Other objects subscribe to be immediately notified of any changes.
    2. Mediator. The mediator pattern is used to reduce coupling between classes that communicate with each other. Instead of classes communicating directly, and thus requiring knowledge of their implementation, the classes send messages via a mediator object.
    3. Chain of Responsibility. The chain of responsibility pattern is used to process varied requests, each of which may be dealt with by a different handler.

---

## Risk Analysis

In any software, using risk analysis at the beginning of a project highlights the potential problem areas. After knowing about the risk areas, it helps the developers and managers to mitigate the risks. When a test plan has been created, risks involved in testing the product are to be taken into consideration along with the possibility of the damage they may cause to your software along with solutions.

Now, you might think what could be the possible risks that you could encounter? Well here is a list:

1. Use of new hardware
2. Use of new technology
3. Use of new automation tool
4. The sequence of code
5. Availability of test resources for the application

### Risk Assessment

In the risk analysis process, these steps prove to be the most important one. It is said that this step is way too complex and should be tackled with the utmost care. After risk identification, assessment has to be dealt programmatically. There are a few perspectives on risk assessment.

The perspective of Risk Assessment
There are three perspectives of Risk Assessment:

- Effect

- Cause

- Likelihood

Effect – To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.

Cause – To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.

Likelihood – To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.

How to perform Risk Analysis?
There are three steps:

1. Searching the risk

2. Analyzing the impact of each individual risk

3. Measures for the risk identified

---

## Dependency Injection

In software engineering, dependency injection is a technique whereby one object (or static method) supplies the dependencies of another object. A dependency is an object that can be used (a service).

### Why should I use dependency injection?

Let’s say we have a car class which contains various objects such as wheels, engine, etc.

Here the car class is responsible for creating all the dependency objects. Now, what if we decide to ditch MRFWheels in the future and want to use Yokohama Wheels?

We will need to recreate the car object with a new Yokohama dependency. But when using dependency injection (DI), we can change the Wheels at runtime (because dependencies can be injected at runtime rather than at compile time).

You can think of DI as the middleman in our code who does all the work of creating the preferred wheels object and providing it to the Car class.

It makes our Car class independent from creating the objects of Wheels, Battery, etc.

### There are basically three types of dependency injection

- constructor injection: the dependencies are provided through a class constructor.
- setter injection: the client exposes a setter method that the injector uses to inject the dependency.
- interface injection: the dependency provides an injector method that will inject the dependency into any client passed to it. Clients must implement an interface that exposes a setter method that accepts the dependency.
So now its the dependency injection’s responsibility to:

- Create the objects
- Know which classes require those objects
- And provide them all those objects

### Benefits of using DI

- Helps in Unit testing.
- Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
- Extending the application becomes easier.
- Helps to enable loose coupling, which is important in application programming.

### Disadvantages of DI

- It’s a bit complex to learn, and if overused can lead to management issues and other problems.
- Many compile time errors are pushed to run-time.
- Dependency injection frameworks are implemented with reflection or dynamic programming. This can hinder use of IDE automation, such as “find references”, “show call hierarchy” and safe refactoring.
