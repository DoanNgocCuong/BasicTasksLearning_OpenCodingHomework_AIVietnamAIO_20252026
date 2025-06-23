---
title: "M01W03W - [v4] OOP (Custom PyTorch Class)"
datePublished: Mon Jun 23 2025 06:38:43 GMT+0000 (Coordinated Universal Time)
cuid: cmc8q6z7f002v02l16nwtbcim
slug: m01w03w-v4-oop-custom-pytorch-class

---

![Comprehensive overview of Object-Oriented Programming concepts and their relationships](https://pplx-res.cloudinary.com/image/upload/v1750654585/pplx_code_interpreter/6f87f4cf_xb0f9i.jpg align="left")

## **I. Introduction to Object-Oriented Programming**

### **1.1 What is OOP and Why It Matters**

![Comprehensive comparison of the four fundamental Object-Oriented Programming principles](https://pplx-res.cloudinary.com/image/upload/v1750657401/pplx_code_interpreter/c30f5ed1_m5yyuw.jpg align="left")

Object-Oriented Programming is a programming paradigm based on the concept of "objects," which represent both data and behavior. Unlike procedural programming that focuses on functions and procedures, OOP structures code around objects that can interact with each other, making it easier to model real-world entities and their relationship . This approach provides several critical advantages including modularity, reusability, scalability, and ease of troubleshooting.

The fundamental concept revolves around creating objects that contain both data (attributes) and functions (methods) that operate on that data. This encapsulation of related functionality into discrete units forms the foundation of modern software architecture, enabling developers to build complex systems that are both understandable and maintainable.`   `

## **II. Fundamental OOP Concepts**

### **2.1 Classes and Objects**

A class serves as a blueprint or template for creating objects, defining the structure and behavior that instances of the class will possess. The relationship between classes and objects can be understood through the analogy of architectural blueprints and actual buildings: a class defines the specifications, while objects are the concrete implementations. In Python, classes are defined using the `class` keyword, followed by the class name and a colon.

Objects are instances of classes that contain specific data and can perform actions defined by their class. Each object maintains its own state through instance variables while sharing methods defined in the class. The creation of objects involves calling the class as if it were a function, which internally invokes the `__init__` method to initialize the new instance.

```python
class Cat:
    def __init__(self, name, age):
        self._name = name  # Protected attribute
        self._age = age
    
    def describe(self):
        print(f'Name: {self._name} - Age: {self._age}')
    
    def increase_age(self, years):
        self._age += years
    
    def __call__(self):
        self.describe()

cat = Cat('Tung', 20)
cat.describe()  # Output: Name: Tung - Age: 20
```

### **2.2 Attributes and Methods**

Attributes represent the data or state that objects maintain, while methods define the operations or behaviors that objects can perform. In Python, attributes can be defined at the class level (shared by all instances) or at the instance level (unique to each object). Instance attributes are typically initialized within the `__init__` method using the `self` parameter.

Methods are functions defined within a class that operate on the object's data. The first parameter of any method must be `self`, which provides a reference to the current instance and allows access to the object's attributes and other methods. This mechanism enables objects to maintain and manipulate their internal state while providing controlled access to external code.  

### **2.3 The** `self` Keyword and Instance Creation

  
The `self` keyword serves as a reference to the current instance of a class, enabling access to instance attributes and methods from within the class definition. This parameter is automatically provided when methods are called on objects, though it must be explicitly included in method definitions.

The `__init__` method, often called the constructor, is automatically invoked when a new object is created. This special method allows classes to initialize instance variables and perform any necessary setup procedures. The `__init__` method does not return a value and serves specifically to establish the initial state of new objects.

## **III. The Four Pillars of OOP**

### **3.1 Encapsulation and Data Hiding**

Encapsulation represents the practice of bundling data and methods that operate on that data within a single unit while restricting direct access to internal implementation details. This principle promotes data security by controlling how external code can interact with an object's internal state. Python implements encapsulation through naming conventions and access modifiers that indicate the intended visibility of attributes and methods.

```python
class Bike:
    def __init__(self, make, model):
        self._make = make        # Protected attribute
        self.__model = model     # Private attribute

    def start_engine(self):
        print(f"{self._make} {self.__model} engine started")

    def __drive(self):
        print(f"{self._make} {self.__model} is driving")

my_bike = Bike("Tung","ABC123")
my_bike.start_engine()         # Public method
print(my_bike._make)           # Accessing protected attribute
print(my_bike._Bike__model)    # Accessing private attribute (name mangling)
```

### **3.2 Inheritance and Code Reuse**

```python
class Employee:
    def __init__(self, name, salary):
        self._name = name
        self._salary = salary
    
    def compute_salary(self):
        return self._salary

class Manager(Employee):  # Manager inherits from Employee
    def __init__(self, name, salary, bonus):
        super().__init__(name, salary)  # Call parent constructor
        self._bonus = bonus
    
    def compute_salary(self):  # Method overriding
        return super().compute_salary() + self._bonus
```

Inheritance enables the creation of new classes based on existing ones, allowing child classes to inherit attributes and methods from parent classes. This mechanism promotes code reuse by eliminating the need to rewrite common functionality, while enabling specialization through method overriding and additional features. Python supports single inheritance (one parent class) and provides the `super()` function to access parent class methods.

### **3.3 Polymorphism and Interface Consistency**

Polymorphism allows objects of different classes to be treated as instances of a common superclass, enabling the same interface to be used for different underlying forms. This principle manifests in Python through method overriding, where child classes provide specific implementations of methods defined in parent classes. Duck typing, a Python-specific feature, enables polymorphism without explicit inheritance relationships.

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    def speak(self):
        print("Woof, Woof")

class Cat(Animal):
    def speak(self):
        print("Meow, Meow")

def make_animal_speak(animal):
    animal.speak()

dog = Dog()
cat = Cat()
make_animal_speak(dog)  # Output: Woof, Woof
make_animal_speak(cat)  # Output: Meow, Meow
```

### **3.4 Abstraction and Complexity Management**

Abstraction involves hiding implementation details while exposing only essential features and interfaces. This principle simplifies the interaction with complex systems by providing high-level interfaces that encapsulate low-level operations. Python implements abstraction through abstract base classes (ABC) using the `abc` module and `@abstractmethod` decorator.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def compute_area(self):
        pass
    
    @abstractmethod  
    def compute_perimeter(self):
        pass

class Square(Shape):
    def __init__(self, side):
        self._side = side
    
    def compute_area(self):
        return self._side * self._side
    
    def compute_perimeter(self):
        return 4 * self._side
```

![Python Access Modifiers: Understanding encapsulation and visibility scope](https://pplx-res.cloudinary.com/image/upload/v1750657491/pplx_code_interpreter/50c18333_y1vzyi.jpg align="left")

## **IV. Python-Specific OOP Features**

### **4.1 Access Modifiers: Public, Protected, and Private**

Python implements access control through naming conventions rather than strict keyword-based access modifiers. Public attributes and methods have no special prefix and can be accessed from anywhere in the program. Protected members use a single underscore prefix (\_) and are intended for use within the class and its subclasses, though the interpreter does not enforce this.

Private attributes and methods employ a double underscore prefix (\_\_) and trigger name mangling, making them accessible only within the defining class. This mechanism provides the strongest level of encapsulation in Python, though the mangled names can still be accessed with knowledge of the internal naming scheme. Understanding these conventions is essential for writing maintainable and secure Python code.

### **4.2 Special Methods and Magic Functions**

Special methods, also known as magic methods or dunder methods, enable Python objects to integrate seamlessly with built-in functions and operators. These methods have names surrounded by double underscores and provide hooks for customizing object behavior. Common special methods include `__init__` for initialization, `__str__` for string representation, and `__call__` for making objects callable.

The `__call__` method deserves particular attention as it allows objects to behave like functions, enabling elegant APIs and functional programming patterns. Implementing `__call__` makes objects callable, which is particularly useful for creating function-like objects that maintain state. This feature is extensively used in frameworks like PyTorch for creating neural network layers.

### **4.3 Property Decorators and Getters/Setters**

Property decorators provide a Pythonic way to implement getters and setters while maintaining attribute-like access syntax. The `@property` decorator converts a method into a getter, allowing it to be accessed like an attribute. The corresponding `@attribute_name.setter` decorator enables the creation of setter methods with validation and control logic.

This approach enables developers to add validation, computation, or side effects to attribute access without changing the client code interface.

## **V. Advanced OOP Concepts**

### **5.1 Delegation and Composition**

Delegation represents a design pattern where one object passes work to another object to achieve functionality. This pattern enables code reuse through composition rather than inheritance, promoting flexibility and reducing coupling between components. In Python, delegation is typically implemented by storing references to other objects and forwarding method calls to them.

```python
class Date:
    def __init__(self, day, month, year):
        self._day = day
        self._month = month
        self._year = year
    
    def describe(self):
        print(f'{self._day}/{self._month}/{self._year}')

class Person:
    def __init__(self, name, date_of_birth):
        self._name = name
        self._date_of_birth = date_of_birth  # Composition
    
    def describe(self):
        print(self._name)
        self._date_of_birth.describe()  # Delegation
```

Composition builds objects using other objects, establishing "has-a" relationships rather than "is-a" relationships. This approach often provides greater flexibility than inheritance, as it allows dynamic reconfiguration of object behavior and avoids the complexities of deep inheritance hierarchies. The principle "favor composition over inheritance" has become a widely accepted best practice in object-oriented design.

### **5.2 Abstract Classes and Interfaces**

Abstract base classes (ABCs) provide a mechanism for defining interfaces and ensuring consistent implementation across related classes. The `abc` module in Python enables the creation of abstract classes that cannot be instantiated directly. Abstract methods marked with the `@abstractmethod` decorator must be implemented by all concrete subclasses.

This mechanism promotes interface consistency and provides compile-time checking for missing method implementations. Abstract classes serve as contracts that define the expected behavior of subclasses while allowing for diverse implementations. They are particularly valuable in framework design where consistent interfaces are crucial for extensibility.

### **5.3 Method Resolution Order (MRO)**

Method Resolution Order determines the sequence in which Python searches for methods in inheritance hierarchies, particularly in cases of multiple inheritance. Python uses the C3 linearization algorithm to create a consistent and predictable method lookup order. Understanding MRO is crucial for designing complex inheritance structures and avoiding method resolution conflicts.

The `super()` function respects the MRO and ensures that each class in the hierarchy is called exactly once. This behavior enables cooperative inheritance patterns where multiple classes can participate in method implementation. Proper use of MRO principles prevents common pitfalls in multiple inheritance scenarios.

**Source: M01W03W -** [**\[v4\] OOP (Custom PyTorch Class)**](https://aivnlearning.edu.vn/meeting?date=2025-06-15T17%3A00%3A00.000Z&cohort=2025&meetingId=683175ad519c0e157fb51483)