---
title: "An Introduction to Tuple, Set, and Dictionary in Data Structure"
datePublished: Tue Jun 17 2025 03:46:48 GMT+0000 (Coordinated Universal Time)
cuid: cmbzzesoq000w02jp2l4ie854
slug: an-introduction-to-tuple-set-and-dictionary-in-data-structure
tags: ai, aio2025

---

> This article explores essential data structures in Python, including tuples, sets, and dictionaries. It explains the characteristics and use cases of each structure, highlighting tuples for immutability, sets for handling unique elements, and dictionaries for efficient key-value storage. The article also covers practical examples and coding techniques, emphasizing how understanding these structures ensures efficient data management and application-specific coding in Python.

# Tuple in Python

Do you know what a data structure is? A data structure is a system used to store and organize data. It arranges data on a computer so it can be accessed and updated efficiently.

## 1D List Solution

Dr. Nguyen presents a math problem where you use Python to create a list of about 6 students in a class. You need to check their seating arrangement, which is organized in 3 rows and 2 columns. This **1D List Solution** means you solve the problem using only a basic list in Python, not a matrix.

You have 6 students:

```css
["Vinh", "An", "Toan", "Lam", "Tam", "Chuyen"]
```

They sit in **3 rows** and **2 columns**, from top to bottom, left to right:

```sql
Row 1: Vinh   | An
Row 2: Toan   | Lam
Row 3: Tam    | Chuyen
       Col 1    Col 2
```

Dr. Nguyen suggests a solution for this problem using an algorithm that can be difficult for beginners. He uses two examples, Tam and Chuyen, to explain this solution. This is a classic 2D-to-1D indexing problem that you can solve using Python.

```python
# List of students arranged row-wise
student_list = ["Vinh", "An", "Toan", "Lam", "Tam", "Chuyen"]

# Dimensions of the classroom
row_class = 3
col_class = 2

# Function to find the student at a given (row, column)
def find_student(student_list, r, c):
    index = (r - 1) * col_class + (c - 1)
    return student_list[index]

# Find student at location (3, 1)
print(find_student(student_list, 3, 1))  # Output: Tam

# Find student at location (3, 2)
print(find_student(student_list, 3, 2))  # Output: Chuyen
```

The key part of this solution is the algorithm for calculating the **index** in the **find\_student** function. It shows how we convert from 2D to 1D using simple math to solve the problem.

To get the student at row `r` and column `c`, you calculate the index in the list with the formula:

```python
index = (r - 1) * col_class + (c - 1)
```

The formula moves us row by row:

* Row 1: starts at index 0 → positions 0, 1
    
* Row 2: starts at index 2 → positions 2, 3
    
* Row 3: starts at index 4 → positions 4, 5
    

Using `(r - 1) * col_class` helps us skip whole rows, and `(c - 1)` picks the seat in the row.

| **Example** | **Result** | **Analysis** |
| --- | --- | --- |
| `find_student(student_list, 3, 1)` | Tam | Row 1: starts at index 0 |
| `find_student(student_list, 3, 2)` | Chuyen | Row 2: starts at index 2 |
| `find_student(student_list, 2, 1)` | Toan | Row 3: starts at index 4 |
| `find_student(student_list, row, col)` |  | Row 1 index: `(1 - 1) * 2 = 0` |
|  |  | Row 2 index: `(2 - 1) * 2 = 2` |
|  |  | Row 3 index: `(3 - 1) * 2 = 4` |
| `find_student(student_list, 3, 1)` | Tam | `Index = (3 - 1) * 2 + (1 - 1) = 4` |
| `find_student(student_list, 3, 2)` | Chuyen | `Index = (3 - 1) * 2 + (2 - 1) = 5` |

You can see that it can be challenging for people using Python or learning data structures for the first time. Dr. Nguyen will teach you a **2D List Solution** that is much easier and more understandable for everyone, similar to algebra.

## 2D List Solution

