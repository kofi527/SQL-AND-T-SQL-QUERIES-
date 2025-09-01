### SQL-AND-T-SQL-QUERIES###-
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
RESULTS
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


   
