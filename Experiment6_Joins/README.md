# Experiment 6: Joins

### Name : THARUN DANIEL Y
### Reg No :212224050054

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
<img width="1112" height="608" alt="image" src="https://github.com/user-attachments/assets/01fd38f9-b066-47b9-80af-beccbabb1545" />



```sql
SELECT 
    customer.cust_name AS "Customer Name", 
    customer.city AS "city", 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    customer
JOIN 
    salesman
ON 
    customer.salesman_id = salesman.salesman_id
WHERE 
    salesman.commission > 0.12;
```




**Output:**
<img width="885" height="467" alt="image" src="https://github.com/user-attachments/assets/5e5d8fa2-9333-4233-ab30-783f1ff50889" />



**Question 2**
---
<img width="1333" height="448" alt="6Q2" src="https://github.com/user-attachments/assets/6e3a6c5d-7a75-481d-87c6-755eaf151d8d" />


```sql
SELECT 
    patients.date_of_birth, 
    appointments.*
FROM 
    patients
JOIN 
    appointments
ON 
    patients.patient_id = appointments.patient_id
WHERE 
    patients.first_name = 'Alice';
```

**Output:**

<img width="1143" height="220" alt="6O2" src="https://github.com/user-attachments/assets/02bf4621-56d6-49dc-8c5b-90f92499ee00" />


**Question 3**
---
<img width="890" height="655" alt="6(3)" src="https://github.com/user-attachments/assets/1c4af177-5a02-402f-81da-621fab301694" />


```sql
SELECT 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt, 
    customer.cust_name AS "Customer Name", 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    orders
JOIN 
    customer ON orders.customer_id = customer.customer_id
JOIN 
    salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**

<img width="1318" height="761" alt="6O(3)" src="https://github.com/user-attachments/assets/bd00a557-924c-46d0-a69c-13cab7aee215" />


**Question 4**
---
<img width="1215" height="385" alt="6(4)" src="https://github.com/user-attachments/assets/fe767411-5a2c-4167-8c5a-c6e19b13ce4e" />


```sql
SELECT 
    customer.cust_name, 
    customer.city, 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.city AS "city"
FROM 
    customer
JOIN 
    salesman ON customer.salesman_id = salesman.salesman_id
WHERE 
    customer.grade < 300
ORDER BY 
    customer.customer_id ASC;
```

**Output:**

<img width="1026" height="462" alt="6(4)o" src="https://github.com/user-attachments/assets/64cf7072-8114-4d53-bb0a-963ca4fa2a70" />


**Question 5**
---
<img width="1297" height="273" alt="6(5)" src="https://github.com/user-attachments/assets/ead1fd18-6197-4038-a7e0-5f7e92438ebb" />


```sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**

<img width="270" height="267" alt="6(5)o" src="https://github.com/user-attachments/assets/83792556-b0a2-4af0-8fd1-0714e3183711" />


**Question 6**
---
<img width="971" height="259" alt="6(6)" src="https://github.com/user-attachments/assets/f67f5098-cd99-4674-a108-779cd2dba8ce" />


```sql
SELECT 
    c.cust_name
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id;
```

**Output:**

<img width="274" height="759" alt="6(6)o" src="https://github.com/user-attachments/assets/b9465cf5-82e6-4fcc-a676-016d7d45c81f" />





**Question 7**
---
<img width="1560" height="360" alt="image" src="https://github.com/user-attachments/assets/c5fbb76e-d472-4234-a334-7977ac2b3f20" />


```sql
SELECT 
    p.first_name AS patient_name, 
    t.*
FROM 
    patients AS p
INNER JOIN 
    test_results AS t ON p.patient_id = t.patient_id;
```

**Output:**

<img width="1370" height="367" alt="6(7)o" src="https://github.com/user-attachments/assets/d1f1d5fd-5993-456a-8cbb-5b6559867aa5" />


**Question 8**
---
<img width="1154" height="459" alt="6(8)" src="https://github.com/user-attachments/assets/93228d2e-05ac-4df2-9ef4-4db2d8ebd1c1" />


```sql
SELECT 
    c.cust_name, 
    c.city AS city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="1202" height="657" alt="6(8)o" src="https://github.com/user-attachments/assets/40fa3aed-ddcd-455e-9e8c-401cac33a3d4" />


**Question 9**
---
<img width="1300" height="435" alt="6(9)" src="https://github.com/user-attachments/assets/908abebb-a176-43fd-97d8-3fccb794a748" />


```sql
SELECT 
    p.admission_date, 
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;
```

**Output:**

<img width="555" height="368" alt="6(9)o" src="https://github.com/user-attachments/assets/0a3efcb8-7466-46bb-8989-10046a5f96ce" />


**Question 10**
---
<img width="1041" height="464" alt="6(10)" src="https://github.com/user-attachments/assets/c645f55d-535e-439a-9e89-7f3f856a0e83" />


```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.commission
FROM 
    customer c
JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id;
```

**Output:**
<img width="1037" height="660" alt="6(10)o" src="https://github.com/user-attachments/assets/6f163c9c-a039-4e4c-a1db-c8b1ab1a9518" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
