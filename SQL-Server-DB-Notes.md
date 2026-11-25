### What is database ?

Database a container which contains functions, 

### How to create a database in MS-SQL ?

Right click on Databases => Click on New Database =>

There will a window open => Database Name => Practice_DB

### A basic Select Statement

SELECT 1 + 2 AS Result


### Why we write GO?

SELECT 1 + 2 AS Result
GO

SELECT 1 - 2 AS Result
GO

**Without GO - In this case the SQL satement will consider the whole as a batch and execute.**

**With Go - If we use GO, SQL statement will not consider this as a batch.**

Batches are not important for SELECT statement but for other SQL statements e.g Update, Delete

**AS Result** As is a alias for the column header, without AS Result it will return as Not Column Name

### Creating a Table

Using GUI => Right Click on the Tables => New => Table...
Name it with anything=> tblFirst.

**tbl** this is a hungerian nemeing convention

**[dbo].[tblFirst]** Here dbo stannds for Database Owner

### Create database objects
1.Create and alter tables using T-SQL syntax(simple statements)

	a. Create tables using without using the built in tools 
	b. ALTER
	c. DROP
	d. ALTER Column
	e. CREATE

```sql
CREATE TABLE tbl_demo_table
(FirstName varchar, LastName varchar, age int)
```

```sql
	--CREATE TABLE [tbl_demo_table](FirstName varchar(100), LastName varchar(100), age int)
	SELECT * FROM [tbl_demo_table]
	GO -- Is groups the SQL statement

	--Insert data into the exsting table
	INSERT INTO [tbl_demo_table](FirstName, LastName, age)
	VALUES
	('Pabitra', 'Nahak', 20),
	('Robin', 'A', 21),
	('Maria', 'Na', 22),
	('Nick', 'M', 23);
	 
	GO

	--DELETE FROM [tbl_demo_table] where age = 25

	--DROP TABLE [tbl_demo_table] - Deletes the entire table from Databse

	--DELETE FROM [tbl_demo_table] -- Deletes the contents inside the table  

	--TRUNCATE TABLE [tbl_demo_table] -- Deletes the contents inside the table - its faster then DELETE syntax
```


### Variable Declaration

```sql
	 DECLARE @Value AS int = 5
	 Set @Value = @Value * 4 - 2
	 SELECT   @Value AS Data
```

## Create table 

- ### tblEmployee

```sql
	CREATE TABLE tblEmployee (
		EmployeeId INT IDENTITY(1,1) PRIMARY KEY,
		FirstName VARCHAR(50) NOT NULL,
		LastName VARCHAR(50) NOT NULL,
		Email VARCHAR(100) UNIQUE,
		PhoneNumber VARCHAR(50),
		DateOfBirth Date,
		HireDate Date,
		Department VARCHAR(50),
		JobTitle VARCHAR(50),
		Salary DECIMAL(10, 2),
		IsActive BIT DEFAULT 1,
		CreatedDate DATETIME DEFAULT GETDATE()
	);
```

# tblEmployee Columns Explained (Short & Informative)

## EmployeeId (`INT IDENTITY(1,1) PRIMARY KEY`)
- Unique ID for each employee.
- Auto-generated starting from 1.
- Acts as the table's primary key.

## FirstName (`VARCHAR(50) NOT NULL`)
- Stores the employee's first name.
- Required field (cannot be empty).

## LastName (`VARCHAR(50) NOT NULL`)
- Stores the employee's last name/surname.
- Required field.

## Email (`VARCHAR(100) UNIQUE`)
- Stores the employee's email address.
- Must be unique for every employee.

## PhoneNumber (`VARCHAR(50)`)
- Stores the employee's contact number.
- Uses text type to support country codes and special characters.

## DateOfBirth (`DATE`)
- Stores the employee's birth date.
- Used for age-related calculations.

## HireDate (`DATE`)
- Stores the date the employee joined the company.
- Used to calculate experience or tenure.

