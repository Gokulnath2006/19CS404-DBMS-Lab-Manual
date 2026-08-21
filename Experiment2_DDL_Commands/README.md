# Experiment 2: DDL Commands

## AIM
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
```
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
```
```sql
CREATE TABLE products (product_id INTEGER PRIMARY KEY, product_name TEXT NOT NULL, list_price DECIMAL(10,2) Not NULL,discount DECIMAL(10,2) DEFAULT 0 NOT NULL,
CHECK(list_price>=discount AND discount>=0 AND list_price>=0));
```

**Output:**

<img width="1187" height="263" alt="image" src="https://github.com/user-attachments/assets/e25951a9-e310-4a6b-a13e-c1cc55707920" />


**Question 2**
```
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```

```sql
CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,InvoiceDate DATE,Amount REAL, DueDate DATE, OrderID INTEGER
CHECK(Amount>0 AND DueDate>InvoiceDate),FOREIGN KEY(OrderId) References Orders(OrderId));
```

**Output:**

<img width="1184" height="259" alt="image" src="https://github.com/user-attachments/assets/8db5a8f6-b4ee-49c0-85e0-092571fd57a2" />


**Question 3**
```
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
```

```sql
INSERT INTO Employee
VALUES(5,"George Clark","Consultant",null,null);
INSERT INTO Employee
VALUES(7,"Noah Davis","Manager","HR",60000);
INSERT INTO Employee
VALUES(8,"Ava Miller","Consultant","IT",null);
```

**Output:**

<img width="1177" height="264" alt="image" src="https://github.com/user-attachments/assets/3b25885b-3ca5-499a-92cc-510c22383630" />

**Question 4**
```
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.
```

```sql
INSERT INTO Books
VALUES("978-1234567890","Data Science Essentials","Jane Doe","TechBooks",2024);
```

**Output:**

<img width="1250" height="187" alt="image" src="https://github.com/user-attachments/assets/3e976624-8bfe-4c5f-9070-594f93a52945" />

**Question 5**
```
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```

```sql
CREATE TABLE contacts(contact_id INTEGER PRIMARY KEY,first_name TEXT NOT NULL,last_name TEXT NOT NULL,email TEXT,phone TEXT NOT NULL ,
CHECK(LENGTH(phone)>=10));
```

**Output:**

<img width="1216" height="292" alt="image" src="https://github.com/user-attachments/assets/a26c7cff-f7cd-4d5d-bdf4-3528ef25907f" />

**Question 6**
```
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.
```

```sql
CREATE TABLE Products(ProductID INTEGER PRIMARY KEY,ProductName TEXT UNIQUE NOT NULL,Price REAL,StockQuantity INTEGER,
CHECK(Price>=0 AND StockQuantity>=0));
```

**Output:**

<img width="1180" height="253" alt="image" src="https://github.com/user-attachments/assets/6f3570d4-83df-4fb2-b757-0c21724037dc" />

**Question 7**
```
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.
```

```sql
ALTER TABLE Student_details
ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details
ADD COLUMN Adhar_Number number;
```

**Output:**

<img width="1216" height="336" alt="image" src="https://github.com/user-attachments/assets/e1b4b5b7-ec86-45b7-8211-555f7442638d" />

**Question 8**
```
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
```

```sql
insert into student_details
Select*from  archived_students;
```

**Output:**

<img width="1218" height="242" alt="image" src="https://github.com/user-attachments/assets/325a5a1e-2e02-4740-9cfc-2c1748c4c073" />

**Question 9**
```
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
```

```sql
CREATE TABLE Products(ProductID PRIMARY KEY,ProductName NOT NULL,Price REAL,Stock INTEGER,
CHECK(Price>=0 AND Stock>=0));
```

**Output:**

<img width="1216" height="225" alt="image" src="https://github.com/user-attachments/assets/bb8b3592-e73b-49f5-beef-f8ebe9d2399c" />

**Question 10**
```
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'
```

```sql
ALTER TABLE Student_details ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**

<img width="1190" height="210" alt="image" src="https://github.com/user-attachments/assets/15e2d1be-8c2d-40de-9f46-a68ec0f8577f" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