Dr. Nguyen suggests using a 3x**1D List** in one list instead of just a **1D list** for all.

Instead of one giant list, you can structure each row as a 1D list:

```python
row1_student = ["Vinh", "An"]
row2_student = ["Toan", "Lam"]
row3_student = ["Tam", "Chuyen"]
```

Then, we combine them into a 2D list:

```python
student_list = [row1_student, row2_student, row3_student]
```

### 2D List

* Easy to visualize and manage tabular data.
    
* Helps with real-world mapping: seating plans, spreadsheets, matrices, etc.
    
* Provides clean indexing for accessing or updating values.
    

And by combining all of this, you will have a program to solve this problem more easily.

```python
# Step 1: Define each row as a 1D list
row1_student = ["Vinh", "An"]
row2_student = ["Toan", "Lam"]
row3_student = ["Tam", "Chuyen"]

# Step 2: Combine rows into a 2D list
student_list = [row1_student, row2_student, row3_student]

# Step 3: Define a function to find a student at row r and column c (1-based indexing)
def find_student(student_list, r, c):
    return student_list[r - 1][c - 1]

# Step 4: Use the function to find students
print(find_student(student_list, 3, 1))  # Output: Tam
print(find_student(student_list, 3, 2))  # Output: Chuyen
```

## Python Basics: Mutable vs. Immutable

In Python, everything is treated as an **object**. Each object has three core attributes:

