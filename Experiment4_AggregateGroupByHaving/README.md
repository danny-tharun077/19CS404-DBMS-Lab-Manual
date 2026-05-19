# Experiment 4: Aggregate Functions, Group By and Having Clause
### Name : THARUN DANIEL Y
### Reg no : 212224050054
# AIM
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
How many appointments are scheduled for each patient?

```sql
SELECT PatientID , count(AppointmentID) as TotalAppointments
FROM Appointments 
group by PatientID
ORDER BY PatientID

```

**Output:**

<img width="693" height="635" alt="4(1)" src="https://github.com/user-attachments/assets/cdabfa3c-7999-4514-a5d7-f80c1184b34b" />


**Question 2**
---
What is the average duration of insurance coverage for patients covered by each insurance company? 

```sql
SELECT InsuranceCompany, AVG(enddate - startdate) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**


<img width="955" height="684" alt="4(2)" src="https://github.com/user-attachments/assets/19967224-5230-4702-9a31-0f42639cda7d" />

**Question 3**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)? 

```sql
select Frequency, count(PatientID) as TotalPrescriptions
FROM Prescriptions
group by Frequency;
```

**Output:**



<img width="786" height="530" alt="4(3)" src="https://github.com/user-attachments/assets/8c65d1a0-8fd7-4f70-ba25-e1ed4ef74f71" />

**Question 4**
---
Write a SQL query to find the average salary of all employees?

```sql
SELECT AVG(income) AS Average_Salary 
FROM employee;
```

**Output:**

<img width="500" height="311" alt="4(4)" src="https://github.com/user-attachments/assets/8e4c6e6d-37c0-4c5b-80bc-439675434034" />


**Question 5**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

```sql
SELECT count(distinct salesman_id) AS COUNT
FROM orders;
```

**Output:**


<img width="399" height="316" alt="4(5)" src="https://github.com/user-attachments/assets/6eeae9e8-0596-493c-ac74-84ed40a2a519" />

**Question 6**
---
 Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```sql
 SELECT COUNT(id) AS COUNT FROM customer 
WHERE city != 'Noida';
```

**Output:**

<img width="394" height="311" alt="4(6)" src="https://github.com/user-attachments/assets/41658891-8838-4501-93e2-e72600800ff8" />


**Question 7**
---
 Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

```sql
SELECT MAX(age) - MIN(age) AS age_difference 
FROM employee;
```

**Output:**

<img width="458" height="312" alt="4(7)" src="https://github.com/user-attachments/assets/862b76e8-b683-4db6-bea9-dd5b4e655a1a" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

```sql
SELECT jdate, MIN(workhour) 
FROM employee1 
GROUP BY jdate 
HAVING MIN(workhour) < 10;
```

**Output:**

<img width="656" height="379" alt="4(8)" src="https://github.com/user-attachments/assets/7717bf68-33d4-4c00-96e5-83de3961aa72" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

```sql
SELECT jdate, SUM(workhour)
FROM employee1 
GROUP BY jdate
HAVING SUM(workhour) >= 40;
```

**Output:**


<img width="636" height="373" alt="4(9)" src="https://github.com/user-attachments/assets/a85a2dde-e41c-4b55-92f9-d9c68a1a870a" />

**Question 10**
---
 Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

```sql
SELECT age, MIN(income) 
FROM employee 
GROUP BY age
HAVING MIN(income) < 400000;
```

**Output:**


<img width="565" height="333" alt="4(10)" src="https://github.com/user-attachments/assets/b3491f63-2157-4933-a792-4ed42c366d89" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
