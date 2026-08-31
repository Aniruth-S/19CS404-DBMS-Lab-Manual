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
<img width="1082" height="422" alt="image" src="https://github.com/user-attachments/assets/41924df0-cfda-4ffc-a8e9-e6e0cabc5734" />

-- 

```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);
```

**Output:**

<img width="722" height="463" alt="image" src="https://github.com/user-attachments/assets/fda63544-d12b-4de7-bde0-dc51a803dd89" />


**Question 2**
--
<img width="1101" height="673" alt="image" src="https://github.com/user-attachments/assets/41bdc853-ca4f-4905-997e-cb6f3fa9830f" />

-- 

```sql
SELECT salesman_id, name
FROM salesman
WHERE salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
);
```

**Output:**

<img width="670" height="508" alt="image" src="https://github.com/user-attachments/assets/23a158bd-7390-47b3-a1a7-b238070bf2e1" />


**Question 3**
--
<img width="1017" height="641" alt="image" src="https://github.com/user-attachments/assets/e224968a-4b35-4b77-b3cd-0823cdf9289f" />

-- 

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

<img width="1161" height="475" alt="image" src="https://github.com/user-attachments/assets/62970151-b207-4539-b174-9a40841601d6" />

**Question 4**
--
<img width="1067" height="515" alt="image" src="https://github.com/user-attachments/assets/b9adce7b-c569-4d1c-9443-6dec22099057" />

-- 

```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);
```

**Output:**

<img width="765" height="485" alt="image" src="https://github.com/user-attachments/assets/869aad7b-03d8-4bcb-9ef3-1a8e9eeee094" />


**Question 5**
--
<img width="1016" height="637" alt="image" src="https://github.com/user-attachments/assets/49e5e6cb-9416-431b-8bc8-3807410c425b" />

--

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;
```

**Output:**

<img width="1200" height="483" alt="image" src="https://github.com/user-attachments/assets/37719102-cbd9-4671-8e64-3b0b31056bd0" />


**Question 6**
--
<img width="1302" height="616" alt="image" src="https://github.com/user-attachments/assets/7adedde5-994c-43a0-98c6-391242ae46c6" />

-- 

```sql
SELECT student_name, grade
FROM GRADES
WHERE (subject, grade) IN (
    SELECT subject, MIN(grade)
    FROM GRADES
    GROUP BY subject
);
```

**Output:**

<img width="890" height="457" alt="image" src="https://github.com/user-attachments/assets/574def39-3927-4ce8-b1c8-8e9f169389e6" />

**Question 7**
--
<img width="1162" height="591" alt="image" src="https://github.com/user-attachments/assets/f04ce34e-e784-42b6-b5ae-67204e56c66a" />

-- 

```sql
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="1252" height="487" alt="image" src="https://github.com/user-attachments/assets/7793b6d8-b271-4fc9-8316-2d841aa493b8" />


**Question 8**
--
<img width="1315" height="547" alt="image" src="https://github.com/user-attachments/assets/50e6fb81-8adb-48be-a38f-4f7ac2da15b8" />

-- 

```sql
SELECT *
FROM orders
WHERE salesman_id IN (
    SELECT DISTINCT salesman_id
    FROM orders
    WHERE customer_id = 3007
);
```

**Output:**
<img width="1178" height="480" alt="image" src="https://github.com/user-attachments/assets/39f6d095-cfdb-4f70-bee2-1be6cda505f3" />


**Question 9**
--
<img width="1008" height="591" alt="image" src="https://github.com/user-attachments/assets/2a74fbb2-ff00-46af-a879-fa726e986813" />

--

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;
```

**Output:**

<img width="1150" height="385" alt="image" src="https://github.com/user-attachments/assets/8c755505-0d8c-4060-b401-5965e81d5d5e" />


**Question 10**
--
<img width="973" height="562" alt="image" src="https://github.com/user-attachments/assets/7dd7154a-2c7a-4e2b-b393-bc0d47fd01a4" />

-- 

```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi' AND AGE < 30
ORDER BY ID;
```

**Output:**

<img width="1160" height="392" alt="image" src="https://github.com/user-attachments/assets/38e37930-6ba3-4c2a-897a-03515bb7c4fd" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
