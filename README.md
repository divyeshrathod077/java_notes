Java OOP — Complete Quick Revision Notes

Below is a brief, easy-to-revise OOP guide. The goal is to understand the concept first and then remember the syntax.


---

1. What is OOP?

OOP = Object-Oriented Programming

It organizes a program around objects rather than only functions.

Main 4 pillars

Concept	Simple meaning

Encapsulation	Hide data + control access
Inheritance	Reuse properties of another class
Polymorphism	One name, different behavior
Abstraction	Hide implementation details



---

2. Class

A class is a blueprint/template for creating objects.

class Student {
    String name;
    int age;

    void study() {
        System.out.println("Student is studying");
    }
}

Think:

> Class = Blueprint




---

3. Object

An object is an instance of a class.

Student s1 = new Student();

Here:

Student → class

s1 → reference variable

new Student() → creates object


s1.name = "Rahul";
s1.age = 20;
s1.study();

> Class → blueprint
Object → actual thing created from blueprint




---

4. Constructor

A constructor is used to initialize an object.

Rules:

Same name as class

No return type

Automatically called when object is created


class Student {
    String name;

    Student(String name) {
        this.name = name;
    }
}

Student s = new Student("Rahul");

Types

Default constructor

No-argument constructor

Parameterized constructor



---

5. this Keyword

this refers to the current object.

class Student {
    String name;

    Student(String name) {
        this.name = name;
    }
}

Here:

this.name → object's variable
name      → constructor parameter


---

6. Encapsulation

Encapsulation = wrapping data and methods together + restricting direct access.

Usually achieved using:

private

getters

setters


class BankAccount {
    private double balance;

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}

Why?

To protect data from unwanted direct modification.

> Encapsulation = Data hiding + controlled access




---

7. Access Modifiers

Java has four important access levels:

Modifier	Access

private	Same class
default	Same package
protected	Same package + subclasses
public	Everywhere


Example:

private int age;
public String name;


---

8. Inheritance

Inheritance allows one class to acquire properties and methods of another class.

class Animal {
    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking");
    }
}

Dog d = new Dog();
d.eat();
d.bark();

Dog inherits eat() from Animal.

Keyword

extends

> Inheritance = Code reusability




---

9. Types of Inheritance

Single

A
|
B

Multilevel

A
|
B
|
C

Hierarchical

A
   / \
  B   C

Java does not support multiple inheritance through classes:

A   B
 \ /
  C

This can create ambiguity.

Java can achieve multiple inheritance of type using interfaces.


---

10. super Keyword

super refers to the parent class.

Parent variable

super.name;

Parent method

super.display();

Parent constructor

super();

Example:

class Animal {
    Animal() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
    Dog() {
        super();
        System.out.println("Dog");
    }
}


---

11. Polymorphism

Poly = many
Morphism = forms

One interface/name can have different behavior.

Two major types:

1. Compile-time polymorphism

Method overloading

2. Runtime polymorphism

Method overriding


---

12. Method Overloading

Same method name but different parameters.

class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}

This is:

> Compile-time polymorphism



Parameters must differ by:

Number

Type

Order


Return type alone cannot create overloading.


---

13. Method Overriding

Child class provides its own implementation of a parent method.

class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Bark");
    }
}

Animal a = new Dog();
a.sound();

Output:

Bark

This is runtime polymorphism.

> Method selection happens according to the actual object at runtime.




---

14. Dynamic Method Dispatch

Important for runtime polymorphism.

Animal a = new Dog();

Reference type:

Animal

Actual object:

Dog

Overridden method of Dog executes.


---

15. Abstraction

Abstraction = hiding unnecessary implementation details and showing only essential functionality.

Example:

You use:
ATM.withdraw()

You don't need to know:
how the bank server processes it internally.

Java provides abstraction mainly through:

Abstract classes

Interfaces



---

16. Abstract Class

A class declared using abstract.

abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Eating");
    }
}

A child class implements the abstract method:

class Dog extends Animal {

    void sound() {
        System.out.println("Bark");
    }
}

You cannot directly create an object of an abstract class.

// Animal a = new Animal(); ❌


---

17. Interface

An interface defines a contract that implementing classes follow.

interface Vehicle {
    void start();
}

class Car implements Vehicle {

    public void start() {
        System.out.println("Car starts");
    }
}

Keyword:

implements

Interface is useful for:

Abstraction

Loose coupling

Multiple inheritance of type


class A implements X, Y {
}


---

18. Abstract Class vs Interface

Abstract Class	Interface

extends	implements
Can have instance variables	Fields are constants by default
Can have constructors	No constructors
Can have abstract + concrete methods	Can define abstract methods and also default/static methods
Class can extend one class	Class can implement multiple interfaces



