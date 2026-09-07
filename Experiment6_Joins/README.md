# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1133" height="666" alt="image" src="https://github.com/user-attachments/assets/f5b86750-abad-4bcf-8fc3-32c84bb13da3" />


```sql
select p.first_name AS patient_name,a.*
FROM PATIENTS p
INNER JOIN APPOINTMENTS a ON p.patient_id=a.patient_id;
```

**Output:**
<img width="1145" height="532" alt="image" src="https://github.com/user-attachments/assets/c840f55c-c9fd-4fbc-8edd-85051e0126e1" />


**Question 2**
---
<img width="1148" height="643" alt="image" src="https://github.com/user-attachments/assets/a3a71e08-670c-4e97-b069-728262f361af" />


```sql
SELECT c.*
FROM CUSTOMER c
LEFT JOIN ORDERS o
ON c.customer_id=o.customer_id
where ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

<img width="1148" height="457" alt="image" src="https://github.com/user-attachments/assets/f3e49502-d981-4f7d-b184-b16f71c5df13" />


**Question 3**
---
<img width="1159" height="791" alt="image" src="https://github.com/user-attachments/assets/678610a4-3cf3-4bcb-9f3e-ed2405b0361c" />

```sql
SELECT p.first_name AS patient_name,
        d.first_name AS doctor_name
fROM PATIENTS p
JOIN DOCTORS d ON p.doctor_id=d.doctor_id
where p.discharge_date IS NOT NULL;
```

**Output:**

<img width="909" height="388" alt="image" src="https://github.com/user-attachments/assets/0714faaa-223d-422d-a740-32f1afd22e0a" />


**Question 4**
---
<img width="1165" height="765" alt="image" src="https://github.com/user-attachments/assets/7c3d082d-a670-49a0-b338-dc90c7c92201" />


```sql
SELECT s.name,c.cust_name,c.city,c.grade,c.salesman_id
FROM Salesman s
LEFT JOIN Customer c ON s.salesman_id=c.salesman_id
where c.salesman_id IN (SELECT salesman_id
FROM Customer
GROUP BY salesman_id
having COUNT(*)>1)
ORDER BY grade;
```

**Output:**

<img width="1149" height="607" alt="image" src="https://github.com/user-attachments/assets/1919f3d7-ebf9-42db-9798-1425a69c5e74" />


**Question 5**
---
<img width="1166" height="644" alt="image" src="https://github.com/user-attachments/assets/835a1d08-3d75-45a1-9b9b-4af8f5beda12" />


```sql
SELECT p.*
FROM PATIENTS p
INNER JOIN TEST_RESULTS t
ON p.patient_id=t.patient_id
WHERE (t.test_name='Blood Test' OR t.test_name='Blood Pressure')
AND t.result NOT LIKE '%Normal%';
```

**Output:**
<img width="1151" height="389" alt="image" src="https://github.com/user-attachments/assets/a229b406-bec5-4a3f-b778-765d6649e75c" />


**Question 6**
---
<img width="1168" height="658" alt="image" src="https://github.com/user-attachments/assets/8c8a12b6-3eb0-47d9-acdf-336e6eb450b8" />


```sql
SELECT p.date_of_birth,a.*
FROM PATIENTS p
INNER JOIN APPOINTMENTS a ON p.patient_id=a.patient_id
WHERE p.first_name='Alice';
```

**Output:**

<img width="1153" height="382" alt="image" src="https://github.com/user-attachments/assets/a08d87a5-a101-4505-854e-5d3edcf01ca1" />


**Question 7**
---
<img width="1161" height="740" alt="image" src="https://github.com/user-attachments/assets/33e26480-8a6d-425d-ac3c-30814013414e" />


```sql
SELECT c.cust_name,s.name
FROM Customer c
LEFT JOIN Salesman s ON c.salesman_id=s.salesman_id
where c.city=s.city;
```

**Output:**

<img width="819" height="515" alt="image" src="https://github.com/user-attachments/assets/2d05d732-de7b-47b1-a0ea-643367321715" />


**Question 8**
---
<img width="1158" height="838" alt="image" src="https://github.com/user-attachments/assets/f95a80e5-5600-4334-9ce1-f88f2a1c3a61" />


```sql
SELECT p.*,d.first_name AS doctor_name
FROM PATIENTS p
INNER JOIN DOCTORS d ON p.doctor_id=d.doctor_id;
```

**Output:**

<img width="1153" height="520" alt="image" src="https://github.com/user-attachments/assets/ee1658dd-e04d-4fd8-82f4-8d4fa1c4542c" />


**Question 9**
---
<img width="1116" height="986" alt="image" src="https://github.com/user-attachments/assets/4665dff9-db21-407d-aa2e-a056a9a6c903" />


```sql
SELECT c.cust_name,
c.city,c.grade,s.name AS Salesman,
s.city FROM customer c
JOIN salesman s ON c.salesman_id=s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1147" height="900" alt="image" src="https://github.com/user-attachments/assets/2ffdd825-7dfa-4e04-a6c3-ce2a28ffee63" />


**Question 10**
---
<img width="1168" height="784" alt="image" src="https://github.com/user-attachments/assets/b09694f2-2cb6-4c31-ab46-90048231194a" />


```sql
SELECT p.first_name,s.*
FROM PATIENTS p 
INNER JOIN SURGERIES s ON p.patient_id=s.patient_id
where p.date_of_birth>'1990-01-01';
```

**Output:**

<img width="1151" height="388" alt="image" src="https://github.com/user-attachments/assets/e453df5c-da9d-4513-b25d-6c3ac1f464d7" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