## Department (`VARCHAR(50)`)
- Stores the department where the employee works.
- Examples: IT, HR, Finance, Sales.

## JobTitle (`VARCHAR(50)`)
- Stores the employee's role or designation.
- Examples: Software Engineer, Manager, Accountant.

## Salary (`DECIMAL(10,2)`)
- Stores the employee's salary.
- Supports up to 10 digits with 2 decimal places.

## IsActive (`BIT DEFAULT 1`)
- Indicates whether the employee is active.
- `1 = Active`, `0 = Inactive`.
- New employees are active by default.

## CreatedDate (`DATETIME DEFAULT GETDATE()`)
- Stores when the employee record was created.
- Automatically populated with the current date and time.

## Inserting values to tblEmployee

```sql
-- By passing the excact value to the column
INSERT INTO tblEmployee
VALUES(
    'John',
    'Thomas',
    'johnthomas@dev.com',
    '965656565',
    GETDATE(),
    GETDATE(),
    'IT',
    'Software Engineer',
    200,
    1, 
    GETDATE()
)


-- Keeping the order of the columns and insert the data based on that
	INSERT INTO tblEmployee
	(
		FirstName,
		LastName,
		Email,
		PhoneNumber,
		DateOfBirth,
		HireDate,
		Department,
		JobTitle,
		Salary
	)
	VALUES
	(
		'John',
		'Smith',
		'john.smith@company.com',
		'+91-9876543210',
		'1995-06-15',
		'2024-01-10',
		'IT',
		'Software Engineer',
		75000.00
	);
```

## Inserting more records

```sql
INSERT INTO tblEmployee
(
    FirstName,
    LastName,
    Email,
    PhoneNumber,
    DateOfBirth,
    HireDate,
    Department,
    JobTitle,
    Salary
)
VALUES
('John', 'Smith', 'john.smith@company.com', '+91-9876543201', '1990-05-12', '2020-01-15', 'IT', 'Software Engineer', 75000.00),
('Mary', 'Johnson', 'mary.johnson@company.com', '+91-9876543202', '1992-08-23', '2019-06-10', 'HR', 'HR Manager', 68000.00),
('David', 'Brown', 'david.brown@company.com', '+91-9876543203', '1988-11-05', '2018-03-20', 'Finance', 'Accountant', 62000.00),
('Sarah', 'Davis', 'sarah.davis@company.com', '+91-9876543204', '1995-02-18', '2021-07-12', 'Marketing', 'Marketing Executive', 58000.00),
('Michael', 'Wilson', 'michael.wilson@company.com', '+91-9876543205', '1991-09-30', '2017-04-25', 'Sales', 'Sales Manager', 85000.00),
('Emily', 'Taylor', 'emily.taylor@company.com', '+91-9876543206', '1994-07-14', '2022-02-01', 'IT', 'QA Engineer', 65000.00),
('Robert', 'Anderson', 'robert.anderson@company.com', '+91-9876543207', '1987-12-11', '2016-09-15', 'Operations', 'Operations Manager', 90000.00),
('Jessica', 'Thomas', 'jessica.thomas@company.com', '+91-9876543208', '1993-04-06', '2020-11-16', 'Finance', 'Financial Analyst', 70000.00),
('Daniel', 'Jackson', 'daniel.jackson@company.com', '+91-9876543209', '1989-10-27', '2019-01-07', 'IT', 'System Administrator', 72000.00),
('Jennifer', 'White', 'jennifer.white@company.com', '+91-9876543210', '1996-03-19', '2023-05-08', 'HR', 'Recruiter', 55000.00),
('James', 'Harris', 'james.harris@company.com', '+91-9876543211', '1990-06-24', '2018-08-13', 'Sales', 'Sales Executive', 60000.00),
('Linda', 'Martin', 'linda.martin@company.com', '+91-9876543212', '1992-01-17', '2019-10-21', 'Marketing', 'Content Specialist', 57000.00),
('William', 'Thompson', 'william.thompson@company.com', '+91-9876543213', '1986-08-09', '2015-12-14', 'IT', 'Technical Lead', 110000.00),
('Patricia', 'Garcia', 'patricia.garcia@company.com', '+91-9876543214', '1994-05-28', '2021-09-06', 'Customer Support', 'Support Executive', 50000.00),
('Christopher', 'Martinez', 'christopher.martinez@company.com', '+91-9876543215', '1988-02-22', '2017-06-19', 'Operations', 'Project Manager', 95000.00),
('Barbara', 'Robinson', 'barbara.robinson@company.com', '+91-9876543216', '1995-11-03', '2022-04-11', 'Finance', 'Accounts Executive', 59000.00),
('Joseph', 'Clark', 'joseph.clark@company.com', '+91-9876543217', '1991-07-16', '2018-11-01', 'IT', 'Database Administrator', 88000.00),
('Susan', 'Rodriguez', 'susan.rodriguez@company.com', '+91-9876543218', '1993-09-08', '2020-03-09', 'HR', 'Training Coordinator', 61000.00),
('Charles', 'Lewis', 'charles.lewis@company.com', '+91-9876543219', '1987-04-13', '2016-07-25', 'Sales', 'Regional Sales Manager', 98000.00),
('Karen', 'Lee', 'karen.lee@company.com', '+91-9876543220', '1996-12-01', '2023-01-17', 'Marketing', 'Digital Marketing Specialist', 56000.00);
```

