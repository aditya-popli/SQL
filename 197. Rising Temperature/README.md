# 🌡️ 197. Rising Temperature

**Difficulty:** Easy  
**Topic:** SQL  

---

## 🧾 Problem Description

We are given a `Weather` table:

| Column Name   | Type  | Description                               |
|---------------|-------|-------------------------------------------|
| id            | int   | Unique ID for each record                 |
| recordDate    | date  | Date of the temperature record            |
| temperature   | int   | Temperature on the given recordDate       |

We are to find the IDs of **dates when the temperature was higher than the previous day (yesterday).**

---

## 🧪 Example

### Input:

| id | recordDate | temperature |
|----|------------|-------------|
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |

### Output:

| id |
|----|
| 2  |
| 4  |

**Explanation:**
- 2015-01-02 → temp rose from 10 to 25 → include id 2
- 2015-01-04 → temp rose from 20 to 30 → include id 4

---

## ✅ SQL Query

```sql
SELECT w1.id
FROM Weather w1
JOIN Weather w2
  ON DATEDIFF(w1.recordDate, w2.recordDate) = 1
WHERE w1.temperature > w2.temperature;
```

---

