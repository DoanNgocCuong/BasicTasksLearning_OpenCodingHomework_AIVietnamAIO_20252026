---
title: "M01W03 - Classes and Objects"
datePublished: Tue Jun 24 2025 11:06:08 GMT+0000 (Coordinated Universal Time)
cuid: cmcaf6qq7000j02iha2fk4obu
slug: m01w03-classes-and-objects
tags: ai, aio2025

---

> Step into Object-Oriented Programming explores the transition from procedural to object-oriented programming. It covers key concepts such as abstraction, classes, and objects, highlighting their role in structuring code to model real-world entities. The article illustrates the benefits of object-oriented programming, including code reusability, scalability, and encapsulation through examples like library management and building math classes. It also delves into inheritance, showcasing how it enables the reuse and extension of code while maintaining a clean and efficient codebase. Additionally, it discusses naming conventions, encapsulation, and the importance of the self keyword in defining methods and accessing object attributes.

## Step into Object-Oriented Programming

### Programming

Every day, we see and use many things like taxis, stores, books, and ATMs. These are part of the **real world** . When we write a program, we take these real things and **change them into code**. This is called **abstraction**. We use **programming** to tell the computer how these things work, so it can copy them in the **digital world** . For example, we can make a program that works like a shop or a taxi app. That’s how real life becomes software!

### Procedural Programming

In procedural programming, we solve problems by writing a list of steps using **functions**. Each function does a specific job, like **adding a book** or **listing all books**. All the data (like the list of books) is stored in one place and shared between functions. In this example, we use two functions: `add_book()` to save a book’s title and author, and `list_books()` to print all the books.

The program runs from top to bottom, following the steps one by one. This method works well for small projects, but as programs grow bigger, it can get harder to manage because all functions use the same data.

```python
# Global list of books
books = []

def add_book(title, author):
    books.append({"title": title, "author": author})

def list_books():
    for book in books:
        print(f"{book['title']} by {book['author']}")

# Main program
add_book("1984", "George Orwell")
add_book("The Hobbit", "J.R.R. Tolkien")
list_books()
```

In this session, **Library Management** is explained in a simple and detailed way in the sections below.

## Abstraction

In Object-Oriented Programming (OOP), **abstraction** means we take complex real-world things and turn them into simple models in code. For example, in social media apps like Facebook or Instagram, we deal with **users**. In code, we can create a **User object**.

This object has **attributes** like name, birthday, gender, phone number, and email — these are pieces of information about the user. It also has **methods**, which are actions the user can do, like adding friends, making a post, sending a message, or liking and commenting. By using objects like this, programmers can write code that is easier to understand, reuse, and grow.

## Library Management in Object-Oriented Programming (OOP)

Managing a library may sound simple at first — you have **books**, **readers**, and **librarians**. But when it comes to building a software system for it, we need to think in a more organized way. That’s where **Object-Oriented Programming (OOP)** comes in.

### Problem Definition

In a real library, we deal with different parts:

* **Books** that hold content
    
* **Readers** who borrow books
    
* **Librarians** who manage the process
    
* A **process** that connects them (borrowing, returning, checking)
    

OOP helps us turn these into **objects** in our program.

### Classes

Each real-world thing becomes a **class** in code:

```python
class Book
class Reader
class Librarian
```

These classes define what the object is and what it can do. For example, a `Book` class tells us what a book has (attributes) and can do (methods).

### Abstraction

We don’t need every detail — just the important parts.  
For a **Book**, useful attributes might include:

* Name
    
* Author
    
* Year of Publication
    
* Language
    
* Size/Weight
    
* Old or New
    
* Publishing House
    
* Color
    

Abstraction helps us **simplify complexity** and focus only on what's needed to solve the problem.

### What Do We Really Need?

Now, we design the data we’ll manage in the system.  
Here’s a simple **book table** for a library:

