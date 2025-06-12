---

## 620. Not Boring Movies

### Problem

Write a solution to report the movies with an **odd-numbered ID** and a **description that is not "boring"**.

Return the result table ordered by **rating in descending order**.

---

### Schema

**Cinema**

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| movie       | varchar |
| description | varchar |
| rating      | float   |

- `id` is the primary key.
- `rating` is a 2-decimal float in [0, 10].

---

### Example

**Input**

| id | movie      | description | rating |
|----|------------|-------------|--------|
| 1  | War        | great 3D    | 8.9    |
| 2  | Science    | fiction     | 8.5    |
| 3  | irish      | boring      | 6.2    |
| 4  | Ice song   | Fantacy     | 8.6    |
| 5  | House card | Interesting | 9.1    |

**Output**

| id | movie      | description | rating |
|----|------------|-------------|--------|
| 5  | House card | Interesting | 9.1    |
| 1  | War        | great 3D    | 8.9    |

---

### SQL

```sql
SELECT *
FROM Cinema
WHERE MOD(id, 2) = 1
  AND description != 'boring'
ORDER BY rating DESC;
```