* **Identity**: The memory address (where it's stored)
    
* **Type**: The kind of object (e.g., list, string, int)
    
* **Value**: The actual data stored in the object
    

Understanding the difference between **mutable** and **immutable** types is essential for writing reliable and efficient Python code.

|  | **Mutable** | **Immutable** |
| --- | --- | --- |
| Can change value? | ✅ Yes | ❌ No |
| Examples | List, Dictionary, Set | String, Tuple, Integer |

### **Lists Are Mutable**

Mutable objects like **lists** can have their content changed **without changing their identity**.

```python
list = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
print("original list")
print(list)

# Change value at index 4
list[4] = 'hello'
print("changed list")
print(list)
#original list
#['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
#changed list
#['a', 'b', 'c', 'd', 'hello', 'f', 'g', 'h']
```

### **Strings Are Immutable**

Immutable objects like **strings** **cannot be changed** after creation.

```python
words = "AI is trending"
words[3] = 'e'  # Attempt to change character at index 3
#TypeError: 'str' object does not support item assignment
```

### **Memory Address Check**

List (Mutable):

```python
list1 = [1, 2, 3, 4, 5]
list2 = [1, 2, 3, 4, 5]

print(id(list1))  # Memory address of list1
print(id(list2))  # Memory address of list2
#Different between 2 ID
```

String (Immutable):

```python
str1 = "AI2024"
str2 = "AI2024"

print(id(str1))  # Memory address of str1
print(id(str2))  # Memory address of str2
# Two ID are the same
```

Conclusion:

| Feature | Mutable (e.g., List) | Immutable (e.g., String) |
| --- | --- | --- |
| Can change value? | ✅ Yes | ❌ No (new object is created) |
| Memory behavior | New object → new memory address | Identical values may share memory address |

## Tuple Motivation And Definition of Tuple

### **Definition**

Tuple are another kind of sequence that functions much like a list - they have elements which are indexed starting at 0. Unlike a list, once you create a tuple, you cannot alter its contents - similar to a string.

| Feature | Tuple | List |
| --- | --- | --- |
| Mutable | ❌ No | ✅ Yes |
| Faster | ✅ Yes | ❌ No |
| Hashable | ✅ (if elements are) | ❌ No |
| Safe for configs | ✅ Yes | ❌ No |
| Can be dict key | ✅ Yes | ❌ No |

### **Structure**

```python
 tuple_name = (element-1, …, element-n)
```

When you use a tuple, you can use many functions in Python like **len(), zip(), sorted(), etc.**

### **Tuple Examples**

* Swapping two variables
    
    ```python
    def swap(v1, v2):
        (v2, v1) = (v1, v2)
        return (v1, v2)
    
    v1 = 2
    v2 = 3
    (v1, v2) = swap(v1, v2)
    
    print(v1)
    print(v2)
    ```
    
* Memory requirement
    
    ```python
    # memory comparison
    import sys
    alist = [3, 4, 5, 6, 7]
    aTuple = (3, 4, 5, 6, 7)
    
    print(sys.getsizeof(alist))
    print(sys.getsizeof(aTuple))
    ```
    
* Tuple slicing
    
    ```python
    data = (1, 2, 3, 4, 5)
    print(data[2:])  # (3, 4, 5)
    ```
    
* List2tuple
    
    ```python
    # convert from list to tuple
    alist = [3, 4, 5, 6, 7]
    aTuple = tuple(alist)
    
    print(aTuple)
    print(type(aTuple))  # <class 'tuple'>
    ```
    
* Tuple2list
    
    ```python
    # convert from tuple to list
    aTuple = (3, 4, 5, 6, 7)
    alist = list(aTuple)
    
    print(alist)
    print(type(alist))  # <class 'list'>
    ```
    

### **Example: Solve quadratic equation**

```python
import math

def quadratic_equation(a, b, c):
    # This function solves the quadratic equation
    # a, b, c -- three parameters and a != 0
    # compute delta
    delta = b*b - 4*a*c

    if delta < 0:
        return ()
    elif delta == 0:
        x = (-b)/(2*a)
        return (x,)
    else:
        x1 = (-b + math.sqrt(delta))/(2*a)
        x2 = (-b - math.sqrt(delta))/(2*a)
        return (x1, x2)

# Case 1: delta > 0
result = quadratic_equation(1, -5, 6)
print(result)  # (3.0, 2.0)
print(type(result))  # <class 'tuple'>

# Case 2: delta = 0
result = quadratic_equation(1, 2, 1)
print(result)  # (-1.0,)
print(type(result))  # <class 'tuple'>

# Case 3: delta < 0
result = quadratic_equation(1, 1, 1)
print(result)  # ()
print(type(result))  # <class 'tuple'>

# Data is protected
result = quadratic_equation(1, 1, 1)
```

# Set Motivation in Python

## Definition

Sets, unlike lists or tuples, do not allow duplicate elements and store values in no particular order.

## What you can do?

### Create a set

* Using curly brackets
    
    ```python
    # create a set
    animals = {"cat", "dog", "tiger"}
    print(type(animals))
    # <class 'set'>
    ```
    
* Items with different data types
    
    ```python
    # a set
    a = {"cat", 5, True, 40.0}
    print(type(a))
    # <class 'set'>
    ```
    
* Set comprehension
    
    ```python
    # a set comprehension
    a_set = {i * i for i in range(10)}
    print(a_set)
    # {0, 1, 4, 9, 16, 25, 36, 49, 64, 81}
    ```
    
* Access the items of a set
    
    ```python
    # accessing the items of a set
    animals = {"cat", "dog", "tiger"}
    for animal in animals:
        print(animal)
    # dog
    # cat
    # tiger
    ```
    
* Copy a set
    
    ```python
    # copy a set
    animals = {"cat", "dog", "tiger"}
    print(animals)  # animals
    a_copy = animals.copy()
    print(a_copy)  # a_copy
    # Animals: {'dog', 'cat', 'tiger'}
    # Copy: {'dog', 'cat', 'tiger'}
    ```
    
* Add an item
    
    ```python
    # add an item
    animals = {"cat", "dog", "tiger"}
    animals.add("bear")
    print(animals)
    # {'dog', 'bear', 'cat', 'tiger'}
    ```
    
* Insert a set to another set
    
    ```python
    # insert a set into another set
    animals = {"cat", "dog", "tiger"}
    animals.update({"chicken", "duck"})
    print(animals)
    # {'Duck', 'tiger', 'dog', 'cat', 'chicken'}
    ```
    
* Join two sets
    
    ```python
    # join two sets
    set1 = {"duck", "dog"}
    set2 = {"cat", "tiger"}
    set3 = set1.union(set2)
    print(set3)
    # {'duck', 'dog', 'cat', 'tiger'}
    ```
    
* Not allow duplicate values
    
    ```python
    # no duplication
    animals = {"cat", "dog", "tiger"}
    animals.add("cat")
    print(animals)
    # {'tiger', 'cat', 'dog'}
    ```
    
* Difference function
    
    ```python
    # difference function
    set1 = {"apple", "banana", "cherry"}
    set2 = {"pineapple", "apple"}
    set3 = set1.difference(set2)
    print(set3)
    # {'cherry', 'banana'}
    ```
    

* Symmetric\_difference
    
    ```python
    # symmetric difference
    set1 = {"apple", "banana", "cherry"}
    set2 = {"pineapple", "apple"}
    set3 = set1.symmetric_difference(set2)
    print(set3)
    # {'pineapple', 'cherry', 'banana'}
    ```
    

* Difference\_update function
    
    ```python
    # difference update function
    set1 = {"apple", "banana", "cherry"}
    set2 = {"pineapple", "apple"}
    set1.difference_update(set2)
    print(set1)
    # {'cherry', 'banana'}
    ```
    

* Symmetric\_difference\_update
    
    ```python
    # symmetric difference update
    set1 = {"apple", "banana", "cherry"}
    set2 = {"pineapple", "apple"}
    set1.symmetric_difference_update(set2)
    print(set1)
    # {'pineapple', 'cherry', 'banana'}
    ```
    

* Unordered and unindexed
    
    ```python
    # not support indexing
    animals = {"cat", "dog", "tiger"}
    print(animals[1])  # Raises TypeError
    # TypeError: 'set' object is not subscriptable
    ```
    

* Cannot contain unhashable types
    
    ```python
    # create a set
    a_list = [1, 2, 3]
    a_set = {"cat", a_list}  # Raises TypeError
    print(a_set)
    # TypeError: unhashable type: 'list'
    ```
    

### Bitwise operator

* AND
    
    ```python
    # AND (&)
    set1 = {1, 2, 3}
    set2 = {3, 4, 5}
    print(set1 & set2)
    # {3}
    ```
    

* XOR
    
    ```python
    # XOR (^)
    set1 = {1, 2, 3}
    set2 = {3, 4, 5}
    print(set1 ^ set2)
    # {1, 2, 4, 5}
    ```
    

* OR
    
    ```python
    # OR (|)
    set1 = {1, 2, 3}
    set2 = {3, 4, 5}
    print(set1 | set2)
    # {1, 2, 3, 4, 5}
    ```
    

* SUBTRACTION
    
    ```python
    # subtraction (-)
    set1 = {1, 2, 3}
    set2 = {3, 4, 5}
    print(set1 - set2)
    # {1, 2}
    ```
    

### Remove an item

Instead of using remove, you must use discard when working with a set which item is not contained in this set

* remove(item)
    
    ```python
    # remove an item
    animals = {"cat", "dog", "tiger"}
    animals.remove("cat")
    print(animals)
    # {'dog', 'tiger'}
    ```
    

* discard(item)
    
    ```python
    # remove an item from the set if it is present
    animals = {"cat", "dog", "tiger"}
    animals.discard("tiger")
    print(animals)
    # {'dog', 'cat'}
    ```
    

* Set comprehension
    
    ```python
    # a set comprehension
    a_set = {i for i in range(10)}
    print(a_set)
    # {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
    ```
    

* remove(item)  
    Remove an item from the set.  
    Raises KeyError if elem is not contained in the set.
    
    ```python
    # remove an item
    animals = {"cat", "dog", "tiger"}
    animals.remove("duck")  # Raises KeyError if 'duck' is not in the set
    print(animals)
    # KeyError: 'duck'
    ```
    

* discard(item)  
    Remove an item from the set if it is present.
    
    ```python
    # remove an item from the set if it is present
    animals = {"cat", "dog", "tiger"}
    animals.discard("duck")
    print(animals)
    # {'dog', 'cat', 'tiger'}
    ```
    

### Set to List and Tuple

* Set to List
    
    ```python
    # convert from set to list
    aSet = {1, 2, 3, 4, 5}
    aList = list(aSet)
    print(aList)
    print(type(aList))
    # [1, 2, 3, 4, 5]
    # <class 'list'>
    ```
    
* List to Set
    
    ```python
    # convert from list to set
    aList = [1, 2, 3, 2, 1]
    aSet = set(aList)
    print(aSet)
    print(type(aSet))
    # {1, 2, 3}
    # <class 'set'>
    ```
    
* Set to Tuple
    
    ```python
    # convert from set to tuple
    aSet = {1, 2, 3, 4, 5}
    aTuple = tuple(aSet)
    print(aTuple)
    print(type(aTuple))
    # (1, 2, 3, 4, 5)
    # <class 'tuple'>
    ```
    
* Tuple to Set
    
    ```python
    # convert from tuple to set
    aTuple = (1, 2, 3, 2, 1)
    aSet = set(aTuple)
    print(aSet)
    print(type(aSet))
    # {1, 2, 3}
    # <class 'set'>
    ```
    

# Dictionary in Python

## Definition

A dictionary in Python is a built-in data structure that stores data as key-value pairs. It's an unordered, mutable collection where each element consists of a unique key and its associated value.

## Structure

Dictionaries use curly braces `{}` and store data in the format `{key: value, key: value, ...}`  

```python
 dictionary_name = {key-1:value-1, …, key-n:value-n}
```

**Key Properties**:

* Keys must be unique and immutable (strings, numbers, tuples)
    
* Values can be of any data type and can be duplicated
    
* Dictionaries are mutable (can be modified after creation)
    
* As of Python 3.7+, dictionaries maintain insertion order
    

## Comparing between List and Dictionary

| **Aspect** | **Lists** | **Dictionaries** |
| --- | --- | --- |
| **Keys/Indices** | Numeric indices only | Any immutable type (strings, numbers, tuples) |
| **Duplicates** | Values can be duplicated | Keys must be unique, values can be duplicated |
| **Performance** | O(n) for searching | O(1) average for key lookup |
| **Use Case** | Sequential data, ordered collections | Mappings, lookups, related data |

**Use Lists when**:

* You need ordered data
    
* Working with sequences
    
* Indices have meaning (like time series)
    
* Need to maintain duplicates
    

**Use Dictionaries when**:

* You need fast lookups
    
* Data has natural key-value relationships
    
* Keys are more meaningful than positions
    
* Building mappings or associations
    

## What you can do?

### Create a Dictionary

* Dictionary comprehension
    
    ```python
    # dic comprehension
    a_dict = {i: i * i for i in range(5)}
    print(a_dict)
    # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
    ```
    

* From zip
    
    ```python
    # from zip
    tuple1 = (1, 2, 3)
    tuple2 = (4, 5, 6)
    a_dict = dict(zip(tuple1, tuple2))
    print(a_dict)
    # {1: 4, 2: 5, 3: 6}
    ```
    

* From zip (alternative)
    
    ```python
    # from zip
    list1 = [1, 2, 3]
    list2 = [4, 5, 6]
    a_dict = dict(zip(list1, list2))
    print(a_dict)
    # {1: 4, 2: 5, 3: 6}
    ```
    

* From zip
    
    ```python
    # from zip
    set1 = {1, 2, 3}
    set2 = {4, 5, 6}
    a_dict = dict(zip(set1, set2))
    print(a_dict)
    # {1: 4, 2: 5, 3: 6}
    ```
    

### Update a value

```python
# update a value
parameters = {"learning_rate": 0.1, "metric": "Accuracy"}
parameters["learning_rate"] = 0.2
print(parameters)
# {'learning_rate': 0.2, 'metric': 'Accuracy'}
```

### Copy a dictionary

```python
# copy a dictionary
parameters = {"learning_rate": 0.1, "metric": "Accuracy"}
a_copy = parameters.copy()
print(a_copy)
# {'learning_rate': 0.1, 'metric': 'Accuracy'}
```

### Copy() function just only copy shallow type

```python
# shallow copy
d1 = {"a": [1, 2], "b": 1}
d2 = d1.copy()
# thay đổi d1 sẽ không ảnh hưởng đến d2
d1["a"][0] = 3
print(d1)  # {'a': [3, 2], 'b': 1}
print(d2)  # {'a': [3, 2], 'b': 1}
```

### Using deepcopy() function in module copy

```python
# using deepcopy
import copy
d1 = {"a": [1, 2], "b": 1}
d2 = copy.deepcopy(d1)
d1["a"][0] = 3
print(d1)  # {'a': [3, 2], 'b': 1}
print(d2)  # {'a': [1, 2], 'b': 1}
```

### Get keys and values

* Get keys
    
    ```python
    # Get keys
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    keys = parameters.keys()
    print(keys)
    # dict_keys(['learning_rate', 'optimizer', 'metric'])
    ```
    

* Get values
    
    ```python
    # Get values
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    values = parameters.values()
    print(values)
    # dict_values([0.1, 'Adam', 'Accuracy'])
    ```
    

* Get keys and values
    
    ```python
    # Get keys and values
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    items = parameters.items()
    for key, value in items:
        print(key, value)
    # learning_rate 0.1
    # optimizer Adam
    # metric Accuracy
    ```
    

### Get a value by a key

* Get value using get() function
    
    ```python
    # Get value using get() function
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    value = parameters.get("learning_rate")
    print(value)
    print("After using get() function:")
    print(parameters)
    # 0.1
    # After using get() function:
    # {'learning_rate': 0.1, 'optimizer': 'Adam', 'metric': 'Accuracy'}
    ```
    
* Get value and delete the corresponding item
    
    ```python
    # Get value and delete the corresponding item
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    value = parameters.pop("learning_rate")
    print(value)
    print("After using pop() function:")
    print(parameters)
    # 0.1
    # After using pop() function:
    # {'optimizer': 'Adam', 'metric': 'Accuracy'}
    ```
    

### Dictionary operations

* popitem()
    
    ```python
    # popitem() - Lấy ra một phần tử cuối cùng của dictionary
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    item = parameters.popitem()
    print(item)
    print(parameters)
    # ('metric', 'Accuracy')
    # {'learning_rate': 0.1, 'optimizer': 'Adam'}
    ```
    
* clear()
    
    ```python
    # clear() - Xóa tất cả các phần tử trong dictionary
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    print("Before using clear() function:")
    print(parameters)
    parameters.clear()
    print("After using clear() function:")
    print(parameters)
    # Before using clear() function:
    # {'learning_rate': 0.1, 'optimizer': 'Adam', 'metric': 'Accuracy'}
    # After using clear() function:
    # {}
    ```
    
* Use del keyword to delete an item
    
    ```python
    # Use del keyword to delete an item
    parameters = {"learning_rate": 0.1, "metric": "Accuracy"}
    print(parameters)
    del parameters["metric"]
    print(parameters)
    # {'learning_rate': 0.1, 'metric': 'Accuracy'}
    # {'learning_rate': 0.1}
    ```
    

### Key that does not exist

* Try to delete a non-existing item
    
    ```python
    # Try to delete a non-existing item
    parameters = {"learning_rate": 0.1, "metric": "Accuracy"}
    del parameters["algorithm"]
    # KeyError: 'algorithm'
    ```
    
* Try to get an item by a non-existing key
    
    ```python
    # Try to get an item by a non-existing key
    parameters = {"learning_rate": 0.1, "optimizer": "Adam", "metric": "Accuracy"}
    value = parameters.pop("algorithm")
    # KeyError: 'algorithm'
    ```
    
* Setdefault() function
    
    * Example 1
        
        ```python
        # setdefault() function
        fruits = {"banana": 2}
        fruits.setdefault("apple", 0)
        print(fruits)
        # {'banana': 2, 'apple': 0}
        ```
        
    
    * Example 2
        
        ```python
        # setdefault() function
        fruits = {"banana": 2, "apple": 4}
        fruits.setdefault("apple", 0)
        print(fruits)
        # {'banana': 2, 'apple': 4}
        ```
        
    
    * Example 3
        
        ```python
        # setdefault() function
        fruits = {"banana": 2}
        fruits["apple"] += 10
        print(fruits)
        # KeyError: 'apple'
        ```
        
    
    * Example 4
        
        ```python
        # setdefault() function
        fruits = {"banana": 2}
        fruits.setdefault("apple", 0)
        fruits["apple"] += 10
        print(fruits)
        # {'banana': 2, 'apple': 10}
        ```
        

### Get a value via a key

* Method 1
    
    ```python
    # access value via key
    fruits = {"banana": 2, "apple": 4}
    print(fruits["apple"])
    print(fruits["corn"])
    # 4
    # KeyError: 'corn'
    ```
    

* Method 2
    
    ```python
    # access value via key
    fruits = {"banana": 2, "apple": 4}
    print(fruits.get("apple"))
    print(fruits.get("corn"))
    # 4
    # None
    ```
    

* Merge two dictionaries
    
    ```python
    # merge two dicts
    fruits = {"banana": 2, "apple": 4}
    cereal = {"rice": 3, "corn": 7}
    result = {**fruits, **cereal}
    print(result)
    # {'banana': 2, 'apple': 4, 'rice': 3, 'corn': 7}
    ```
    

* Check if a key exists
    
    ```python
    # check if a key exists
    fruits = {"banana": 2, "apple": 4}
    print("apple" in fruits)
    print("corn" in fruits)
    # True
    # False
    ```
    

* Remove empty items
    
    ```python
    # remove empty items
    fruits = {"banana": 2, "apple": None}
    dict1 = {key: value for (key, value) in fruits.items() if value is not None}
    print(dict1)
    # {'banana': 2}
    ```
    

* Dictionary comprehension
    
    ```python
    # dic comprehension
    aDict = {str(i): i for i in range(5)}
    print(aDict)
    # {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4}
    ```
    

# Conclusion

In conclusion, understanding the various data structures in Python, such as tuples, sets, and dictionaries, is crucial for efficient data management and manipulation. Each data structure has its unique properties and use cases.

Tuples are immutable and can be used as keys in dictionaries, making them suitable for configurations and ensuring data integrity.

Sets are ideal for operations involving unique elements and provide efficient methods for set operations like union and intersection.

Dictionaries offer a flexible way to store key-value pairs, allowing for fast lookups and data retrieval. By mastering these data structures, you can write more efficient and effective Python code, tailored to the specific needs of your applications.

*Reference source (original document):* [Documents/2025-5/M01W02 - \[v2\] Advanced Data Structure (IoU, NMS, and Histogram)/AIO2025\_AdvancedDataStructure\_v2.pdf](https://aivnlearning.edu.vn/api/files/68317576519c0e157fb51481/Documents%2F2025-5%2FM01W02%20-%20%5Bv2%5D%20Advanced%20Data%20Structure%20\(IoU%2C%20NMS%2C%20and%20Histogram\)%2FAIO2025_AdvancedDataStructure_v2.pdf)