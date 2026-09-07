# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="865" height="462" alt="image" src="https://github.com/user-attachments/assets/8a13f346-5b73-4682-b1a2-32ca4df3b8c8" />


```sql
select name,max(income)
from employee
where city='California';

```

**Output:**

<img width="686" height="286" alt="image" src="https://github.com/user-attachments/assets/e3e5d8d5-68b4-4359-9e4c-47e45e470f4a" />


**Question 2**
---
<img width="986" height="487" alt="image" src="https://github.com/user-attachments/assets/97c29052-82ad-45d6-9c52-2451b8246199" />


```sql
select count(*) AS COUNT
from customer
where city<>'Noida';
```

**Output:**

<img width="586" height="302" alt="image" src="https://github.com/user-attachments/assets/506b0d36-c1e7-4a33-b66b-00774126faf2" />


**Question 3**
---
<img width="951" height="493" alt="image" src="https://github.com/user-attachments/assets/057295bd-defc-4d1f-9040-cce2c5c27e20" />


```sql
select count(*) AS COUNT
from customer
where city='Noida';
```

**Output:**

<img width="490" height="291" alt="image" src="https://github.com/user-attachments/assets/09dd5387-9fd2-4141-bfbf-f9ce5a96b982" />


**Question 4**
---
<img width="1033" height="577" alt="image" src="https://github.com/user-attachments/assets/487cec96-573c-4c7e-952c-eb2ac833e81d" />


```sql
select Specialty ,
       COUNT(*) AS TotalDocto
from Doctors
group by specialty;
```

**Output:**
<img width="902" height="649" alt="image" src="https://github.com/user-attachments/assets/da8e4cf9-d2c5-4e99-954c-134108b7e0d0" />


**Question 5**
---
<img width="675" height="607" alt="image" src="https://github.com/user-attachments/assets/f02e60e1-1a27-4212-a58f-f360cefc4d1a" />


```sql
-select PatientID,
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY PatientID;
```

**Output:**

<img width="869" height="609" alt="image" src="https://github.com/user-attachments/assets/c2053056-dcab-4ead-ba16-b2e6c9e5a2de" />


**Question 6**
---
<img width="971" height="569" alt="image" src="https://github.com/user-attachments/assets/70246a8f-46e2-4290-b3ee-e47c2a47a0e7" />


```sql
select Frequency,
        Count(*) AS TotalPrescriptions
from prescriptions
group by Frequency;
```

**Output:**

<img width="957" height="514" alt="image" src="https://github.com/user-attachments/assets/528e2e75-5ebc-43f6-a84e-8ecc56fadd33" />


**Question 7**
---
<img width="1159" height="473" alt="image" src="https://github.com/user-attachments/assets/6b078389-9131-46b8-8fb2-2cea4dbe5cbe" />


```sql
select category_id,
       AVG(Price)
from products
group by category_id
having AVG(Price) BETWEEN 10 AND 15;

```

**Output:**

<img width="700" height="308" alt="image" src="https://github.com/user-attachments/assets/4fdc911c-0524-4a0f-a3f4-dcda95d1df86" />


**Question 8**
---
<img width="1142" height="592" alt="image" src="https://github.com/user-attachments/assets/5a522361-1617-4963-889b-7b561efed598" />


```sql
select (age/5)*5 AS age_group,MAX(salary)
FROM customer1
group by age_group
having max(salary)>8000;
```

**Output:**

<img width="688" height="327" alt="image" src="https://github.com/user-attachments/assets/105e6b13-adcd-43f1-9f89-d35fcef7827b" />


**Question 9**
---
<img width="1181" height="533" alt="image" src="https://github.com/user-attachments/assets/2d3d053b-bb48-422e-9124-fd376f9acbea" />


```sql
select age,MIN(income) AS Income
from employee
group by age
having MIN(income)<1000000;
```

**Output:**

<img width="697" height="406" alt="image" src="https://github.com/user-attachments/assets/72692f66-a10d-408e-a5d7-7b946388fd0e" />


**Question 10**
---
<img width="1160" height="501" alt="image" src="https://github.com/user-attachments/assets/6cc2664b-966a-469d-80c9-95efa9161fd7" />


```sql
select jdate,MIN(workhour)
from employee1
group by jdate
having MIN(workhour)<10;
```

**Output:**

<img width="777" height="405" alt="image" src="https://github.com/user-attachments/assets/4a06599a-412f-441e-8b01-5d7f66b7f953" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
