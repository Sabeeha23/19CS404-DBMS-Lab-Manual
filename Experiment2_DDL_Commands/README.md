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
![image](https://github.com/user-attachments/assets/cdea5005-6352-404c-a471-d6f1dd0698b3)

```
UPDATE Employees
SET salary = salary + 500, 
    email = 'updated'
WHERE job_id = 'SA_REP' 
AND commission_pct > 0.15;

```

**Output:**

![image](https://github.com/user-attachments/assets/4891dc75-f201-4f25-b34b-0bacfc848ff6)


**Question 2**
---
![image](https://github.com/user-attachments/assets/b339d292-e87b-49b8-939f-efae6fde7fed)


```sql
UPDATE SALES
SET total_sell_price = quantity * sell_price
WHERE product_id = 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/4e40977f-bc14-4b49-afa7-8b051be2c1e1)


**Question 3**
---
![image](https://github.com/user-attachments/assets/54c4b87b-f5d3-4b94-80ce-a026b14b2629)

```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

![image](https://github.com/user-attachments/assets/d28f8d97-ef55-47f9-bd29-9188ed3ccdce)


**Question 4**
---
![image](https://github.com/user-attachments/assets/4de4e4bf-b81f-449a-bf85-3022005d524b)


```sql
UPDATE Products
SET quantity = quantity * 1.10;

```

**Output:**
![image](https://github.com/user-attachments/assets/332da780-707d-40f8-806e-7dc2f5d25011)



**Question 5**
---
![image](https://github.com/user-attachments/assets/dc9be2ee-7c07-45cd-b2ba-e297f44ba82d)


```sql
UPDATE Customer
SET grade = 5
WHERE city = 'Chennai';
```

**Output:**

![image](https://github.com/user-attachments/assets/969a302b-e2e1-43dc-9fdf-a7b5244517a2)


**Question 6**
---
![image](https://github.com/user-attachments/assets/75be09fd-9964-4f48-9d28-baf3ee528450)


```sql
DELETE FROM Customer
WHERE GRADE = 3 
AND CUST_NAME LIKE '%BBB%' 
AND PAYMENT_AMT > 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/e9bf16d8-f1ea-43c3-aa7e-96b7441e0e1e)


**Question 7**
---
![image](https://github.com/user-attachments/assets/71a18510-9981-4bdf-a5e1-36d1313f54f6)


```sql
DELETE FROM Customer
WHERE WORKING_AREA = 'New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/3653adac-3102-4f40-bbf0-cbaa70a72ede)


**Question 8**
---
![image](https://github.com/user-attachments/assets/f6ed5596-bea6-4ac9-bf16-9bebf774f5b2)


```sql
DELETE FROM Customer
WHERE GRADE = 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/f19e6569-577d-4db1-89b4-e5273f7aeb8c)


**Question 9**
---
![image](https://github.com/user-attachments/assets/80f175e9-d280-430a-a631-febb6be5ff4e)

```sql
DELETE FROM Customer
WHERE GRADE = 2 
AND CUST_NAME LIKE 'M%' 
AND PAYMENT_AMT < 3000;
```

**Output:**

![image](https://github.com/user-attachments/assets/2b849eda-3912-4362-9d78-adf50a0914ea)


**Question 10**
---
![image](https://github.com/user-attachments/assets/ec3bbf86-2ecb-496b-8e06-0228c6294b3c)


```sql
DELETE FROM Customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;

```

**Output:**

![image](https://github.com/user-attachments/assets/9274b244-b319-406c-b19b-330a9b245514)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
