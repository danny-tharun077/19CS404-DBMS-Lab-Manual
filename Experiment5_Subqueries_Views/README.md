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
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject. Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="1136" height="335" alt="5(1)" src="https://github.com/user-attachments/assets/1043ea79-b20c-4a81-a8ec-182d8f97f140" />


**Question 2**
---
Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer
```
name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER
```

```sql
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);

```

**Output:**

<img width="1118" height="367" alt="5(2)" src="https://github.com/user-attachments/assets/3b6ded95-9dea-48a5-953a-6f6cc0898971" />


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS
```
ID          NAME          AGE            ADDRESS           SALARY
----------  ----------  ----------     ----------         ----------

1          Ramesh       32              Ahmedabad           2000
2          Khilan       25              Delhi               1500
3          Kaushik      23              Kota                2000
4          Chaitali     25              Mumbai              6500
5          Hardik       27              Bhopal              8500
6          Komal        22              Hyderabad           4500
7          Muffy        24              Indore              10000
```

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```

**Output:**

<img width="1000" height="352" alt="5(3)" src="https://github.com/user-attachments/assets/9fe848fd-f4f6-40a9-a27a-c23b2031ad9f" />


**Question 4**
---
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

customer table
```
name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int
```
```sql
SELECT grade, COUNT(*)
FROM customer
WHERE  grade > (SELECT AVG(grade) FROM customer WHERE city = 'New York')
GROUP BY grade;

```

**Output:**

<img width="493" height="257" alt="5(4)" src="https://github.com/user-attachments/assets/08775749-c0e1-468b-9032-68116d298966" />


**Question 5**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS
```

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
```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';

```

**Output:**



**Question 6**
---
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE<img width="1005" height="250" alt="5(5)" src="https://github.com/user-attachments/assets/f2615b6a-c267-4eb7-953c-a075d3edabe7" />

```
name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```
```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM ORDERS
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM ORDERS
    WHERE ord_date = '2012-10-10'
);

```

**Output:**

<img width="1015" height="348" alt="5(6)" src="https://github.com/user-attachments/assets/27786e0c-a59f-4fbe-abcd-fb83e1a5bbd0" />


**Question 7**
---
From the following tables write a SQL query to find all orders generated by New York-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table
```
name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)
```
orders table
```
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**
<img width="998" height="353" alt="5(7)" src="https://github.com/user-attachments/assets/5249bc21-70a9-41f1-8790-f494372ed12a" />


**Question 8**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table
```
name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)
```
orders table
```
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);

```

**Output:**

<img width="826" height="357" alt="5(8)" src="https://github.com/user-attachments/assets/aa772c1d-d1f5-4260-bb43-737b2b016885" />


**Question 9**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE
```
name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

```


ORDERS TABLE
```

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**

<img width="981" height="371" alt="5(9)" src="https://github.com/user-attachments/assets/dcc66d10-cd3e-429f-a965-f69ec43a5fd7" />


**Question 10**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT student_id, student_name, subject, grade
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1087" height="330" alt="5(10)" src="https://github.com/user-attachments/assets/c4caf0b9-ce35-40a0-a9d3-c30f0dabae3d" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
