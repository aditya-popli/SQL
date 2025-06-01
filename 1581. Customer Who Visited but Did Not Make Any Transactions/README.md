# 🛍️ 1581. Customer Who Visited but Did Not Make Any Transactions

**Difficulty:** Easy  
**Topic:** SQL    

---

## 🧾 Problem Description

We are given two tables:

### `Visits`

| Column Name | Type | Description                        |
|-------------|------|------------------------------------|
| visit_id    | int  | Unique ID for a visit              |
| customer_id | int  | ID of the customer visiting        |

---

### `Transactions`

| Column Name    | Type | Description                            |
|----------------|------|----------------------------------------|
| transaction_id | int  | Unique transaction ID                  |
| visit_id       | int  | Foreign key referring to `Visits`      |
| amount         | int  | Transaction amount                     |

---

## ✅ Objective

Return a table with:

- `customer_id` — of customers who **visited the mall but made no transaction**
- `count_no_trans` — how many such **no-transaction** visits each customer made

---

## 🧪 Example

### Input:

**Visits:**

| visit_id | customer_id |
|----------|--------------|
| 1        | 23           |
| 2        | 9            |
| 4        | 30           |
| 5        | 54           |
| 6        | 96           |
| 7        | 54           |
| 8        | 54           |

**Transactions:**

| transaction_id | visit_id | amount |
|----------------|----------|--------|
| 2              | 5        | 310    |
| 3              | 5        | 300    |
| 9              | 5        | 200    |
| 12             | 1        | 910    |
| 13             | 2        | 970    |

### Output:

| customer_id | count_no_trans |
|-------------|----------------|
| 54          | 2              |
| 30          | 1              |
| 96          | 1              |

---

## 🧠 SQL Query

```sql
SELECT v.customer_id, COUNT(*) AS count_no_trans
FROM Visits v
LEFT JOIN Transactions t
ON v.visit_id = t.visit_id
WHERE t.transaction_id IS NULL
GROUP BY v.customer_id;
```
