.. _ch08:

================================
Chapter 8: Python Object & Class
================================

Python Objects and Classes
+++++++++++++++++++++++++++

1. What is a Class and an Object
=================================

A class is a blueprint for creating objects. An object is an instance of a class:

.. code-block:: python

    class Person:
        pass

    p1 = Person()
    print(p1)

Classes define structure; objects represent real entities.


2. Defining a Class with Attributes
====================================

Attributes represent properties of the class:

.. code-block:: python

    class Person:
        name = "Alice"
        age = 25

    p = Person()
    print(p.name)
    print(p.age)


3. Constructor Method (__init__)
=================================

The constructor initializes object data at creation:

.. code-block:: python

    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age

    p = Person("Bob", 30)
    print(p.name, p.age)


4. Instance Methods
===================

Instance methods operate on object data using self:

.. code-block:: python

    class Person:
        def __init__(self, name):
            self.name = name

        def greet(self):
            return f"Hello, my name is {self.name}"

    p = Person("Alice")
    print(p.greet())


5. Class Variables vs Instance Variables
=========================================

Class variables are shared, instance variables are unique per object:

.. code-block:: python

    class Student:
        school = "Global Academy"  # Class variable

        def __init__(self, name):
            self.name = name        # Instance variable

    s1 = Student("Alice")
    s2 = Student("Bob")

    print(s1.school)
    print(s2.school)


6. Creating Multiple Objects
=============================

Multiple objects can be created from the same class:

.. code-block:: python

    class Car:
        def __init__(self, brand):
            self.brand = brand

    c1 = Car("Toyota")
    c2 = Car("Tesla")

    print(c1.brand)
    print(c2.brand)


7. Modifying Object Properties
===============================

Objects allow runtime modification of attributes:

.. code-block:: python

    class Employee:
        def __init__(self, name):
            self.name = name

    emp = Employee("John")
    emp.name = "Michael"

    print(emp.name)


8. Deleting Object Properties and Objects
==========================================

Use del to remove attributes or the object itself:

.. code-block:: python

    class Product:
        def __init__(self, price):
            self.price = price

    item = Product(100)

    del item.price
    # del item  # Deletes the object entirely


9. Built-in Object Functions
=============================

Common object-related built-ins:

- type()
- isinstance()

.. code-block:: python

    class User:
        pass

    user = User()

    print(isinstance(user, User))  # True
    print(type(user))              # <class '__main__.User'>


10. Real-World Class Example
=============================

Encapsulation of data and behavior into a single unit:

.. code-block:: python

    class BankAccount:
        def __init__(self, owner, balance):
            self.owner = owner
            self.balance = balance

        def deposit(self, amount):
            self.balance += amount

        def withdraw(self, amount):
            self.balance -= amount

    account = BankAccount("Alice", 1000)
    account.deposit(500)
    print(account.balance)  # Output: 1500


Python Inheritance
+++++++++++++++++++

1. What is Inheritance
======================

Inheritance allows a class (child) to acquire properties and behaviors of another class (parent):

.. code-block:: python

    class Animal:
        def eat(self):
            print("Animal is eating")

    class Dog(Animal):
        pass

    d = Dog()
    d.eat()  # Inherited method

Promotes code reusability and hierarchical design.


2. Single Inheritance
=====================

A child class inherits from one parent class:

.. code-block:: python

    class Parent:
        def show(self):
            print("This is the parent class")

    class Child(Parent):
        pass

    c = Child()
    c.show()


3. Adding New Methods in Child Class
====================================

Child classes can extend functionality beyond the parent:

.. code-block:: python

    class Animal:
        def sound(self):
            print("Some sound")

    class Dog(Animal):
        def bark(self):
            print("Dog barks")

    d = Dog()
    d.sound()
    d.bark()


4. Method Overriding
====================

Child class can redefine parent methods:

.. code-block:: python

    class Animal:
        def sound(self):
            print("Animal makes sound")

    class Dog(Animal):
        def sound(self):
            print("Dog barks")

    d = Dog()
    d.sound()  # Dog barks


5. Using super() to Call Parent Methods
=======================================