| Title | Author | Room Time | Is Borrowed |
| --- | --- | --- | --- |
| Mastery | A | 5d | True |
| Five Forms of Intel | B | 3d | False |
| Python Programming | C | 1d | True |
| Machine Learning | D | 0d | False |

This table shows how OOP lets us store **important data** and manage it easily through programming.

### Conclusion

OOP isn't just about code — it's about thinking like a designer. We look at real life, find the **important parts**, and turn them into **structured code**. That’s the power of **abstraction and classes** in building systems like library management!

## Class & Object

In object-oriented programming, a class is a blueprint for creating objects (a particular data structure), providing initial values for state (member variables or attributes), and implementations of behavior (member functions or methods).

### Class & Object: The Blueprint and the Product

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750524465618/0d1746ee-09d5-422a-91a4-22338608f254.png align="center")

A **class** is like a **blueprint** — it defines what something is and how it behaves.  
An **object** is an actual item made using that blueprint.

Think of a `Book` class like a car design — it can produce many real objects: "Mastery", "1984", etc.

```python
book1 = Book("Mastery", "Robert Greene")
book2 = Book("1984", "George Orwell")
```

Each book object will have its own **title**, **author**, and other information.

### Constructor: Setting Things Up

The **constructor** is a special function called `__init__()` in Python.  
It runs automatically when we create a new object, setting the **starting values** for the object’s attributes.

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
        self.rm_time = 0
        self.is_borrow = False
```

So when we write `Book("1984", "George Orwell")`, the constructor sets up all the book's details.

## Methods: What the Object Can Do

Objects can also **do things** using their **methods**. In this example, books can be **borrowed** or **returned**:

```python
def borrow(self):
    if not self.is_borrowed:
        self.is_borrowed = True
        print(f"Bạn đã mượn: {self.title}")
    else:
        print(f"Sách {self.title} đã có người mượn.")

def return_book(self):
    self.is_borrowed = False
    print(f"Đã trả sách: {self.title}")
```

These methods allow us to **interact** with the object just like in the real world.

## Class and Object

### Syntax for creating a class

A **class** is like a **blueprint** or plan for creating objects. It tells the computer what **attributes** (data) and **methods** (actions) an object should have.

In this example, we create a class called `Rectangle`. This class has:

* **Attributes**: `width`, `height`
    
* **Methods**: `calculate_area()`, `calculate_perimeter()`
    

```python
class Rectangle:
    def __init__(self, my_width, my_height):
        self.width = my_width
        self.height = my_height

    def calculate_area(self):
        self.area = self.width * self.height
        return self.area

    def calculate_perimeter(self):
        return (self.width + self.height) * 2
```

An **object** is a **real item** created using a class. You can make many objects from one class, each with different values.

```python
my_rec = Rectangle(4, 7)
print(my_rec.calculate_area())         # Output: 28
print(my_rec.calculate_perimeter())    # Output: 22
```

Here, `my_rec` is an **object** (or **instance**) of the `Rectangle` class.

### Class - Constructor

The **init**() function is called automatically every time the class is being used to create a new object.

The **init**() method is used to initialize the attributes of the object with specific values.

```python
class Rectangle:
    def __init__(self, my_width, my_height):
        self.width = my_width
        self.height = my_height
```

We don’t have to define **all attributes** in the constructor. We can add more in other methods:

```python
def calculate_area(self):
    self.area = self.width * self.height
    return self.area
