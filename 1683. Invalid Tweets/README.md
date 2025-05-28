# 🐦 1683. Invalid Tweets

**Difficulty:** Easy  
**Topic:** SQL  

---

## 🧾 Problem Description

Given a table `Tweets` that logs the tweet content on a social media app:

### Table: `Tweets`

| Column Name | Type    | Description                        |
|-------------|---------|------------------------------------|
| tweet_id    | int     | Primary key, ID of the tweet       |
| content     | varchar | The content of the tweet           |

- Tweets can contain alphanumeric characters, spaces `' '`, and exclamation marks `'!'`.
- A tweet is **invalid** if its content exceeds **15 characters**.

---

## ✅ Objective

Write a SQL query to return the IDs of tweets that are **invalid** (i.e., `LENGTH(content) > 15`).

Return the result in any order.

---

## 🧪 Example

### Input:

**Tweets Table:**

| tweet_id | content                           |
|----------|-----------------------------------|
| 1        | Let us Code                       |
| 2        | More than fifteen chars are here! |

### Output:

| tweet_id |
|----------|
| 2        |

### Explanation:

- Tweet 1: 11 characters → ✅ Valid  
- Tweet 2: 33 characters → ❌ Invalid

---

## 🧠 SQL Query

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```
