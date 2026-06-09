# Core IT Fundamentals 

---

| Topic | Description |
|-------|-------------|
| Programming basics | Conditions, loops, functions, OOP |
| Data structures | Arrays, linked lists, stacks, queues |
| Databases | SQL basics, queries |
| Networking basics | IP, DNS, HTTP/HTTPS |
| Operating systems basics | Processes, memory, file systems |

---

# Programming Basics (Conditions, Loops, Functions, OOP)

**Mental Model:** You are giving a computer a recipe.

| Concept | Analogy |
|---------|---------|
| **Conditions** | If it's raining, take an umbrella; otherwise, don't. |
| **Loops** | Repeat an action 10 times, or *while* food is not cooked, keep stirring. |
| **Functions** | Wrap a set of steps (e.g., "make coffee") so you can call it anytime. |
| **OOP** (Object-Oriented Programming) | Bundle data + actions into "things" (objects). A `Car` has `color` and can `drive()`. |

---

```
# condition
age = 18
if age >= 18:
    print("adult")

# loop
for i in range(3):
    print("hello")

# function
def greet(name):
    return "Hi " + name

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

# Data Structures (Arrays, Linked Lists, Stacks, Queues)

**Mental Model:**

| Data Structure | Mental Model |
|----------------|--------------|
| Array | Numbered boxes in a row. Box[0], Box[1], Box[2]. Fast to jump to any box. |
| Linked list | Treasure hunt. Each box has a clue to the next box. Slow to find 10th box. |
| Stack | Stack of plates. Last plate you put on top is first you take off (LIFO). |
| Queue | Line at a ticket counter. First in, first out (FIFO). |

**When to care:**

| Use Case | Best Structure |
|----------|----------------|
| Grocery list | Array |
| Undo in editor (Ctrl+Z) | Stack |
| Printer jobs | Queue |

---

```
# array (list in Python)
arr = [10, 20, 30]
print(arr[1])

# stack
stack = []
stack.append(1)   # push
stack.append(2)
print(stack.pop()) # 2

# queue
from collections import deque
q = deque()
q.append(1)
q.append(2)
print(q.popleft()) # 1

```
---

# Databases (SQL Basics, Queries)

**Mental Model:** Database = Excel spreadsheet but way more powerful. A table = one sheet. Rows = records, Columns = fields.

| SQL Command | Mental Model |
|-------------|--------------|
| SELECT | Look at data from a table |
| INSERT | Add a new row |
| UPDATE | Change existing rows |
| DELETE | Remove rows |
| WHERE | Filter which rows (forget this and you update/delete everything!) |

**Key SQL commands :**

```
SELECT * FROM users WHERE id = 1;
INSERT INTO users (name) VALUES ('Alice');
UPDATE users SET name = 'Bob' WHERE name = 'Alice';
DELETE FROM users WHERE name = 'Bob';
```

Create this:

- CREATE TABLE students (id INTEGER, name TEXT);
- INSERT INTO students VALUES (1, 'Maria');
- SELECT * FROM students WHERE id = 1;

**Golden rule:** WHERE filters rows. Forget WHERE and you update/delete everything.

---

# Networking Basics (IP, DNS, HTTP/HTTPS)

**Mental Model:**

| Concept | Mental Model |
|---------|--------------|
| IP address | Your house's street address (e.g., 192.168.1.5) |
| DNS | Phonebook of the internet. You type google.com, DNS returns IP address. |
| HTTP | Language browsers use to ask for web pages. |
| HTTPS | Same but encrypted (lock icon in browser) |

---

# Operating Systems Basics (Processes, Memory, File Systems)

**Mental Model:**

| Concept | Mental Model |
|---------|--------------|
| Process | A running program (e.g., Chrome, Spotify) |
| Memory (RAM) | Your desk. Fast but small. If power cuts, desk is wiped. |
| File system | Filing cabinet (folders, files) that survives reboot. |

**Key ideas:**

- One app can freeze but not crash other apps (separate processes).
- Too many apps open → computer slows (RAM full).
- File paths: C:\Users\name\doc.txt (Windows) or /home/name/doc.txt (Mac/Linux).


---
