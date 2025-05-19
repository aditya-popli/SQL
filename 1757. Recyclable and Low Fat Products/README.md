# 1757. Recyclable and Low Fat Products

**Difficulty:** Easy  
**Tags:** `SELECT`, `WHERE`, `Filtering`

---

## 🧾 Problem Description

You are given a table named `Products` with the following schema:

| Column Name | Type         |
|-------------|--------------|
| product_id  | int          |
| low_fats    | enum('Y','N') |
| recyclable  | enum('Y','N') |

- `product_id` is the **primary key** for this table.
- `low_fats` is an ENUM where `'Y'` means the product is low fat, and `'N'` means it is not.
- `recyclable` is an ENUM where `'Y'` means the product is recyclable, and `'N'` means it is not.

---

## 🎯 Objective

Write an SQL query to **find the IDs** of products that are **both low fat and recyclable**.

Return the result table in **any order**.

---

## 🧪 Example

### Input:

**Products table:**

| product_id | low_fats | recyclable |
|------------|----------|------------|
| 0          | Y        | N          |
| 1          | Y        | Y          |
| 2          | N        | Y          |
| 3          | Y        | Y          |
| 4          | N        | N          |

### Output:

| product_id |
|------------|
| 1          |
| 3          |

---

## ✅ Solution

```sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```
---
