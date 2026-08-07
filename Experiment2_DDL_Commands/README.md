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
--
<img width="858" height="322" alt="image" src="https://github.com/user-attachments/assets/362a5327-f4c6-4344-8633-f081e647e904" />

**Program**
```sql
CREATE TABLE Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE);
```
**Output:**

<img width="1318" height="315" alt="image" src="https://github.com/user-attachments/assets/34a5eba9-6e07-4499-ae5e-6f84ea5e55d1" />

--

**Question 2**
---
<img width="827" height="282" alt="image" src="https://github.com/user-attachments/assets/88c29b05-3665-4043-8d64-ed3eedb0717d" />

**Program**
```sql
ALTER TABLE Student_details
ADD COLUMN ParentsNumber number;

ALTER TABLE Student_details
ADD COLUMN Adhar_Number number;
```

**Output:**

<img width="1247" height="317" alt="image" src="https://github.com/user-attachments/assets/c6488c0d-74f0-428e-9330-b1893c83152e" />

**Question 3**
---
<img width="980" height="251" alt="image" src="https://github.com/user-attachments/assets/714c4d0f-f8d9-433f-b1c5-d516b7a26f3a" />

**Program**
```sql
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL,
Location TEXT);
```

**Output:**

<img width="1212" height="172" alt="image" src="https://github.com/user-attachments/assets/5ec16721-e87e-4317-9f05-1b9fd350c911" />

**Question 4**
---
<img width="897" height="287" alt="image" src="https://github.com/user-attachments/assets/ba47c79b-640e-4e55-9912-54a5f5fea549" />

**Program**
```sql
CREATE TABLE Employees(
EmployeeID INT PRIMARY KEY,
FirstName VARCHAR(255) NOT NULL,
LastName VARCHAR(255) NOT NULL,
Email VARCHAR(255) UNIQUE,
Salary DECIMAL CHECK (Salary>0),
DepartmentID INT,
FOREIGN KEY(DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1335" height="330" alt="image" src="https://github.com/user-attachments/assets/68c1a853-6155-4e51-b8fd-baecf5f7085c" />

**Question 5**
---
<img width="543" height="243" alt="image" src="https://github.com/user-attachments/assets/3228e40f-4b66-4ed7-8062-f3d94d02d50a" />

**Program**
```sql
INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID,ProductName,Price,Stock
FROM Discontinued_products;
```

**Output:**

<img width="907" height="247" alt="image" src="https://github.com/user-attachments/assets/3d28b085-cc75-4bbe-90b1-3a0dd6918889" />

**Question 6**
---
<img width="977" height="342" alt="image" src="https://github.com/user-attachments/assets/459762b8-8baa-4b2a-8b58-ccbf91b11033" />

**Program**
```sql
CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL(10,12) NOT NULL DEFAULT 0,
CHECK(
list_price>=discount AND
discount>=0 AND
list_price>=0
)
);
```

**Output:**

<img width="1333" height="252" alt="image" src="https://github.com/user-attachments/assets/86b598f6-2194-40a2-8552-09a8f8061de1" />

**Question 7**
---
<img width="1165" height="332" alt="image" src="https://github.com/user-attachments/assets/90cf25b5-4ac4-4109-a957-630e6182f800" />

**Program**
```sql
INSERT INTO Customers (CustomerID,Name,Address)
VALUES (306,'Diana Prince','Themyscira');
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (307, 'Bruce Wayne','Wayne Mano','Gotham',10007);
INSERT INTO Customers (CustomerID,Name,Address,Zipcode)
VALUES (308,'Peter Parker','Queens',11375);

```

**Output:**

<img width="1046" height="246" alt="image" src="https://github.com/user-attachments/assets/ef908efd-5311-45fe-9a29-ac7d73cc2a07" />

**Question 8**
---
<img width="1168" height="287" alt="image" src="https://github.com/user-attachments/assets/ad8b8963-d685-424e-b227-5ef1b63ccf96" />

**Program**
```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK (Amount>0),
DueDate DATE CHECK (DueDate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1325" height="247" alt="image" src="https://github.com/user-attachments/assets/359b8e14-b4fc-4985-8a8e-3b3b641b0a04" />

**Question 9**
---
<img width="777" height="175" alt="image" src="https://github.com/user-attachments/assets/b962c4cb-77d0-4f4f-a839-da68d24fbae9" />

**Program**
```sql
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES ('001','Sarah Parker','Manager','HR',60000);
```

**Output:**

<img width="1127" height="195" alt="image" src="https://github.com/user-attachments/assets/fa951b38-096a-42f9-877d-51d382bb8a30" />

**Question 10**
---
<img width="962" height="257" alt="image" src="https://github.com/user-attachments/assets/0f5aa898-88a0-4566-aee4-2a112038bbef" />

**Program**
```sql
ALTER TABLE Employees 
ADD COLUMN salary INTEGER CHECK (salary > 0);
```

**Output:**

<img width="1218" height="235" alt="image" src="https://github.com/user-attachments/assets/e22ffdfc-e89d-476c-8a80-41572a7d7e74" />

## GRADE:

<img width="526" height="145" alt="image" src="https://github.com/user-attachments/assets/ea9d8522-0e96-411b-a648-940585cde66f" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