```sql
	select * from tblEmployee

	where Salary > 72000.00


	select * from tblEmployee
	where Salary != 200

	select * from tblEmployee
	where Salary between 60000.00 and 68000


	select * from tblEmployee
	where Salary in (60000.00, 63000)

	SELECT *
	FROM tblEmployee
	WHERE HireDate BETWEEN '2024-01-10' AND '2026-11-24';

	select * from tblEmployee
	where HireDate in( '2026-11-24' ,  '2024-01-10')
	
	
	SELECT 
	YEAR(DateOfBirth) AS YearOnly, COUNT(*) AS GroupedByYear
	FROM tblEmployee
	GROUP BY YEAR(DateOfBirth)

	SELECT 
	YEAR(DateOfBirth) AS YearOnly, COUNT(*) AS GroupedByYear
	FROM tblEmployee
	WHERE 1 = 1
	GROUP BY YEAR(DateOfBirth)
	
	SELECT 
	LEFT(FirstName, 1) as Initial, 
	COUNT(*) AS LetterCount 
	from tblEmployee
	GROUP BY LEFT(FirstName, 1)
	ORDER BY LEFT(FirstName, 1)
```

# HAVING Clause in SQL

## What is the HAVING Clause?

The `HAVING` clause is used to **filter grouped data after aggregation** (such as `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()`).

### Key Difference

- `WHERE` filters **rows before grouping**.
- `HAVING` filters **groups after grouping**.

---

## SQL Execution Order

```sql
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
```

---

## Example: Departments with More Than 3 Employees

### Incorrect

```sql
SELECT Department, COUNT(*)
FROM*tblEmployee
WHERE COUNT(*) > 3
GROUP BY Department;
```

❌ Error because aggregate functions cannot be used in the `WHERE` clause.