super() invokes the parent class method within the child:

.. code-block:: python

    class Animal:
        def sound(self):
            print("Animal makes sound")

    class Dog(Animal):
        def sound(self):
            super().sound()
            print("Dog barks")

    d = Dog()
    d.sound()


6. Multilevel Inheritance
==========================

Inheritance chain stretches across multiple levels:

.. code-block:: python

    class Grandparent:
        def feature(self):
            print("Grandparent feature")

    class Parent(Grandparent):
        pass

    class Child(Parent):
        pass

    c = Child()
    c.feature()


7. Multiple Inheritance
=======================

A child class inherits from multiple parent classes:

.. code-block:: python

    class Father:
        def skill(self):
            print("Driving")

    class Mother:
        def talent(self):
            print("Cooking")

    class Child(Father, Mother):
        pass

    c = Child()
    c.skill()
    c.talent()


8. Method Resolution Order (MRO)
=================================

MRO defines the order in which methods are resolved in inheritance:

.. code-block:: python

    class A:
        def show(self):
            print("A")

    class B(A):
        def show(self):
            print("B")

    class C(B):
        pass

    c = C()
    c.show()
    print(C.mro())


9. Constructor Inheritance
===========================

Child constructors can call parent constructors using super():

.. code-block:: python

    class Parent:
        def __init__(self, name):
            self.name = name

    class Child(Parent):
        def __init__(self, name, age):
            super().__init__(name)
            self.age = age

    c = Child("Alice", 25)
    print(c.name, c.age)


10. Real-World Inheritance Example
===================================

Demonstrates inheritance in an object-oriented system:

.. code-block:: python

    class Vehicle:
        def start(self):
            print("Vehicle started")

    class Car(Vehicle):
        def drive(self):
            print("Car is driving")

    class Bike(Vehicle):
        def ride(self):
            print("Bike is riding")

    car = Car()
    bike = Bike()

    car.start()
    car.drive()

    bike.start()
    bike.ride()


Python Multiple Inheritance
++++++++++++++++++++++++++++

1. What is Multiple Inheritance
================================

Multiple inheritance occurs when a class inherits from more than one parent class:

.. code-block:: python

    class Father:
        def skill1(self):
            print("Driving")

    class Mother:
        def skill2(self):
            print("Cooking")

    class Child(Father, Mother):
        pass

    c = Child()
    c.skill1()
    c.skill2()

The child class gains features from all parent classes.


2. Basic Multiple Inheritance Structure
========================================

The child class can access methods from both parents:

.. code-block:: python

    class A:
        def show_a(self):
            print("Class A")

    class B:
        def show_b(self):
            print("Class B")

    class C(A, B):
        pass

    obj = C()
    obj.show_a()
    obj.show_b()


3. Overlapping Method Names
============================

Python follows Method Resolution Order (MRO) to determine which method to invoke:

.. code-block:: python

    class A:
        def display(self):
            print("From A")

    class B:
        def display(self):
            print("From B")

    class C(A, B):
        pass

    obj = C()
    obj.display()


4. Understanding Method Resolution Order (MRO)
===============================================

MRO defines the order of class traversal: C → A → B → object

.. code-block:: python

    class A:
        def show(self):
            print("A")

    class B:
        def show(self):
            print("B")

    class C(A, B):
        pass

    print(C.mro())


5. Calling Parent Methods Explicitly
====================================

Allows execution of logic from multiple parents:

.. code-block:: python

    class A:
        def process(self):
            print("Process A")

    class B:
        def process(self):
            print("Process B")

    class C(A, B):
        def process(self):
            A.process(self)
            B.process(self)

    c = C()
    c.process()


6. Multiple Inheritance with Constructors
==========================================

Only the first parent's constructor executes due to MRO:

.. code-block:: python

    class A:
        def __init__(self):
            print("Constructor A")

    class B:
        def __init__(self):
            print("Constructor B")

    class C(A, B):
        def __init__(self):
            super().__init__()

    c = C()


7. Cooperative Multiple Inheritance Using super()
==================================================

Demonstrates cooperative method chaining through MRO:

.. code-block:: python

    class A:
        def __init__(self):
            print("A init")
            super().__init__()

    class B:
        def __init__(self):
            print("B init")
            super().__init__()

    class C(A, B):
        def __init__(self):
            print("C init")
            super().__init__()

    c = C()


8. Diamond Problem Example
===========================

Python resolves this ambiguity using MRO, avoiding duplicate calls:

.. code-block:: python

    class Grandparent:
        def greet(self):
            print("Hello from Grandparent")

    class Parent1(Grandparent):
        pass

    class Parent2(Grandparent):
        pass

    class Child(Parent1, Parent2):
        pass

    c = Child()
    c.greet()


9. Visualizing the Inheritance Hierarchy
=========================================

Helps understand order of class resolution for debugging:

.. code-block:: python

    class X:
        pass

    class Y(X):
        pass

    class Z(X):
        pass

    class W(Y, Z):
        pass

    print(W.mro())


10. Real-World Multiple Inheritance Example
============================================

Combines cross-cutting concerns such as logging and validation:

.. code-block:: python

    class Logger:
        def log(self):
            print("Logging data")

    class Validator:
        def validate(self):
            print("Validating data")

    class Service(Logger, Validator):
        def execute(self):
            self.log()
            self.validate()
            print("Executing service")

    service = Service()
    service.execute()


Polymorphism in Python
++++++++++++++++++++++

1. What is Polymorphism
=======================

Polymorphism allows the same interface (method or operator) to behave differently based on the object or context:

.. code-block:: python

    print(len("Python"))   # String length
    print(len([1, 2, 3]))  # List length

The same function works for multiple data types.


2. Function Polymorphism
=========================

A single function adapts behavior based on arguments:

.. code-block:: python

    def add(a, b, c=0):
        return a + b + c

    print(add(2, 3))        # 5
    print(add(2, 3, 4))     # 9


3. Built-in Polymorphism
=========================

The + operator behaves differently based on operand types:

.. code-block:: python

    print(5 + 10)          # Integer addition
    print("Hello " + "AI") # String concatenation


4. Method Overriding (Runtime Polymorphism)
============================================

Child class alters the behavior of a parent method:

.. code-block:: python

    class Animal:
        def speak(self):
            print("Animal sound")

    class Dog(Animal):
        def speak(self):
            print("Dog barks")

    pet = Dog()
    pet.speak()


5. Operator Overloading
=======================

Custom behavior for operators using magic methods:

.. code-block:: python

    class Vector:
        def __init__(self, x):
            self.x = x

        def __add__(self, other):
            return Vector(self.x + other.x)

    v1 = Vector(10)
    v2 = Vector(20)
    v3 = v1 + v2

    print(v3.x)  # Output: 30


6. Polymorphism with Different Classes
=======================================

Different objects responding to the same method call:

.. code-block:: python

    class Cat:
        def sound(self):
            print("Meow")

    class Dog:
        def sound(self):
            print("Bark")

    def make_sound(animal):
        animal.sound()

    make_sound(Cat())
    make_sound(Dog())


7. Duck Typing
==============

Behavior is determined by method presence, not class type:

.. code-block:: python

    class Car:
        def move(self):
            print("Car moving")

    class Boat:
        def move(self):
            print("Boat sailing")

    def start(vehicle):
        vehicle.move()

    start(Car())
    start(Boat())


8. Method Overloading via Default Arguments
============================================

Python simulates overloading using default parameters:

.. code-block:: python

    class Calculator:
        def multiply(self, a, b=1):
            return a * b

    calc = Calculator()
    print(calc.multiply(5))     # 5
    print(calc.multiply(5, 3))  # 15


9. Abstract Base Class Polymorphism
====================================

Ensures consistent interface across implementations:

.. code-block:: python

    from abc import ABC, abstractmethod

    class Shape(ABC):
        @abstractmethod
        def area(self):
            pass

    class Rectangle(Shape):
        def area(self):
            return 10 * 5

    shape = Rectangle()
    print(shape.area())


10. Real-World Polymorphism Example
===================================

