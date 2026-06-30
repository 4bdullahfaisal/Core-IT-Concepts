#  PROGRAMMING BASICS — (conditions, loops, functions)
## Language Use : Python
---

**Mental Model:** You are giving a computer a recipe.

| Concept | Analogy |
|---------|---------|
| **Conditions** | If it's raining, take an umbrella; otherwise, don't. |
| **Loops** | Repeat an action 10 times, or *while* food is not cooked, keep stirring. |
| **Functions** | Wrap a set of steps (e.g., "make coffee") so you can call it anytime. |
| **OOP** (Object-Oriented Programming) | Bundle data + actions into "things" (objects). A `Car` has `color` and can `drive()`. |

---

## CONDITIONS (if / elif / else)

### What it does
Lets the computer make decisions based on true/false questions.

### Comparison operators

| Operator | Meaning | Example |
|----------|---------|---------|
| == | equals | 5 == 5 → True |
| > | greater than | 5 > 3 → True |
| < | less than | 5 < 3 → False |
| >= | greater or equal | 5 >= 5 → True |
| <= | less or equal | 3 <= 5 → True |
| != | not equal | 5 != 3 → True |

### Syntax

```python
if condition:
    # runs if condition is True

if condition:
    # runs if True
else:
    # runs if False

if condition1:
    # runs if condition1 is True
elif condition2:
    # runs if condition1 is False AND condition2 is True
else:
    # runs if all conditions are False
    
```

### Example

```python
temperature = 30

if temperature > 25:
    print("It's hot outside")
else:
    print("It's cool outside")

```

### Common Python Mistakes

| Wrong | Right |
|-------|-------|
| `if x = 5` | `if x == 5` |
| `if x > 5` | `if x > 5:` |
| `if x > 5:`<br>`print("ok")` | `if x > 5:`<br>`    print("ok")` |

### Key rule

- Indentation (spaces) tells Python what's inside the if block. Use 4 spaces.

---

## LOOPS

### What they do
Repeat code multiple times.

### Two types

for loop: You know how many times
while loop: You know when to stop (condition-based)

---

### FOR LOOP

### Syntax

```python
for variable in range(count):
    # repeat this block
```

### range() explained

- range(3) produces: 0, 1, 2
- range(1, 5) produces: 1, 2, 3, 4
- range(2, 10, 2) produces: 2, 4, 6, 8

### Examples

```python
# Simple - runs 3 times
for i in range(3):
    print("hello")

# Using the variable
for i in range(3):
    print("Count:", i)
# prints Count: 0, Count: 1, Count: 2

# With custom start
for i in range(5, 10):
    print(i)   # prints 5,6,7,8,9
```

---


### WHILE LOOP

### Syntax

```python
while condition:
    # repeat this block as long as condition is True
```

### Example

```python
x = 0
while x < 3:
    print("x is", x)
    x = x + 1   # IMPORTANT: change the condition

# Output:
# x is 0
# x is 1
# x is 2
```

### DANGER: Infinite loop

- If you forget to change the condition, the loop never stops:

```python
x = 0
while x < 3:
    print("this prints forever")  # x never changes
```

### Real-world example

```python
password = ""
while password != "secret":
    password = input("Enter password: ")
print("Access granted")

```

### Rules summary

| Loop Type | Syntax Example | Best For | When to Use |
|-----------|----------------|----------|--------------|
| `for` loop | `for i in range(5):` | Counting | Know number of times |
| `while` loop | `while x < 5:` | Waiting | Don't know number of times |

---

## FUNCTIONS

### What they do

Wrap reusable code into a named block. Call it anytime.

### Two parts

- Define the function (create it)
- Call the function (run it)

### Syntax

```python
def function_name():
    # code to run

def function_name(parameter):
    # code that uses parameter

def function_name(parameter):
    result = something
    return result
```

### Simple example (no input, no output)

```python
def say_hello():
    print("Hello there")

# Call the function
say_hello()
```

### With input (parameters)

```python
def greet_person(name):
    print("Hello", name)

greet_person("Alice")   # prints: Hello Alice
greet_person("Bob")     # prints: Hello Bob
```

### With output (return value)

```python
def add_two(x):
    result = x + 2
    return result

y = add_two(5)   # y becomes 7
print(y)
```

### Complete example

```python
def double(number):
    return number * 2

def check_even(number):
    if number % 2 == 0:
        return "even"
    else:
        return "odd"

print(double(4))      # 8
print(check_even(10)) # even
```

### What is % (modulo)?

Remainder after division.
10 % 2 = 0 (even)
7 % 2 = 1 (odd)
9 % 3 = 0 (divisible)

### Why use functions?

Without functions:

```python
print(5 + 2)
print(8 + 2)
print(12 + 2)
```

With functions:

```python
def add_two(x):
    return x + 2

print(add_two(5))
print(add_two(8))
print(add_two(12))

Change +2 to +3 once → all three change.
```

---

## 4. COMBINING EVERYTHING

You can put conditions inside loops, loops inside functions, etc.

```python
def count_even(numbers):
    count = 0
    for n in numbers:
        if n % 2 == 0:
            count = count + 1
    return count

print(count_even([1,2,3,4,5,6]))  # prints 3
```

---

## QUICK REFERENCE CARD

```python
# CONDITION
if age >= 18:
    print("adult")
else:
    print("minor")

# FOR LOOP
for i in range(5):
    print(i)          # 0,1,2,3,4

# WHILE LOOP
x = 0
while x < 3:
    print(x)
    x = x + 1         # 0,1,2

# FUNCTION (definition)
def greet(name):
    return "Hello " + name

# FUNCTION (call)
message = greet("Sam")
print(message)        # Hello Sam

# OOP (simple class)
class Dog:
    def __init__(self, name):
        self.name = name
    def bark(self):
        return "woof"

my_dog = Dog("Rex")
print(my_dog.bark())

```

---

## VOCABULARY CHEAT SHEET

| Term | Definition |
|------|-------------|
| Condition | A true/false question |
| Indentation | Spaces at the start of a line (Python uses this to group code) |
| Loop | Repeats code |
| Iteration | One single run of a loop |
| Parameter | Input variable to a function (inside parentheses) |
| Argument | The actual value you pass to a function |
| Return | Send a value back from a function |
| Function call | Running a function by using its name |
| Modulo (%) | Remainder after division |

---

## COMMON ERRORS & FIXES

| Error | Cause | Fix |
|-------|-------|-----|
| `SyntaxError: invalid syntax` | Missing colons or parentheses | Check for missing `:` or `()` |
| `IndentationError` | Inconsistent spacing | Ensure all code inside if/loop/function has same spacing |
| `NameError: name 'x' is not defined` | Using variable before creation | Define the variable first |
| Infinite loop (program never stops) | Forgot to update variable in `while` loop | Add update statement inside the loop |

---