```

We can view all the attributes of an object using `vars()`:

```python
print(vars(my_rec))
# Output: {'width': 4, 'height': 7, 'area': 28}
```

**NOTE:** Not all attributes have to be initialized in the **init**() method. Attributes can be created in other methods.

### Two Ways to Declare Classes in Python

When working with **classes and objects** in Python, there are multiple ways to define values inside the class. Let’s explore two common approaches using a `Rectangle` class.

* ### Fixed Class Attributes (Not Recommended for Most Cases)
    
    ```python
    class Rectangle:
        width = 6
        height = 8
    ```
    
    In this approach, `width` and `height` are **class-level attributes**. All objects created from this class will share the same values unless you change them **after creation**:
    
    ```python
    my_rec = Rectangle()
    print(my_rec.width)   # 6
    print(my_rec.height)  # 8
    
    your_rec = Rectangle()
    your_rec.width = 16
    your_rec.height = 18
    print(your_rec.width) # 16
    print(your_rec.height)# 18
    ```
    
* Using a Constructor with `__init__()` (Recommended)
    
    ```python
    class Rectangle:
        def __init__(self, my_width, my_height):
            self.width = my_width
            self.height = my_height
    ```
    
    This version allows each object to be created with **custom values**:
    
    ```python
    my_rec = Rectangle(4, 7)
    print(my_rec.calculate_area())        # 28
    print(my_rec.calculate_perimeter())   # 22
    ```
    

### Understanding the `self` Keyword in Python Classes

What Happens If We Forget `self`?

```python
class Rectangle:
    def __init__(my_width, my_height):
        width = my_width
        height = my_height
my_rec = Rectangle(4, 7)
```

**ERROR:**

```javascript
TypeError: __init__() takes 2 positional arguments but 3 were given
```

The `self` keyword is used to refer to **the current object** that is being created or used. It lets each object **store and access its own data**.

```python
class Rectangle:
    def __init__(self, my_width, my_height):
        self.width = my_width
        self.height = my_height
```

Now `self.width` and `self.height` are **attributes** of the object, not just temporary local variables.

Using `self` in Methods

```python
def calculate_area(self):
    return self.width * self.height

def calculate_perimeter(self):
    return (self.width + self.height) * 2