### Correct

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM tblEmploye*
GROUP BY Department
HAVING COUNT(*) > 3;
```

✅ Returns departments having more than 3 employees.

---

# Real-World Scenarios

## 1. Departments with High Employee Count

```sql
SELECT Department, COUNT(*) AS TotalEmployees
FROM tblEmploy*e
GROUP BY Department
HAVING COUNT(*) >= 10;
```

**Use Case:** Find departments with at least 10 employees.

---

## 2. Departments with Large Salary Expenses

```sql
SELECT Department, SUM(Salary) AS TotalSalary
FROM tblEmployee
GROUP BY Department
HAVING SUM(Salary) > 500000;
```

**Use Case:** Identify departments whose total salary cost exceeds 500,000.

---

## 3. Managers with Large Teams

```sql
SELECT ManagerId, COUNT(*) AS TeamSize
FROM Employe*s
GROUP BY ManagerId
HAVING COUNT(*) > 5;
```

**Use Case:** Find managers responsible for more than 5 employees.

---

## 4. Customers with Multiple Orders

```sql
SELECT CustomerId, COUNT(*) AS TotalOrders*FROM Orders
GROUP BY CustomerId
HA*ING COUNT(*) > 10;
```

**Use Case:** Identify loyal customers with more than 10 orders.

---

## 5. Products with High Sales

```sql
SELECT ProductId, SUM(Amount) AS TotalSales
FROM Sales
GROUP BY ProductId
HAVING SUM(Amount) > 100000;
```

**Use Case:** Find products generating more than 100,000 in sales.

---

# Using WHERE and HAVING Together

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM tblEmploye*
WHERE HireDate >= '*020-01-01'
GROUP BY Department*HAVING COUNT(*) > 3;
```

### What Happens Here?

1. `WHERE` filters employees hired after January 1, 2020.
2. `GROUP BY` groups the remaining employees by department.
3. `HAVING` returns only departments with more than 3 employees.

---

# WHERE vs HAVING

| WHERE | HAVING |
|---------|---------|
| Filters individual rows | Filters grouped results |
| Executes before `GROUP BY` | Executes after `GROUP BY` |
| Cannot use aggregate functions | Can use aggregate functions |
| Reduces rows before grouping | Filters groups after aggregation |

---

# Memory Trick

✅ **WHERE = Row Filter**

✅ **HAVING = Group Filter**

Example:

```sql
SELECT Department, AVG(Salary) AS AverageSalary
FROM tblEmployee
GROUP BY Department
HAVING AVG(Salary) > 70000;
```

This means:

> Show only the departments whose average salary is greater than 70,000.

```sql
	SELECT Department, Count(*) As DeptCount
	from tblEmployee
	GROUP BY COUNT(*) Department
	HAVING COUNT(*) > 2
```

***Date reflectes here In a number format(1,2 etc.)***
```sql
	SELECT DATEPART(month, HireDate) As MonthNumber, Count(*) As DeptCount
	from tblEmployee
	GROUP BY  DATEPART(month, HireDate)  
	HAVING COUNT(*)< GETDATE()
	Order by DeptCount asc
```

***Date reflectes here In a Name format (January, February, etc.)***
```sql
	SELECT DATEPART(month, HireDate) As MonthNumber, Count(*) As DeptCount
	from tblEmployee
	GROUP BY  DATEPART(month, HireDate)  
	HAVING COUNT(*)< GETDATE()
	Order by DeptCount asc
```

### Creating tblTransaction

```sql
	CREATE TABLE tblTransaction(
		TransactionId INT IDENTITY(1,1) PRIMARY KEY,
		EmployeeId INT NOT NULL,
		TransactionDate DATETIME DEFAULT GETDATE(),
		TransactionType VARCHAR(50) NOT NULL,
		Amount DECIMAL(10, 2),
		Description VARCHAR(255),
		Status VARCHAR(20) DEFAULT 'Pending',
		CreatedDate DATETIME DEFAULT GETDATE(),
		CONSTRAINT FK_tblTransaction_tblEmployee
		FOREIGN KEY (EmployeeId)
		REFERENCES tblEmployee(EmployeeId)
	);
```


### How can you insert data from a excel file to SQL table

```sql
BULK INSERT tblTransaction
FROM 'D:\Database Course\MS-SQL\tblTransaction_500_records_csv.csv'
WITH(
    FIRSTROW = 2,
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n'
);
```

### JOINS

# SQL JOIN Types

## INNER JOIN
- Returns only the rows that have matching values in both tables.
- Excludes unmatched records from either table.

```sql
SELECT *
FROM tblEmployee e
INNER JOIN tblTransaction t
    ON e.EmployeeId = t.EmployeeId;
```

