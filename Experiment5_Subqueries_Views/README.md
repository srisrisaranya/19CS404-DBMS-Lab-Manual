# Experiment 5: Subqueries and Views
# Name: Saranya S
# Register Number: 212223110044
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
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi
Sample table: CUSTOMERS
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
# program:
```
select *
FROM CUSTOMERS
WHERE Address='Delhi';
```
**Output:**

![image](https://github.com/user-attachments/assets/5689c288-1542-43c9-a982-4a050362a054)

**Question 2**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30
Sample table: CUSTOMERS
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
# program:
```
select *
FROM CUSTOMERS
WHERE AGE<30;
```
**Output:**

![image](https://github.com/user-attachments/assets/0d3b299f-0d87-4069-b3cd-1ce2d563cfd5)

**Question 3**
```
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.
salesman table
name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
# program:
```
select o.ord_no, o.purch_amt, o.ord_date,o.salesman_id from orders o
join salesman s on s.salesman_id=o.salesman_id
where s.commission=(select max(commission) from salesman)
```
**Output:**

![image](https://github.com/user-attachments/assets/f2d36606-c921-4828-b172-efa9d9872e97)

**Question 4**
```
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.
Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```
# program;
```
select *
FROM GRADES g
where grade=(
select MIN(grade)
from GRADES
WHERE subject=g.subject
);
```
**Output:**

![image](https://github.com/user-attachments/assets/ca1c6847-16ad-44bf-99d1-cf6ea488970d)


**Question 5**
```
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.
salesman table
name                 type
---------------   ---------------
salesman_id       numeric(5)
name                  varchar(30)
city                     varchar(15)
commission       decimal(5,2)

customer table
name              type
-----------       ----------
customer_id   int
cust_name     text
city                text
grade            int
salesman_id  int
```
# program:
```
select s.salesman_id,s.name
from salesman s
join CUSTOMER c on s.salesman_id=c.salesman_id
group by s.salesman_id,s.name
having COUNT(c.customer_id)>1;
```

**Output:**

![image](https://github.com/user-attachments/assets/a1bce1e0-733e-44db-897d-b52ed765ef89)


**Question 6**
```
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.
Note: date should be yyyy-mm-dd format
ORDERS TABLE
name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```
# program:
```
select * from orders
where purch_amt>(
select avg(purch_amt)
from orders
where ord_date='2012-10-10'
)
```
**Output:**

![image](https://github.com/user-attachments/assets/45674ffb-853f-4d71-9c6a-81b624d6edc0)

**Question 7**
```
Write a SQL query to List departments with names longer than the average length
Departments Table (attributes: department_id, department_name)
```
# program:
```
select *
from departments
where length(department_name)>(
select avg(length(department_name))
from departments);
```
**Output:**

![image](https://github.com/user-attachments/assets/0a7fd5ba-c8c2-4da8-b102-c90acec5ca16)

**Question 8**
```
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
salesman table
name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
 ```
# program:
```
select o.ord_no, o.purch_amt, o.ord_date, o.customer_id ,o.salesman_id
from orders o
join salesman s on s.salesman_id=o.salesman_id
where s.name='Paul Adam'
```
**Output:**

![image](https://github.com/user-attachments/assets/25703c4a-deb0-4da8-9556-ae31d65a861e)

**Question 9**
```
From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.
Table Name: orders
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
# program:
```
select ord_no, purch_amt, ord_date, customer_id, salesman_id
from Orders
where salesman_id in (
select salesman_id
from Orders
where customer_id=3007
);
```
**Output:**

![image](https://github.com/user-attachments/assets/49824a18-dfa0-4e2e-b0e5-e463885a8865)

**Question 10**
```
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
SALESMAN TABLE
name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

ORDERS TABLE
name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```
# program:
```
select o.ord_no, o.purch_amt, o.ord_date, o.customer_id,o.salesman_id
from orders o
join Salesman s on o.salesman_id=s.salesman_id
where s.city='New York';
```
**Output:**

![image](https://github.com/user-attachments/assets/f0b6ce86-d934-4298-9c10-fa9679c48475)

![image](https://github.com/user-attachments/assets/2c7c7d1b-8c3b-4c87-a04a-4373625b80f7)

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
