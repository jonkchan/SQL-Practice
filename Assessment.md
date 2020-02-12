# Self-Assessment 📚📝

### Get Started

Navigate to [W3 School's Database](https://www.w3schools.com/sql/trysqlserver.asp?filename=trysql_func_sqlserver_concat3) to get started.

If you need a SQL refresher, visit the [SQL Start Guide](./README.md).

### Topics:

1. [Basic Queries](#Basic-Queries)
2. [Calculated Fields](#Calculated-Fields)
3. [Grouping Data](#Grouping-Data)
4. [Join Queries](#Join-Queries)
5. [Union](#Union)
6. [Case Examples](#Case-Examples)
7. [Concepts Short Answer Questions](#Concepts-Short-Answer-Questions)

## Basic Queries

1. Query all OrderDetails where order quantity is greater than 10 but less than 30

   <details>
      <summary>Reveal Solution</summary>
      
      Solution #1
      ```sql
      SELECT * FROM OrderDetails
      WHERE Quantity > 10 AND Quantity < 30;
      ```

   Solution #2

   ```sql
   SELECT * FROM OrderDetails
   WHERE Quantity BETWEEN 21 AND 29;
   ```

   </details>

2) Query the names of all Suppliers that are located in either the USA, UK, or Canada

   <details>
      <summary>Reveal Solution</summary>

   ```sql
   SELECT * FROM Suppliers
   WHERE Country IN ("USA", "UK", "Canada")
   ```

   </details>

3) Query the FirstName of Employees who's FirstName starts with the letter A then sort by FirstName in descending order

   <details>
      <summary>Reveal Solution</summary>

   Solution #1

   ```sql
   SELECT * FROM Employees
   WHERE LEFT(FirstName, 1) = 'A'
   ORDER BY FirstName DESC
   ```

   Solution #2

   ```sql
   SELECT * FROM Employees
   WHERE SUBSTRING(FirstName, 1, 1) = 'A'
   ORDER BY FirstName DESC
   ```

   </details>

## Calculated Fields

1. Query all Employees details & concatenate FirstName & LastName columns into new calculated field, FullName

   <details>
      <summary>Reveal Solution</summary>

   ```sql
   SELECT *, CONCAT(FirstName, LastName) AS FullName
   FROM Employees
   ```

   </details>

2. Query Customers to return two new calculated fields

   1. ContactName's first name under new calculated field, FirstName
   2. ContactName's last name under new calculated field, LastName

      <details>
         <summary>Reveal Solution</summary>

      ```sql
      SELECT
         LEFT(ContactName, CHARINDEX(' ', ContactName)) AS FirstName,
         RIGHT(ContactName, LEN(ContactName) - CHARINDEX(' ', ContactName)) As LastName
      FROM Customers
      ```

      </details>

3. Query Products to return two new calculated fields:

   1. The price divided by 2 under new calculated field, HalfOff (Round to nearest 2 decimals)
   2. The price plus 8% tax under new calculated field, NetPrice (Round to nearest 2 decimals)

      <details>
         <summary>Reveal Solution</summary>

      ```sql
      SELECT
         ROUND(Price/2, 2) AS HalfOff,
         ROUND(Price * 1.08, 2) As NetPrice
      FROM Products
      ```

      </details>

## Grouping Data

1. Query OrderDetails to calculate the average quantity order per ProductID under new calculated field, AvgQuantity

   <details>
      <summary>Reveal Solution</summary>

   ```sql
   SELECT AVG(Quantity) As AvgQuantity
   FROM OrderDetails
   GROUP BY ProductID
   ```

   </details>

2. Query Countries from Customers and calculate the total Customers per Country under new calculated field, TotalCustomers. Finally, sort by TotalCustomers in descending order.

   <details>
      <summary>Reveal Solution</summary>

   ```sql
   SELECT
      Country,
      SUM(CustomerID) As TotalCustomers
   FROM Customers
   GROUP BY Country
   ORDER BY TotalCustomers DESC
   ```

   </details>

## Join Queries

1. Query all OrderDetails along with ProductName & Price and return (Quantity \* Price) under new calculated field, Total

2. Query all Orders details along with Customer Name & Employee FirstName & LastName as new calculated field, EmployeeName

3. Query all Shippers details and return the total number of Products shipped under new calculated field, TotalShippedProducts

## Union

1. Query the names and phone numbers across all Shippers and Suppliers

2. Query the fullnames of all customer and employee with the letter "a" is in their First or Last Name (be careful for case sensitivity)

## Case Statements

1. Query all Products details and return new calculated field, PriceRange with the following conditions

   1. If the product price is below or equal to 15, return "Low"
   2. If the product price is above 15 and below/ equal to 30, return "Med"
   3. If the product price is above 30, return "High"

2. Query all OrderDetails and return new calculated field, EvenOdd with the following conditions

   1. If the order quantity is even (e.g. 2, 4, 6), return "Even"
   2. If the order quantity is odd (e.g. 1, 3, 5), return "Odd"

3. Query all Customers details and return new calculated field, Location with the following conditions
   1. If the customer's country is located in the USA, return "Domestic"
   2. If the customer's country is not located in the USA, return "International"

## Concepts Short Answer Questions

1. What is a join in SQL? What are the types of joins?

2. What is the difference between a UNION and a JOIN query?

3. What is a foreign key?

4. What is the difference between a database versus a table versus a field?