---

19. static

static belongs to the class, not individual objects.

class Student {
    static String college = "ABC";
}

Access:

Student.college;

You don't need an object.

Static method

static void display() {
}

Important:

> Static methods cannot directly access non-static instance members.




---

20. final

final means something cannot be changed further, depending on where it is used.

Final variable

final int MAX = 100;

Cannot reassign it.

Final method

Cannot be overridden.

Final class

Cannot be inherited.

final class A {
}


---

21. Packages

A package groups related classes.

package com.example;

Import another package:

import java.util.Scanner;

Benefits:

Organization

Namespace management

Access control



---

22. Object Class

Every Java class ultimately inherits from:

Object

Important methods:

toString()

Returns string representation.

equals()

Used to compare objects logically when overridden appropriately.

hashCode()

Returns hash value used by hash-based collections.


---

23. equals() vs ==

==

For objects, checks whether two references refer to the same object.

equals()

Usually used for logical/content equality, depending on the class's implementation.

Example:

String a = new String("Hello");
String b = new String("Hello");

System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true


---

24. Constructor Overloading

Multiple constructors with different parameters.

class Student {

    Student() {
    }

    Student(String name) {
    }

    Student(String name, int age) {
    }
}

This is constructor overloading.


---

25. Constructor Chaining

One constructor calls another constructor.

Using:

this()

Example:

class Student {

    Student() {
        this("Unknown");
    }

    Student(String name) {
        System.out.println(name);
    }
}

Parent constructor can be called using:

super();


---

26. Exception Handling

Used to handle runtime problems without abruptly terminating normal program flow.

Main keywords:

try
catch
finally
throw
throws

Example:

try {
    int x = 10 / 0;
}
catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}


---

27. throw vs throws

throw

Actually throws an exception.

throw new Exception("Error");

throws

Declares that a method may throw an exception.

void test() throws Exception {
}


---

28. Generics

Generics provide type safety.

ArrayList<String> names = new ArrayList<>();

Now the list is intended for String values.

Another example:

class Box<T> {
    T value;
}

T can represent different types.


---

29. Wrapper Classes

Primitive → Object equivalent.

Primitive	Wrapper

int	Integer
char	Character
double	Double
boolean	Boolean
long	Long


Example:

Integer x = 10;


---

30. Autoboxing / Unboxing

Autoboxing

Primitive → wrapper

int a = 10;
Integer b = a;

Unboxing

Wrapper → primitive

Integer a = 10;
int b = a;


---

31. Inner Class

A class declared inside another class.

class Outer {

    class Inner {
        void show() {
            System.out.println("Hello");
        }
    }
}

Useful when a class is strongly related to another class.


---

32. Enum

Used when a variable can have a fixed set of values.

enum Day {
    MONDAY, TUESDAY, WEDNESDAY
}

Useful for:

Days

Directions

Status

Fixed categories



---

33. Association

Represents a general relationship between objects.

Teacher ---- Student

A teacher is associated with students.


---

34. Aggregation

A weak has-a relationship.

Department ---- Teacher

The teacher can exist independently of the department.


---

35. Composition

A strong has-a relationship.

House ---- Room

The room is treated as part of the house's lifecycle in the model.

Remember

Inheritance → IS-A
Composition → HAS-A

Example:

Dog IS-A Animal
Car HAS-A Engine


---

36. Upcasting

Child object referenced by parent type.

Animal a = new Dog();

Usually safe and common in polymorphism.


---

37. Downcasting

Parent reference converted to child type.

Animal a = new Dog();
Dog d = (Dog) a;

Must be done carefully because an incorrect cast can cause:

ClassCastException


---

38. instanceof

Checks whether an object is compatible with a particular type.

if (a instanceof Dog) {
    Dog d = (Dog) a;
}

Modern Java also supports pattern matching in appropriate language versions.


---

39. SOLID Principles

Very important for professional OOP/design.

S — Single Responsibility

One class should have one main responsibility.

O — Open/Closed

Open for extension, closed for modification.

L — Liskov Substitution

Child objects should be usable where their parent type is expected without breaking expected behavior.

I — Interface Segregation

Prefer small, focused interfaces instead of one huge interface.

D — Dependency Inversion

Depend on abstractions rather than concrete implementations.


---

40. Most Important Interview Differences

Overloading vs Overriding

Overloading	Overriding

Same class commonly	Parent-child relationship
Parameters differ	Same method signature
Compile time	Runtime
Static methods can be overloaded	Static methods are hidden, not overridden


Encapsulation vs Abstraction

Encapsulation → How to protect data?
Abstraction   → What details should be hidden?

this vs super

this  → current object/class context

super → parent class context
