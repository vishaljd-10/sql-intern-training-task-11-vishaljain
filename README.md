Task 11: Indexing and Query Performance Optimization
---
Objectives
- Identify slow-running queries on large datasets
- Measure query performance before indexing
- Create indexes on frequently searched columns
- Compare performance after indexing
- Use EXPLAIN to analyze execution plans
- Understand clustered vs non-clustered indexes
- Identify situations where indexes hurt performance
- Document best indexing practices
---
Database Table Used
CREATE TABLE sales (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_name VARCHAR(100),
    product VARCHAR(100),
    city VARCHAR(50),
    amount DECIMAL(10,2),
    sale_date DATE
);
---
Steps Performed

1. Identify Slow Query (Without Index)

SELECT * FROM sales WHERE city = 'Nagpur';

Observation:
- Full table scan (type = ALL)
- Slow performance

2. Create Index

CREATE INDEX idx_city ON sales(city);

3. Re-run Query

SELECT * FROM sales WHERE city = 'Nagpur';
---
Result:
- Faster execution
- EXPLAIN showed REF instead of ALL
---
Clustered vs Non-Clustered Index

Clustered Index:
- Primary key acts as clustered index in MySQL InnoDB.

Non-Clustered Index:
- Separate structure pointing to table data.
- Example: idx_city
---
When Indexes Can Hurt Performance
- INSERT operations
- UPDATE on indexed columns
- Very small tables
---
Best Indexing Practices
Do:
- Index columns used in WHERE, JOIN, ORDER BY, GROUP BY
---
Avoid:
- Too many indexes
- Low-cardinality columns
- Rarely used columns
---
Conclusion
Indexes improve read performance but must be used wisely to avoid write overhead.
---
