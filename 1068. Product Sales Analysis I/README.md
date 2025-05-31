# 🛒 1068. Product Sales Analysis I

**Difficulty:** Easy  
**Topic:** SQL  

---

## 🧾 Problem Description

We are given two tables:

### `Sales`

| Column Name | Type | Description                             |
|-------------|------|-----------------------------------------|
| sale_id     | int  | Sale identifier (along with `year`)     |
| product_id  | int  | References `product_id` in `Product`    |
| year        | int  | Year of the sale                        |
| quantity    | int  | Quantity sold                           |
| price       | int  | Price per unit                          |

**Primary Key:** (sale_id, year)

---

### `Product`

| Column Name  | Type    | Description              |
|--------------|---------|--------------------------|
| product_id   | int     | Unique product identifier|
| product_name | varchar | Name of the product      |

---

## ✅ Objective

Return a table with:

- `product_name` – from `Product`
- `year` – from `Sales`
- `price` – from `Sales`

---

## 🧪 Example

### Input:

**Sales Table:**

| sale_id | product_id | year | quantity | price |
|---------|-------------|------|----------|--------|
| 1       | 100         | 2008 | 10       | 5000   |
| 2       | 100         | 2009 | 12       | 5000   |
| 7       | 200         | 2011 | 15       | 9000   |

**Product Table:**

| product_id | product_name |
|------------|--------------|
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |

### Output:

| product_name | year | price |
|--------------|------|--------|
| Nokia        | 2008 | 5000   |
| Nokia        | 2009 | 5000   |
| Apple        | 2011 | 9000   |

---

## 🧠 SQL Query

```sql
SELECT p.product_name, s.year, s.price
FROM Sales s
JOIN Product p ON s.product_id = p.product_id;
