# SQL Template - Problem Solving

## Basic Info
- Problem Number:
- Problem Title:
- Problem Description:

---

## Thinking Process

### Step 1: Identify the Problem Type
What kind of problem is this?

Choose one (or more):
- Simple Selection (SELECT)
- Filtering (WHERE)
- Joining Data (JOIN)
- Grouping / Aggregation (GROUP BY, HAVING)
- Sorting (ORDER BY)
- Ranking / Top N (ROW_NUMBER, RANK, DENSE_RANK)
- Row-to-Row Comparison (SELF JOIN / EXISTS)
- Subquery / Derived Logic
- Existence Check (EXISTS / NOT EXISTS)
- Missing Data (LEFT JOIN + NULL)

---

### Step 2: Identify the Entities (Tables)
- Main table:
- Related tables:
- Relationships (FKs):

---

### Step 3: Define the Output (Result Shape)
What should the result look like?

- Columns to display:
- Aliases:
- Expected number of rows (single / multiple):

This step prevents most mistakes.

---

### Step 4: Break Down the Problem
Split the question into smaller logical steps.

Example:
- Step A:
- Step B:
- Step C:

Think in plain English before SQL.

---

### Step 5: Choose the Right Tools
Which SQL features are needed?

- JOIN type (INNER, LEFT, etc.)
- GROUP BY
- Aggregate functions (MAX, AVG, etc.)
- Subquery
- Window functions
- EXISTS / NOT EXISTS

---

### Step 6: Incremental Query Building
Do not jump to the final query.

-- Step 1: basic query
-- Step 2: add join
-- Step 3: add filter
-- Step 4: refine logic


Build → Test → Extend

---

### Step 7: Validate the Logic
Before finalizing, check:

- Are there duplicates?
- Are NULL values handled?
- Does it return too many or too few rows?
- Are edge cases covered?

---

### Step 8: Final Query


---

## Optional (Senior Level)

### Step 9: Optimize (if needed)
- Add indexes
- Rewrite using EXISTS instead of IN
- Avoid unnecessary joins

---

### Step 10: Explain Your Solution
Be ready to explain:

- Why this approach?
- Why not another?
- Complexity and performance considerations

---

# Example

```sql
/* =====================================
SQL Problem Solving Template - FULL EXAMPLE
===================================== */

/* =========================
Basic Info
========================= */
-- Problem Number: 001
-- Problem Title: Employees with Salary Higher Than Department Average
-- Problem Description:
-- Display employee name, salary, and department name
-- for employees whose salary is higher than the average salary of their department.

/* =========================
Step 1: Identify Problem Type
========================= */
-- Comparison with result → Subquery
-- Per group → GROUP BY
-- Joining data → JOIN

/* =========================
Step 2: Identify Entities
========================= */
-- Main table: Employees
-- Related table: Departments
-- Relation: Employees.DepartmentID → Departments.Id

/* =========================
Step 3: Define Output
========================= */
-- Columns:
-- EmployeeName
-- Salary
-- DepartmentName

/* =========================
Step 4: Break Down Problem
========================= */
-- 1. Calculate average salary per department
-- 2. Compare each employee salary with department average
-- 3. Join departments to get department name

/* =========================
Step 5: Choose Tools
========================= */
-- JOIN → get department name
-- Subquery → calculate average per department

/* =========================
Step 6: Incremental Query Building
========================= */

-- Step 6.1: View employees
SELECT * FROM Employees;

-- Step 6.2: Get average salary per department
SELECT DepartmentID, AVG(Salary) AS AvgSalary
FROM Employees
GROUP BY DepartmentID;

-- Step 6.3: Join employees with departments
SELECT 
    e.FirstName,
    e.Salary,
    d.Name AS DepartmentName
FROM Employees e
INNER JOIN Departments d 
    ON e.DepartmentID = d.Id;

/* =========================
Step 7: Final Query
========================= */

SELECT 
    e.FirstName + ' ' + e.LastName AS EmployeeName,
    e.Salary,
    d.Name AS DepartmentName
FROM Employees e
INNER JOIN Departments d 
    ON e.DepartmentID = d.Id
WHERE e.Salary > (
    SELECT AVG(Salary)
    FROM Employees
    WHERE DepartmentID = e.DepartmentID
);

/* =========================
Step 8: Validation
========================= */
-- Works for multiple departments
-- Handles salary comparison correctly
-- Employees with NULL DepartmentID are excluded (expected)
-- No duplicate rows

/* =========================
Step 9: Optimization (Optional)
========================= */
-- Add index on Employees.DepartmentID
-- Consider window function alternative if needed

/* =========================
Final Clean Version (Production Style)
========================= */

SELECT 
    e.FirstName + ' ' + e.LastName AS EmployeeName,
    e.Salary,
    d.Name AS DepartmentName
FROM Employees e
INNER JOIN Departments d 
    ON e.DepartmentID = d.Id
WHERE e.Salary > (
    SELECT AVG(Salary)
    FROM Employees
    WHERE DepartmentID = e.DepartmentID
);