**Example Result:**
- Employees who have transactions.

---

## LEFT JOIN
- Returns all rows from the left table (`tblEmployee`).
- Returns matching rows from the right table (`tblTransaction`).
- If no match exists, `NULL` values are returned for the right table columns.

```sql
SELECT *
FROM tblEmployee e
LEFT JOIN tblTransaction t
    ON e.EmployeeId = t.EmployeeId;
```

**Example Result:**
- All employees, including those without transactions.

---

## RIGHT JOIN
- Returns all rows from the right table (`tblTransaction`).
- Returns matching rows from the left table (`tblEmployee`).
- If no match exists, `NULL` values are returned for the left table columns.

```sql
SELECT *
FROM tblEmployee e
RIGHT JOIN tblTransaction t
    ON e.EmployeeId = t.EmployeeId;
```

**Example Result:**
- All transactions, including those without a matching employee.

---

## FULL JOIN
- Returns all rows from both tables.
- Matches records where possible.
- Returns `NULL` values where no match exists.

```sql
SELECT *
FROM tblEmployee e
FULL JOIN tblTransaction t
    ON e.EmployeeId = t.EmployeeId;
```

**Example Result:**
- All employees and all transactions, whether they match or not.

---

# Quick Summary

| JOIN Type | Returns |
|------------|----------|
| `INNER JOIN` | Matching records only |
| `LEFT JOIN` | All employees + matching transactions |
| `RIGHT JOIN` | All transactions + matching employees |
| `FULL JOIN` | All records from both tables |

## Memory Trick

```text
INNER JOIN = Intersection
LEFT JOIN  = Everything on the Left + Matches
RIGHT JOIN = Everything on the Right + Matches
FULL JOIN  = Everything from Both Tables
```
## GROUP BY
```sql

SELECT 
FirstName, e.EmployeeId, SUM(Amount) AS TOTAL_AMOUNT
FROM tblEmployee e 
JOIN tblTransaction t
ON t.EmployeeId = e.EmployeeId
GROUP BY FirstName, e.EmployeeId 
ORDER BY FirstName
```

# SQL JOIN Types - Interview Explanation

## INNER JOIN

An INNER JOIN returns only the records that have matching values in both tables.

### Example
If I join `tblEmployee` and `tblTransaction` using `EmployeeId`, only employees who have transactions will be returned.

### Business Use Case
Used when we need only related data from both tables.

Example:
- Get employees who received a salary payment.
- Get customers who placed orders.

---

## LEFT JOIN

A LEFT JOIN returns all records from the left table and matching records from the right table.

If no match exists, NULL values are returned for the right table columns.

### Example
If I make `tblEmployee` the left table, all employees will be returned, even if they don't have any transactions.

### Business Use Case
Used to identify missing records.

Example:
- Employees without transactions.
- Customers who have not placed any orders.
- Students who have not enrolled in any courses.

---

## RIGHT JOIN

A RIGHT JOIN returns all records from the right table and matching records from the left table.

If no match exists, NULL values are returned for the left table columns.

### Example
All transactions are returned, even if an employee record is missing.

### Business Use Case
Used when the right table is more important for analysis.

Example:
- Find transactions that don't have associated employee records.
- Audit orphaned records.

---

## FULL JOIN

A FULL JOIN returns all records from both tables.

Matching records are joined together, and non-matching records from either table are returned with NULL values.

### Business Use Case
Used for reconciliation and data validation.

Example:
- Compare employee records with transaction records.
- Identify missing or unmatched data on either side.

---

# Short Interview Answer (30 Seconds)

"A JOIN is used to combine data from multiple tables based on a common column. An INNER JOIN returns only matching records, a LEFT JOIN returns all records from the left table and matching records from the right table, a RIGHT JOIN returns all records from the right table and matching records from the left table, and a FULL JOIN returns all records from both tables, including unmatched records. In real-world projects, INNER JOIN and LEFT JOIN are the most commonly used."
