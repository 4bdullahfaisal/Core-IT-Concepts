# OOP — Classes, Objects
---

## PART 1: CLASSES AND OBJECTS (BASICS)

### What is OOP in one sentence
OOP bundles data and actions into a single thing called an object.

### Real world analogy
A car is an object:
- Data: color, model, speed
- Actions: drive(), brake(), honk()

### Class vs Object

| Term | Meaning | Example |
|------|---------|---------|
| Class | Blueprint / template | Cookie cutter |
| Object | Actual thing made from the class | A cookie |

### The simplest class

```
class Dog:
    pass
```

### Class with data (attributes)

```
class Dog:
    def __init__(self, name):
        self.name = name
```

What is __init__?
- A special function that runs when you create an object
- Sets up the object's data

What is self?
- Refers to the specific object being created
- Always the first parameter of __init__

What is self.name = name?
- Stores the passed name inside the object

### Creating an object from a class

```
my_dog = Dog("Rex")
print(my_dog.name)   # prints: Rex
```

### Class with actions (methods)

A method is just a function inside a class.

```
class Dog:
    def __init__(self, name):
        self.name = name
    
    def bark(self):
        return "Woof!"
    
    def greet(self):
        return self.name + " says hi"

my_dog = Dog("Rex")
print(my_dog.bark())     # Woof!
print(my_dog.greet())    # Rex says hi
```

### Multiple objects from the same class

```
dog1 = Dog("Rex")
dog2 = Dog("Buddy")

print(dog1.name)   # Rex
print(dog2.name)   # Buddy
print(dog1.greet()) # Rex says hi
print(dog2.greet()) # Buddy says hi

```

### Class with more data

```
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def can_vote(self):
        if self.age >= 18:
            return True
        else:
            return False
    
    def introduce(self):
        return "My name is " + self.name + " and I am " + str(self.age) + " years old"

p1 = Person("Alice", 25)
p2 = Person("Bob", 16)

print(p1.can_vote())   # True
print(p2.can_vote())   # False
print(p1.introduce())  # My name is Alice and I am 25 years old
```

### Why OOP matters (compare to non-OOP)

- Without OOP (separate data and functions):

```
name1 = "Alice"
age1 = 25
name2 = "Bob"
age2 = 16

def can_vote(name, age):
    return age >= 18

print(can_vote(name1, age1))  # True
print(can_vote(name2, age2))  # False
```

- With OOP (data + actions together):

```
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def can_vote(self):
        return self.age >= 18

alice = Person("Alice", 25)
bob = Person("Bob", 16)

print(alice.can_vote())  # True
print(bob.can_vote())    # False
```

### OOP Basics Summary

| Concept | What it does | Example |
|---------|--------------|---------|
| class | Creates a blueprint | class Dog: |
| __init__ | Sets up new objects | def __init__(self, name): |
| self | Refers to current object | self.name = name |
| Attribute | Data stored in object | my_dog.name |
| Method | Function inside class | def bark(self): |
| Object | Instance of a class | my_dog = Dog("Rex") |

### Practice example
```
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
    
    def describe(self):
        return "Title: " + self.title + ", Author: " + self.author

b1 = Book("1984", "Orwell")
b2 = Book("Moby Dick", "Melville")

print(b1.describe())
print(b2.describe())
```
---
