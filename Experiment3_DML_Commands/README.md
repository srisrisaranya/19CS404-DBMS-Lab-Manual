# Experiment 3: DML Commands
# Name: Saranya S
# Register Number: 212223110044
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
```
Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.
```
# program:
```
update sales
set total_sell_price=(sell_price*quantity)
where product_id=10;
```
**Output:**
![image](https://github.com/user-attachments/assets/bc725090-e673-4c98-a1ef-860ab8d3a3d6)

**Question 2**
```
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15
```
# program:
```
update Employees
set salary=salary+500,
    email='updated'
where job_id='SA_REP' 
and commission_pct>0.15;
```
**Output:**
![image](https://github.com/user-attachments/assets/a4cc6b8d-cfe7-40ff-84f9-86e396305e2c)

**Question 3**
```
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 
Customer table (customer_id,cust_name,city,grade,salesman_id)
```
# program:
```
update customer
set grade=5
where city='Chennai';
```
**Output:**
![image](https://github.com/user-attachments/assets/f3811151-a438-4103-af9f-05d524c51cd9)

**Question 4**
```
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.
sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)
```
# program:
```
update sales
set sell_price=sell_price*1.05
where product_id=15 and sale_date='2023-01-31';
```
**Output:**
![image](https://github.com/user-attachments/assets/05617002-9a82-45e5-913a-0dcc0ae0295f)

**Question 5**
```
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.
```
# program:
```
update Products
set sell_price=sell_price*1.15
where quantity<50 and supplier_id=10;
```
**Output:**

**Question 6**
```
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:
Sample table: Customer
```
# program:
```
delete from Customer
where (GRADE>2 and PAYMENT_AMT<(select avg(PAYMENT_AMT) from customer))
or OUTSTANDING_AMT>8000;
```

**Output:**

![image](https://github.com/user-attachments/assets/be1a4741-b196-4e4e-acee-0f817d6ade5b)

**Question 7**
```
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.
Sample table: Customer
```
# program:
```
delete from customer
where GRADE>=2;
```
**Output:**

![image](https://github.com/user-attachments/assets/5770e83b-ccec-47f6-8316-4f4a9005dc5a)

**Question 8**
```
Write a SQL query to Delete All Doctors with a NULL Last Name
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization
```
# program:
```
delete from Doctors
where last_name is NULL;
```
**Output:**
![image](https://github.com/user-attachments/assets/67e0d203-149e-451e-8c58-e6c9ba132910)

**Question 9**
```
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.
Sample table: Customer
```
# program:
```
delete from Customer
where CUST_CITY!= 'New York' and OUTSTANDING_AMT>5000;
```
**Output:**
![image](https://github.com/user-attachments/assets/3f397de9-f8bc-43b2-ae3d-93fe87a01f9e)

**Question 10**
```
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000
Sample table: Customer
```
# program:
```
delete from customer
where (GRADE=3 or AGENT_CODE='A008')
AND OUTSTANDING_AMT<5000;
```
**Output:**
![image](https://github.com/user-attachments/assets/b66a2c6d-2b13-49c8-bce3-dc3488c23781)

![image](https://github.com/user-attachments/assets/209ca79e-cee4-44cf-917f-80ea2aaf87e6)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
