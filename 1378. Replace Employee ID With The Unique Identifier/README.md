# 👨‍💼 1378. Replace Employee ID With The Unique Identifier

**Difficulty:** Easy  
**Topic:** SQL   

---

## 🧾 Problem Description

You are given two tables:

### Table: `Employees`

| Column Name | Type    | Description                |
|-------------|---------|----------------------------|
| id          | int     | Employee's company ID      |
| name        | varchar | Employee's name            |

### Table: `EmployeeUNI`

| Column Name | Type    | Description                        |
|-------------|---------|------------------------------------|
| id          | int     | Employee's company ID              |
| unique_id   | int     | Employee's globally unique ID      |

---

## ✅ Objective

Return a table with:

- `unique_id`: From `EmployeeUNI` if it exists, else `null`
- `name`: From `Employees`

Return in any order.

---

## 🧪 Example

### Input:

**Employees Table:**

| id | name     |
|----|----------|
| 1  | Alice    |
| 7  | Bob      |
| 11 | Meir     |
| 90 | Winston  |
| 3  | Jonathan |

**EmployeeUNI Table:**

| id | unique_id |
|----|-----------|
| 3  | 1         |
| 11 | 2         |
| 90 | 3         |

### Output:

| unique_id | name     |
|-----------|----------|
| null      | Alice    |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |
| 1         | Jonathan |

---

## 🧠 SQL Query

```sql
SELECT euni.unique_id, e.name
FROM Employees e
LEFT JOIN EmployeeUNI euni
ON e.id = euni.id;
