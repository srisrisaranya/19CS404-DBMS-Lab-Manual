# Experiment 2: DDL Commands
# Name: Saranya S
# Register number: 212223110044
## AIM:
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--- Insert all books from Out_of_print_books into Books
    Table attributes are ISBN, Title, Author, Publisher, YearPublished
```

--- 
INSERT into Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN,Title,Author,Publisher,YearPublished
FROM Out_of_print_books
```

**Output:**
![image](https://github.com/user-attachments/assets/f1575650-5ab0-440f-aa94-28732464e8cc)


**Question 2**
---
-- Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```
```
# program:
```
--sql CREATE TABLE contacts(
contact_id INTEGER Primary Key,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT not NULL check(length(phone)>=10)
);

```
**Output**:

![image](https://github.com/user-attachments/assets/a8bbe4ee-89ed-44ef-b1ce-2609c96c4e3d)

**Question 3**
---
-- Write an SQL command can to add a column named email of type TEXT to the customers table

```
--sql ALTER TABLE customers
add column email TEXT;
```
**Output:**

**Question 4**
---
-- In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```
--sql INSERT into Products(ProductID,Name,Category)values(106,'Fitness Tracker','Wearables');
INSERT into Products(ProductID,Name,Category,Price,Stock)values(107,'Laptop','Electronic',999.99,50);
INSERT into Products(ProductID,Name,Category,Stock)values(108,'Wireless Earbud','Accessorie',100);
-- 
```

**Output:**
![image](https://github.com/user-attachments/assets/9d513603-578c-44c5-9927-7cc0d4eee0b5)

**Question 5**
---
Create a table named Members with the following columns:
MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```
-- sql CREATE TABLE Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**
![image](https://github.com/user-attachments/assets/b1af10f8-772f-4d27-b7b3-99b0293ea98a)

**Question 6**
---
-- Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```
--sql
INSERT into Employee(EmployeeID,Name,Position,Department,Salary)values(001,'Sarah Parker','Manager','HR',60000);
```

**Output:**
![image](https://github.com/user-attachments/assets/872946d8-c19a-4183-a702-68a2f6c191b0)

**Question 7**
---
-- Create a table named ProjectAssignments with the following constraints:
   AssignmentID as INTEGER should be the primary key.
   EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
   ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
   AssignmentDate as DATE should be NOT NULL.

```sql
-- CREATE TABLE ProjectAssignments(
   AssignmentID INTEGER Primary Key,
   EmployeeID INTEGER,
   ProjectID INTEGER,
   AssignmentDate DATE not NULL,
   foreign key(EmployeeID) references Employees(EmployeeID)
   foreign key(ProjectID) references Projects(ProjectID)
);
```

**Output:**


**Question 8**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- CREATE TABLE Products(
ProductID INTEGER Primary Key,
ProductName TEXT unique not NULL,
Price REAL check(Price>0),
StockQuantity INTEGER check(StockQuantity>0)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/797baddf-4507-4525-85d0-a5f9b23b5499)


**Question 9**
---
-- Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
-- CREATE TABLE Invoices(
InvoiceID INTEGER Primary Key,
InvoiceDate DATE,
Amount REAL check(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER,
foreign key(OrderID) references Orders(OrderID)
);
```

**Output:**

**Question 10**
---
-- Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

```sql
-- ALTER TABLE books
ADD ISBN varchar(30);
ALTER TABLE books
ADD domain_dept varchar(30);
```
**Output:**
![image](https://github.com/user-attachments/assets/c7804088-0bce-4d73-87c1-c2c52c6fffc7)

![image](https://github.com/user-attachments/assets/7ecc775b-f1a8-4500-a295-b3df7b5613d1)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
