---
layout: post
title: Modular Code in OOP with Dependency Injection
description: A step-by-step example on how to write modular code in object-oriented programming by using dependency injection.
---

Let's increase modularity in object-oriented code with _dependency injection_.

## Why Dependency Injection

The pattern of [dependency injection][1]{:target="_blank"} helps developers design modules of code that are more decoupled from each other, which improves code modularity.

And modular code generally increases code quality as well as development efficiency.

### Decoupled Modules

Because decoupled modules share little or no dependencies with each other, developers can easily analyze one module at a time in order to understand the codebase.

Furthermore, they can safely work in parallel on different modules while resting assured their modifications won't affect other modules.

_Note that the latter holds true as long as modifications stay **internal** to each module, namely they don't alter the module's interfaces._

### Mock Testing

Dependency injection simplifies the use of [mock objects][2]{:target="_blank"}, namely simple code artifacts that implement the intefaces of more complex modules.

Mock testing consists in testing single modules in isolation by using mock objects that replace their external dependencies.

This way, programmers can find bugs more quickly by only focusing on the delimited code.

## Dependency Injection: The Idea 

Let's begin with a snippet which **does not apply dependency injection**:

```java
class Driver {
  private Car c;
  public Driver() {
    this.c = new Car(); // object Car created inside Driver
  }
  public void run() {
    this.c.go();
  }
}
```

The snippet above does not apply dependency injection because it creates the object Car directly inside the class Driver, instead of injecting it from the outside.

Let's proceed with the snipped below which **applies dependency injection** just by moving the creation of the object Car outside of the class Driver:

```java
class Driver {
  private Car c;
  public Driver(Car c) { // object Car created outside Driver
    this.c = c;
  }
  public void run() {
    this.c.go();
  }
}
```

Perfect: the object Car is now created outside of the class Driver and gets injected into it by an external entity. **That's the idea** behind dependency injection. No more, no less.

## Dependency Injection with Java Interfaces

Let's improve the example by using the <code>interface</code> construct in Java in order to take advantage of [polymorphism][3]{:target="_blank"}, which is a fundamental OOP paradigm.

We make the class Driver injectable with whatever vehicle.

### Interface Vehicle

Step 1: Define an interface Vehicle.

```java
interface Vehicle {
  public void go();
}
```

Step 2: Define a class Car that implements a Vehicle.

```java
class Car implements Vehicle {
  public void go() {
    System.out.println("Go car, go!");
  }
}
```

Step 3: Make the class Driver injectable with a Vehicle.

```java
class Driver {
  private Vehicle v;
  public Driver(Vehicle v) { // object Vehicle injected
    this.v = v;
  }
  public void run() {
    this.v.go();
  }
}
public static void main(String[] args) {
  Vehicle v = new Car();
  Driver d = new Driver(v);
  d.run();
}
```

Note the object Car is assigned to variables of type Vehicle.

### Injection by Setter Methods

_**Final steps:** make the Driver injectable with other vehicles after instantiation._

Step 4: Implement an additional Vehicle.

```java
class Bike implements Vehicle {
  public void run() {
    System.out.println("Go bike, go!");
  }
}
```

Step 5: Add the method _setVehicle_ to the Driver.

```java
class Driver {
  private Vehicle v;
  public Driver(Vehicle v){
    this.v = v;
  }
  public void setVehicle(Vehicle v) { // vehicle setter
    this.v = v;
  }
  public void run() {
    this.v.go();
  }
}
```

Final step: Make the Driver change vehicle!

```java
public static void main(String[] args) {
  Vehicle v = new Car();
  Driver d = new Driver(v);
  d.run();
  d.setVehicle(new Bike());
  d.run()
}
```

_Program output:_

```
Go car, go!
Go bike, go!
```

## Recap

* Dependency injection can help programmers write more decoupled modules in object-oriented programming, which increases code modularity;
* Decoupled modules make code easier to work with as well as enabling programmers to work in parallel on different modules;
* Dependency injection simplifies the use of mock testing, which helps developers find bugs more quickly by testing modules in isolation; and
* The idea behind dependency injection can be better applied in object-oriented programming by taking advantage of polymorphism.

## The Code

_**[Get the complete code example!][4]{:title="GitHub Repository"}**_

## Read Also

* [Software Architecture Design for Busy Developers][5]
* [Testability = Modularity][6]

[1]: https://it.wikipedia.org/wiki/Dependency_injection
[2]: https://en.wikipedia.org/wiki/Mock_object
[3]: https://en.wikipedia.org/wiki/Polymorphism_(computer_science)
[4]: https://github.com/massimo-nazaria/dependency-injection-example
[5]: {% link _posts/2019-09-05-software-architecture-design.md %}
[6]: {% link _posts/2020-01-15-testability-modularity.md %}