Multiple behaviors implemented under a unified interface:

.. code-block:: python

    class Notification:
        def send(self):
            print("Sending notification")

    class Email(Notification):
        def send(self):
            print("Sending Email")

    class SMS(Notification):
        def send(self):
            print("Sending SMS")

    def notify(service):
        service.send()

    notify(Email())
    notify(SMS())


Python Operator Overloading
++++++++++++++++++++++++++++

1. What is Operator Overloading
================================

Operator overloading allows custom classes to define how standard operators behave using special (dunder) methods:

.. code-block:: python

    class Number:
        def __init__(self, value):
            self.value = value

        def __add__(self, other):
            return self.value + other.value

    n1 = Number(10)
    n2 = Number(20)

    print(n1 + n2)  # Output: 30

The + operator is redefined for the Number class.


2. Overloading the Addition Operator (+)
========================================

Implements vector addition logic:

.. code-block:: python

    class Vector:
        def __init__(self, x):
            self.x = x

        def __add__(self, other):
            return Vector(self.x + other.x)

    v1 = Vector(5)
    v2 = Vector(7)
    v3 = v1 + v2

    print(v3.x)  # Output: 12


3. Overloading the Subtraction Operator (-)
============================================

Custom logic for subtraction:

.. code-block:: python

    class Balance:
        def __init__(self, amount):
            self.amount = amount

        def __sub__(self, other):
            return Balance(self.amount - other.amount)

    b1 = Balance(100)
    b2 = Balance(40)

    result = b1 - b2
    print(result.amount)  # Output: 60


4. Overloading Multiplication Operator (*)
===========================================

Defines how objects behave with *:

.. code-block:: python

    class Repeater:
        def __init__(self, text):
            self.text = text

        def __mul__(self, times):
            return self.text * times

    r = Repeater("AI ")
    print(r * 3)  # Output: AI AI AI


5. Overloading Division Operator (/)
====================================

Implements custom division logic:

.. code-block:: python

    class Calculator:
        def __init__(self, value):
            self.value = value

        def __truediv__(self, other):
            return self.value / other.value

    c1 = Calculator(100)
    c2 = Calculator(4)

    print(c1 / c2)  # Output: 25.0


6. Overloading Equality Operator (==)
======================================

Controls object comparison behavior:

.. code-block:: python

    class Point:
        def __init__(self, x):
            self.x = x

        def __eq__(self, other):
            return self.x == other.x

    p1 = Point(5)
    p2 = Point(5)

    print(p1 == p2)  # True


7. Overloading Less Than and Greater Than
==========================================

Supports sorting and ranking operations:

.. code-block:: python

    class Score:
        def __init__(self, marks):
            self.marks = marks

        def __lt__(self, other):
            return self.marks < other.marks

        def __gt__(self, other):
            return self.marks > other.marks

    s1 = Score(85)
    s2 = Score(70)

    print(s1 > s2)  # True


8. Overloading In-place Operators (+=)
=======================================

Modifies object in-place:

.. code-block:: python

    class Counter:
        def __init__(self, value):
            self.value = value

        def __iadd__(self, other):
            self.value += other
            return self

    c = Counter(10)
    c += 5
    print(c.value)  # Output: 15


9. Overloading String Representation (str())
=============================================

Enhances readability of object display:

.. code-block:: python

    class Product:
        def __init__(self, name, price):
            self.name = name
            self.price = price

        def __str__(self):
            return f"{self.name} costs ${self.price}"

    p = Product("Laptop", 1200)
    print(p)  # Laptop costs $1200


10. Comprehensive Operator Overloading Example
===============================================

Fully custom arithmetic for a domain-specific class:

.. code-block:: python

    class ComplexNumber:
        def __init__(self, real):
            self.real = real

        def __add__(self, other):
            return ComplexNumber(self.real + other.real)

        def __sub__(self, other):
            return ComplexNumber(self.real - other.real)

        def __str__(self):
            return str(self.real)

    c1 = ComplexNumber(10)
    c2 = ComplexNumber(3)

    print(c1 + c2)  # 13
    print(c1 - c2)  # 7
