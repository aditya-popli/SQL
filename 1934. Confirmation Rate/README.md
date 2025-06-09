# 1934. Confirmation Rate

## Problem Description

Given two tables:

- `Signups`: Contains the sign-up timestamps of users.
- `Confirmations`: Records confirmation attempts by users with an `action` of either `'confirmed'` or `'timeout'`.

The **confirmation rate** of a user is calculated as:


If a user has made **no confirmation requests**, their confirmation rate is **0.00**.

Return the **confirmation rate for every user**, rounded to two decimal places.

---

## Table Schemas

### Signups

| Column Name | Type     |
|-------------|----------|
| user_id     | int      |
| time_stamp  | datetime |

- `user_id` is unique.

### Confirmations

| Column Name | Type     |
|-------------|----------|
| user_id     | int      |
| time_stamp  | datetime |
| action      | enum     |

- `action` is either `'confirmed'` or `'timeout'`.
- `(user_id, time_stamp)` is the primary key.
- `user_id` is a foreign key referencing `Signups`.

---

## Example Input

### Signups

| user_id | time_stamp          |
|---------|---------------------|
| 3       | 2020-03-21 10:16:13 |
| 7       | 2020-01-04 13:57:59 |
| 2       | 2020-07-29 23:09:44 |
| 6       | 2020-12-09 10:39:37 |

### Confirmations

| user_id | time_stamp          | action    |
|---------|---------------------|-----------|
| 3       | 2021-01-06 03:30:46 | timeout   |
| 3       | 2021-07-14 14:00:00 | timeout   |
| 7       | 2021-06-12 11:57:29 | confirmed |
| 7       | 2021-06-13 12:58:28 | confirmed |
| 7       | 2021-06-14 13:59:27 | confirmed |
| 2       | 2021-01-22 00:00:00 | confirmed |
| 2       | 2021-02-28 23:59:59 | timeout   |

---

## Expected Output

| user_id | confirmation_rate |
|---------|-------------------|
| 6       | 0.00              |
| 3       | 0.00              |
| 7       | 1.00              |
| 2       | 0.50              |

---

## SQL Solution

```sql
SELECT 
    s.user_id,
    ROUND(
        IFNULL(SUM(c.action = 'confirmed') / COUNT(c.action), 0),
        2
    ) AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c 
    ON s.user_id = c.user_id
GROUP BY s.user_id;
```
