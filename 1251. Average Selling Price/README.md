---

## 1251. Average Selling Price

### Problem

Write a solution to find the **average selling price for each product**.

- The average price should be **rounded to 2 decimal places**.
- If a product has **no sold units**, its average price is **0**.

---

### Schema

**Prices**

| Column Name | Type |
|-------------|------|
| product_id  | int  |
| start_date  | date |
| end_date    | date |
| price       | int  |

- `(product_id, start_date, end_date)` is the primary key.
- No overlapping date ranges for the same `product_id`.

**UnitsSold**

| Column Name   | Type |
|---------------|------|
| product_id    | int  |
| purchase_date | date |
| units         | int  |

---

### Example

**Input**

**Prices**

| product_id | start_date | end_date   | price |
|------------|------------|------------|-------|
| 1          | 2019-02-17 | 2019-02-28 | 5     |
| 1          | 2019-03-01 | 2019-03-22 | 20    |
| 2          | 2019-02-01 | 2019-02-20 | 15    |
| 2          | 2019-02-21 | 2019-03-31 | 30    |

**UnitsSold**

| product_id | purchase_date | units |
|------------|----------------|-------|
| 1          | 2019-02-25     | 100   |
| 1          | 2019-03-01     | 15    |
| 2          | 2019-02-10     | 200   |
| 2          | 2019-03-22     | 30    |

**Output**

| product_id | average_price |
|------------|----------------|
| 1          | 6.96           |
| 2          | 16.96          |

---

### SQL

```sql
SELECT 
    p.product_id,
    ROUND(SUM(u.units * p.price) / SUM(u.units), 2) AS average_price
FROM Prices p
JOIN UnitsSold u 
    ON p.product_id = u.product_id 
   AND u.purchase_date BETWEEN p.start_date AND p.end_date
GROUP BY p.product_id
```
