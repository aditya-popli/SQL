# Employee Bonus

## Problem Description

You are given two tables: `Employee` and `Bonus`.

- The `Employee` table contains employee details including `empId`, `name`, `supervisor` (manager's ID), and `salary`.
- The `Bonus` table contains bonus information for employees with columns `empId` and `bonus`.

Your task is to write a SQL query to report the `name` and `bonus` amount of each employee who has a bonus less than 1000. If an employee does not have a bonus entry, the bonus should be reported as `null`.

Return the result table in any order.

---

## Tables

### Employee

| Column Name | Type    |
|-------------|---------|
| empId       | int     |
| name        | varchar |
| supervisor  | int     |
| salary      | int     |

- `empId` is unique for each employee.
- `supervisor` is the `empId` of the employee's manager (can be null).

### Bonus

| Column Name | Type |
|-------------|------|
| empId       | int  |
| bonus       | int  |

- `empId` is unique and a foreign key referencing `Employee(empId)`.

---

## Example

### Input:

**Employee**

| empId | name   | supervisor | salary |
|-------|--------|------------|--------|
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |

**Bonus**

| empId | bonus |
|-------|-------|
| 2     | 500   |
| 4     | 2000  |

### Output:

| name  | bonus |
|-------|-------|
| Brad  | null  |
| John  | null  |
| Dan   | 500   |

---

## Solution

```sql
SELECT e.name, b.bonus
FROM Employee e
LEFT JOIN Bonus b ON e.empId = b.empId
WHERE b.bonus < 1000 OR b.bonus IS NULL;
```
---
