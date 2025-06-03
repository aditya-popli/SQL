# 🏭 LeetCode 1661: Average Time of Process per Machine

## 📘 Problem Statement

Given a table `Activity` with machine processes and their start and end timestamps, write a SQL query to find the average time **each machine** takes to complete a process.

### Table: `Activity`

| Column Name    | Type   |
|----------------|--------|
| machine_id     | int    |
| process_id     | int    |
| activity_type  | enum   (`'start'`, `'end'`) |
| timestamp      | float  |

- `(machine_id, process_id, activity_type)` is the primary key.
- Each `(machine_id, process_id)` has both a `'start'` and an `'end'`.
- `timestamp` is a float representing time in seconds.

---

## ✅ Goal

Return a table with each `machine_id` and its average `processing_time`, rounded to 3 decimal places.

---

## 🧠 SQL Solution

```sql
SELECT 
    machine_id,
    ROUND(AVG(end_time - start_time), 3) AS processing_time
FROM (
    SELECT 
        machine_id,
        process_id,
        MAX(CASE WHEN activity_type = 'start' THEN timestamp END) AS start_time,
        MAX(CASE WHEN activity_type = 'end' THEN timestamp END) AS end_time
    FROM Activity
    GROUP BY machine_id, process_id
) AS process_times
GROUP BY machine_id;
