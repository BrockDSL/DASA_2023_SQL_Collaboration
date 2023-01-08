# Workshop #1 solutions

### Can you write a query that returns all rows WHERE people have a networth above 1350 (ORDER BY ASC)?
```SQL
SELECT * FROM "first_table"	
WHERE "net_worth" > 1350 
ORDER BY "net_worth" ASC;
```

### What about a query that gives us only the name and ages of people named "John Smith"?
```SQL
SELECT name, age 
FROM "first_table" 
WHERE "name" = "John Smith";
```

### What is the total net worth of all the people with the last name Brown?
```SQL
SELECT SUM("net_worth") 
FROM "first_table" 
WHERE name LIKE "% Brown";
```

### What is the average age of people with the last name Johnson or Smith?
```SQL
SELECT AVG(age) 
FROM "first_table" 
WHERE name LIKE "% Johnson" or name LIKE "% Smith";
```

### What is the total net worth of Kevin Smith and Natalie Thompson?
```SQL
SELECT SUM(net_worth) 
FROM "first_table" 
WHERE name = "Kevin Smith" or name = "Natalie Thompson";
```

### How many people are there with Brown as either their first or last name?
```SQL
SELECT count(name) 
FROM "first_table" 
WHERE name like "% Brown" or name like "Brown %";
```

# Workshop #2 solutions

### How would you write a join that connects Customers to their orders? For the columns, return only the OrderID, OrderDate, ContactName. 
### Consult https://raw.githubusercontent.com/jpwhite3/northwind-SQLite3/master/images/Northwind_ERD.png for table structure or look below.

```SQL
SELECT "OrderID", "OrderDate", "ContactName" 
FROM Customers
JOIN Orders
on Customers.CustomerID = Orders.CustomerID;
```

### Write a query that returns Products and their Categories. Return ProductName, and CategoryName as the columns. 
```SQL
SELECT "ProductName", "CategoryName" 
FROM "Products"
JOIN "Categories"
ON "Products"."CategoryID" = "Categories"."CategoryID";
```

### Write a query that returns Territories and the Regions that they are in (Select columns TerritoryID, TerritoryDescription, RegionID, RegionDescription). Order by the RegionID.
```SQL 
SELECT "TerritoryID", "TerritoryDescription", "Territories"."RegionID", "RegionDescription" 
FROM "Territories" 
JOIN "Regions"
ON "Territories".RegionID = "Regions"."RegionID"
ORDER BY "Territories".RegionID asc;
```

### Write a query that shows which Territories each Employees resides in.
```SQL
SELECT "Employees.EmployeeID", "LastName", "FirstName", "TerritoryDescription"
FROM "Employees" 
JOIN "EmployeeTerritories"
JOIN "Territories"
ON "Employees"."EmployeeID" = "EmployeeTerritories"."EmployeeID" AND "EmployeeTerritories"."TerritoryID" = "Territories"."TerritoryID";
```

# Workshop #3 solutions
### Can you write a query that returns the number of Customers in each city?
```SQL
SELECT count("CustomerID"), "City"
FROM Customers
GROUP BY "City"
ORDER BY count("CustomerID") DESC
```

### What about a query that returns the number of Products under each Category? Hint: A join is required here. 
```SQL
SELECT "CategoryName","Description",count("ProductID")
FROM "Categories"
JOIN "Products"
ON "Categories"."CategoryID" = "Products"."CategoryID"
GROUP BY "Categories"."CategoryID"
ORDER BY COUNT("ProductID") ASC;
```

### Write a query using a set operator that returns all of the cities where an Employee and a Customer reside.
```SQL
SELECT "City" FROM "Employees" 
INTERSECT 
SELECT "City" FROM Customers
```

### Can you write a query that uses a sub query, to find out the Supplier contact name and phone number of any supplier that has a product out of stock? 
### Hint: You can write this query either using a JOIN or with IN. 

### Answer using JOIN
```SQL
SELECT ContactName, Phone FROM "Suppliers" 
JOIN (select SupplierID FROM "Products" WHERE "UnitsInStock" = 0) as t 
ON "Suppliers"."SupplierID" = t.SupplierID;
```

### Answer using IN
```SQL
SELECT ContactName, Phone FROM "Suppliers" 
WHERE SupplierID IN (select SupplierID FROM "Products" WHERE "UnitsInStock" = 0); 
```

### What Supplier provides Products in the broadest number of Categories?
```SQL
SELECT SupplierID, count(CategoryID) 
FROM 
  (SELECT distinct "Suppliers"."SupplierID", "Products"."CategoryID"
  FROM "Suppliers"
  JOIN "Products"
  ON "Suppliers"."SupplierID" = "Products"."SupplierID") as t 
GROUP BY SupplierID
ORDER BY count(CategoryID) DESC;
```

### Find the SupplierID that have more than three Products with a UnitPrice of $5. Also show the count of these Products as a column.
```SQL
SELECT Count(*), "SupplierID" 
FROM "Products"
WHERE "UnitPrice" > 5.00
GROUP BY "SupplierID"
HAVING COUNT(*) > 3;
```
### Now find the CompanyName, ContactName, and Phone of these Suppliers.
```SQL
SELECT "CompanyName", "ContactName", "Phone" 
FROM "Suppliers"
JOIN 
  (SELECT Count(*), "SupplierID" 
  FROM "Products"
  WHERE "UnitPrice" > 5.00
  GROUP BY "SupplierID"
  HAVING COUNT(*) > 3) as t
ON t."SupplierID" = "Suppliers"."SupplierID";
```