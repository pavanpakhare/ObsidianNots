# DBMS Interview Topic List (Beginner to Advanced)

## 1. Database Basics

* What is DBMS?
* Advantages of DBMS
* Types of DBMS

  * Hierarchical DBMS
  * Network DBMS
  * Relational DBMS (RDBMS)
  * NoSQL Databases
* DBMS vs File System
* Database Architecture (1-tier, 2-tier, 3-tier)

---

## 2. Relational Database Concepts

* Table, Row, Column
* Schema
* Instance
* Domain
* Degree and Cardinality
* Tuple
* Relationship

---

## 3. Keys

* Primary Key
* Candidate Key
* Super Key
* Alternate Key
* Composite Key
* Foreign Key
* Unique Key

### Interview Questions

* Difference between Primary Key and Unique Key?
* Can a table have multiple Primary Keys?
* What is a Composite Key?

---

## 4. Constraints

* NOT NULL
* UNIQUE
* PRIMARY KEY
* FOREIGN KEY
* CHECK
* DEFAULT

### Example

```sql
CREATE TABLE Employee(
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) CHECK(salary > 0)
);
```

---

## 5. SQL Basics

### DDL (Data Definition Language)

* CREATE
* ALTER
* DROP
* TRUNCATE
* RENAME

### DML (Data Manipulation Language)

* INSERT
* UPDATE
* DELETE

### DQL (Data Query Language)

* SELECT

### DCL (Data Control Language)

* GRANT
* REVOKE

### TCL (Transaction Control Language)

* COMMIT
* ROLLBACK
* SAVEPOINT

---

## 6. SQL Queries

* SELECT
* WHERE
* ORDER BY
* GROUP BY
* HAVING
* DISTINCT
* LIMIT/TOP

### Important Interview Queries

* Find Second Highest Salary
* Find Nth Highest Salary
* Find Duplicate Records
* Delete Duplicate Records
* Count Employees Department Wise

---

## 7. Joins

### Types of Joins

* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL JOIN
* CROSS JOIN
* SELF JOIN

### Interview Questions

* Difference between INNER and OUTER JOIN?
* What is SELF JOIN?
* What is CROSS JOIN?

---

## 8. Subqueries

* Single Row Subquery
* Multiple Row Subquery
* Correlated Subquery

### Example

```sql
SELECT *
FROM Employee
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employee
);
```

---

## 9. Set Operations

* UNION
* UNION ALL
* INTERSECT
* MINUS/EXCEPT

---

## 10. Functions

### Aggregate Functions

* COUNT()
* SUM()
* AVG()
* MAX()
* MIN()

### String Functions

* UPPER()
* LOWER()
* LENGTH()
* SUBSTRING()

### Date Functions

* NOW()
* CURDATE()
* DATEDIFF()

---

## 11. Normalization

### Normal Forms

* 1NF
* 2NF
* 3NF
* BCNF
* 4NF
* 5NF

### Interview Questions

* What is Normalization?
* Why do we normalize tables?
* Difference between 3NF and BCNF?

---

## 12. Denormalization

* Advantages
* Disadvantages
* Use Cases

---

## 13. Transactions

### ACID Properties

* Atomicity
* Consistency
* Isolation
* Durability

### Interview Questions

* What is a Transaction?
* Explain ACID Properties.

---

## 14. Concurrency Control

* Lost Update Problem
* Dirty Read
* Non-repeatable Read
* Phantom Read

### Lock Types

* Shared Lock
* Exclusive Lock

---

## 15. Indexing

### Types

* Clustered Index
* Non-Clustered Index
* Composite Index
* Unique Index

### Interview Questions

* What is Indexing?
* Why Indexes Improve Performance?
* Drawbacks of Indexes?

---

## 16. Views

* Simple View
* Complex View

### Example

```sql
CREATE VIEW emp_view AS
SELECT id, name
FROM Employee;
```

---

## 17. Stored Procedures

### Example

```sql
CREATE PROCEDURE GetEmployees()
BEGIN
    SELECT * FROM Employee;
END;
```

---

## 18. Triggers

### Types

* BEFORE INSERT
* AFTER INSERT
* BEFORE UPDATE
* AFTER UPDATE

### Interview Question

* Difference between Trigger and Stored Procedure?

---

## 19. Cursors

* What is Cursor?
* Types of Cursor
* Advantages and Disadvantages

---

## 20. Database Design

* ER Diagram
* Entity
* Attribute
* Relationship
* Cardinality
* Participation Constraints

---

## 21. ER Model

* One-to-One
* One-to-Many
* Many-to-One
* Many-to-Many

---

## 22. Query Optimization

* Execution Plan
* Index Usage
* Query Cost
* Explain Command

---

## 23. Database Security

* Authentication
* Authorization
* Roles
* Privileges
* SQL Injection

---

## 24. Backup and Recovery

* Full Backup
* Incremental Backup
* Differential Backup
* Recovery Techniques

---

## 25. Advanced DBMS Topics

### Partitioning

* Horizontal Partitioning
* Vertical Partitioning

### Sharding

* Concept
* Benefits

### Replication

* Master-Slave
* Master-Master

### CAP Theorem

* Consistency
* Availability
* Partition Tolerance

---

# Most Asked DBMS Interview Questions

1. What is DBMS?
2. DBMS vs RDBMS?
3. What is Primary Key?
4. Difference between Primary Key and Foreign Key?
5. What are Joins?
6. Difference between DELETE, DROP, and TRUNCATE?
7. What is Normalization?
8. Explain ACID Properties.
9. What is an Index?
10. Clustered vs Non-Clustered Index?
11. What is a View?
12. What is a Trigger?
13. What is a Stored Procedure?
14. What is a Transaction?
15. What are SQL Joins?
16. Difference between WHERE and HAVING?
17. What is a Subquery?
18. What is a Cursor?
19. What is Deadlock?
20. Explain 1NF, 2NF, 3NF, and BCNF.

### For Cognizant, IBM, CGI, TCS, Infosys, Wipro, Accenture Freshers

Focus heavily on:

* SQL Queries
* Joins
* Keys
* Normalization
* ACID Properties
* Indexes
* Transactions
* ER Diagrams
* Stored Procedures & Triggers
* DBMS vs RDBMS


