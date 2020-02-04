# Self-Assessment 📚📝

### Get Started

Navigate to [W3 School's Database](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all) to get started

## Basic Queries

1. Query all OrderDetails where order quantity is greater than 10 but less than 30
2. Query all Suppliers that are located in either the USA, UK, or Canada
3. Query all Employees with the letter "a" in either their First or Last Name (be careful for case sensitivity)

## Calculated Fields

1. Query all Employees details & concatenate FirstName & LastName columns into new calculated field, FullName
2. Query Customers & separate ContactName into two new calculated fields, FirstName & LastName
3. Query Products to return two new calculated fields:
   1. The price divided by 2 under new calculated field, HalfOff
   2. The price plus 8% tax under new calculated field, NetPrice

## Grouping Data

1. Query all OrderDetails and calculated the average quantity order per ProductID under new calculated field, AverageQuantity
2. Query all Customers details and calculate the total Customers per Country under new calculated field, TotalCustomers
3. Query all Products to return two new calculated fields:
   1. The minimum price under new calculated field, MinPrice
   2. The maximum price under new calculated field, MaxPrice

## Union

1. Query the names and phone numbers across all Shippers and Suppliers
2. Query the fullnames of all customer and employee with the letter "a" is in their First or Last Name (be careful for case sensitivity)

## Join Queries

1. Query all OrderDetails along with ProductName & Price and return (Quantity \* Price) under new calculated field, Total
2. Query all Orders details along with Customer Name & Employee FirstName & LastName as new calculated field, EmployeeName
3. Query all Shippers details and return the total number of Products shipped under new calculated field, TotalShippedProducts

## Case Examples

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
