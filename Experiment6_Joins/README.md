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
<img width="1302" height="566" alt="image" src="https://github.com/user-attachments/assets/32bd4d20-a728-494c-82c2-265a235b9ca6" />

-- 

```sql
SELECT p.date_of_birth, a.*
FROM patients AS p
INNER JOIN appointments AS a
    ON p.patient_id = a.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="1332" height="420" alt="image" src="https://github.com/user-attachments/assets/b617cd03-81a5-41ff-abc0-88fe4cf4a8aa" />

**Question 2**
--
<img width="1092" height="782" alt="image" src="https://github.com/user-attachments/assets/e1ab4ec8-5aa9-40ab-bf45-609215ae06d6" />

-- 

```sql
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS "Salesman",
       s.commission
FROM customer AS c
INNER JOIN salesman AS s
    ON c.salesman_id = s.salesman_id;
```

**Output:**
<img width="1153" height="797" alt="image" src="https://github.com/user-attachments/assets/bd9bf0d4-e8c4-4c55-9683-dc6f94eb26bb" />


**Question 3**
--
<img width="1300" height="577" alt="image" src="https://github.com/user-attachments/assets/1131f379-702b-4d9e-9e4f-281106169faa" />

--

```sql
SELECT p.first_name AS patient_name, t.*
FROM patients AS p
INNER JOIN test_results AS t
    ON p.patient_id = t.patient_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1337" height="415" alt="image" src="https://github.com/user-attachments/assets/e9bbac4d-6719-4fa8-a10d-79f9f476eaea" />


**Question 4**
--
<img width="1302" height="741" alt="image" src="https://github.com/user-attachments/assets/ed75d516-bb8c-4c33-9636-4fdb97412c40" />

-- 

```sql
SELECT c.cust_name AS "Customer Name",
       c.city AS "city",
       s.name AS "Salesman",
       s.city AS "city",
       s.commission
FROM customer AS c
INNER JOIN salesman AS s
    ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
  AND s.commission > 0.12;
```

**Output:**

<img width="1323" height="558" alt="image" src="https://github.com/user-attachments/assets/e34c65d5-f287-409e-a3b2-8c962af76086" />


**Question 5**
--
<img width="1326" height="303" alt="image" src="https://github.com/user-attachments/assets/6d4afe1d-8154-40d3-adf2-ea86b8bace66" />

-- 

```sql
SELECT s.name
FROM salesman AS s
LEFT JOIN customer AS c
    ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';
```

**Output:**
<img width="452" height="392" alt="image" src="https://github.com/user-attachments/assets/deb4db45-c0c8-4b59-a5e4-236dfb076347" />


**Question 6**
--
<img width="1007" height="927" alt="image" src="https://github.com/user-attachments/assets/2c8d1dcb-26b2-462d-9732-126d01edb9e8" />

-- 

```sql
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS "Customer Name",
       c.grade,
       s.name AS "Salesman",
       s.commission
FROM orders AS o
INNER JOIN customer AS c
    ON o.customer_id = c.customer_id
INNER JOIN salesman AS s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1372" height="602" alt="image" src="https://github.com/user-attachments/assets/e2cfa4f6-d198-4976-98c8-718554227c94" />


**Question 7**
--
<img width="1306" height="387" alt="image" src="https://github.com/user-attachments/assets/d5cf2d4c-6ad3-4f45-aa8a-d8a32a012bbe" />

--

```sql
SELECT c.cust_name,
       o.ord_no,
       o.ord_date,
       o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
WHERE o.purch_amt > 1000;
```

**Output:**

<img width="1066" height="587" alt="image" src="https://github.com/user-attachments/assets/e5b826ac-f71c-4c65-9253-f6d1eff59547" />


**Question 8**
--
<img width="1262" height="613" alt="image" src="https://github.com/user-attachments/assets/83f9160b-c657-444f-950d-d955db628512" />

-- 

```sql
SELECT p.admission_date,
       s.surgery_date
FROM patients AS p
INNER JOIN surgeries AS s
    ON p.patient_id = s.patient_id;
```

**Output:**

<img width="757" height="480" alt="image" src="https://github.com/user-attachments/assets/13712aac-b351-4c16-b34b-9097c39cfcb4" />


**Question 9**
--
<img width="1333" height="837" alt="image" src="https://github.com/user-attachments/assets/65080708-a804-4a9e-879c-ebdd38cd760d" />

--

```sql
SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount"
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**
<img width="1258" height="597" alt="image" src="https://github.com/user-attachments/assets/ea7c36e1-ef4c-4612-83c9-9ccf24384678" />


**Question 10**
--
<img width="1328" height="783" alt="image" src="https://github.com/user-attachments/assets/ea9f53d0-b072-40db-9ea8-000779f22185" />

-- 

```sql
SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name,
       s.commission
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
LEFT JOIN salesman AS s
    ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1327" height="672" alt="image" src="https://github.com/user-attachments/assets/a92fecaa-8c87-4bf3-bd70-dc139cab6bb5" />

## GRADE:
<img width="635" height="152" alt="image" src="https://github.com/user-attachments/assets/7df32448-1aa5-4edf-b35d-147cee37b5f5" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
