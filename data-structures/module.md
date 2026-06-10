# DATA STRUCTURES — (Arrays, linked lists, stacks, queues)
---

## WHAT ARE DATA STRUCTURES

Ways to organize and store data in a computer.

## ARRAYS // (lIST in PYTHON)

### What is an array

A collection of items stored in numbered boxes.

### Real life analogy

A row of lockers. 

Each locker has a number (0, 1, 2, 3...).

> In Python (we use "lists" which are like arrays)

### Creating an array

fruits = ["apple", "banana", "cherry"]

### Accessing by position (index starts at 0)

`print(fruits[0])   # apple`

`print(fruits[1])   # banana`

`print(fruits[2])   # cherry`

### Changing a value

`fruits[1] = "blueberry"`

`print(fruits)      # ["apple", "blueberry", "cherry"]`

### Index positions visual

```
Index:   0         1         2
Value: "apple"  "banana"  "cherry"
```

### Common array operations

### Creating

`numbers = [10, 20, 30, 40]`

### Length (how many items)

`print(len(numbers))   # 4`

### Add to end

```
numbers.append(50)
print(numbers)        # [10, 20, 30, 40, 50]
```

### Remove from end

```
last = numbers.pop()
print(last)           # 50
print(numbers)        # [10, 20, 30, 40]
```

### Remove from specific position

```
removed = numbers.pop(1)   # removes index 1 (20)
print(removed)        # 20
print(numbers)        # [10, 30, 40]
```

### Loop through an array

```
for item in numbers:
    print(item)       # prints 10, then 30, then 40
```

### Loop with index

```
for i in range(len(numbers)):
    print(i, numbers[i])
```

### Array cheat sheet

| Operation | Code | Speed |
|-----------|------|-------|
| Get by index | arr[2] | Fast |
| Set by index | arr[2] = 10 | Fast |
| Add to end | arr.append(x) | Fast |
| Remove from end | arr.pop() | Fast |
| Add at beginning | arr.insert(0, x) | Slow |
| Remove from beginning | arr.pop(0) | Slow |
| Find item | arr.index(x) | Slow |

### When to use arrays

- You have a list of items
- You need to access by position (item #3)
- Order matters

---

## PART 2: LINKED LISTS

### What is a linked list

A chain of nodes where each node points to the next node.

### Real life analogy

Treasure hunt. Each clue tells you where the next clue is.

### Visual

```
Array:  [10][20][30]   (boxes side by side)

Linked List:  [10|*] --> [20|*] --> [30|/]
               data next     data next     data end
```

### Simple node class (the building block)

```
class Node:
    def __init__(self, data):
        self.data = data    # the value
        self.next = None    # pointer to next node
```

### Create three nodes

```
node1 = Node(10)
node2 = Node(20)
node3 = Node(30)
```

### Link them

```
node1.next = node2
node2.next = node3
```

### Traverse (walk through) the linked list

```
current = node1
while current is not None:
    print(current.data)   # 10, then 20, then 30
    current = current.next
```

### Array vs Linked List

| Operation | Array | Linked List |
|-----------|-------|-------------|
| Access by index | Fast (instantly) | Slow (must walk from start) |
| Add to beginning | Slow (shift all) | Fast (just update head) |
| Add to middle | Slow (shift) | Fast (change pointers) |
| Remove from middle | Slow (shift) | Fast (change pointers) |
| Memory | Wastes less | Wastes more (stores pointers) |

### When to use linked lists

- You add/remove items frequently from middle/beginning
- You never need random access like "give me item #47"
- You don't know the size ahead of time

---

## PART 3: STACKS

### What is a stack

Last In, First Out (LIFO). Like a stack of plates.

### Real life analogy

Stack of plates: you put a plate on top, you take a plate from top.

### Visual

```
Push 1:  [1]
Push 2:  [2]
         [1]
Push 3:  [3]
         [2]
         [1]

Pop:     remove 3 -> stack becomes [2][1]
```

### Stack operations (only 2 main ones)

| Operation | What it does | Python code |
|-----------|--------------|-------------|
| Push | Add to top | stack.append(x) |
| Pop | Remove from top | stack.pop() |
| Peek | Look at top (don't remove) | stack[-1] |

### Stack example

### Stack using Python list

`stack = []`

### Push

```
stack.append(1)
stack.append(2)
stack.append(3)
print(stack)   # [1, 2, 3]
```

### Pop

```
top = stack.pop()
print(top)     # 3
print(stack)   # [1, 2]

top = stack.pop()
print(top)     # 2
print(stack)   # [1]
```

### Peek (look without removing)

`print(stack[-1])   # 1`

### Real world uses of stacks

- Undo (Ctrl+Z) in editors
- Back button in browsers
- Function calls (what happens when you call a function)
- Balanced parentheses checking

### Balanced parentheses example

```
def is_balanced(text):
    stack = []
    for char in text:
        if char == "(":
            stack.append("(")
        elif char == ")":
            if len(stack) == 0:
                return False
            stack.pop()
    return len(stack) == 0

print(is_balanced("(hello)"))     # True
print(is_balanced("((hello))"))   # True
print(is_balanced("(hello"))      # False
print(is_balanced("(hello)]"))    # False
```

---

## PART 4: QUEUES

### What is a queue

First In, First Out (FIFO). Like a line at a ticket counter.

### Real life analogy

Line at a store: first person in line gets served first.

### Visual

```
Enqueue 1: [1]
Enqueue 2: [1, 2]
Enqueue 3: [1, 2, 3]

Dequeue:   remove 1 -> [2, 3]
Dequeue:   remove 2 -> [3]
```

### Queue operations

| Operation | What it does | Python code |
|-----------|--------------|-------------|
| Enqueue | Add to back | queue.append(x) |
| Dequeue | Remove from front | queue.pop(0) |
| Peek | Look at front (don't remove) | queue[0] |

### Queue example (simple)

### Simple queue using list (pop(0) is slow)

`queue = []`

### Enqueue

```
queue.append(1)
queue.append(2)
queue.append(3)
print(queue)   # [1, 2, 3]
```

### Dequeue

```
front = queue.pop(0)
print(front)   # 1
print(queue)   # [2, 3]
```

### Queue example (fast way using collections.deque)

from collections import deque

`queue = deque()`

### Enqueue

```
queue.append(1)
queue.append(2)
queue.append(3)
print(queue)   # deque([1, 2, 3])
```

### Dequeue

```
front = queue.popleft()
print(front)   # 1
print(queue)   # deque([2, 3])
```

### Real world uses of queues

- Printer queue (jobs wait in line)
- Customer service call centers
- Keyboard buffer (keys pressed in order)
- Breadth-first search (graph algorithm)

---

## SUMMARY TABLE

| Structure | Order | Add to front | Add to back | Access by position |
|-----------|-------|--------------|-------------|--------------------|
| Array | By position | Slow | Fast | Fast |
| Linked List | By links | Fast | Fast | Slow |
| Stack | LIFO | N/A | Push (top) | No (only top) |
| Queue | FIFO | Dequeue (remove) | Enqueue (add) | No (only front) |

---

## QUICK REFERENCE CODE

### ARRAY (list in Python)

```
arr = [1, 2, 3]
arr.append(4)      # add to end
arr.pop()          # remove from end
arr[0]             # get first
```

### STACK

```
stack = []
stack.append(1)    # push
stack.pop()        # pop
```

### QUEUE (fast way)

```
from collections import deque
q = deque()
q.append(1)        # enqueue
q.popleft()        # dequeue
```

### LINKED LIST (manual - just know concept)

```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

```
---

**End of Data Structures Notes**
