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
Write a SQL query to Add a new column State as text in the Student_details table.
![image](https://github.com/user-attachments/assets/6c8e5fd1-3ebb-4bb9-a386-badd70a33509)


```sql
ALTER TABLE Student_details ADD COLUMN State TEXT;
```

**Output:**
![image](https://github.com/user-attachments/assets/d7d4a4b8-765b-46bc-ab59-e8a7044b3bd8)



**Question 2**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values. 
![image](https://github.com/user-attachments/assets/adc8254f-a91d-47b1-be4a-58a1ff4986fb)

```sql
INSERT INTO Employee(EmployeeID,Name,Position)

VALUES('4','Emily White','Analyst');
```

**Output:**

![image](https://github.com/user-attachments/assets/b8132679-59de-4bfb-8939-c5f913a70895)


**Question 3**
---
Insert all employees from Former_employees into Employee
![image](https://github.com/user-attachments/assets/5e568b2c-c0f9-4b74-b67a-7c39ea7a7210)


```sql
INSERT into Employee(EmployeeID,Name,Department,Salary)

SELECT EmployeeID,Name,Department,Salary FROM Former_employees;
```

**Output:**

![image](https://github.com/user-attachments/assets/2c6432ef-4a7f-44a9-b5ac-c5b1fa302459)


**Question 4**
---
Create a table named Customers with the following columns:
![image](https://github.com/user-attachments/assets/6ce109be-a15c-433e-8fc9-ebb44f891b8d)

```sql
CREATE TABLE Customers(

CustomerID INTEGER,

Name TEXT,

Email TEXT,

JoinDate DATETIME );
```

**Output:**

![image](https://github.com/user-attachments/assets/085a42a0-dca9-4617-b028-dc60839fb7ad)


**Question 5**
---
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'
![image](https://github.com/user-attachments/assets/d0852d99-cde7-4f06-a5b5-5b9ba068976a)


```sql
ALTER TABLE Student_details

ADD COLUMN email TEXT not NULL default'Invalid';
```

**Output:**
![image](https://github.com/user-attachments/assets/9063bc1f-6afe-4033-910f-a944805122ff)


**Question 6**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.

InvoiceDate as DATE.

Amount as REAL should be greater than 0.

DueDate as DATE should be greater than the InvoiceDate.

OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
![image](https://github.com/user-attachments/assets/a253b236-d623-44b1-8829-5ed146c0d98d)


```sql
CREATE TABLE Invoices(

InvoiceID INTEGER primary key,

InvoiceDate DATE,

Amount REAL CHECK(Amount>=0),

DueDate DATE CHECK(DueDate>=InvoiceDate),

OrderID INTEGER,

foreign key (OrderID) references Orders(OrderID) );
```

**Output:**

![image](https://github.com/user-attachments/assets/7298394d-1e47-4f73-9eca-1492c07dafd7)


**Question 7**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.

ProductName should be NOT NULL.

Price is of real datatype and should be greater than 0.

Stock is of integer datatype and should be greater than or equal to 0.
![image](https://github.com/user-attachments/assets/e34b7531-9035-41cd-a34e-5a005a3c7ed1)


```sql
CREATE TABLE Products(

ProductID INTEGER primary key,

ProductName not NULL,

Price REAL CHECK (Price>0),

Stock INTEGER CHECK (Stock>=0) );
```

**Output:**

![image](https://github.com/user-attachments/assets/fdaacaf5-b729-4e62-b928-719d901cd7fc)


**Question 8**
---
Create a table named Orders with the following constraints:

OrderID as INTEGER should be the primary key.

OrderDate as DATE should be not NULL.

CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
![image](https://github.com/user-attachments/assets/49e5809c-b081-401d-a79d-0c7233e701af)



```sql
CREATE TABLE Orders(

OrderID INTEGER primary key,

OrderDate DATE not NULL,

CustomerID INTEGER,

foreign key (CustomerID) references Customers(CustomerID) );
```

**Output:**

![image](https://github.com/user-attachments/assets/2551c47b-8760-46d4-a3b6-05bb45d67f09)


**Question 9**
---
Create a table named Department with the following constraints:

DepartmentID as INTEGER should be the primary key.

DepartmentName as TEXT should be unique and not NULL.

Location as TEXT.
![image](https://github.com/user-attachments/assets/a1b5f5c6-c9a0-43e9-813e-a18ab2e5d96a)


```sql
CREATE TABLE Department(

DepartmentID INTEGER primary key,

DepartmentName TEXT UNIQUE not NULL,

Location TEXT );
```

**Output:**

![image](https://github.com/user-attachments/assets/e38c47f6-3a4b-41c5-af2f-ed51f3f8b87f)


**Question 10**
---
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

![image](https://github.com/user-attachments/assets/fca258dc-984f-49f8-878d-aa7065fc8924)


```sql
INSERT INTO Books(ISBN, Title, Author, Publisher, Year)

VALUES('978-1234567890', 'Introduction to AI', 'John Doe', null, null);

INSERT INTO Books(ISBN, Title, Author, Publisher, Year)

VALUES('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', '2022');

INSERT INTO Books(ISBN, Title, Author, Publisher, Year)

VALUES('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', null, 2021);
```

**Output:**

![image](https://github.com/user-attachments/assets/b27a4f29-dfa2-4253-994a-8cb401a83b90)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
