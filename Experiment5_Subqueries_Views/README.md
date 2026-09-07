# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1096" height="607" alt="image" src="https://github.com/user-attachments/assets/17755e42-9a31-4fd9-8784-ec42653d4e30" />


```sql
SELECT * FROM Employee
where age< ( SELECT AVG(AGE) FROM Employee WHERE income>1000000);
```

**Output:**

<img width="1140" height="369" alt="image" src="https://github.com/user-attachments/assets/f6cb1326-7094-4f9f-882a-b6d5dbba3263" />


**Question 2**
---
<img width="1076" height="676" alt="image" src="https://github.com/user-attachments/assets/efc5d1fa-3d11-4d3e-b775-a160c064ff4a" />


```sql
SELECT commission
from salesman
where salesman_id IN (SELECT salesman_id
from customer
where city='Paris');

```

**Output:**

<img width="543" height="312" alt="image" src="https://github.com/user-attachments/assets/004e6334-9d71-419e-818d-e0bccce1ad55" />


**Question 3**
---
<img width="1020" height="539" alt="image" src="https://github.com/user-attachments/assets/98c48222-aa20-4718-a2d8-1cd215e947b9" />


```sql
SELECT * FROM customer
where city<>(SELECT city FROM customer where id=(select max(id) from customer));
```

**Output:**

<img width="1151" height="466" alt="image" src="https://github.com/user-attachments/assets/eb20b413-1341-4559-8e4f-858003db2c60" />


**Question 4**
---
<img width="961" height="658" alt="image" src="https://github.com/user-attachments/assets/fcd58a5a-a672-48bb-8732-1019357fe137" />


```sql
select * from CUSTOMERS
WHERE salary<2500;
```

**Output:**

<img width="1148" height="437" alt="image" src="https://github.com/user-attachments/assets/b0b901cd-50c2-40d9-976e-983206dab837" />


**Question 5**
---
<img width="976" height="493" alt="image" src="https://github.com/user-attachments/assets/962e827e-b097-4a77-a882-8596be98e422" />


```sql
select medication_id,medication_name,dosage
from Medications
where dosage=(select min(dosage) from Medications);
```

**Output:**

<img width="938" height="388" alt="image" src="https://github.com/user-attachments/assets/57e00b01-1b5d-415d-92aa-23d9c9dd7f03" />


**Question 6**
---
<img width="988" height="726" alt="image" src="https://github.com/user-attachments/assets/b6a18a6b-26de-42d8-a7cc-843dcf9975a2" />


```sql
select * from customer
where customer_id=(select salesman_id-2001
from salesman
where name='Mc Lyon');
```

**Output:**

<img width="1149" height="287" alt="image" src="https://github.com/user-attachments/assets/d448f69a-ce79-4929-93f8-7f7ea044b076" />


**Question 7**
---
<img width="1110" height="451" alt="image" src="https://github.com/user-attachments/assets/c96da5a6-97e1-409d-969f-c507fcbc59ed" />


```sql
select department_id,department_name
from Departments
where length(department_name)>(select AVG(LENGTH(department_name)) from Departments);
```

**Output:**
<img width="582" height="377" alt="image" src="https://github.com/user-attachments/assets/b57c6102-2e90-4c8b-94b2-a6edf63d0c78" />


**Question 8**
---
<img width="1071" height="640" alt="image" src="https://github.com/user-attachments/assets/becc1b5c-79bc-4c69-9a31-4676c869d481" />


```sql
select * from CUSTOMERS
WHERE ADDRESS='Delhi' and AGE <30
ORDER BY ID;
```

**Output:**
<img width="1148" height="342" alt="image" src="https://github.com/user-attachments/assets/ca180eb6-2325-40df-8fea-540a24d1d017" />



**Question 9**
---
<img width="1033" height="741" alt="image" src="https://github.com/user-attachments/assets/154c7edb-80aa-40d8-b581-667c6e777fcb" />


```sql
SELECT * FROM CUSTOMERS
WHERE SALARY>1500;
```

**Output:**

<img width="1150" height="590" alt="image" src="https://github.com/user-attachments/assets/edbb6401-bc77-475f-a091-009f4d0567ca" />


**Question 10**
---
<img width="986" height="669" alt="image" src="https://github.com/user-attachments/assets/74eb3ab0-36e7-4e25-811b-5b4b4f8c42a9" />


```sql
SELECT * FROM CUSTOMERS
WHERE SALARY>4500;
```

**Output:**

<img width="1145" height="419" alt="image" src="https://github.com/user-attachments/assets/922ef875-007f-4dfc-bc5f-83ff503f7f00" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
