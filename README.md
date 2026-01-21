# Find Duplicate Records in SQL

This repository demonstrates how to identify **duplicate records** in a table using
SQL **window functions**.

## 🧠 Problem Statement
Find duplicate records in a table when a column (e.g., `CustID`) is *supposed* to be unique,
but duplicates may exist due to data quality issues.

## ✅ Solution (Using ROW_NUMBER)

```sql
SELECT *
FROM (
    SELECT *,
           ROW_NUMBER() OVER (PARTITION BY CustID) AS rn
    FROM Customers
) t
WHERE rn > 1;
