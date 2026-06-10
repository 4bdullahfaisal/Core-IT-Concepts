# DATABASES — (SQL basics, queries)

## WHAT IS A DATABASE

A database is an organized collection of data stored in tables.

## REAL LIFE ANALOGY

Excel spreadsheet. A database is like multiple Excel sheets that can talk to each other.

## KEY TERMS

| Term | Meaning | Excel analogy |
|------|---------|---------------|
| Database | Collection of tables | Entire workbook |
| Table | One set of data | One sheet |
| Row | One record | One row in sheet |
| Column | One field | One column in sheet |
| Primary Key | Unique ID for each row | Row number (but stays fixed) |

## VISUAL

Table: Users

| id (Primary Key) | name | age |
|-----------------|------|-----|
| 1 | Alice | 25 |
| 2 | Bob | 30 |
| 3 | Carol | 22 |

id = 1, name = Alice, age = 25 (one ROW)

name column holds Alice, Bob, Carol

---

## WHAT IS SQL

Structured Query Language. The language used to talk to databases.

> `--` is a comment in SQL.

## THE 4 MAIN COMMANDS (CRUD)

| Operation | SQL command | Meaning |
|-----------|-------------|---------|
| Create | INSERT | Add new row |
| Read | SELECT | Get data |
| Update | UPDATE | Change existing row |
| Delete | DELETE | Remove row |

---

## SELECT (Reading data)

### Basic SELECT

-- Select everything from a table

```
SELECT * FROM users;
```

-- Select specific columns

```
SELECT name, age FROM users;
```

-- Select with condition (WHERE)

```
SELECT * FROM users WHERE age > 25;
```

-- Select with multiple conditions

```
SELECT * FROM users WHERE age > 20 AND age < 30;
```

-- Select one specific row by id

```
SELECT * FROM users WHERE id = 2;
```

### SELECT examples with output

Table: users

| id | name | age | city |
|----|------|-----|------|
| 1 | Alice | 25 | London |
| 2 | Bob | 30 | Paris |
| 3 | Carol | 22 | London |

```
SELECT name FROM users;                           -- Returns: Alice, Bob, Carol
```

```
SELECT * FROM users WHERE city = 'London';        -- Returns: row 1 (Alice) and row 3 (Carol) 
```

```
SELECT name, age FROM users WHERE age >= 25;      -- Returns: Alice (25), Bob (30)
```

### Comparison operators in SQL

| Operator | Meaning |
|----------|---------|
| = | equals |
| > | greater than |
| < | less than |
| >= | greater or equal |
| <= | less or equal |
| <> | not equal |

---

## INSERT (Adding data)

### Basic INSERT

```

-- Insert a complete row

INSERT INTO users (id, name, age, city)

VALUES (4, 'David', 28, 'Berlin');


-- Insert without id (if id auto-increments)

INSERT INTO users (name, age, city)

VALUES ('Emma', 35, 'Madrid');


-- Insert multiple rows at once

INSERT INTO users (name, age, city)
VALUES 
('Frank', 40, 'Rome'),
('Grace', 27, 'Amsterdam');

```

### Rules for INSERT

- Strings go in single quotes: 'London'
- Numbers don't need quotes: 25
- Column order must match VALUES order

---

## UPDATE (Changing data)

### Basic UPDATE

```
-- Update one column for one row

UPDATE users 
SET age = 26 
WHERE id = 1;


-- Update multiple columns

UPDATE users 
SET name = 'Robert', city = 'Vienna' 
WHERE id = 2;


-- Update multiple rows (be careful!)

UPDATE users 
SET city = 'Unknown' 
WHERE city IS NULL;
```

### WARNING: Without WHERE

- THIS UPDATES EVERY ROW IN THE TABLE

`UPDATE users SET age = 18;`

- All users become age 18

- Always use WHERE unless you mean EVERY row

---

## DELETE (Removing data)

### Basic DELETE

```
-- Delete one specific row

DELETE FROM users WHERE id = 3;


-- Delete rows matching condition

DELETE FROM users WHERE age > 50;


-- Delete all rows (table becomes empty)

DELETE FROM users;
```

### WARNING: Same as UPDATE

```
-- THIS DELETES EVERY ROW

DELETE FROM users;

-- Always use WHERE unless you want empty table

DELETE FROM users WHERE id = 5;

```

---

## CREATE TABLE (Making new tables)

### Basic CREATE TABLE

```
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER,
    grade TEXT
);
```

### Data types (common ones)

| Type | What it stores | Example |
|------|----------------|---------|
| INTEGER | Whole numbers | 25, -3, 0 |
| TEXT | Strings | 'Alice', 'hello' |
| REAL | Decimal numbers | 3.14, 0.5 |
| BOOLEAN | True/False | TRUE, FALSE |
| DATE | Dates | '2024-01-15' |

### Constraints (rules for columns)

| Constraint | What it does |
|------------|--------------|
| PRIMARY KEY | Uniquely identifies each row |
| NOT NULL | Cannot be empty |
| UNIQUE | No duplicates allowed |
| DEFAULT | Default value if none given |

```
CREATE TABLE products (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    price REAL DEFAULT 0.00,
    email TEXT UNIQUE
);
```
---

## DROP TABLE (Deleting entire table)

```
-- Deletes the entire table (all rows + structure)

DROP TABLE users;


-- Safer: check if exists first

DROP TABLE IF EXISTS users;
```

DROP is different from DELETE:

- DELETE removes rows (table still exists)
- DROP removes the entire table

---

## COMPLETE EXAMPLE

-- Step 1: Create table

```
CREATE TABLE employees (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    position TEXT,
    salary INTEGER
);
```

-- Step 2: Insert data

```
INSERT INTO employees (name, position, salary)
VALUES ('Alice', 'Developer', 50000);

INSERT INTO employees (name, position, salary)
VALUES ('Bob', 'Manager', 70000);

INSERT INTO employees (name, position, salary)
VALUES ('Carol', 'Designer', 45000);
```

-- Step 3: Query data

```
SELECT * FROM employees WHERE salary > 48000;
```

-- Step 4: Update data

```
UPDATE employees SET salary = 55000 WHERE name = 'Alice';
```

-- Step 5: Delete data

```
DELETE FROM employees WHERE name = 'Carol';
```

-- Step 6: See final table

```
SELECT * FROM employees;
```

---

## SQL CHEAT SHEET

| Operation | Command |
|-----------|---------|
| Read (all columns) | `SELECT * FROM table;` |
| Read (specific columns) | `SELECT col1, col2 FROM table;` |
| Read with filter | `SELECT * FROM table WHERE condition;` |
| Create (add row) | `INSERT INTO table (col1, col2) VALUES (val1, val2);` |
| Update (change rows) | `UPDATE table SET col1 = new_value WHERE condition;` |
| Delete (remove rows) | `DELETE FROM table WHERE condition;` |
| Create table | `CREATE TABLE table_name (column1 TYPE, column2 TYPE);` |
| Delete table | `DROP TABLE table_name;` |

---

## COMMON SQL MISTAKES

| Mistake | Wrong | Right |
|---------|-------|-------|
| Missing quotes on strings | WHERE city = London | WHERE city = 'London' |
| Using = with NULL | WHERE name = NULL | WHERE name IS NULL |
| Forgetting WHERE on UPDATE | UPDATE users SET age=20 | UPDATE users SET age=20 WHERE id=1 |
| Forgetting WHERE on DELETE | DELETE FROM users | DELETE FROM users WHERE id=1 |
| Duplicate primary key | INSERT id that exists | Use auto-increment or check first |

---
