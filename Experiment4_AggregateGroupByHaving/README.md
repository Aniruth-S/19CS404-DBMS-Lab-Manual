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
<img width="1126" height="432" alt="image" src="https://github.com/user-attachments/assets/970bd496-d4c5-4331-a3c0-34089d24fef9" />
--

```sql
SELECT Gender, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="675" height="402" alt="image" src="https://github.com/user-attachments/assets/a87c1fa9-63b7-4825-b4e2-41226c4dca1a" />


**Question 2**
--
<img width="875" height="615" alt="image" src="https://github.com/user-attachments/assets/ab149920-1df5-4f5f-8013-7b62eaa9bbdd" />

-- 

```sql
SELECT DATE(AppointmentDateTime) AS AppointmentDate,
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime);
```

**Output:**

<img width="877" height="667" alt="image" src="https://github.com/user-attachments/assets/79e0ddb0-5fc3-476a-8194-a37386618cbc" />

**Question 3**
--
<img width="1133" height="492" alt="image" src="https://github.com/user-attachments/assets/6280778a-dc53-4063-bff7-9d0ec5e12da4" />

-- 

```sql
SELECT PatientID,
       COUNT(Medications) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**
<img width="652" height="642" alt="image" src="https://github.com/user-attachments/assets/8a42609b-a390-48f6-8cf3-0f88b2fdf2e0" />


**Question 4**
--
<img width="1151" height="445" alt="image" src="https://github.com/user-attachments/assets/ce107117-5a82-4953-bfc3-6142bd667698" />

-- 

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30
FROM customer
WHERE city = 'Mumbai';
```

**Output:**

<img width="636" height="396" alt="image" src="https://github.com/user-attachments/assets/d21ad5c3-4fc0-4466-bcd3-12857422cb7c" />

**Question 5**
--
<img width="877" height="528" alt="image" src="https://github.com/user-attachments/assets/413d40ff-8f6b-48b2-b0aa-ef5cc009812c" />

-- 

```sql
SELECT name AS fruit_name,
       MIN(inventory) AS lowest_quantity
FROM fruits;
```

**Output:**

<img width="666" height="345" alt="image" src="https://github.com/user-attachments/assets/5fd6a6d7-cf07-483b-8afb-25cf4557b037" />

**Question 6**
--
<img width="1137" height="452" alt="image" src="https://github.com/user-attachments/assets/c11bdce6-bbfa-4048-b71e-b13d89ce6c87" />

-- 

```sql
SELECT SUM(workhour) AS "Total working hours"
FROM employee1;
```

**Output:**

<img width="642" height="355" alt="image" src="https://github.com/user-attachments/assets/5f14fe8f-e9db-4aa8-8201-dfe85c33ebc1" />


**Question 7**
--
<img width="928" height="456" alt="image" src="https://github.com/user-attachments/assets/29800191-6d93-40d0-a252-20e4d026773e" />

--

```sql
SELECT COUNT(DISTINCT age) AS COUNT
FROM employee;
```

**Output:**
<img width="447" height="361" alt="image" src="https://github.com/user-attachments/assets/62acce31-7432-4373-b79e-7f0d67d4eb02" />


**Question 8**
--
<img width="1418" height="452" alt="image" src="https://github.com/user-attachments/assets/5fd4339a-a650-4b78-9ca0-46f35a3b1a1b" />

-- 

```sql
SELECT jdate,
       AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour) < 10;
```

**Output:**

<img width="626" height="393" alt="image" src="https://github.com/user-attachments/assets/6711584a-a253-4ce5-8fa8-b525be203f28" />


**Question 9**
--
<img width="1415" height="505" alt="image" src="https://github.com/user-attachments/assets/74355d8a-9339-4e11-92e0-286dc52cf1db" />

-- 

```sql
SELECT category_id,
       SUM(price * category_id) AS Revenue
FROM products
GROUP BY category_id
HAVING SUM(price * category_id) > 25;
```

**Output:**

<img width="642" height="476" alt="image" src="https://github.com/user-attachments/assets/241fae57-d308-4a2a-8296-07461ea1958f" />


**Question 10**
--
<img width="1413" height="503" alt="image" src="https://github.com/user-attachments/assets/72d15af2-a533-4db4-a53c-c751b0701ff9" />

-- 

```sql
SELECT category_id,
       count(product_name)
FROM products
GROUP BY category_id
HAVING MIN(category_id) < 3;
```

**Output:**

<img width="731" height="402" alt="image" src="https://github.com/user-attachments/assets/d630e692-75c9-435d-a77f-3c299eaff4d4" />

## GRADE:
<img width="600" height="202" alt="image" src="https://github.com/user-attachments/assets/8156b56e-c5a5-4fe6-8b38-bf6ea92b1f34" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
