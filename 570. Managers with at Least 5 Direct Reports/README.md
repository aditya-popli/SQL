# 570. Managers with at Least 5 Direct Reports

## Problem Description

You are given a table `Employee` that contains employee details including their `id`, `name`, `department`, and `managerId`.  
Your task is to find all **managers** who have **at least 5 direct reports**.

Return a list of manager names. The order of results does not matter.

---

## Table Schema

### Employee

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |

- `id` is the primary key.
- If `managerId` is `null`, the employee has no manager.
- No employee manages themselves.

---

## Example Input

**Employee**

| id  | name  | department | managerId |
|-----|-------|------------|-----------|
| 101 | John  | A          | null      |
| 102 | Dan   | A          | 101       |
| 103 | James | A          | 101       |
| 104 | Amy   | A          | 101       |
| 105 | Anne  | A          | 101       |
| 106 | Ron   | B          | 101       |

---

## Expected Output

| name |
|------|
| John |

---

## SQL Solution

```sql
SELECT e.name
FROM Employee e
JOIN (
    SELECT managerId
    FROM Employee
    WHERE managerId IS NOT NULL
    GROUP BY managerId
    HAVING COUNT(*) >= 5
) m ON e.id = m.managerId;
```
---
