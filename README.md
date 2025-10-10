### SQL-AND-T-SQL-QUERIES###-

This page Gives indepth details of various sql queries and thier related results. These are related to different T-SQL concepts using CTE'S case, subqueries etc

![SQL](https://github.com/user-attachments/assets/8354e85b-ad2c-417c-b84e-c56c1ccc1f75)


1. **QUERY: SELECT BusinessEntityID,
    LastName,
    TerritoryName,
    CountryRegionName
FROM Sales.vSalesPerson
WHERE TerritoryName IS NOT NULL
ORDER BY CASE CountryRegionName
        WHEN 'United States' THEN TerritoryName
        ELSE CountryRegionName
        END;**

EXPLANATION : WHERE TerritoryName IS NOT NULL  - This ensures that only salespeople who are assigned to a territory are included.
Salespersons with no assigned territory are excluded.

ORDER BY 
    CASE CountryRegionName
        WHEN 'United States' THEN TerritoryName
        ELSE CountryRegionName
    END;   
    This custom ordering does two things:

For U.S. salespeople: Sort by their TerritoryName.

For all other countries: Sort alphabetically by CountryRegionName.

This makes it easier to group U.S. territories together while still keeping international entries logically ordered.

**RESULTS**

<img width="1242" height="589" alt="CASEVSTATEMENT" src="https://github.com/user-attachments/assets/5eca55b6-0e92-4cc0-bf32-c9ef815e5b0d" />

DECLARING AND USING VARIABLES

3.  QUERY
   **USE AdventureWorks2019;
GO
-- Declare two variables.
DECLARE @FirstNameVariable NVARCHAR(50),
    @PostalCodeVariable NVARCHAR(15);
-- Set their values.
SET @FirstNameVariable = N'Amy';
SET @PostalCodeVariable = N'BA5 3HX';
-- Use them in the WHERE clause of a SELECT statement.
SELECT LastName,
    FirstName,
    JobTitle,
    City,
    StateProvinceName,
    CountryRegionName
FROM HumanResources.vEmployee
WHERE FirstName = @FirstNameVariable
    OR PostalCode = @PostalCodeVariable;**

Results - 
<img width="731" height="147" alt="DECLARING AND USING VARIABLES" src="https://github.com/user-attachments/assets/58eff1ce-30f1-477f-a8b5-e0c3003e5aad" />

5. Use scalar or multi-valued subqueries

   A scalar subquery is an inner SELECT statement within an outer query, written to return a single value. Scalar subqueries might be used anywhere in an outer T-SQL statement where a single-valued expression is permitted—such as in a SELECT clause, a WHERE clause, a HAVING clause, or even a FROM clause. They can also be used in data modification statements, such as UPDATE or DELETE.

6.  Differentiate between SQL and T-SQL.
SQL is a standard query language for managing and manipulating relational databases. T-SQL is an extension of SQL, providing additional functionality like control-of-flow statements (IF, WHILE), local variables, stored procedures, functions, and triggers, specifically for Microsoft SQL Server.

7. Understanding the logic behind stored procedure
   CREATE PROCEDURE GetAllEmployees
AS
BEGIN
    SELECT * FROM Employees;
END;

GetAllEmployees is the procedure name.

It selects all rows from the Employees table.

9.  What are Stored Procedures and their benefits?
A stored procedure is a pre-compiled set of T-SQL statements stored in the database.
Benefits: Improved performance (pre-compiled), reduced network traffic, enhanced security (permissions can be granted only on the procedure), reusability, and easier maintenance.

10. What are VIEWs in T-SQL and when would you use them
    A VIEW is a virtual table based on the result-set of a SQL query. It does not store data itself but presents data from one or more underlying tables. Views are used for:
Security: Restricting user access to specific columns or rows.
Simplification: Presenting complex queries as a single, simpler virtual table.
Data Consistency: Ensuring consistent data presentation across applications.

11. What are INDEXes and why are they important?
    An INDEX is a database object that provides fast access to data in tables. It works like an index in a book, allowing the database engine to quickly locate specific rows without scanning the entire table. Indexes improve query performance for SELECT statements but can slow down INSERT, UPDATE, and DELETE operations.
