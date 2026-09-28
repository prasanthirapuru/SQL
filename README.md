# Top 20 SQL Interview Questions for Backend Developers

## Complete interview answers + terminology explanations + SQL syntax with comments

This guide covers all 20 questions in an interview-ready format. For each question, you get a short answer you can speak to the interviewer, explanations of the important terminology, and SQL examples with comments explaining what each command does.

Note: The examples mainly use PostgreSQL-compatible SQL. Where syntax differs in MySQL, SQL Server, or Oracle, I’ll point it out.

---

## 📑 Table of Contents

- [1. SQL Fundamentals](#1-sql-fundamentals)
  - [Q1. What is SQL, and what are the different types of SQL commands?](#q1-what-is-sql-and-what-are-the-different-types-of-sql-commands)
- [2. SELECT Queries](#2-select-queries)
  - [Q2. How do you retrieve, filter, sort, and limit data using SELECT, WHERE, ORDER BY, DISTINCT, and LIMIT?](#q2-how-do-you-retrieve-filter-sort-and-limit-data-using-select-where-order-by-distinct-and-limit)
- [3. SQL Operators](#3-sql-operators)
  - [Q3. What are the different SQL operators?](#q3-what-are-the-different-sql-operators)
- [4. SQL Joins](#4-sql-joins)
  - [Q4. What are the different types of SQL joins?](#q4-what-are-the-different-types-of-sql-joins)
- [5. Aggregate Functions](#5-aggregate-functions)
  - [Q5. What are aggregate functions, and how do GROUP BY and HAVING work?](#q5-what-are-aggregate-functions-and-how-do-group-by-and-having-work)
- [6. NULL Handling](#6-null-handling)
  - [Q6. What is NULL, and how do IS NULL, COALESCE(), and NULLIF() work?](#q6-what-is-null-and-how-do-is-null-coalesce-and-nullif-work)
- [7. Subqueries](#7-subqueries)
  - [Q7. What is a subquery, and what are its different types?](#q7-what-is-a-subquery-and-what-are-its-different-types)
- [8. Set Operations](#8-set-operations)
  - [Q8. What is the difference between UNION, UNION ALL, INTERSECT, and EXCEPT?](#q8-what-is-the-difference-between-union-union-all-intersect-and-except)
- [9. Conditional Expressions](#9-conditional-expressions)
  - [Q9. How do you use CASE expressions in SQL?](#q9-how-do-you-use-case-expressions-in-sql)
- [10. SQL Functions](#10-sql-functions)
  - [Q10. What are the different types of SQL functions?](#q10-what-are-the-different-types-of-sql-functions)
- [11. Window Functions](#11-window-functions)
  - [Q11. What are window functions, and how do ROW_NUMBER(), RANK(), DENSE_RANK(), LAG(), LEAD(), and aggregate window functions work?](#q11-what-are-window-functions-and-how-do-row_number-rank-dense_rank-lag-lead-and-aggregate-window-functions-work)
- [12. Common Table Expressions (CTEs)](#12-common-table-expressions-ctes)
  - [Q12. What is a CTE, how is it different from a subquery, and how do recursive CTEs work?](#q12-what-is-a-cte-how-is-it-different-from-a-subquery-and-how-do-recursive-ctes-work)
- [13. SQL Coding Problems](#13-sql-coding-problems)
  - [Q13. How do you find the second-highest salary, Nth-highest salary, duplicate records, and highest-paid employee in each department?](#q13-how-do-you-find-the-second-highest-salary-nth-highest-salary-duplicate-records-and-highest-paid-employee-in-each-department)
- [14. Data Modification](#14-data-modification)
  - [Q14. How do INSERT, UPDATE, DELETE, MERGE, and upsert work? What is the difference between DELETE, TRUNCATE, and DROP?](#q14-how-do-insert-update-delete-merge-and-upsert-work-what-is-the-difference-between-delete-truncate-and-drop)
- [15. SQL Constraints and Keys](#15-sql-constraints-and-keys)
  - [Q15. What are primary keys, foreign keys, unique constraints, NOT NULL, CHECK, and DEFAULT?](#q15-what-are-primary-keys-foreign-keys-unique-constraints-not-null-check-and-default)
- [16. Views and Temporary Tables](#16-views-and-temporary-tables)
  - [Q16. What are views, materialized views, temporary tables, and derived tables?](#q16-what-are-views-materialized-views-temporary-tables-and-derived-tables)
- [17. Indexes and Query Performance](#17-indexes-and-query-performance)
  - [Q17. What are indexes, clustered and non-clustered indexes, composite indexes, and covering indexes?](#q17-what-are-indexes-clustered-and-non-clustered-indexes-composite-indexes-and-covering-indexes)
- [18. Transactions and Concurrency](#18-transactions-and-concurrency)
  - [Q18. How do COMMIT, ROLLBACK, and SAVEPOINT work, and how do isolation levels affect concurrent queries?](#q18-how-do-commit-rollback-and-savepoint-work-and-how-do-isolation-levels-affect-concurrent-queries)
- [19. Advanced SQL Query Optimization](#19-advanced-sql-query-optimization)
  - [Q19. How do you analyze an execution plan and optimize slow SQL queries?](#q19-how-do-you-analyze-an-execution-plan-and-optimize-slow-sql-queries)
- [20. Backend SQL Best Practices](#20-backend-sql-best-practices)
  - [Q20. How do parameterized queries, prepared statements, pagination, transactions, and batch operations work? How do you prevent SQL injection?](#q20-how-do-parameterized-queries-prepared-statements-pagination-transactions-and-batch-operations-work-how-do-you-prevent-sql-injection)
- [Quick revision: SQL commands and syntax](#quick-revision-sql-commands-and-syntax)
- [How to explain SQL answers to an interviewer](#how-to-explain-sql-answers-to-an-interviewer)

---

# 1. SQL Fundamentals

## Q1. What is SQL, and what are the different types of SQL commands?

### Interview answer

SQL stands for Structured Query Language. It is used to communicate with relational databases to retrieve, insert, update, and delete data. SQL commands are commonly classified into DDL, DML, DQL, DCL, and TCL based on their purpose.

### Important terminologies

**DDL — Data Definition Language**

* DDL defines or modifies database structures such as tables, schemas, and indexes.

* It is used to create, change, or remove database objects.

* Common commands are `CREATE`, `ALTER`, `DROP`, and `TRUNCATE`.

```sql
-- Create a new table
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2)
);

-- Add a new column to the table
ALTER TABLE employees
ADD email VARCHAR(150);
```

**DML — Data Manipulation Language**

* DML is used to insert, update, and delete records in a table.

* Backend applications use these commands when users create or modify information.

* Common commands are `INSERT`, `UPDATE`, and `DELETE`.

```sql
-- Insert a new employee
INSERT INTO employees (employee_id, name, salary)
VALUES (1, 'Ravi', 50000);

-- Update an employee's salary
UPDATE employees
SET salary = 55000
WHERE employee_id = 1;

-- Delete the employee with ID 1
DELETE FROM employees
WHERE employee_id = 1;
```

**DQL — Data Query Language**

* DQL retrieves data from database tables.

* The primary command is `SELECT`.

* It supports filtering, sorting, grouping, and joining data.

```sql
-- Retrieve employees earning more than 40,000
SELECT name, salary
FROM employees
WHERE salary > 40000;
```

**DCL — Data Control Language**

* DCL manages permissions for accessing database objects.

* It determines which users can read or modify particular data.

* Common commands are `GRANT` and `REVOKE`.

```sql
-- Allow app_user to read the employees table
GRANT SELECT ON employees TO app_user;

-- Remove that permission
REVOKE SELECT ON employees FROM app_user;
```

**TCL — Transaction Control Language**

* TCL manages transactions, which are groups of database operations.

* `COMMIT` saves a transaction's changes, while `ROLLBACK` undoes uncommitted changes.

* `SAVEPOINT` creates a point within a transaction to which you can roll back.

```sql
BEGIN; -- Start a transaction

UPDATE employees
SET salary = 60000
WHERE employee_id = 1;

COMMIT; -- Save the transaction
```

[⬆ Back to top](#-table-of-contents)

---

# 2. SELECT Queries

## Q2. How do you retrieve, filter, sort, and limit data using SELECT, WHERE, ORDER BY, DISTINCT, and LIMIT?

### Interview answer

`SELECT` retrieves data from a table, and `WHERE` filters rows based on conditions. `ORDER BY` sorts the results, `DISTINCT` removes duplicate result rows, and `LIMIT` restricts the number of rows returned. Together, these clauses let us retrieve exactly the data an application needs.

### Important terminologies

**SELECT**

* `SELECT` specifies which columns or expressions should appear in the result.

* We can select individual columns or use `*` to select all columns.

* Selecting only the required columns reduces unnecessary data transfer.

**WHERE**

* `WHERE` filters individual rows according to a condition.

* Rows for which the condition is not TRUE are excluded.

* It is commonly used with comparison and logical operators.

**ORDER BY**

* `ORDER BY` sorts the result using one or more columns or expressions.

* `ASC` means ascending order, and `DESC` means descending order.

* If consistent ordering matters, include a unique tie-breaker column.

**DISTINCT**

* `DISTINCT` removes duplicate rows from the selected result.

* When selecting multiple columns, it considers the combination of those columns.

* Duplicate elimination may require extra processing.

**LIMIT**

* `LIMIT` restricts the number of rows returned.

* It is useful for retrieving a small result set or implementing pagination.

* PostgreSQL and MySQL support `LIMIT`; SQL Server commonly uses `TOP` or `OFFSET ... FETCH`.

### SQL syntax with comments

```sql
SELECT DISTINCT department_id -- Return unique department IDs
FROM employees
WHERE salary > 40000           -- Filter employees by salary
ORDER BY department_id ASC     -- Sort IDs in ascending order
LIMIT 10;                       -- Return at most 10 rows
```

How to explain this query: It retrieves up to 10 unique department IDs from employees earning more than 40,000, sorted in ascending order.

[⬆ Back to top](#-table-of-contents)

---

# 3. SQL Operators

## Q3. What are the different SQL operators?

### Interview answer

SQL operators are used to compare values, combine conditions, perform calculations, and filter records. Comparison and logical operators are commonly used in `WHERE` clauses. Operators such as `IN`, `BETWEEN`, `LIKE`, and `EXISTS` make filtering more expressive.

### Important terminologies

**Comparison operators**

* Comparison operators compare two values.

* Common operators include `=`, `<>`, `!=`, `>`, `<`, `>=`, and `<=`.

* They are frequently used in `WHERE` and `HAVING` clauses.

**Logical operators**

* `AND` requires both conditions to be TRUE; `OR` requires at least one.

* `NOT` reverses a condition's truth value.

* SQL also has UNKNOWN results when NULL affects a condition.

**Arithmetic operators**

* Arithmetic operators perform calculations on numeric values.

* Common operators are `+`, `-`, `*`, and `/`.

* Example: `salary * 12` calculates annual salary for monthly-paid employees.

**IN**

* `IN` checks whether a value matches any value in a list or subquery.

* It is a convenient alternative to several equality checks joined with `OR`.

* Example: `department_id IN (10, 20, 30)`.

**BETWEEN**

* `BETWEEN` checks whether a value falls within a specified range.

* Both the lower and upper boundaries are included.

* Example: `salary BETWEEN 30000 AND 60000`.

**LIKE**

* `LIKE` matches text against a pattern.

* `%` matches zero or more characters; `_` matches exactly one character.

* Example: `name LIKE 'A%'` matches names beginning with A.

**EXISTS**

* `EXISTS` checks whether a subquery returns at least one row.

* It is commonly used to check whether related records exist.

* It is often useful for queries involving parent-child relationships.

### SQL syntax with comments

```sql
SELECT name, salary
FROM employees
WHERE salary >= 30000             -- Comparison operator
  AND department_id IN (10, 20)   -- Match either department
  AND name LIKE 'A%'              -- Name begins with A
  AND salary BETWEEN 30000 AND 80000
ORDER BY salary DESC;
```

EXISTS example:

```sql
-- Find employees who have at least one order
SELECT e.employee_id, e.name
FROM employees e
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.employee_id = e.employee_id
);
```

[⬆ Back to top](#-table-of-contents)

---

# 4. SQL Joins

## Q4. What are the different types of SQL joins?

### Interview answer

A JOIN combines rows from two tables using a related column or condition. `INNER JOIN` returns matching rows, while outer joins also preserve unmatched rows from one or both tables. `CROSS JOIN` produces combinations of rows, and `SELF JOIN` joins a table to itself.

### Important terminologies

**INNER JOIN**

* Returns rows that satisfy the join condition in both tables.

* Rows without a match are excluded.

* Use it when only matching records are required.

**LEFT JOIN**

* Returns every row from the left table and matching rows from the right.

* If no match exists, right-side columns contain NULL.

* It is useful for finding records that may not have related data.

**RIGHT JOIN**

* Returns every row from the right table and matching rows from the left.

* Unmatched left-side columns contain NULL.

* It can often be rewritten as a LEFT JOIN by reversing table order.

**FULL OUTER JOIN**

* Returns matched rows and unmatched rows from both tables.

* Missing values on either side are represented by NULL.

* It is useful for comparing datasets and identifying unmatched records.

**CROSS JOIN**

* Returns every possible combination of rows from two tables.

* Three rows joined with four rows produce twelve combinations.

* It is useful for generating combinations but can produce large results.

**SELF JOIN**

* Joins a table with itself using aliases.

* It is useful for relationships between rows in the same table.

* A common example is connecting employees to their managers.

### SQL syntax with comments

```sql
-- Return employees with matching department records
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d
    ON e.department_id = d.department_id;
```

```sql
-- Return all employees, even those without a department
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d
    ON e.department_id = d.department_id;
```

```sql
-- Find employees who have no matching department
SELECT e.name
FROM employees e
LEFT JOIN departments d
    ON e.department_id = d.department_id
WHERE d.department_id IS NULL;
```

```sql
-- SELF JOIN: display each employee and their manager
SELECT e.name AS employee,
       m.name AS manager
FROM employees e
LEFT JOIN employees m
    ON e.manager_id = m.employee_id;
```

[⬆ Back to top](#-table-of-contents)

---

# 5. Aggregate Functions

## Q5. What are aggregate functions, and how do GROUP BY and HAVING work?

### Interview answer

Aggregate functions calculate summary values from multiple rows, such as counts, totals, and averages. `GROUP BY` calculates these values separately for each group, while `HAVING` filters groups after aggregation. They are commonly used in reporting and analytics.

### Important terminologies

**COUNT()**

* `COUNT(*)` counts rows, including rows containing NULL values.

* `COUNT(column)` counts only rows where that column is not NULL.

* `COUNT(DISTINCT column)` counts distinct non-NULL values.

**SUM()**

* `SUM()` calculates the total of numeric values.

* It ignores NULL values in the aggregated column.

* It is commonly used to calculate total sales or expenses.

**AVG()**

* `AVG()` calculates the average of non-NULL numeric values.

* NULL values are excluded from the calculation.

* It is useful for calculating average salary, price, or order value.

**MIN() and MAX()**

* `MIN()` returns the smallest value; `MAX()` returns the largest.

* They work with numeric, date, and other comparable values.

* They can identify the earliest date or highest salary.

**GROUP BY**

* `GROUP BY` combines rows with matching values into groups.

* Aggregate functions calculate a result for each group.

* Non-aggregated selected columns generally need to be included in the grouping.

**HAVING**

* `HAVING` filters groups after aggregation.

* It is commonly used with aggregate expressions such as `COUNT(*)`.

* Unlike `WHERE`, it can filter based on an aggregate result.

### SQL syntax with comments

```sql
SELECT
    department_id,
    COUNT(*) AS employee_count, -- Count employees
    SUM(salary) AS total_salary, -- Total salary
    AVG(salary) AS avg_salary,   -- Average salary
    MIN(salary) AS min_salary,   -- Lowest salary
    MAX(salary) AS max_salary    -- Highest salary
FROM employees
GROUP BY department_id           -- One result per department
HAVING COUNT(*) >= 3             -- Keep groups with 3+ employees
ORDER BY avg_salary DESC;
```

[⬆ Back to top](#-table-of-contents)

---

# 6. NULL Handling

## Q6. What is NULL, and how do IS NULL, COALESCE(), and NULLIF() work?

### Interview answer

`NULL` represents missing or unknown information; it is different from zero or an empty string. Comparisons such as `column = NULL` do not correctly test for missing values, so SQL provides `IS NULL`. `COALESCE()` supplies a fallback value, while `NULLIF()` returns NULL when two expressions are equal.

### Important terminologies

**NULL**

* NULL represents missing, unknown, or unavailable information.

* Comparisons involving NULL generally produce UNKNOWN.

* SQL uses three-valued logic: TRUE, FALSE, and UNKNOWN.

**IS NULL**

* `IS NULL` checks whether a value is missing.

* `IS NOT NULL` checks whether a value is present.

* Use these instead of `= NULL` or `<> NULL`.

**COALESCE()**

* Returns the first non-NULL value from its arguments.

* It is often used to display a default when data is missing.

* Example: `COALESCE(commission, 0)` returns zero for a NULL commission.

**NULLIF()**

* Returns NULL when its two arguments are equal.

* Otherwise, it returns the first argument.

* It can prevent division by zero when the denominator is zero.

### SQL syntax with comments

```sql
-- Find employees whose commission is missing
SELECT name
FROM employees
WHERE commission IS NULL;
```

```sql
-- Display zero when commission is NULL
SELECT name, COALESCE(commission, 0) AS commission
FROM employees;
```

```sql
-- Avoid division by zero
SELECT amount / NULLIF(quantity, 0) AS unit_price
FROM order_items;
```

[⬆ Back to top](#-table-of-contents)

---

# 7. Subqueries

## Q7. What is a subquery, and what are its different types?

### Interview answer

A subquery is a SQL query nested inside another SQL statement. It may return a single value, one row, or multiple rows, depending on its purpose. A correlated subquery references the outer query, whereas a non-correlated subquery can be evaluated independently.

### Important terminologies

**Scalar subquery**

* Returns exactly one value: one row and one column.

* It can be used in expressions or comparisons.

* If it returns multiple rows, many SQL systems raise an error.

**Single-row subquery**

* Returns at most one row, potentially containing multiple columns.

* It can be used when comparing against a single record.

* The query must ensure that no more than one row is returned.

**Multi-row subquery**

* Returns multiple rows.

* It is commonly used with `IN`, `ANY`, or `ALL`.

* Example: finding employees belonging to a set of departments.

**Correlated subquery**

* References a column from the outer query.

* Its result depends on the current outer row.

* It is useful for comparisons within a related group.

**Non-correlated subquery**

* Does not reference columns from the outer query.

* It can be evaluated independently of the outer row.

* The optimizer decides how to execute it; it is not guaranteed to run only once.

### SQL syntax with comments

```sql
-- Find employees earning more than the company average
SELECT name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary) -- Scalar subquery
    FROM employees
);
```

```sql
-- Correlated subquery: compare salary with department average
SELECT e.name, e.salary, e.department_id
FROM employees e
WHERE e.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e.department_id
);
```

```sql
-- Multi-row subquery: employees in departments with high salaries
SELECT name
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM employees
    WHERE salary > 100000
);
```

[⬆ Back to top](#-table-of-contents)

---

# 8. Set Operations

## Q8. What is the difference between UNION, UNION ALL, INTERSECT, and EXCEPT?

### Interview answer

Set operations combine or compare the results of multiple SELECT queries. `UNION` combines results and removes duplicates, while `UNION ALL` preserves duplicates. `INTERSECT` returns rows common to both results, and `EXCEPT` returns rows from the first result that are absent from the second.

### Important terminologies

**UNION**

* Combines rows from multiple SELECT queries.

* Removes duplicate result rows.

* Each query must return the same number of columns with compatible data types.

**UNION ALL**

* Combines results without removing duplicates.

* Preserves repeated rows.

* It is generally more efficient when duplicate elimination is unnecessary.

**INTERSECT**

* Returns rows that appear in both query results.

* Standard set-operation behavior removes duplicates.

* Availability and syntax can vary by database system.

**EXCEPT / MINUS**

* `EXCEPT` returns rows from the first result that are absent from the second.

* Oracle commonly uses `MINUS` for this operation.

* It is useful for comparing datasets and identifying missing records.

### SQL syntax with comments

```sql
-- Combine employee names from two departments; remove duplicates
SELECT name FROM employees WHERE department_id = 10
UNION
SELECT name FROM employees WHERE department_id = 20;
```

```sql
-- Combine results while preserving duplicates
SELECT name FROM employees WHERE department_id = 10
UNION ALL
SELECT name FROM employees WHERE department_id = 20;
```

```sql
-- Return names appearing in both result sets
SELECT name FROM employees WHERE department_id = 10
INTERSECT
SELECT name FROM employees WHERE salary > 50000;
```

```sql
-- Return names in the first result but not the second
SELECT name FROM employees WHERE department_id = 10
EXCEPT
SELECT name FROM employees WHERE salary > 50000;
```

[⬆ Back to top](#-table-of-contents)

---

# 9. Conditional Expressions

## Q9. How do you use CASE expressions in SQL?

### Interview answer

The `CASE` expression provides conditional logic inside SQL queries. It checks conditions in order and returns the result associated with the first matching condition. It is useful for categorizing values, creating labels, and calculating conditional results.

### Important terminologies

**CASE expression**

* Evaluates one or more conditions.

* Returns the result associated with the first condition that is TRUE.

* `ELSE` provides a fallback when no condition matches.

**Simple CASE**

* Compares one expression against several specified values.

* It is useful for mapping codes to descriptions.

* Example: converting status codes into readable status names.

**Searched CASE**

* Evaluates separate Boolean conditions.

* It supports ranges, comparisons, and compound conditions.

* It is useful for classifying salaries or calculating conditional values.

### SQL syntax with comments

```sql
SELECT name, salary,
       CASE
           WHEN salary >= 80000 THEN 'High'   -- First condition
           WHEN salary >= 40000 THEN 'Medium' -- Second condition
           ELSE 'Low'                         -- Default result
       END AS salary_level
FROM employees;
```

```sql
-- Simple CASE: map status codes to descriptions
SELECT order_id,
       CASE status
           WHEN 1 THEN 'Pending'
           WHEN 2 THEN 'Shipped'
           WHEN 3 THEN 'Delivered'
           ELSE 'Unknown'
       END AS status_name
FROM orders;
```

[⬆ Back to top](#-table-of-contents)

---

# 10. SQL Functions

## Q10. What are the different types of SQL functions?

### Interview answer

SQL functions perform operations on values and return a result. Common categories include string, numeric, date/time, conversion, and NULL-handling functions. They help transform data, perform calculations, format values, and handle missing information.

### Important terminologies

**String functions**

* String functions manipulate text.

* Examples include `UPPER()`, `LOWER()`, `LENGTH()` or `LEN()`, and `SUBSTRING()`.

* They are useful for formatting and searching text.

**Numeric functions**

* Numeric functions perform calculations on numbers.

* Examples include `ROUND()`, `ABS()`, `CEIL()` or `CEILING()`, and `FLOOR()`.

* They are useful for calculations and numeric formatting.

**Date/time functions**

* Date/time functions work with dates, times, and timestamps.

* Examples include `CURRENT_DATE` and `CURRENT_TIMESTAMP`.

* Date arithmetic and formatting syntax vary across database systems.

**Conversion functions**

* Conversion functions change a value from one data type to another.

* `CAST()` is widely supported; `CONVERT()` is also available in some systems.

* They help when values need to be represented in a different type.

**NULL-handling functions**

* NULL-handling functions help deal with missing values.

* `COALESCE()` returns the first non-NULL argument.

* `IFNULL()` and `ISNULL()` are database-specific alternatives with differing syntax.

### SQL syntax with comments

```sql
SELECT
    UPPER(name) AS uppercase_name,       -- Convert text to uppercase
    ROUND(salary, 0) AS rounded_salary,   -- Round salary
    CURRENT_DATE AS today,               -- Current date
    CAST(salary AS VARCHAR(20)) AS salary_text
FROM employees;
```

```sql
-- Use a fallback when commission is missing
SELECT name,
       COALESCE(commission, 0) AS commission
FROM employees;
```

[⬆ Back to top](#-table-of-contents)

---

# 11. Window Functions

## Q11. What are window functions, and how do ROW_NUMBER(), RANK(), DENSE_RANK(), LAG(), LEAD(), and aggregate window functions work?

### Interview answer

Window functions perform calculations across related rows without collapsing them into a single row per group. The `OVER()` clause defines the window, and `PARTITION BY` divides it into groups. They are useful for ranking records, comparing rows, and calculating running totals.

### Important terminologies

**OVER()**

* Defines the rows considered by a window function.

* It can contain `PARTITION BY`, `ORDER BY`, and a frame specification.

* Unlike `GROUP BY`, it preserves the individual rows.

**PARTITION BY**

* Divides rows into groups for the window calculation.

* The function operates independently within each partition.

* Example: ranking employees separately within each department.

**ROW_NUMBER()**

* Assigns a unique sequential number to each row.

* The order is determined by the window's `ORDER BY`.

* Tied values receive different row numbers.

**RANK()**

* Assigns the same rank to rows tied on the ordering values.

* It leaves gaps after ties.

* Example: ranks can be 1, 1, 3.

**DENSE_RANK()**

* Assigns the same rank to tied rows.

* It does not leave gaps after ties.

* Example: ranks can be 1, 1, 2.

**LAG()**

* Retrieves a value from a preceding row in the window.

* It is useful for comparing a current row with a previous row.

* Example: comparing this month's sales with last month's sales.

**LEAD()**

* Retrieves a value from a following row in the window.

* It is useful for comparing a current row with a future row.

* Example: comparing an order with the next order.

**Aggregate window functions**

* Functions such as `SUM()` and `AVG()` can operate over a window.

* They calculate values while preserving individual rows.

* They can produce running totals, moving averages, or group-level values.

### SQL syntax with comments

```sql
SELECT
    name,
    department_id,
    salary,

    ROW_NUMBER() OVER (
        PARTITION BY department_id
        ORDER BY salary DESC, employee_id
    ) AS row_num, -- Unique sequence within department

    RANK() OVER (
        PARTITION BY department_id
        ORDER BY salary DESC
    ) AS salary_rank, -- Ties share rank; gaps follow

    DENSE_RANK() OVER (
        PARTITION BY department_id
        ORDER BY salary DESC
    ) AS dense_salary_rank, -- Ties share rank; no gaps

    LAG(salary) OVER (
        PARTITION BY department_id
        ORDER BY salary
    ) AS previous_salary, -- Previous row's salary

    LEAD(salary) OVER (
        PARTITION BY department_id
        ORDER BY salary
    ) AS next_salary, -- Next row's salary

    SUM(salary) OVER (
        PARTITION BY department_id
        ORDER BY salary, employee_id
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS running_total -- Running total within department

FROM employees;
```

[⬆ Back to top](#-table-of-contents)

---

# 12. Common Table Expressions (CTEs)

## Q12. What is a CTE, how is it different from a subquery, and how do recursive CTEs work?

### Interview answer

A Common Table Expression, or CTE, is a named query result defined using the `WITH` clause. It improves readability by breaking complex SQL into logical steps. A recursive CTE can refer to its own results, making it useful for hierarchical data such as employee-manager relationships.

### Important terminologies

**CTE**

* A CTE is a named result set available to a single SQL statement.

* It is defined using the `WITH` keyword.

* It helps organize complex queries into readable sections.

**CTE vs. subquery**

* A CTE gives a query result a name that can be referenced in the statement.

* A subquery is nested directly inside another SQL expression or statement.

* Performance depends on the optimizer; a CTE is not automatically faster.

**Recursive CTE**

* A recursive CTE refers to itself while building its result.

* It usually contains an anchor query and a recursive query.

* It is useful for hierarchies, category trees, and parent-child relationships.

**Anchor query**

* The anchor query provides the initial rows for the recursive CTE.

* It does not reference the CTE itself.

* These rows form the starting point for recursion.

**Recursive query**

* The recursive query references the CTE's previous results.

* It generates additional rows from the existing result.

* Recursion stops when no further rows are produced, subject to database limits.

### SQL syntax with comments

```sql
-- Basic CTE: calculate average salary by department
WITH department_salary AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT *
FROM department_salary
WHERE avg_salary > 50000;
```

```sql
-- Recursive CTE: find employees reporting under a manager
WITH RECURSIVE employee_hierarchy AS (
    -- Anchor: begin with the selected manager
    SELECT employee_id, name, manager_id, 1 AS level
    FROM employees
    WHERE employee_id = 1

    UNION ALL

    -- Recursive part: find their direct reports
    SELECT e.employee_id, e.name, e.manager_id, h.level + 1
    FROM employees e
    JOIN employee_hierarchy h
        ON e.manager_id = h.employee_id
)
SELECT *
FROM employee_hierarchy;
```

Note: Recursive CTE syntax differs in some databases. SQL Server uses `WITH` without the `RECURSIVE` keyword.

[⬆ Back to top](#-table-of-contents)

---

# 13. SQL Coding Problems

## Q13. How do you find the second-highest salary, Nth-highest salary, duplicate records, and highest-paid employee in each department?

### Interview answer

These are common SQL interview problems that test ranking, grouping, and filtering. Window functions such as `DENSE_RANK()` can find the Nth distinct salary and the highest-paid employees in each department. `GROUP BY` with `HAVING` is commonly used to identify duplicate values.

### Important terminology

**Nth-highest salary**

* The Nth-highest salary usually means the Nth distinct salary value.

* `DENSE_RANK()` assigns ranks without gaps when salaries are tied.

* This differs from selecting the Nth row after sorting.

**Duplicate records**

* Duplicate records are rows sharing the same values in specified columns.

* `GROUP BY` combines rows with the same selected values.

* `HAVING COUNT(*) > 1` identifies groups occurring more than once.

**Highest-paid employee per department**

* This means finding the maximum salary within each department.

* `RANK()` or `DENSE_RANK()` can preserve all employees tied for the highest salary.

* `ROW_NUMBER()` instead selects one row when a deterministic tie-breaker is provided.

### A. Find the second-highest distinct salary

```sql
WITH ranked_salaries AS (
    SELECT salary,
           DENSE_RANK() OVER (
               ORDER BY salary DESC
           ) AS salary_rank
    FROM employees
)
SELECT DISTINCT salary
FROM ranked_salaries
WHERE salary_rank = 2;
```

Explanation: `DENSE_RANK()` assigns rank 1 to the highest salary and rank 2 to the second distinct salary. `DISTINCT` avoids returning the same salary more than once.

### B. Find the Nth-highest distinct salary

```sql
-- Replace 3 with the required rank N
WITH ranked_salaries AS (
    SELECT salary,
           DENSE_RANK() OVER (
               ORDER BY salary DESC
           ) AS salary_rank
    FROM employees
)
SELECT DISTINCT salary
FROM ranked_salaries
WHERE salary_rank = 3;
```

Explanation: This query finds the third-highest distinct salary. Replace `3` with the required value of N.

### C. Find duplicate email addresses

```sql
SELECT email, COUNT(*) AS occurrences
FROM employees
GROUP BY email
HAVING COUNT(*) > 1; -- Keep emails appearing more than once
```

Explanation: The query groups employees by email and returns emails that appear multiple times. If NULL emails should not be considered duplicates, add `WHERE email IS NOT NULL`.

### D. Find the highest-paid employee in each department

```sql
WITH ranked_employees AS (
    SELECT employee_id, name, department_id, salary,
           DENSE_RANK() OVER (
               PARTITION BY department_id
               ORDER BY salary DESC
           ) AS salary_rank
    FROM employees
)
SELECT employee_id, name, department_id, salary
FROM ranked_employees
WHERE salary_rank = 1; -- Return all top-salary ties
```

Explanation: `PARTITION BY` ranks employees separately in each department. `DENSE_RANK() = 1` returns every employee tied for the highest salary.

[⬆ Back to top](#-table-of-contents)

---

# 14. Data Modification

## Q14. How do INSERT, UPDATE, DELETE, MERGE, and upsert work? What is the difference between DELETE, TRUNCATE, and DROP?

### Interview answer

`INSERT` adds rows, `UPDATE` modifies existing rows, and `DELETE` removes selected rows. `MERGE` can perform conditional inserts, updates, or deletes, while an upsert inserts a record or updates it when a conflict occurs. `TRUNCATE` removes all table rows, whereas `DROP` removes the table object itself.

### Important terminologies

**INSERT**

* Adds new records to a table.

* You can provide values for selected columns.

* It can also insert rows returned by a SELECT query.

**UPDATE**

* Modifies existing records.

* `WHERE` specifies which rows should change.

* Without a `WHERE` clause, every row may be updated.

**DELETE**

* Removes selected rows from a table.

* It supports a `WHERE` clause to choose which rows to remove.

* Without `WHERE`, it deletes all rows, subject to constraints and database behavior.

**MERGE**

* Matches source rows against target rows using a condition.

* It can perform actions such as UPDATE or INSERT based on the match.

* Exact syntax and supported actions vary by database.

**Upsert**

* Upsert means insert a row if it does not exist, or update it if it does.

* It is useful for safely handling repeated writes to the same logical record.

* The syntax differs between databases.

**DELETE vs. TRUNCATE vs. DROP**

* `DELETE` removes rows and can target specific records with `WHERE`.

* `TRUNCATE` removes all rows without a row-by-row filtering condition.

* `DROP` removes the table definition and its data; transaction and rollback behavior varies by database.

### SQL syntax with comments

```sql
-- INSERT: add a record
INSERT INTO employees (employee_id, name, salary)
VALUES (10, 'Anu', 60000);

-- UPDATE: modify a selected record
UPDATE employees
SET salary = 65000
WHERE employee_id = 10;

-- DELETE: remove a selected record
DELETE FROM employees
WHERE employee_id = 10;
```

Upsert in PostgreSQL:

```sql
INSERT INTO employees (employee_id, name, salary)
VALUES (10, 'Anu', 65000)
ON CONFLICT (employee_id)
DO UPDATE SET
    name = EXCLUDED.name,
    salary = EXCLUDED.salary;
-- If employee_id exists, update that record
```

TRUNCATE and DROP:

```sql
TRUNCATE TABLE employees; -- Remove all rows; keep table

DROP TABLE employees; -- Remove the table itself
```

Important: `TRUNCATE` and `DROP` can have different transaction, identity-reset, trigger, and foreign-key behavior depending on the database. Do not assume they behave identically everywhere.

[⬆ Back to top](#-table-of-contents)

---

# 15. SQL Constraints and Keys

## Q15. What are primary keys, foreign keys, unique constraints, NOT NULL, CHECK, and DEFAULT?

### Interview answer

Constraints enforce rules that protect data integrity. A primary key uniquely identifies each row, while a foreign key maintains relationships between tables. Other constraints, such as `UNIQUE`, `NOT NULL`, `CHECK`, and `DEFAULT`, prevent invalid data and provide sensible default values.

### Important terminologies

**Primary key**

* A primary key uniquely identifies each row in a table.

* It cannot contain NULL values.

* A table has one primary-key constraint, which may contain multiple columns.

**Foreign key**

* A foreign key references a primary or unique key in another table or the same table.

* It helps prevent references to nonexistent parent records.

* Referential actions can define what happens when referenced rows are updated or deleted.

**UNIQUE**

* A UNIQUE constraint prevents duplicate key values.

* It can apply to one column or a combination of columns.

* NULL handling under UNIQUE constraints varies between database systems.

**NOT NULL**

* `NOT NULL` prevents a column from storing NULL.

* It is useful for mandatory fields.

* It does not prevent empty strings or zero values.

**CHECK**

* A CHECK constraint enforces a condition on inserted or updated values.

* It can validate rules such as non-negative salary.

* NULL handling depends on SQL's condition logic, so use `NOT NULL` too when necessary.

**DEFAULT**

* A DEFAULT supplies a value when an INSERT omits that column.

* It can provide values such as the current timestamp or a default status.

* An explicitly supplied NULL is not generally replaced by the default.

### SQL syntax with comments

```sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY, -- Unique department identifier
    department_name VARCHAR(100) UNIQUE NOT NULL
);

CREATE TABLE employees (
    employee_id INT PRIMARY KEY, -- Unique employee identifier
    name VARCHAR(100) NOT NULL,  -- Name is required
    email VARCHAR(150) UNIQUE,   -- Email must be unique
    salary DECIMAL(10, 2) CHECK (salary >= 0), -- Non-negative salary
    department_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
        -- Department must exist in the parent table
);
```

[⬆ Back to top](#-table-of-contents)

---

# 16. Views and Temporary Tables

## Q16. What are views, materialized views, temporary tables, and derived tables?

### Interview answer

A view is a saved SQL query that presents data like a virtual table. A materialized view stores the query result, while a temporary table stores temporary data for a session or transaction, depending on the database. A derived table is a subquery used in the `FROM` clause.

### Important terminologies

**View**

* A view is a named query that can be selected from like a table.

* A regular view generally stores the query definition, not a separate copy of the results.

* It can simplify complex queries and restrict which columns users can access.

**Materialized view**

* A materialized view stores the results of a query.

* It can speed up expensive reporting queries.

* Its data may become stale and generally needs refreshing.

**Temporary table**

* A temporary table stores intermediate data for a limited lifetime.

* Depending on the database, it may last for a session or transaction.

* It is useful for multi-step processing and complex data transformations.

**Derived table**

* A derived table is a subquery placed in the `FROM` clause.

* It acts as a table for the outer query.

* It is useful for organizing calculations or filtering intermediate results.

### SQL syntax with comments

```sql
-- Create a view for employees earning more than 50,000
CREATE VIEW high_salary_employees AS
SELECT employee_id, name, salary
FROM employees
WHERE salary > 50000;

-- Query the view like a table
SELECT *
FROM high_salary_employees;
```

```sql
-- PostgreSQL: create a materialized view
CREATE MATERIALIZED VIEW department_totals AS
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id;

-- Refresh the stored result
REFRESH MATERIALIZED VIEW department_totals;
```

```sql
-- Create a temporary table
CREATE TEMPORARY TABLE high_salary_temp AS
SELECT employee_id, name, salary
FROM employees
WHERE salary > 50000;
```

```sql
-- Derived table: query an intermediate result
SELECT department_id, avg_salary
FROM (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
) AS department_averages
WHERE avg_salary > 50000;
```

[⬆ Back to top](#-table-of-contents)

---

# 17. Indexes and Query Performance

## Q17. What are indexes, clustered and non-clustered indexes, composite indexes, and covering indexes?

### Interview answer

An index is a data structure that helps the database locate rows without scanning the entire table. Indexes can improve filtering, joining, and sorting, but they require storage and add overhead to inserts, updates, and deletes. The right index depends on the query patterns and execution plan.

### Important terminologies

**Index**

* An index stores search keys and references to table rows.

* It can speed up queries that filter or join on indexed columns.

* Too many indexes increase storage and write costs.

**Clustered index**

* In database systems that support this concept, a clustered index organizes table data according to its index key.

* A table generally has only one such physical organization.

* Exact implementation and terminology differ by database.

**Non-clustered index**

* A non-clustered index stores keys separately from the table's main row organization.

* It contains information that helps locate the corresponding rows.

* A table can have multiple non-clustered indexes, subject to database limits.

**Composite index**

* A composite index contains more than one column.

* Column order matters because it affects which query conditions can efficiently use the index.

* For a B-tree index on `(department_id, salary)`, queries filtering by the leading column are especially relevant.

**Covering index**

* A covering index contains all the columns needed by a particular query.

* The database may answer the query from the index without fetching the table row.

* Whether this is possible depends on the database and the chosen execution plan.

### SQL syntax with comments

```sql
-- Create an index to help queries filtering by department
CREATE INDEX idx_employees_department
ON employees (department_id);
```

```sql
-- Composite index: department first, salary second
CREATE INDEX idx_employees_dept_salary
ON employees (department_id, salary);
```

```sql
-- PostgreSQL example: include columns to help cover a query
CREATE INDEX idx_employees_dept_cover
ON employees (department_id)
INCLUDE (name, salary);
```

Note: PostgreSQL supports `INCLUDE`; MySQL and other databases have different covering-index approaches. A covering index is a property of an index-query combination, not a universal index type.

[⬆ Back to top](#-table-of-contents)

---

# 18. Transactions and Concurrency

## Q18. How do COMMIT, ROLLBACK, and SAVEPOINT work, and how do isolation levels affect concurrent queries?

### Interview answer

A transaction groups multiple SQL operations into one logical unit of work. `COMMIT` saves its changes, `ROLLBACK` undoes uncommitted changes, and `SAVEPOINT` allows partial rollback. Isolation levels control how concurrent transactions see each other's changes and help balance consistency with concurrency.

### Important terminologies

**Transaction**

* A transaction is a group of operations treated as one logical unit.

* It helps ensure that related changes succeed or fail together.

* Transactions are important for operations such as transferring money between accounts.

**COMMIT**

* `COMMIT` makes a transaction's changes permanent according to the database's transaction guarantees.

* Other transactions can then observe the committed changes according to their isolation level.

* Once committed, ordinary rollback cannot undo that transaction.

**ROLLBACK**

* `ROLLBACK` undoes changes made by the current uncommitted transaction.

* It is useful when an operation fails partway through.

* The exact behavior depends on transaction boundaries and database features.

**SAVEPOINT**

* A savepoint marks a position inside a transaction.

* `ROLLBACK TO SAVEPOINT` undoes changes made after that point.

* It allows partial recovery without necessarily cancelling the whole transaction.

**Isolation levels**

* Isolation levels define how transactions interact when running concurrently.

* Common levels are Read Uncommitted, Read Committed, Repeatable Read, and Serializable.

* The exact guarantees and implementation differ between database systems.

**Dirty read**

* A dirty read occurs when a transaction reads another transaction's uncommitted changes.

* If those changes are rolled back, the first transaction has read data that never committed.

* Read Committed and stronger standard isolation levels prevent dirty reads.

**Non-repeatable read**

* A transaction reads a row, then reads it again and gets a different committed value.

* This can happen if another transaction updates that row between reads.

* Stronger isolation or appropriate locking can prevent this behavior.

**Phantom read**

* Repeating a query for a range can return additional or fewer matching rows.

* This can happen when another transaction inserts or deletes matching records.

* Serializable isolation aims to prevent outcomes that violate serial execution.

### SQL syntax with comments

```sql
BEGIN; -- Start a transaction

UPDATE accounts
SET balance = balance - 100
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE account_id = 2;

COMMIT; -- Save both changes together
```

```sql
BEGIN;

UPDATE employees
SET salary = salary + 1000
WHERE employee_id = 1;

SAVEPOINT salary_updated; -- Mark a recovery point

UPDATE employees
SET salary = salary + 5000
WHERE employee_id = 2;

ROLLBACK TO SAVEPOINT salary_updated;
-- Undo changes after the savepoint

COMMIT; -- Commit changes that remain
```

### Isolation levels at a glance

| Isolation level | General behavior |
| --- | --- |
| Read Uncommitted | May allow dirty reads; actual behavior varies |
| Read Committed | Prevents dirty reads |
| Repeatable Read | Prevents non-repeatable reads; phantom handling varies |
| Serializable | Strongest standard isolation; aims for serial-equivalent results |

Interview tip: PostgreSQL treats Read Uncommitted as Read Committed. PostgreSQL's Repeatable Read also prevents phantom reads under its implementation, while other database systems may differ.

[⬆ Back to top](#-table-of-contents)

---

# 19. Advanced SQL Query Optimization

## Q19. How do you analyze an execution plan and optimize slow SQL queries?

### Interview answer

I first identify the slow query and inspect its execution plan using tools such as `EXPLAIN`. I check for full table scans, expensive joins, sorting, row estimates, and index usage. Then I optimize filters, joins, indexes, and query structure, and measure the execution time again to confirm the improvement.

### Important terminologies

**Execution plan**

* An execution plan describes how the database intends to execute a query.

* It shows operations such as scans, joins, sorts, and aggregations.

* It helps identify where the database expects to spend resources.

**EXPLAIN**

* `EXPLAIN` displays the planned execution strategy.

* It can reveal whether an index or table scan is expected.

* In PostgreSQL, `EXPLAIN ANALYZE` executes the query and reports actual runtime statistics.

**Full table scan**

* A full table scan reads the table's rows to evaluate a query.

* It may be appropriate for small tables or queries returning many rows.

* For selective queries on large tables, an index may be more efficient.

**Index scan**

* An index scan uses an index to locate relevant rows.

* It can reduce the number of rows the database must examine.

* It is not always faster than a sequential scan, especially when many rows match.

**Query selectivity**

* Selectivity describes how narrowly a condition filters the data.

* A highly selective condition matches a small portion of the table.

* Indexes are often especially useful for selective conditions.

**Join optimization**

* Join optimization determines how tables should be combined.

* The optimizer chooses join methods and execution order based on estimates and available options.

* Indexes, statistics, and appropriate join conditions can affect the plan.

**Query rewriting**

* Query rewriting changes a query's structure while preserving its intended result.

* It can remove unnecessary columns, repeated calculations, or redundant subqueries.

* Always check that the rewritten query returns equivalent results.

### SQL syntax with comments

```sql
-- PostgreSQL: inspect the query plan
EXPLAIN
SELECT employee_id, name
FROM employees
WHERE department_id = 10;
```

```sql
-- PostgreSQL: execute the query and inspect actual performance
EXPLAIN ANALYZE
SELECT employee_id, name
FROM employees
WHERE department_id = 10;
```

```sql
-- Add an index for a frequently used filter
CREATE INDEX idx_employees_department
ON employees (department_id);
```

```sql
-- Avoid SELECT * when only two columns are required
SELECT employee_id, name
FROM employees
WHERE department_id = 10;
```

### Practical optimization checklist

1. Inspect the execution plan and actual runtime where possible.

2. Select only the columns the application needs.

3. Add appropriate indexes for frequently used filters and joins.

4. Check join conditions and avoid accidental many-to-many row multiplication.

5. Avoid applying functions to indexed columns in filters when that prevents efficient index use.

6. Keep database statistics current.

7. Measure the query again after every significant change.

[⬆ Back to top](#-table-of-contents)

---

# 20. Backend SQL Best Practices

## Q20. How do parameterized queries, prepared statements, pagination, transactions, and batch operations work? How do you prevent SQL injection?

### Interview answer

In backend development, I use parameterized queries to separate SQL code from user input and prevent SQL injection. Prepared statements can reuse a query structure, while pagination limits the number of records returned. I use transactions for related changes and batch operations to reduce repeated database calls.

### Important terminologies

**Parameterized queries**

* Parameterized queries use placeholders for values supplied by the application.

* The database treats those values as data rather than executable SQL syntax.

* They are a primary defense against SQL injection.

**Prepared statements**

* A prepared statement separates the SQL statement from its parameter values.

* Depending on the driver and database, it may allow reuse of the statement structure.

* Prepared statements are commonly used through backend database libraries.

**SQL injection**

* SQL injection occurs when untrusted input changes the intended SQL statement.

* It can expose data or allow unauthorized database operations.

* Parameterized queries prevent user-provided values from being interpreted as SQL syntax.

**Pagination**

* Pagination retrieves a subset of a larger result set.

* `LIMIT` and `OFFSET` are common for page-based pagination.

* Keyset pagination uses a last-seen key and is often more efficient for deep pages.

**Transactions**

* Transactions group related operations into a logical unit.

* They help ensure that related changes succeed or fail together.

* They are essential for operations such as placing an order and reducing inventory.

**Batch operations**

* Batch operations send multiple records or operations together.

* They can reduce network round trips between the application and database.

* Batch size should be chosen carefully to avoid excessive memory use or long transactions.

### A. Parameterized queries — prevent SQL injection

Unsafe example:

```sql
-- UNSAFE: user input is concatenated into SQL
-- A malicious input could alter the query's meaning
SELECT *
FROM users
WHERE email = 'USER_INPUT';
```

Safe SQL syntax:

```sql
-- Use a placeholder instead of concatenating user input
SELECT *
FROM users
WHERE email = $1; -- PostgreSQL parameter placeholder
```

The application passes the email separately as a parameter. The placeholder syntax depends on the driver: PostgreSQL commonly uses `$1`, while other drivers may use `?` or named parameters.

Example using Python with a PostgreSQL driver:

```python
# Safe: the value is passed separately from the SQL
cursor.execute(
    "SELECT * FROM users WHERE email = %s",
    (email,)
)
```

Important: Parameters are for values, not table names or column names. If a query must choose a column dynamically, use a strict allowlist of permitted identifiers.

### B. Prepared statements

```sql
-- PostgreSQL: prepare a parameterized statement
PREPARE employee_by_id (INT) AS
SELECT employee_id, name, salary
FROM employees
WHERE employee_id = $1;

-- Execute the prepared statement with a value
EXECUTE employee_by_id(10);
```

A backend driver may handle preparation automatically. The exact lifecycle and performance benefits depend on the database and driver.

### C. Pagination using LIMIT and OFFSET

```sql
-- Page 1: return the first 10 employees
SELECT employee_id, name
FROM employees
ORDER BY employee_id
LIMIT 10 OFFSET 0;

-- Page 2: return the next 10 employees
SELECT employee_id, name
FROM employees
ORDER BY employee_id
LIMIT 10 OFFSET 10;
```

Keyset pagination:

```sql
-- Fetch the next 10 employees after the last seen ID
SELECT employee_id, name
FROM employees
WHERE employee_id > 100
ORDER BY employee_id
LIMIT 10;
```

Keyset pagination is useful for large datasets because the database does not need to skip a large number of earlier rows. The ordering key should be stable and unique, or use a unique tie-breaker.

### D. Transactions in backend applications

```sql
BEGIN; -- Start the transaction

-- Create the order
INSERT INTO orders (order_id, customer_id, total)
VALUES (1001, 10, 500);

-- Reduce available inventory
UPDATE products
SET stock = stock - 1
WHERE product_id = 25
  AND stock > 0;

-- Application should verify that the expected row was updated.
-- If the order or inventory operation fails, roll back.
COMMIT;
```

In real backend code, check whether the inventory update affected a row. If it did not, roll back the transaction so an order is not committed without available stock. Handle errors and rollback in the application's transaction API.

### E. Batch inserts

```sql
-- Insert multiple employees in one statement
INSERT INTO employees (employee_id, name, salary)
VALUES
    (101, 'Asha', 45000),
    (102, 'Kiran', 50000),
    (103, 'Meena', 55000);
```

Batching multiple rows can reduce the number of database round trips. For very large batches, split the data into manageable chunks and use transactions according to the application's consistency requirements.

[⬆ Back to top](#-table-of-contents)

---

# Quick revision: SQL commands and syntax

Use this table for a final review before your interview.

| Requirement | SQL syntax |
| --- | --- |
| Retrieve data | `SELECT ... FROM ...` |
| Filter rows | `WHERE condition` |
| Sort rows | `ORDER BY column ASC/DESC` |
| Remove duplicates | `SELECT DISTINCT` |
| Limit results | `LIMIT n` |
| Join tables | `JOIN ... ON ...` |
| Group records | `GROUP BY column` |
| Filter groups | `HAVING condition` |
| Insert data | `INSERT INTO ... VALUES ...` |
| Update data | `UPDATE ... SET ... WHERE ...` |
| Delete rows | `DELETE FROM ... WHERE ...` |
| Create a table | `CREATE TABLE ...` |
| Create an index | `CREATE INDEX ... ON ...` |
| Start a transaction | `BEGIN` |
| Save changes | `COMMIT` |
| Undo uncommitted changes | `ROLLBACK` |
| Define a CTE | `WITH name AS (...)` |
| Rank rows | `DENSE_RANK() OVER (...)` |
| Handle missing values | `COALESCE(value, fallback)` |
| Check for missing values | `column IS NULL` |

[⬆ Back to top](#-table-of-contents)

---

## How to explain SQL answers to an interviewer

For each question, follow this simple structure:

1. Define the concept: Start with one clear sentence explaining what it is.

2. Explain its purpose: Say why it is used in real applications.

3. Mention the important difference: For example, `WHERE` vs. `HAVING`, or `UNION` vs. `UNION ALL`.

4. Give a small SQL example: Explain what the query returns and why.

For coding questions, explain the approach before writing the query. For performance questions, mention that you would inspect the execution plan and measure the result rather than assuming an index or rewrite will always be faster.

Interview tip: You do not need to memorize every sentence word for word. Understand the definition, the key difference, and the example. That will help you answer follow-up questions naturally.

[⬆ Back to top](#-table-of-contents)
