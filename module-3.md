# OOP - FOUR PILLARS 
---

| Pillar | Definition| Python syntax |
|--------|--------------|---------------|
| Encapsulation | Protects data from direct access. | `__variable`, `get_/set_ methods` |
| Abstraction | Hides unnecessary details. |`Private methods (__method)`, `simple public methods` |
| Polymorphism | Allows the same method to behave differently. |`Same method name in different classes` |
| Inheritance | Reuses code from existing classes. | `class Child(Parent):` |

---

## PILLAR 1: ENCAPSULATION

### What it means

Keep data inside an object and control who can see/change it.

### Real life analogy

A bank account: balance is private, you use deposit() and withdraw() methods.

### Without encapsulation (bad) 

 ```
class BankAccount:
    def __init__(self):
        self.balance = 100

acc = BankAccount()
acc.balance = -1000   # BAD! No protection
```

### With encapsulation (good)

```
class BankAccount:
    def __init__(self):
        self.__balance = 100   # __ means private
    
    def get_balance(self):
        return self.__balance
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance = self.__balance + amount
    
    def withdraw(self, amount):
        if amount > 0 and amount <= self.__balance:
            self.__balance = self.__balance - amount
            return True
        return False

acc = BankAccount()
print(acc.get_balance())   # 100
acc.deposit(50)
print(acc.get_balance())   # 150
```

### Private syntax

| Symbol | Meaning |
|--------|---------|
| __ (double underscore) | Makes attribute private (cannot access directly) |
| _ (single underscore) | Means "don't touch this" (just a warning) |

### Encapsulation rules

1. Make data private (__variable)
2. Provide public methods to access/change data
3. Validate inside methods

### Practice example

```
class Person:
    def __init__(self):
        self.__age = 0
    
    def set_age(self, age):
        if 0 <= age <= 150:
            self.__age = age
    
    def get_age(self):
        return self.__age

p = Person()
p.set_age(25)
print(p.get_age())   # 25
```

---

## ABSTRACTION

### What it means

Hide the complex details, show only the essential features.

### Real life analogy

Driving a car: You see steering wheel, pedals (simple interface). You don't see engine, fuel injection (complex details).

### Abstraction vs Encapsulation

| Pillar | What it hides | Why |
|--------|---------------|-----|
| Encapsulation | Data (variables) | To protect from invalid changes |
| Abstraction | Implementation (how it works) | To reduce complexity |

### Without abstraction (bad)

```
car = Car()
car.ignition_on()
car.fuel_pump_start()
car.starter_motor_turn()
car.engine_check()
car.release_brake()
car.press_gas()
```

### With abstraction (good)

```
car = Car()
car.start()   # One simple method hides all those steps
```

### Private methods (internal helpers)

```
class CoffeeMachine:
    def make_coffee(self):
        self.__heat_water()
        self.__grind_beans()
        self.__brew()
        return "Coffee ready"
    
    def __heat_water(self):    # private method (starts with __)
        print("Heating water...")
    
    def __grind_beans(self):
        print("Grinding beans...")
    
    def __brew(self):
        print("Brewing coffee...")

machine = CoffeeMachine()
print(machine.make_coffee())   # User only needs this
```

### Abstract classes (forces child to implement methods)

from abc import ABC, abstractmethod

```
class Payment(ABC):
    @abstractmethod
    def pay(self, amount):
        pass   # Child MUST implement this

class CreditCard(Payment):
    def pay(self, amount):
        return f"Paid {amount} with credit card"

class Cash(Payment):
    def pay(self, amount):
        return f"Paid {amount} with cash"

cc = CreditCard()
print(cc.pay(100))
```

### Why abstraction matters

| Without abstraction | With abstraction |
|--------------------|------------------|
| User needs to know everything | User needs to know one method |
| Changes break user code | Changes hidden inside |
| Hard to use | Easy to use |

---

## POLYMORPHISM

### What it means

The same method name works differently for different classes.

### Word breakdown

Poly = many, Morph = form, Polymorphism = many forms

### Example

```
class Bird:
    def fly(self):
        return "Bird flies"

class Airplane:
    def fly(self):
        return "Airplane flies with engines"

class Superman:
    def fly(self):
        return "Superman flies with cape"

things_that_fly = [Bird(), Airplane(), Superman()]

for thing in things_that_fly:
    print(thing.fly())

```
### Why polymorphism matters

