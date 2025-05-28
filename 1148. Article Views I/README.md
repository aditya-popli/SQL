# 📰 1148. Article Views I

**Difficulty:** Easy  
**Topic:** SQL  
**Companies:** Amazon, Bloomberg  

---

## 🧾 Problem Description

You are given a table `Views` that logs when a viewer views an article written by an author.

### Table: `Views`

| Column Name | Type | Description                        |
|-------------|------|------------------------------------|
| article_id  | int  | ID of the article                  |
| author_id   | int  | ID of the article's author         |
| viewer_id   | int  | ID of the viewer                   |
| view_date   | date | The date the article was viewed    |

- No column is a primary key, meaning duplicates are possible.
- If `author_id == viewer_id`, it means the **author viewed their own article**.

---

## ✅ Objective

Write a SQL query to find all **distinct authors** who **viewed at least one of their own articles**.

- Return the result as a table with a single column: `id`.
- Sort the output by `id` in ascending order.

---

## 🧪 Example

### Input:

**Views Table:**

| article_id | author_id | viewer_id | view_date  |
|------------|-----------|-----------|------------|
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |

### Output:

| id |
|----|
| 4  |
| 7  |

---

## 🧠 SQL Query

```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id;
```
---

