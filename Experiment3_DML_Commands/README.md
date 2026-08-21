# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
```
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'London'
  AND grade > 200;
```

**Output:**


<img width="1189" height="343" alt="image" src="https://github.com/user-attachments/assets/30a218c0-da7b-4f26-b049-7db0cf945d2f" />


**Question 2**
```
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('UK','USA','Canada')
    AND GRADE>=3;
```

**Output:**

<img width="1298" height="286" alt="image" src="https://github.com/user-attachments/assets/3a7e4a69-f9ab-4347-841d-5efa426722a3" />

**Question 3**
```
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```

```sql
UPDATE products
SET sell_price=sell_price*1.10
WHERE category='Bakery';
```

**Output:**

<img width="1297" height="346" alt="image" src="https://github.com/user-attachments/assets/4fba9e56-6483-4911-b07d-5002c1f97d30" />


**Question 4**
```
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization
```

```sql
DELETE FROM doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="1191" height="702" alt="image" src="https://github.com/user-attachments/assets/69cc5b60-d38a-4123-834a-6fb620e8e23c" />


**Question 5**
```
Write a SQL query to list the employee name those are starting with ‘S’ and with five characters.

Table name: emp

name        type
----------  ----------
empno       INT
ename       VARCHAR(100)
job         VARCHAR(50)
mgr         INT
hiredate    DATE
sal         DECIMAL(10,2)
comm        DECIMAL(10,2)
deptno      INT
```

```sql
SELECT ename
FROM emp
WHERE ename LIKE 'S____';
```

**Output:**

<img width="329" height="316" alt="image" src="https://github.com/user-attachments/assets/cb064276-a209-4bc2-8d94-a08969d39509" />

**Question 6**
```
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```

```sql
UPDATE Products
SET quantity = quantity * 1.10;
```

**Output:**

<img width="1179" height="615" alt="image" src="https://github.com/user-attachments/assets/ce94b3c6-0fa2-4d12-8cf7-5adb160504ef" />

**Question 7**
```
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```

```sql
UPDATE Products
SET quantity = quantity * 1.10;
```

**Output:**

<img width="1182" height="533" alt="image" src="https://github.com/user-attachments/assets/f85ab389-fc0b-46ef-aa47-dab56941d00f" />

**Question 8**
```
Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission.

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
```

```sql
SELECT salesman_id, name, city, commission
FROM salesman
WHERE city NOT IN ('Paris', 'Rome');
```

**Output:**

<img width="997" height="371" alt="image" src="https://github.com/user-attachments/assets/196618ec-7b29-4eea-bbc4-3b88571ffe8c" />

**Question 9**
```
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```

```sql
DELETE FROM customer WHERE grade<>3;
```

**Output:**

<img width="666" height="515" alt="image" src="https://github.com/user-attachments/assets/b400866c-ab25-4b82-b9da-22bd4f055455" />

**Question 10**
```
Write a SQL query to find all employees who were hired in the last 6 months from the emp table. 

Note: Assume current date as '01-09-2024'

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT
```

```sql
SELECT *
FROM emp
WHERE hiredate>date('2024-09-01','-6 month');
```

**Output:**

<img width="1178" height="359" alt="image" src="https://github.com/user-attachments/assets/27ebe6f8-8a22-4bca-9782-b8d5ecde06d9" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
