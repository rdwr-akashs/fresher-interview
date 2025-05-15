# DBMS Interview Questions for Freshers

This document provides a curated list of DBMS interview questions for freshers, categorized by difficulty (easy, medium, hard/tricky). Each question includes a detailed answer, and SQL queries are provided where relevant to demonstrate practical application.

---

## Easy Questions

### 1. What is a DBMS, and how does it differ from a file-based system?
**Answer**: A DBMS (Database Management System) is software that manages databases, allowing storage, retrieval, and manipulation of data efficiently. It provides features like data integrity, security, and concurrency control.

**Difference from File-Based System**:
- **DBMS**: Centralized control, supports complex queries, ensures data consistency, provides backup/recovery.
- **File-Based System**: Data stored in flat files, no query language, prone to redundancy, lacks concurrency control.

### 2. What is a primary key?
**Answer**: A primary key is a unique identifier for each record in a database table. It ensures that no two rows have the same value and cannot contain NULL values.

**Example**:
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT
);
```
In this table, `StudentID` is the primary key.

### 3. What is the difference between `DELETE` and `TRUNCATE` in SQL?
**Answer**:
- **DELETE**: Removes specific rows from a table based on a condition. It is a DML (Data Manipulation Language) command, logged, and can be rolled back.
- **TRUNCATE**: Removes all rows from a table, resetting it to an empty state. It is a DDL (Data Definition Language) command, faster, but cannot be rolled back in some DBMS.

**Example**:
```sql
-- DELETE
DELETE FROM Students WHERE Age < 18;

-- TRUNCATE
TRUNCATE TABLE Students;
```

### 4. What is a foreign key?
**Answer**: A foreign key is a column (or set of columns) in one table that refers to the primary key in another table, establishing a relationship between them. It enforces referential integrity.

**Example**:
```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    StudentID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);
```
Here, `StudentID` in `Orders` is a foreign key referencing `StudentID` in `Students`.

### 5. What is the `SELECT` statement used for?
**Answer**: The `SELECT` statement retrieves data from one or more tables in a database. It allows filtering, sorting, and grouping of data.

**Example**:
```sql
SELECT Name, Age FROM Students WHERE Age > 18 ORDER BY Name;
```
This query retrieves names and ages of students older than 18, sorted by name.

---

## Medium Questions

### 6. What is normalization, and why is it important?
**Answer**: Normalization is the process of organizing data in a database to eliminate redundancy and ensure data integrity by dividing tables into smaller, related tables based on functional dependencies. It follows rules like 1NF, 2NF, 3NF, etc.

**Importance**:
- Reduces data redundancy.
- Prevents anomalies during insertion, update, or deletion.
- Improves query performance for certain operations.

**Example**: A table with student and course details:
```
StudentID | Name | Course | CourseInstructor
1         | John | Math   | Prof. Smith
1         | John | Physics| Prof. Brown
```
**Normalized (2NF)**:
```sql
-- Students Table
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50)
);

-- Courses Table
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50),
    Instructor VARCHAR(50)
);

