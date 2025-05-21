# 584. Find Customer Referee

**Difficulty:** Easy  
**Tags:** `SELECT`, `Filtering`, `NULL`

---

## 🧾 Problem Description

You are given a table named `Customer` with the following schema:

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |

- `id` is the **primary key** of this table.
- Each row represents a customer, including:
  - Their `id`
  - Their `name`
  - The `id` of the customer who referred them (nullable)

---

## 🎯 Objective

Write an SQL query to **find the names of customers who were NOT referred by the customer with `id = 2`**.

Return the result table in **any order**.

---

## 🧪 Example

**Input:**

Customer table:

| id | name | referee_id |
|----|------|------------|
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |

**Output:**

| name |
|------|
| Will |
| Jane |
| Bill |
| Zack |

---

## ✅ Solution

```sql
SELECT name
FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL;
```

---

