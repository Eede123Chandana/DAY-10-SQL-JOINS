# 🔗 SQL JOINS | Connecting Relational Data

## 🎯 Overview

SQL JOINS combine related data from multiple tables using common columns.

They are essential for relational database analysis, customer reporting, sales analysis, inventory management, and business intelligence.

**Objective:** Understand seven important JOIN types, their differences, SQL syntax, and practical applications.

---

## 1️⃣ What is a JOIN?

A JOIN combines rows from two or more tables using related columns.

### Why JOINS Matter

- Connect related datasets.
- Analyze relationships between tables.
- Retrieve information from multiple sources.
- Build meaningful reports and dashboards.
- Support business decision-making.

---

## 2️⃣ Sample Dataset

### Table A: customers

| customer_id | customer_name |
|---|---|
| 101 | Amit |
| 102 | Ravi |
| 103 | Neha |

### Table B: orders

| customer_id | amount |
|---|---:|
| 101 | 5000 |
| 103 | 3000 |
| 104 | 7000 |

**Matching Customer IDs:** 101 and 103.

**Unmatched Customer:** 102.

**Unmatched Order Customer ID:** 104.

---

## 3️⃣ INNER JOIN

Returns only records matching in both tables.

```sql
SELECT
    c.customer_id,
    c.customer_name,
    o.amount
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

### Output

| customer_id | customer_name | amount |
|---|---|---:|
| 101 | Amit | 5000 |
| 103 | Neha | 3000 |

**Business Use Case:** Identify customers who have placed orders.

---

## 4️⃣ LEFT JOIN

Returns all rows from the left table and matching rows from the right table.

```sql
SELECT
    c.customer_id,
    c.customer_name,
    o.amount
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

### Output

| customer_id | customer_name | amount |
|---|---|---:|
| 101 | Amit | 5000 |
| 102 | Ravi | NULL |
| 103 | Neha | 3000 |

**Business Use Case:** Identify customers with and without orders.

---

## 5️⃣ RIGHT JOIN

Returns all rows from the right table and matching rows from the left table.

```sql
SELECT
    o.customer_id,
    c.customer_name,
    o.amount
FROM customers c
RIGHT JOIN orders o
ON c.customer_id = o.customer_id;
```

### Output

| customer_id | customer_name | amount |
|---|---|---:|
| 101 | Amit | 5000 |
| 103 | Neha | 3000 |
| 104 | NULL | 7000 |

**Business Use Case:** Find orders without corresponding customer records.

---

## 6️⃣ FULL OUTER JOIN

Returns all rows from both tables, whether matched or unmatched.

```sql
SELECT
    COALESCE(c.customer_id, o.customer_id)
        AS customer_id,
    c.customer_name,
    o.amount
FROM customers c
FULL OUTER JOIN orders o
ON c.customer_id = o.customer_id;
```

### Output

| customer_id | customer_name | amount |
|---|---|---:|
| 101 | Amit | 5000 |
| 102 | Ravi | NULL |
| 103 | Neha | 3000 |
| 104 | NULL | 7000 |

**Business Use Case:** Compare complete customer and order datasets.

**MySQL Note:** MySQL does not directly support FULL OUTER JOIN. It can be simulated using LEFT JOIN, RIGHT JOIN, and UNION.

---

## 7️⃣ CROSS JOIN

Returns every possible combination of rows from both tables.

```sql
SELECT
    c.customer_name,
    o.amount
FROM customers c
CROSS JOIN orders o;
```

### Result

3 customers × 3 orders = **9 combinations**

**Business Use Case:** Generate product-store combinations or testing scenarios.

**Important:** CROSS JOIN can create very large result sets.

---

## 8️⃣ LEFT ANTI JOIN

Returns records from the left table without matching records in the right table.

```sql
SELECT
    c.customer_id,
    c.customer_name
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.customer_id IS NULL;
```

### Output

| customer_id | customer_name |
|---|---|
| 102 | Ravi |

**Business Use Case:** Find customers who have never placed an order.

---

## 9️⃣ RIGHT ANTI JOIN

Returns records from the right table without matching records in the left table.

```sql
SELECT
    o.customer_id,
    o.amount
FROM customers c
RIGHT JOIN orders o
ON c.customer_id = o.customer_id
WHERE c.customer_id IS NULL;
```

### Output

| customer_id | amount |
|---|---:|
| 104 | 7000 |

**Business Use Case:** Identify orders without corresponding customer records.

**Note:** Anti joins are commonly expressed using outer joins with IS NULL or NOT EXISTS.

---

## 🔟 Quick JOIN Comparison

| JOIN Type | What It Returns |
|---|---|
| INNER JOIN | Matching records from both tables |
| LEFT JOIN | All left rows and matching right rows |
| RIGHT JOIN | All right rows and matching left rows |
| FULL OUTER JOIN | All rows from both tables |
| CROSS JOIN | Every possible row combination |
| LEFT ANTI JOIN | Left rows without right matches |
| RIGHT ANTI JOIN | Right rows without left matches |

---

## 1️⃣1️⃣ Real-World Applications

### 🛒 Customer Analytics

Combine customer records with purchase histories.

### 📦 Product Analytics

Connect product information with sales transactions.

### 🏬 Retail Reporting

Match stores with revenue and performance metrics.

### 🚚 Inventory Management

Connect inventory records with supplier information.

### 📊 Business Intelligence

Build dashboards using related data from multiple tables.

---

## 1️⃣2️⃣ Important SQL Interview Questions

**Q1. INNER JOIN vs LEFT JOIN?**

INNER JOIN returns matching rows only; LEFT JOIN preserves all left-table rows.

**Q2. LEFT JOIN vs RIGHT JOIN?**

LEFT JOIN preserves left-table rows; RIGHT JOIN preserves right-table rows.

**Q3. What is FULL OUTER JOIN?**

It returns matched and unmatched rows from both tables.

**Q4. What is CROSS JOIN?**

It returns every possible combination of rows between two tables.

**Q5. What is an Anti Join?**

An anti join identifies records without a match in another table.

**Q6. Can JOIN produce duplicate rows?**

Yes. One-to-many and many-to-many relationships can produce multiple matching rows.

**Q7. What happens when JOIN keys do not match?**

INNER JOIN excludes unmatched rows, while outer joins preserve unmatched rows from the relevant table.

---

## 🎯 Key Takeaways

✅ JOINS connect related tables.

✅ INNER JOIN returns matching rows.

✅ LEFT and RIGHT JOIN preserve rows from one side.

✅ FULL OUTER JOIN preserves both sides.

✅ CROSS JOIN creates all possible combinations.

✅ Anti joins identify missing matches.

✅ Understanding relationships is essential for accurate JOIN results.

---

## 💡 Final Thoughts

**SQL JOINS are foundational to relational data analysis.**

They allow analysts to connect datasets, explore relationships, identify missing information, and transform separate records into meaningful business insights.

### 🏷️ Topics

`SQL` `SQL JOINS` `INNER JOIN` `LEFT JOIN` `RIGHT JOIN` `FULL OUTER JOIN` `CROSS JOIN` `ANTI JOIN` `MySQL` `Data Analytics` `Business Analytics`