```

These methods **use the object’s own data** through `self`.

**Example Output**

```python
my_rec = Rectangle(4, 7)
print(my_rec.calculate_area())        # 28
print(my_rec.calculate_perimeter())   # 22
```

### Some rules when using self keyword

1. Rule 1: `self` Must Be the First Parameter in a Method
    
    When you write a method inside a class, the first parameter **must be** `self`. This allows the method to access the object that calls it.
    
    ```python
    class Calculator:
        def add(self, a, b):
            return a + b
    
        def subtract(self, a, b):
            return a - b
    ```
    
    Even though the method works with `a` and `b`, it still needs `self` first.
    
2. Rule 2: You Don’t Pass `self` When Calling a Method
    
    When you use the method, **you do not** pass `self` manually. Python does it for you automatically.
    
    ```python
    calc = Calculator()
    
    result_add = calc.add(10, 5)          # self is passed by Python
    result_sub = calc.subtract(10, 5)
    
    print("Addition result:", result_add)      # Output: 15  
    print("Subtraction result:", result_sub)  # Output: 5
    ```
    
    Behind the scenes, `calc.add(10, 5)` is like: `Calculator.add(calc, 10, 5)`
    

### Understanding Classes and Objects in Python

1. Replacing `self` Keyword
    
    In Python, you **can technically rename** `self`, but it's a convention to use `self` as the first parameter of instance methods.
    
    ```python
    class Point:
        def __init__(this, x, y):
            this.x = x
            this.y = y
    
        def func(this, factor):
            return (this.x + this.y) * factor
    
    my_point = Point(4, 5)
    print(my_point.func(2))  # Output: 18
    ```
    
2. How We Create an Object
    
    When we create an object in Python using a class, the `__init__()` method (also known as the constructor) is automatically called to initialize the object.
    
    ```python
    class Rectangle:
        def __init__(self, my_width, my_height):
            self.width = my_width
            self.height = my_height
    
        def calculate_area(self):
            return self.width * self.height
    
        def calculate_perimeter(self):
            return (self.width + self.height) * 2
    
    my_rec = Rectangle(4, 7)
    ```
    
3. The Special Method: `__call__()`
    
    The `__call__()` method allows an instance of a class to be called like a function!
    
    ```python
    class Greeting:
        def __init__(self, name):
            self.name = name
    
        def __call__(self, greeting):
            print(f"{greeting}, {self.name}!")
    
    greet = Greeting("Alice")
    
    greet("Hello")   # Output: Hello, Alice!
    greet("Good morning")  # Output: Good morning, Alice!
    ```
    

## Naming Conventions in Python

1. Example from YOLOv5
    
    ```python
    class Detect(nn.Module):
        # YOLOv5 Detect head for detection models
        def __init__(self, nc=80, anchors=(), ch=(), inplace=True):
            super().__init__()
            self.nc = nc  # number of classes
            self.no = nc + 5  # number of outputs per anchor
            self.nl = len(anchors)  # number of detection layers
            self.na = len(anchors[0]) // 2  # number of anchors
            self.grid = [torch.empty(0)] * self.nl  # init grid
            self.anchor_grid = [torch.empty(0)] * self.nl  # init anchor grid
            self.register_buffer("anchors", torch.tensor(anchors).float().view(self.nl, -1, 2))
            self.m = nn.ModuleList([nn.Conv2d(x, self.no, 1) for x in ch])
            self.inplace = inplace
    ```
    
    **Pattern highlights:**
    
    * Snake\_case for variables: `anchor_grid`, `anchor`, `anchor_grid`
        
    * Class name in PascalCase: `Detect`
        
2. Example from Diffusion Models
    
    ```python
    class GaussianDiffusion(Module):
        def __init__(
            self,
            *,
            model,
            image_size,
            sampling_timesteps=1000,
            loss_type="l2",
            objective="pred_noise",
            beta_schedule="sigmoid",
            ddim_sampling_eta=0.0,
            auto_normalize=True,
            clip_denoised=True,
            prediction_scale=False,
            skip_scale=False,
            device=None,
        ):
            super().__init__()
            assert not (objective == "pred_x0" and model.channels != model.out_dim)
            self.model = model
            self.channels = model.channels
            self.self_condition = model.self_condition
    ```
    
    **Pattern highlights:**
    
    * Parameters and attributes: all in **snake\_case**
        
    * Constants are written in **UPPERCASE** when applicable
        
    * Long parameter lists use line breaks and indentation for clarity
        
3. Method Naming Patterns in Action
    
    ```python
    class GaussianDiffusion(Module):
        def predict_start_from_noise(self, x_t, t, noise):
            return (
                extract(self.sqrt_recip_alphas_cumprod, t, x_t.shape) * x_t -
                extract(self.sqrt_recipm1_alphas_cumprod, t, x_t.shape) * noise
            )
    
        def predict_noise_from_start(self, x_t, t, x0):
            return (
                extract(self.sqrt_alphas_cumprod, t, x_t.shape) * x0 -
                extract(self.sqrt_one_minus_alphas_cumprod, t, x_t.shape) * x_t
            )
    ```
    
    **Pattern highlights:**
    
    * Method names use **verbs + descriptive phrases**
        
    * Words separated by underscores
        
4. Simple Example for Naming
    
    ```python
    class SuperCat:
        def __init__(self, cat_name, cat_color, cat_age):
            self.cat_name = cat_name
            self.cat_color = cat_color
            self.cat_age = cat_age
    
        def get_name(self):
            return self.cat_name
    
        def set_name(self, new_name):
            self.cat_name = new_name
    
    my_cat = SuperCat("Joey", "white", "2")
    print(my_cat.get_name())  # Joey
    
    my_cat.set_name("Rachel")
    print(my_cat.get_name())  # Rachel
    ```
    
    **Naming Style Guide:**
    
    * **Class names:** PascalCase (`SuperCat`)
        
    * **Attributes & methods:** snake\_case (`cat_name`, `get_name`)
        
    * **Methods:** Start with verbs (`get_`, `set_`)
        
    * **Constants (if used):** UPPERCASE (`IMAGE_SIZE = 128`)
        

## Inheritance

### With vs Without Inheritance

1. With Inheritance
    
    ```python
    class Animal:
        def __init__(self, name):
            self.name = name
    
        def eat():
            print("Eating")
    
        def speak(self):
            print(f"{self.name} makes a sound.")
    
    class Dog(Animal):
        def speak(self):
            print(f"{self.name} says Woof!")
    
    class Cat(Animal):
        def speak(self):
            print(f"{self.name} says Meow!")
    ```
    
    In this structure:
    
    * `Dog` and `Cat` **inherit** from `Animal`
        
    * Shared behavior like `name` and `eat()` exists only **once** in `Animal`
        
    * Each subclass **overrides** `speak()` to provide specific behavior
        
2. Without Inheritance
    
    ```python
    class Dog:
        def __init__(self, name):
            self.name = name
    
        def eat():
            print("Eating")
    
        def speak(self):
            print(f"{self.name} says Woof!")
    
    class Cat:
        def __init__(self, name):
            self.name = name
    
        def eat():
            print("Eating")
    
        def speak(self):
            print(f"{self.name} says Meow!")
    ```
    
    This leads to **duplicate code**, especially in methods like `eat()` and attribute handling ([`self.name`](http://self.name)). Maintenance becomes harder as the codebase grows.
    

### What is Inheritance?

**Inheritance** is a mechanism in object oriented programming (OOP) that allows a new class to inherit the **attributes** and **methods** of an existing class.

**Syntax**

```python
class SuperClass:
    # Attributes and methods of SuperClass

