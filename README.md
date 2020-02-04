# A Quick Start Guide to Learning SQL

> Give ordinary people the right tools and they will design and build the most extraordinary things. - Neil Gershenfeld

### Table of Contents:

1. [Defining SQL](#Defining-SQL)
2. [Retrieving Data](#Retrieving-Data)
3. [Sorting Data](#Sorting-Data)
4. [Filtering Data](#Filtering-Data)
5. [Advance Filtering](#Advance-Filtering)
6. [Wildcard Filtering](#Wildcard-Filtering)
7. [Calculated Fields](#Calculated-Fields)
8. [Summarizing Data](#Summarizing-Data)
9. [Grouping Data](#Grouping-Data)
10. [Subqueries](#Subqueries)
11. [Joining Tables](#Joining-Tables)
12. [Advanced Joins](#Advanced-Joins)
13. [Combining Queries](#Combining-Queries)
14. [Case Statement](#Case-Statement)

### Resources:

- [SQL Playground](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all)
- [SQL Quiz](https://www.w3schools.com/sql/sql_quiz.asp)
- [SQL Assessment](./Assessment.md)

---

## Defining SQL

### What is SQL?

- Structured Query Language (SQL) is a domain specific language used in programming and designed for managed data held in relational database management
- It is particularly useful in handling STRUCTURED data, i.e. data incorporating relations among entities and variables

### Key Terms (_Simplified_):

- **Database:** A container to store organized data
- **Table:** A structured list of data of a specific type
- **Column:** A single field in a table. All tables are made up of one or more columns
- **Row:** A record in a table

---

## Retrieving Data

### Retrieving Data from a Single Column

To use the SELECT keyword to retrieve table data you must, at a minimum, specify two pieces of information

- What do you want to select? (_e.g. CustomerName Column_)
- Where do you want to select from? (_e.g. Customers Table_)

```sql
SELECT CustomerName
FROM Customers;
```

#### Note:

- All extra white space within a SQL statement is ignored when the statement is processed. SQL statements can be specified on one long line or broken up over many lines
- Most SQL developers find that breaking up statements over multiple lines makes it easier to read and debug.

#### Example:

```sql
SELECT CustomerName
FROM Customers;

SELECT CustomerName FROM Customers;

SELECT
CustomerName
FROM
Customers;
```

---

### Retrieving Data from Multiple Columns

The difference with retrieving data from multiple columns is:

- Multiple column names must be specified after the SELECT keyword
- Each column must be separated by a comma

#### Example:

- The following SELECT statement will retrieve two columns from the Customers table

```sql
SELECT CustomerName, Address
FROM Customers;
```

- The following SELECT statement will retrieve three columns from the Customers table

```sql
SELECT CustomerName, Address, Country
FROM Customers;
```

---

### Retrieving Data from all Columns

This In addition to being able to specify column(s), the SELECT keyword can be used to request all columns without having to list them out individually. This can be done by using the asterisk (\*) wildcard

#### Example:

- The following SELECT statement will retrieve all columns from the Customers table

```sql
SELECT *
FROM Customers;
```

### Limiting Results

What if you only wanted to return the first row or a set number of rows?
This can be done by specifying the quantity with the LIMIT keyword

#### Example:

- The following SELECT statement with the LIMIT keyword will retrieve the first 5 rows from the CustomerName Column from the Customers Table

```sql
SELECT CustomerName
FROM Customers
LIMIT 5;
```

---

## Sorting Data

### Order By

- To explicitly sort data retrieved using a SELECT statement, the ORDER BY keyword is used.
- ORDER BY takes the name of one or more columns by which to sort the output
- To sort by descending order, ensure to include the DESC keyword

#### Example

- The following SELECT statement with the GROUP BY keyword will retrieve the CustomerName Column in ASCENDING order from the Customers Table

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName;
```

- The following SELECT statement with the GROUP BY keyword will retrieve the CustomerName Column in DESCENDING order from the Customers Table

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName DESC;
```

#### Sorting by Multiple Columns

- It is often necessary to sort by multiple columns. For example, if you want to retrieve a list of customer names and their countries in ASCENDING order.
- To sort by multiple columns, specify the column names separated by commas

#### Example:

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName, Country;
```

#### Note:

- The DESC keyword only applies to the column name that directly precedes it.
- If you want to sort descending on multiple columns, ensure each column has its own DESC keyword.

#### Example:

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName DESC, Country DESC;
```

---

## Filtering Data

### The WHERE Keyword

- Within a SELECT statement, data is filtered by specifying search criteria in the WHERE clause
- The WHERE keyword is specified after the FROM keyword

#### Example:

- The following SELECT statement with the WHERE keyword will retrieve the CustomerName Column where their Country field is EQUAL to Canada

```sql
SELECT CustomerName
FROM Customers
WHERE Country = "Canada";
```

### WHERE Clause Operators

SQL supports a whole range of conditional operators (depending on your database management system)

<table>
<tr>
    <th>Operator</th>
    <th>Description</th>
</tr>
<tr>
    <td><></td>
    <td>Non-Equality</td>
</tr>
<tr>
    <td>!=</td>
    <td>Non-Equality</td>
</tr>
<tr>
    <td><</td>
    <td>Less Than</td>
</tr>
<tr>
    <td><=</td>
    <td>Less than or equal to</td>
</tr>
<tr>
    <td>!<</td>
    <td>Not less than</td>
</tr>
<tr>
    <td>></td>
    <td>Greater than</td>
</tr>
<tr>
    <td>>=</td>
    <td>Greater than or equal to</td>
</tr>
<tr>
    <td>!></td>
    <td>Not greater than</td>
</tr>
<tr>
    <td>BETWEEN</td>
    <td>Between two specified values</td>
</tr>
<tr>
    <td>IS NULL</td>
    <td>Is a NULL value</td>
</tr>
</table>

#### Example:

- The following SELECT statement with the WHERE keyword will retrieve the CustomerName Column where their Country field is NOT EQUAL to Canada

```sql
SELECT CustomerName
FROM Customers
WHERE Country <> "Canada";
```

- The following SELECT statement with the WHERE keyword will retrieve the ProductName and Price Column where the Price field is LESS THAN OR EQUAL to 20

```sql
SELECT ProductName, Price
FROM Products
WHERE Price <= 20;
```

- The following SELECT statement with the WHERE keyword will retrieve the ProductName and Price Column where the Price field is BETWEEN 10 and 20

```sql
SELECT ProductName, Price
FROM Products
WHERE Price BETWEEN 10 and 20;
```

#### Note:

- != and <> can usually be used interchangeably, However, not all database management systems support both forms of the non-equality operator

---

## Advance Filtering

### The AND keyword

To filter by more than one column, you use the AND operator to append conditions to your WHERE clauses.

#### Example:

```sql
SELECT CustomerName
FROM Customers
WHERE Country = "Canada" AND City <> "Vancouver";
```

### The OR keyword

The OR operator retrieves rows that match either conditions listed under the WHERE clauses

#### Example:

```sql
SELECT CustomerName
FROM Customers
WHERE Country = "Canada" OR City <> "Vancouver";
```

### The IN keyword

The IN operator is used to specify a range of conditions, any of which can be matched. In takes a comma-delimited list of valid values, all enclosed within parentheses

#### Example:

```sql
SELECT CustomerName
FROM Customers
WHERE Country IN ("USA", "Canada");
```

### The NOT keyword

The WHERE clause's NOT operator has one function and one function only - NOT negates whatever condition comes next.

#### Example:

```sql
SELECT CustomerName
FROM Customers
WHERE Country NOT IN ("USA", "Canada");
```

---

## Wildcard Filtering

### The LIKE keyword

- **Wildcards:** Special characters used to match parts of a value
- **Search pattern:** A search condition made up of literal text, wildcard characters, or any combination of the above.
- Using wildcards, you can create search patterns that can be compared against your data
- To use wildcards in search clauses, the LIKE operator must be used.

### The Percent Sign (%) Wildcard

- The most frequently used wildcard is the percent sign (%).
- Within a search string, % means, match any number of occurrences of any character.

#### Example:

- To find all customers that start with the letter A, you can issue the following SELECT statement.

```sql
SELECT CustomerName
FROM Customers
Where CustomerName LIKE 'A%'
```

- To find all customers that have the letter A in their name, you can issue the following SELECT statement.

```sql
SELECT CustomerName
FROM Customers
Where CustomerName LIKE '%a%'
```

#### Note:

- If you are using Microsoft Access, then you may need to use \* instead of %.
- Depending on your DBMS and how it is configured, searches may be case-sensitive.

### The Underscore (\_) Wildcard

- The underscore is used just like % but instead of matching multiple characters the underscore matches just a single character.

#### Example:

- To find all customers that live in the postal codes between 12200 to 12209, you can issue the following SELECT statement.

```sql
SELECT CustomerName
FROM Customers
Where PostalCode LIKE '1220_'
```

#### Note:

- If you are using Microsoft Access, then you may need to use ? instead of \_.

### The Brackets ([]) Wildcard

- The brackets ([]) is used to specify a set of characters, any one of which must match a character in the specified position (the location of the wildcard).

#### Example:

- To find all customers that start with the letter A or B, you can issue the following SELECT statement.

```sql
SELECT CustomerName
FROM Customers
Where CustomerName LIKE '[AB]%'
```

---

## Calculated Fields

### What is a Calculated Field?

- Data stored within a database's tables is often not available in the exact format needed by your application.
  - City, State, and ZIP codes are stored in separate columns, but your mailing label needs them retrieved as one correctly formatted field.
  - Column data is in mixed upper and lowercase, and your report needs all data presented in uppercase.
  - You need total, averages, or other calculations based on table data.
- What you really want is to retrieve converted, calculated, or reformatted data directly from the database.
- Calculated fields don't actually exist in database tables but rather a calculated field is created on-the-fly within a SQL SELECT statement.

### Concatenating Fields

- **Concatenate:** Joining values together (_by appending them to each other_) to form a single long value.
- The Customers table contains Address, City, PostalCode, and Country
  - For your report, you want to concatenate the columns to make one full address.
- In SQL SELECT statements, you can concatenate columns using a special operator.
  - Depending on what DBMS you are using, this can be a plus sign (+) or two pipes (||).

#### Example:

Concatenation performed with plus sign (+)

```sql
SELECT Address + City + PostalCode + Country
FROM Customers
```

Concatenation performed with two pipes (||)

```sql
SELECT Address || City || PostalCode || Country
FROM Customers
```

### Using Aliases

- The SELECT statement used to concatenate the address field works well but what is the name of the new calculated field? The truth is, it has no name; it is simply a value
- To solve this problem, SQL supports aliases.
  - Alias: an alternative name for a field or value.
  - Aliases are assigned with the AS keyword
  - Use of the AS keyword is optional, but using it is considered a best practice

#### Example:

```sql
SELECT Address + City + PostalCode + Country AS full_address
FROM Customers
```

### Performing Calculations

- Another frequent use of calculated fields is performing mathematical calculations on retrieved data.
- SQL supports the basic mathematical operators listed below:

| Operator | Description    |
| -------- | -------------- |
| +        | Addition       |
| -        | Subtraction    |
| \*       | Multiplication |
| /        | Division       |

#### Example:

```sql
SELECT Price / 2 As half_off_price
FROM Products
```

---

## Summarizing Data

### Aggregate Functions

- **Aggregate Functions:** Functions that operate on a set of rows to calculate and return a single value.

### The AVG() Function

- AVG() is used to return the average value of a specific column by counting the number of rows in the table and the sum of their values.
- AVG() can be used to return the average value of all columns or of specific columns or rows.

#### Example:

```sql
SELECT AVG(Price) As avg_price
FROM Products
```

### The COUNT() Function

- COUNT() is used to determine the number of rows in a table or the number of rows that match a specific criterion
- COUNT() can be used two ways:
  - Use COUNT(\*) to count the number of rows in a table, whether the columns contain values or NULL values.
  - Use COUNT(column) to count the number of rows that have values in a specific column, ignoring NULL values.

#### Example:

```sql
SELECT COUNT(*) As num_of_customers
FROM Customers
```

#### Note:

- NULL Values - Column rows with NULL values in them are ignored by the COUNT() function if a column name is specified, but not if the asterisk (\*) is used.

### The MAX() / MIN() Function

- MAX() returns the highest value in a specified column.
- MIN() returns the lowest value in a specified column.
- Note: Both MAX() & MIN() require that the column name be specified.

#### Example:

```sql
SELECT MIN(Price) As min_price
FROM Products
```

### The SUM() Function

- SUM() is used to return the sum (total) of the values in a specific column.

#### Example:

```sql
SELECT SUM(Price) As total_price
FROM Products
```

---

## Grouping Data

### Creating Groups

- Grouping lets you divide data into logical sets so that you can perform aggregate calculations on each group.
- Groups are created using the GROUP BY clause in your SELECT statement.

#### Important Rules:

- GROUP BY clauses can contain as many columns as you want. This enables you to nest groups, providing you with more granular control over how data is grouped.
- If you have nested groups in your GROUP BY clauses, data is summarized at the last specified group. In other words, all the columns specified are evaluated together when grouping is established,
- The GROUP BY clause must come after any WHERE clauses and before any ORDER BY clause.

#### Example

- The below SELECT statement uses the GROUP BY clause to instruct the DBMS to sort the data and group it by CategoryID.

```sql
SELECT AVG(*) AS num_of_products
FROM Products
GROUP BY CategoryID
```

### Filtering Groups

- SQL allows you to filter which groups to include and which to exclude.
  - For example, you might want a list of all customers who have made at least two orders.
  - To obtain this data you must filter based on the complete group, not on individual rows.
- SQL provides a clauses for this purpose: the HAVING clause
  - HAVING is very similar to WHERE, all types of WHERE clauses can also be used with HAVING.

#### Example

- The below SELECT statement groups by CategoryID and returns the data where the count of products for each group of categories is greater than 2.

```sql
SELECT COUNT(*) AS count_of_products
FROM Products
GROUP BY CategoryID
HAVING COUNT(*) > 2
```

#### Note:

- The Difference between HAVING and WHERE
  - WHERE filters before data is grouped, and HAVING filters after data is grouped.
  - Rows that are eliminated by a WHERE clauses will not be included in the group. This could change the calculated values which in turn could affect which groups are filtered based on the use of those values in the HAVING clauses.

### SELECT Clause Ordering

- This is a good time to review the order in which SELECT statement clauses are to be specified.

| Operator | Description                           | Require                                 |
| -------- | ------------------------------------- | --------------------------------------- |
| SELECT   | Columns or expressions to be returned | Yes                                     |
| FROM     | Table to retrieve data from           | Only if selecting data from a table     |
| WHERE    | Row-level filtering                   | No                                      |
| GROUP BY | Group specification                   | Only if calculating aggregates by group |
| HAVING   | Group-level filtering                 | No                                      |
| ORDER BY | Output sort order                     | No                                      |

---

## Subqueries

### Filtering by Subqueries

- **Subquery:** queries that are embedded into other queries
- Subqueries can be used to combine multiple queries into one single statement.

#### Example:

- The below SQL statement returns all products with suppliers located in the USA

```sql
SELECT ProductName, SupplierID
FROM Products
WHERE SupplierID IN (SELECT SupplierID
                    FROM Suppliers
                    WHERE Country = 'USA')

```

### Using Subqueries as Calculated Fields

- Another way to use subqueries is in creating calculated fields

#### Example:

- The below SQL statement returns the suppliers from the Suppliers table with a count of their products.

```sql
SELECT SupplierID,
        SupplierName,
        (SELECT COUNT(*)
        FROM Products
        WHERE Products.SupplierID = Suppliers.SupplierID) As product_count
FROM Suppliers
```

---

## Joining Tables

### Why use Joins?

- Breaking data into multiple tables enables more efficient storage, easier manipulation, and greater scalability. If data is stored in multiple tables, how can you retrieve that data with a single SELECT statement?
- The answer is to use a join. A join is a mechanism used to associate tables within a SELECT statement.
- Using a special syntax, multiple tables can be joined so that a single set of output is returned, and the join associates the correct rows in each table on-the-fly.

### Creating a Join

- Creating a join is very simple. You must specify all the tables to be included and how they are related to each other.

#### Example:

```sql
SELECT Products.ProductName, Suppliers.SupplierName, Suppliers.Country
FROM Products, Suppliers
WHERE Products.SupplierID = Suppliers.SupplierID
```

### The Importance of the WHERE clause

- The WHERE clause acts as a filter to only include rows that match the specified filter condition - the join condition.
- Without the WHERE clause, every row in the first table will be paired with every row in the second table, regardless if they logically go together or not.

#### Example:

- Run the below SQL statement to see the difference between the SQL statements with and without the WHERE clause

```sql
SELECT Products.ProductName, Suppliers.SupplierName, Suppliers.Country
FROM Products, Suppliers
```

---

## Advanced Joins

### Using Table Aliases

- In addition to using aliases for column names and calculated fields, SQL also enables you to alias table names. There are two primary reasons to do this:

  - To shorten the SQL syntax
  - To enable multiple uses of the same table within a single SELECT statement

#### Example:

```sql
SELECT p.ProductName, s.SupplierName, s.Country
FROM Products AS p, Suppliers AS s
WHERE p.SupplierID = s.SupplierID
```

#### Note:

- Not all DBMS support the AS keyword. In that case, simply specify the alias without the AS keyword (so `Products p` instead of `Products AS p`).

### Using (INNER) JOIN, LEFT/ RIGHT (OUTER) JOIN, FULL (OUTER) JOIN

- A JOIN clause is used to combine rows from two or more tables, based on a related column between them.
- Here are the different types of JOINS in SQL
  - (INNER) JOIN: Returns records that have matching values in both tables
  - LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
  - RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
  - FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table

#### Example:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

#### JOINs Diagram:

![JOINs Diagram](https://i.imgur.com/9zyrJM2.png)

---

## Combining Queries

- SQL also enables you to perform multiple queries (multiple SELECT statements) and return the results as a single query result set.
- These combined queries are usually known as unions or compound queries

### Using Union

- Specify each SELECT statement and place the keyword UNION between each.
- Rules:
  - A UNION must be composed of two or more SELECT statements, each separated by the keyword UNION (so, if combining four SELECT statements that would be three UNION keywords used.)
  - Each query in a UNION must contain the same columns, expressions, or aggregate functions (and some DBMSs even require that columns be listed in the same order).
  - Column datatypes must be compatible; They need not be the exact same type, but they must be of a type that the DBMS can implicitly convert (for example, different numeric types or different date types).

#### Example:

- The below SQL Statement returns all unique countries from the Suppliers and Customers table within a single query result set.

```sql
SELECT Country FROM Suppliers
UNION
SELECT Country FROM Customers
```

### Including or Eliminating Duplicates

- The UNION keyword automatically removes any duplicate rows from the query result set
- If you want all occurrences to be returned (regardless of duplicates), you can use UNION ALL instead of UNION

#### Example:

```sql
SELECT Country FROM Suppliers
UNION ALL
SELECT Country FROM Customers
```

---

## Case Statement

- The CASE statement goes through conditions and returns a value when the first condition is met (like an IF-THEN-ELSE statement)
- Once a condition is true, it will stop reading and return the result.
- If no conditions are true, it returns the value in the ELSE clause.

#### Example:

- The below SQL statement returns a value of LOW if the order quantity is less than 20.
- If the order quantity is greater or equal to 20 and less than 40, a value of MEDIUM is returned.
- If the order does not meet the first two conditions, the else clause returns a value of HIGH

```sql
SELECT OrderID,
CASE
    WHEN Quantity < 20 THEN "LOW"
    WHEN Quantity >= 20 AND Quantity < 40 THEN "MEDIUM"
    ELSE "HIGH"
END as QuantityCategory
FROM OrderDetails
```

---

> You have reached the end of the SQL quick start guide!

[Go Back to Top](#A-Quick-Start-Guide-to-Learning-SQL)