You can write code that works with any object that has a certain method.

```
def make_it_fly(flying_object):
    print(flying_object.fly())

make_it_fly(Bird())       # Bird flies
make_it_fly(Airplane())   # Airplane flies with engines
make_it_fly(Superman())   # Superman flies with cape
```

### Duck typing (Python's style)

```
class Duck:
    def sound(self):
        return "Quack"

class Person:
    def sound(self):
        return "I can quack too"

def make_sound(obj):
    print(obj.sound())

make_sound(Duck())    # Quack
make_sound(Person())  # I can quack too

Python doesn't care about the class name. Only cares that sound() exists.
```
---

## INHERITANCE

### What it means

 A child class gets everything from the parent class, then adds or changes things.

### Real life analogy

- Parent class: Vehicle (has wheels, can move)

- Child class: Car (inherits wheels + move, adds doors)

### Basic inheritance

```
class Animal:
    def __init__(self, name):
        self.name = name
    
    def eat(self):
        return self.name + " is eating"
    
    def sleep(self):
        return self.name + " is sleeping"

class Dog(Animal):   # (Animal) means Dog inherits from Animal
    pass

my_dog = Dog("Rex")
print(my_dog.eat())    # Rex is eating (inherited)
```

### Adding new methods to child

```
class Dog(Animal):
    def bark(self):
        return self.name + " says Woof!"

my_dog = Dog("Rex")
print(my_dog.bark())   # Rex says Woof! (new method)
```

### Overriding parent methods

```
class Dog(Animal):
    def eat(self):     # SAME name as parent
        return self.name + " is eating dog food VERY fast"

my_dog = Dog("Rex")
print(my_dog.eat())   # Rex is eating dog food VERY fast
```

### Using super() to call parent method

```
class Dog(Animal):
    def eat(self):
        parent_result = super().eat()   # calls Animal's eat
        return parent_result + " like a good dog"

my_dog = Dog("Rex")
print(my_dog.eat())   # Rex is eating like a good dog
```

### Multiple child classes example

```
class Animal:
    def __init__(self, name):
        self.name = name
    def make_sound(self):
        return "some sound"

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"

class Cow(Animal):
    pass   # uses parent's "some sound"

animals = [Dog("Rex"), Cat("Kitty"), Cow("Betsy")]
for a in animals:
    print(a.name + " says " + a.make_sound())
```

### Inheritance terminology

| Term | Meaning |
|------|---------|
| Parent / Base class | The class being inherited from |
| Child / Derived class | The class that inherits |
| super() | Refers to the parent class |
| Override | Replace a parent method with a new version |
| Inherit | Automatically get all methods and attributes |

### Practice example

```
class Shape:
    def __init__(self, color):
        self.color = color
    def get_color(self):
        return self.color

class Circle(Shape):
    def __init__(self, color, radius):
        super().__init__(color)
        self.radius = radius
    def area(self):
        return 3.14 * self.radius * self.radius

class Square(Shape):
    def __init__(self, color, side):
        super().__init__(color)
        self.side = side
    def area(self):
        return self.side * self.side

c = Circle("red", 5)
s = Square("blue", 4)
print(c.get_color(), c.area())   # red 78.5
print(s.get_color(), s.area())   # blue 16
```

---

## COMPLETE EXAMPLE (4 pillars together)

from abc import ABC, abstractmethod

```
class Animal(ABC):
    def __init__(self, name):
        self.__name = name
    
    def get_name(self):
        return self.__name
    
    @abstractmethod
    def make_sound(self):
        pass

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow"

animals = [Dog("Rex"), Cat("Kitty")]
for animal in animals:
    print(animal.get_name() + " says " + animal.make_sound())

```

---

## FINAL PRACTICE (combine all 4)

from abc import ABC, abstractmethod

```
class Device(ABC):
    def __init__(self, brand):
        self.__brand = brand
    
    def get_brand(self):
        return self.__brand
    
    @abstractmethod
    def operate(self):
        pass

class Laptop(Device):
    def operate(self):
        return self.get_brand() + " laptop is booting..."

class Phone(Device):
    def operate(self):
        return self.get_brand() + " phone is ringing..."

devices = [Laptop("Dell"), Phone("Apple")]
for d in devices:
    print(d.operate())
```
