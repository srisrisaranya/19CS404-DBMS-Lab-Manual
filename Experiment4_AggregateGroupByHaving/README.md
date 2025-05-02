# Experiment 4: Aggregate Functions, Group By and Having Clause
# Name: Saranya S
# Register Number: 212223110044
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
```
What is the total number of appointments scheduled for each day?
Table: Appointments

name                 type
-------------------  ----------
AppointmentID        INTEGER
PatientID            INTEGER
DoctorID             INTEGER
AppointmentDateTime  DATETIME
Purpose              TEXT
Status               TEXT
```
# program:
```
select DATE(AppointmentDateTime) as AppointmentDate,
count(*) as TotalAppointments
from Appointments
group by DATE(AppointmentDateTime)
order by AppointmentDate;
```

**Output:**

![image](https://github.com/user-attachments/assets/27ff126f-b56d-4b66-ba50-f6382ca1fd99)

**Question 2**
```
How many prescriptions were written by each doctor?
Sample tablePrescriptions Table
```
# program:
```
select DoctorID,
count(*) as TotalPrescriptions
from Prescriptions
group by DoctorID;
```

**Output:**

![image](https://github.com/user-attachments/assets/173e25e4-e9fe-4ee7-a3ca-9fbe25c83a37)

**Question 3**
```
How many patients are there in each city?
Sample table: Patients Table
```
# program:
```
select Address,
count(*) as TotalPatients
from Patients
group by Address;
```

**Output:**

![image](https://github.com/user-attachments/assets/1d81f11d-6a08-49a1-a3a6-05f351f20017)

**Question 4**
```
Write a SQL query to calculate the total number of working hours of all employees
Sample table: employee1
```
# program:
```
select sum(workhour) as "Total working hours"
from employee1
```

**Output:**

![image](https://github.com/user-attachments/assets/a156af16-017b-424b-998c-2d38d7ee1f39)

**Question 5**
```
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.
Sample table: customer
```
# program:
```
select count(*) as COUNT
from customer
where city='Noida';
```

**Output:**

![image](https://github.com/user-attachments/assets/1ea1a845-4fbc-4edd-bfe0-a960a1ea6770)

**Question 6**
```
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
# program:
```
select sum(purch_amt) as TOTAL
from orders
```

**Output:**

![image](https://github.com/user-attachments/assets/066397a1-02ad-4ee3-8c77-3fa35849479e)

**Question 7**
```
Write a SQL query to find the average length of email addresses (in characters):
Table: customer
name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```
# program:
```
select avg(length(email)) as avg_email_length
from customer
```

**Output:**

![image](https://github.com/user-attachments/assets/bb697094-c247-4863-a903-d3a75b46e34c)

**Question 8**
```
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.
Sample table: products
```
# program:
```
select category_id,count(*) as "count(product_name)"
from products
group by category_id
having category_id<3;
```

**Output:**

![image](https://github.com/user-attachments/assets/b7450e6a-84ee-49f8-98b2-d704abd40929)

**Question 9**
```
Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.
Sample table: customer1
```
# program:
```
select (age/5)*5 as age_group,min(age) as "MIN(age)"
from customer1
group by age_group
having MIN(age)<25;
```

**Output:**

![image](https://github.com/user-attachments/assets/57cd75a8-3dc1-49fb-874c-617d1e4c4859)

**Question 10**
```
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000
Sample table: customer1
```
# program:
```
select address, avg(salary) as "AVG(salary)"
from customer1
group by address
having AVG(salary)<15000;
```

**Output:**

![image](https://github.com/user-attachments/assets/fa67ef19-0e2b-4672-89d3-4f620a621763)

![image](https://github.com/user-attachments/assets/53f79fd2-4ce6-40e1-8335-6fa9bdad7986)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
