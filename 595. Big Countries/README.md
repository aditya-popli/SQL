# 🌍 595. Big Countries

**Difficulty:** Easy  
**Topic:** SQL  
**Companies:** Amazon, Bloomberg

---

## 🧾 Problem Description

You are given a table `World` with information about countries:

### Table: `World`

| Column Name | Type    | Description                              |
|-------------|---------|------------------------------------------|
| name        | varchar | The name of the country (Primary Key)    |
| continent   | varchar | The continent where the country is       |
| area        | int     | The area of the country (in km²)         |
| population  | int     | The population of the country            |
| gdp         | bigint  | The gross domestic product of the country|

A **country is big** if:

- Its `area` is at least **3,000,000 km²**, **OR**
- Its `population` is at least **25,000,000**

---

## 🧪 Example

### Input:  
**World Table**

| name        | continent | area    | population | gdp          |
|-------------|-----------|---------|------------|--------------|
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |

### Output:  

| name        | population | area    |
|-------------|------------|---------|
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |

---

## 🧠 SQL Query

```sql
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;