-- Enrollments Table
CREATE TABLE Enrollments (
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

### 7. Explain the difference between `INNER JOIN` and `LEFT JOIN`.
**Answer**:
- **INNER JOIN**: Returns only the matching records from both tables.
- **LEFT JOIN**: Returns all records from the left table and matching records from the right table. Non-matching rows from the right table return NULL.

**Example**:
```sql
SELECT s.Name, o.OrderID
FROM Students s
INNER JOIN Orders o ON s.StudentID = o.StudentID;
```
This retrieves students who have placed orders.

```sql
SELECT s.Name, o.OrderID
FROM Students s
LEFT JOIN Orders o ON s.StudentID = o.StudentID;
```
This retrieves all students, with NULL for `OrderID` if they have no orders.

### 8. What is an index, and how does it improve performance?
**Answer**: An index is a database structure that improves the speed of data retrieval operations on a table by creating a quick lookup mechanism. It works like a book’s index, pointing to data locations.

**Types**: Clustered (affects physical order of data) and Non-Clustered (separate structure).

**Example**:
```sql
CREATE INDEX idx_student_name ON Students(Name);
```
This creates an index on the `Name` column to speed up queries like:
```sql
SELECT * FROM Students WHERE Name = 'John';
```

**Trade-off**: Indexes speed up SELECT queries but slow down INSERT, UPDATE, DELETE due to index maintenance.

### 9. Write a query to find the second-highest salary from an Employees table.
**Answer**:
```sql
SELECT MAX(Salary) AS SecondHighestSalary
FROM Employees
WHERE Salary < (SELECT MAX(Salary) FROM Employees);
```
**Explanation**: The subquery finds the highest salary, and the outer query finds the maximum salary less than that, giving the second-highest salary.

**Alternative (Using LIMIT/OFFSET)**:
```sql
SELECT Salary
FROM Employees
ORDER BY Salary DESC
LIMIT 1 OFFSET 1;
```

### 10. What is a self-join, and when is it used?
**Answer**: A self-join is a join where a table is joined with itself to compare rows within the same table. It’s used when a table has a hierarchical relationship or to compare records.

**Example**: Find employees who have the same manager:
```sql
SELECT e1.EmployeeName, e2.EmployeeName AS Manager
FROM Employees e1
INNER JOIN Employees e2 ON e1.ManagerID = e2.EmployeeID;
```

---

## Hard/Tricky Questions

### 11. What is a deadlock, and how can it be prevented in a DBMS?
**Answer**: A deadlock occurs when two or more transactions wait indefinitely for each other to release resources (e.g., locks on rows). For example, Transaction A locks Row 1 and waits for Row 2, while Transaction B locks Row 2 and waits for Row 1.

**Prevention**:
- **Lock Ordering**: Ensure transactions acquire locks in a consistent order.
- **Timeouts**: Set a timeout for transactions to release locks.
- **Deadlock Detection**: Use DBMS tools to detect and resolve deadlocks by terminating one transaction.
- **Minimize Lock Scope**: Reduce the time a transaction holds locks.

**Example (Illustrative, not executable)**:
```sql
-- Transaction 1
BEGIN TRANSACTION;
UPDATE Table1 SET Col1 = 100 WHERE ID = 1;
-- Waits for Table2
UPDATE Table2 SET Col2 = 200 WHERE ID = 2;
COMMIT;

-- Transaction 2
BEGIN TRANSACTION;
UPDATE Table2 SET Col2 = 200 WHERE ID = 2;
-- Waits for Table1
UPDATE Table1 SET Col1 = 100 WHERE ID = 1;
COMMIT;
```
**Prevention**: Ensure both transactions update `Table1` before `Table2`.

### 12. Write a query to find duplicate records in a table.
**Answer**:
```sql
SELECT Name, COUNT(*) AS Count
FROM Students
GROUP BY Name
HAVING COUNT(*) > 1;
```
**Explanation**: This query groups records by `Name` and uses `HAVING` to filter groups with more than one occurrence, indicating duplicates.

**To Delete Duplicates (Keep One)**:
```sql
DELETE FROM Students
WHERE StudentID NOT IN (
    SELECT MIN(StudentID)
    FROM Students
    GROUP BY Name
);
```

### 13. What is the difference between a correlated subquery and a non-correlated subquery?
**Answer**:
- **Non-Correlated Subquery**: Executes independently of the outer query, once, and returns a result used by the outer query.
- **Correlated Subquery**: Executes repeatedly for each row of the outer query, using values from the outer query.

**Example (Non-Correlated)**:
```sql
SELECT Name
FROM Students
WHERE StudentID IN (SELECT StudentID FROM Orders);
```

**Example (Correlated)**:
```sql
SELECT Name
FROM Students s
WHERE EXISTS (
    SELECT 1
    FROM Orders o
    WHERE o.StudentID = s.StudentID
);
```
**Explanation**: The correlated subquery checks for each `Student` if they have an order, re-running for each row in `Students`.

### 14. Write a query to pivot data (convert rows to columns).
**Answer**: Consider a table `Sales` with columns `Year`, `Product`, and `Revenue`. Pivot to show revenue for each product as columns.

```sql
SELECT *
FROM (
    SELECT Year, Product, Revenue
    FROM Sales
) AS SourceTable
PIVOT (
    SUM(Revenue)
    FOR Product IN (Laptop, Phone, Tablet)
) AS PivotTable;
```
**Explanation**: This query transforms rows of products into columns (`Laptop`, `Phone`, `Tablet`) with their respective `Revenue` summed for each `Year`. Note: Syntax may vary (e.g., MySQL uses conditional aggregation):

```sql
SELECT Year,
       SUM(CASE WHEN Product = 'Laptop' THEN Revenue ELSE 0 END) AS Laptop,
       SUM(CASE WHEN Product = 'Phone' THEN Revenue ELSE 0 END) AS Phone,
       SUM(CASE WHEN Product = 'Tablet' THEN Revenue ELSE 0 END) AS Tablet
FROM Sales
GROUP BY Year;
```

### 15. Explain ACID properties with an example.
**Answer**: ACID stands for **Atomicity**, **Consistency**, **Isolation**, **Durability**, ensuring reliable database transactions.

- **Atomicity**: Ensures a transaction is treated as a single unit—either all operations succeed or none do.
- **Consistency**: Ensures the database remains in a valid state before and after a transaction.
- **Isolation**: Ensures transactions are executed independently of one another.
- **Durability**: Ensures committed transactions are permanently saved, even in case of system failure.

**Example**:
```sql
BEGIN TRANSACTION;
UPDATE Accounts SET Balance = Balance - 100 WHERE AccountID = 1;
UPDATE Accounts SET Balance = Balance + 100 WHERE AccountID = 2;
COMMIT;
```
- **Atomicity**: If the second `UPDATE` fails, the first is rolled back.
- **Consistency**: Total balance across accounts remains the same.
- **Isolation**: Another transaction cannot see partial updates.
- **Durability**: After `COMMIT`, the changes are saved permanently.

---

This set of questions covers a broad range of DBMS topics, preparing freshers for technical interviews with practical SQL examples and clear explanations.
