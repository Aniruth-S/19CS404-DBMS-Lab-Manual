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
--
<img width="1405" height="516" alt="image" src="https://github.com/user-attachments/assets/8d8b4fee-8a7d-4514-9e36-f6f868ec07d1" />

-- 

```sql
Update Products
set reorder_lvl=20
where quantity<10 and category='Snacks';
```

**Output:**

<img width="1311" height="501" alt="image" src="https://github.com/user-attachments/assets/29029ffa-4bc1-4e2d-b74e-6aba586674f1" />


**Question 2**
---
<img width="1355" height="462" alt="image" src="https://github.com/user-attachments/assets/91a8f5e9-e8d1-40dd-b763-9d6c8a8764cd" />

```sql
update Employees
set email='not available',commission_pct=0.55
where department_id=110;
```

**Output:**

<img width="1300" height="347" alt="image" src="https://github.com/user-attachments/assets/20e35676-58cc-4aec-a285-c9773a7e3f22" />


**Question 3**
---
<img width="1237" height="545" alt="image" src="https://github.com/user-attachments/assets/5d804bf0-a547-4344-8b50-7dd16318b7df" />

```sql
update Employees
set salary=salary+500,email='updated'
where job_id='SA_REP' and commission_pct>0.15;
```

**Output:**

<img width="1302" height="465" alt="image" src="https://github.com/user-attachments/assets/50f2f964-e1dd-43ac-a0e9-4780b8dad139" />

**Question 4**
---
<img width="1113" height="418" alt="image" src="https://github.com/user-attachments/assets/7374465e-bb71-45ea-8913-cd33c46a0959" />

```sql
Update Products
set reorder_lvl=(reorder_lvl*0.7)
where cost_price>50 and quantity<100;
```

**Output:**

<img width="1303" height="403" alt="image" src="https://github.com/user-attachments/assets/569ea59e-c6c2-4a30-bb40-9c312536b72d" />

**Question 5**
---
<img width="1102" height="532" alt="image" src="https://github.com/user-attachments/assets/fd313724-bd95-40c0-b6e5-a46f93b820f6" />

```sql
update Employees
set email='Unavailable';
```

**Output:**
<img width="1143" height="397" alt="image" src="https://github.com/user-attachments/assets/fe215009-c97c-46fd-b8cd-d7da40de6528" />

**Question 6**
---
<img width="1425" height="475" alt="image" src="https://github.com/user-attachments/assets/46c0a2ba-61f2-4bb3-b504-2bd60f9266fb" />

```sql
delete from Customer
where cust_city like "L%";
```

**Output:**
<img width="1400" height="797" alt="image" src="https://github.com/user-attachments/assets/6ce7f498-f4d2-42d5-9850-bf26cd36763f" />

**Question 7**
---
<img width="1165" height="460" alt="image" src="https://github.com/user-attachments/assets/060344ec-00b0-4ea9-a3eb-d417d832168a" />

```sql
delete from customer
where GRADE=2;
```

**Output:**

<img width="543" height="461" alt="image" src="https://github.com/user-attachments/assets/580a7b35-447a-42bc-b3cc-f539bcdcd186" />


**Question 8**
---
<img width="750" height="439" alt="image" src="https://github.com/user-attachments/assets/267b2234-0a5f-40e3-bea8-0e654db3b050" />

```sql
delete from Surgeries
where surgery_id=3 or surgeon_id=4;
```

**Output:**

<img width="894" height="679" alt="image" src="https://github.com/user-attachments/assets/510c52d6-09c0-427c-8dcd-39c5fbecb75e" />

**Question 9**
---
<img width="1424" height="608" alt="image" src="https://github.com/user-attachments/assets/b0a8b063-3034-4c28-8a12-e87808197e09" />
---
```sql
delete from customer
where CUST_COUNTRY='India' and not CUST_CITY='Chennai';
```

**Output:**

<img width="1335" height="662" alt="image" src="https://github.com/user-attachments/assets/df1a0f0e-ae2d-41b4-9ca6-70653d18d794" />

**Question 10**
---
<img width="814" height="351" alt="image" src="https://github.com/user-attachments/assets/eeab46a8-6c17-4f8f-901f-dd84ef6c08d1" />

```sql
delete from Surgeries
where surgery_date='2024-02-28';
```

**Output:**

<img width="908" height="301" alt="image" src="https://github.com/user-attachments/assets/f73e98f7-383b-4ec2-b341-60a6bf45275d" />

## GRADE:

<img width="506" height="172" alt="image" src="https://github.com/user-attachments/assets/371ddac3-92d8-47b2-9bba-5d9f9a9c8e1a" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