class SubClass(SuperClass):
    # Inherits everything from SuperClass
    # Can have its own methods and attributes too
```

**Example**

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def eat(self):
        print("Eating")

    def speak(self):
        print(f"{self.name} makes a sound.")

class Dog(Animal):
    def speak(self):
        print(f"{self.name} says Woof!")

class Cat(Animal):
    def speak(self):
        print(f"{self.name} says Meow!")
```

#### Benefits of Inheritance

1. **Code Reusability**  
    You don’t have to rewrite shared logic. Just define it once in the superclass and inherit it wherever needed.
    
2. **Scalability**  
    Easily extend and enhance functionality by modifying the superclass or overriding methods in the subclass.
    
3. **Cleaner Code**  
    Like using variables to avoid redundancy, inheritance structures your code efficiently and reduces duplication.
    

**Example**

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def make_sound(self):
        return "Some generic animal sound"

class Cat(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # Inherit name from Animal
        self.breed = breed

    def info(self):
        return f"{self.name} is a Cat of breed {self.breed}"
my_cat = Cat(name="Joey", breed="Siamese")
print(my_cat.info())         # Joey is a Cat of breed Siamese
print(my_cat.make_sound())   # Some generic animal sound
```

### Overriding in Inheritance

One powerful feature of inheritance is **method overriding** — where a subclass redefines a method inherited from its superclass to change or extend its behavior.

**Example**

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound.")

class Dog(Animal):
    def speak(self):
        print(f"{self.name} says Woof!")

class Cat(Animal):
    def speak(self):
        print(f"{self.name} says Meow!")
```

### Types of Inheritance: Single Inheritance

**Single Inheritance** is when a subclass inherits from **only one** superclass. It’s the most straightforward and common form of inheritance.

**Example**

```python
class Parent:
    def __init__(self, name):
        self.name = name

    def display(self):
        print(f"Parent Name: {self.name}")

class Child(Parent):
    def __init__(self, name, age):
        super().__init__(name)
        self.age = age

    def display(self):
        super().display()
        print(f"Child Age: {self.age}")
```

```javascript
#output
Parent Name: Alice
Child Age: 20
```

## Building Reusable Math Classes with Inheritance

When you find yourself rewriting similar functions in multiple classes, it’s a clear sign you should use **inheritance**.

We first define a **base class** `Math1` that provides basic functionality:

```python
class Math1:
    def is_even(self, number):
        return number % 2 == 0

    def factorial(self, number):
        result = 1
        for i in range(1, number + 1):
            result *= i
        return result
```

Then we create a more advanced class `Math2` that **inherits** from `Math1` and adds more functionality:

```python
class Math2(Math1):
    def estimate_euler(self, number):
        result = 1
        for i in range(1, number + 1):
            result += 1 / self.factorial(i)
        return result
```

### Why Inheritance Works Here

* `Math2` **doesn’t duplicate** code for `is_even()` or `factorial()` — it inherits them from `Math1`.
    
* You can easily test `Math2` using all three methods:
    
    ```python
    math2 = Math2()
    print(math2.is_even(6))         # True
    print(math2.factorial(5))       # 120
    print(math2.estimate_euler(8))  # ≈ 2.71828
    ```
    

### Euler's Number Explained

The method `estimate_euler(n)` is based on this mathematical expansion:

This is a great example of **extending base functionality** — we’re building on what’s already defined in `Math1` to do more in `Math2`.

### Summary of Concepts

| Class | Methods Available |
| --- | --- |
| Math1 | `is_even()`, `factorial()` |
| Math2 | Inherits `is_even()`, `factorial()`, adds `estimate_euler()` |

## Bonus Example and Knowledge

### Classes and Objects

**The** `Date` **Class**

```python
class Date:
    def __init__(self, day, month, year):
        self.day = day
        self.month = month
        self.year = year
    
    def __call__(self):
        return f"{self.day:02d}/{self.month:02d}/{self.year}"
```

* The `Date` class models a calendar date.
    
* The `__init__` method initializes day, month, and year attributes.
    
* The `__call__` method allows the object itself to be called like a function to return a nicely formatted date string.
    

```python
birth = Date(4, 1, 1643)
print(birth())  # Output: 04/01/1643
```

**The** `Person` **Class**

```python
class Person:
    def __init__(self, name, birth):
        self.name = name
        self.birth = birth
    
    def info(self):
        print(f"Name: {self.name} – Birth: {self.birth()}")
```

* The `Person` class has two attributes: `name` (a string) and `birth` (a `Date` object).
    
* This demonstrates **composition**: the `Person` class contains a `Date` object as an attribute.
    
* The `info()` method displays the person's name and formatted birth date.
    

```python
physicist = Person("Isaac Newton", birth)
physicist.info()
# Output: Name: Isaac Newton – Birth: 04/01/1643
```

### Lists and Classes

**Sorting a List of Integers**

```python
list_int = [1, 5, 4, 7, 3, 9]
list_int.sort()
print(list_int)
# Output: [1, 3, 4, 5, 7, 9]
```

**Defining a** `Square` **Class**

```python
class Square:
    def __init__(self, side):
        self.side = side

    def compute_area(self):
        return self.side * self.side

    def describe(self):
        print(f"Side is {self.side}")
```

Now we create a list of `Square` objects:

```python
s1 = Square(3)
s2 = Square(8)
s3 = Square(1)
s4 = Square(6)
s5 = Square(5)

list_squares = [s1, s2, s3, s4, s5]
```

Looping through the list:

```python
for square in list_squares:
    square.describe()
```

---

**What Happens When You Try to Sort?**

```python
list_squares.sort()
```

You’ll get this error:

```javascript
TypeError: '<' not supported between instances of 'Square' and 'Square'
```

Because Python doesn’t know **how** to compare two `Square` objects — should it use the side length, the area, or some other attribute?

---

**Defining Comparison Criteria**

There are two ways to help Python sort:

#### Define the `__lt__` Method

```python
def __lt__(self, other):
    return self.side < other.side
```

With this method added to the `Square` class, Python now knows how to compare `Square` objects based on their `side` length.

```python
list_squares.sort()
```

---

#### Use a Sorting Key (More Flexible)

An alternative approach is to use the `key` parameter with `sort()`:

```python
list_squares.sort(key=lambda x: x.side)
```

This is very flexible — you can sort by side, area, or any attribute — without modifying the class.

### Encapsulation

**Encapsulation** is one of the core principles of object-oriented programming (OOP). It’s about controlling access to the internal state and behavior of an object — protecting data from unauthorized access and accidental modification.

In Python, we achieve encapsulation using **access modifiers**:

---

**Access Modifiers**

1. **Public**
    
    * Accessible from anywhere.
        
    * No special notation.  
        Example: [`self.name`](http://self.name)
        
2. **Protected**
    
    * Accessible within the class and its subclasses.
        
    * Convention: prefix with a single underscore `_`.  
        Example: `self._color`
        
3. **Private**
    
    * Accessible only within the class.
        
    * Prefix with double underscore `__`.  
        Example: `self.__age`
        

---

**Example: Public Access**

```python
class Cat:
    def __init__(self, name, color, age):
        self.name = name
        self.color = color
        self.age = age

cat = Cat('Calico', 'Black, white, and brown', 2)
print(cat.name)
print(cat.color)
print(cat.age)
```

Output:

```javascript
Calico
Black, white, and brown
2
```

Here, all attributes are **public** and can be accessed directly.

---

**Example: Private Access**

```python
pythonCopyEditclass Cat:
    def __init__(self, name, color, age):
        self.name = name
        self.color = color
        self.__age = age  # private

cat = Cat('Calico', 'Black, white, and brown', 2)
print(cat.name)
print(cat.color)
print(cat.__age)  # Raises AttributeError!
```

Trying to access `__age` directly will raise an `AttributeError`.

---

**Access Private Data with Getters/Setters**

```python
class Cat:
    def __init__(self, name, color, age):
        self.name = name
        self.color = color
        self.__age = age  # private

    def get_age(self):
        return self.__age

    def set_age(self, age):
        self.__age = age

cat = Cat('Calico', 'Black, white, and brown', 2)
print(cat.get_age())  # 2
cat.set_age(4)
print(cat.get_age())  # 4
```

Using **getter** and **setter** methods allows controlled access to private data.

---

**Protected Data and Inheritance**

```python
class Animal:
    def __init__(self, name, color):
        self.name = name
        self._color = color  # protected

    def _make_sound(self):
        return "Some generic animal sound"

class Cat(Animal):
    def __init__(self, name, color, breed):
        super().__init__(name, color)
        self.breed = breed

    def info(self):
        return f"{self.name} is a {self._color} Cat of breed {self.breed}"

    def sound(self):
        return self._make_sound()

my_cat = Cat("Joey", "white", "Siamese")
print(my_cat._color)          # allowed but discouraged
print(my_cat._make_sound())   # allowed but discouraged
```

**Protected attributes and methods** are intended for internal use but can still be accessed in subclasses.

## Summary

### **Classes and Objects**

* **Class Diagram**  
    Visual map of classes, attributes, methods, and relationships between them.
    
* **Creating Classes and Objects**  
    Classes are templates; objects are instances of those templates.
    
* **Constructor (**`__init__`)  
    Special method to initialize new objects with specific values.
    
* `self` Keyword  
    Refers to the current object instance; used to access attributes and methods.
    
* **Special Method (**`__call__`)  
    Allows objects to be used like functions.
    
* **Naming Convention**  
    Standard ways of naming classes and variables for clarity and consistency.
    
* **Other Uses of Classes**  
    Classes can also serve as attributes of other classes or be part of more complex structures (composition, etc.).
    

---

### **Inheritance**

* **Definition and Syntax**  
    Mechanism where one class (child) can derive properties and behaviors from another class (parent).
    
* **Override**  
    Child class can provide a new version of a method inherited from the parent class.
    
* **Types of Inheritance**
    
    * Single
        
    * Multiple
        
    * Multilevel
        
    * Hierarchical
        

*Reference source (original document):* [Classes and Objects](https://aivnlearning.edu.vn/api/files/68317ab8519c0e157fb51489/Documents%2F2025-5%2FM01W03%20-%20Classes%20and%20Objects%2FClasses%20and%20Objects_V2.pdf)