# A Quick Start Guide to Learning SQL

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

### Resources:

- [Online SQL Playground](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all)

---

## Defining SQL

### What is SQL?

- Structured Query Language (SQL) is a domain specific language used in programming and designed for managed data held in relational database management
- It is particularly useful in handling STRUCTURED data, i.e. data incorporating rleations among entities and variables

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

- All extra white space within a SQL statement is ignored when the statement is processed. SQL statements can be specificed on one long line or broken up over many lines
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
- Each column must be seperated by a comma

#### Example:

The following SELECT statement will retrieve three columns from the Customers table

```sql
SELECT CustomerName, Address, Country
FROM Customers;
```

---

### Retrieving Data from all Columns

This In addition to being able to specify column(s), the SELECT keyword can be used to request all columns without having to list them out individually.This can be done by using the asterik (\*) wildcard

#### Example:

```sql
SELECT *
FROM Customers;
```

### Limiting Results

What if you only wanted to return the first row or a set number of rows?
This can be done by specifying the quantity with the LIMIT keyword

#### Example:

The following SELECT statement with the LIMIT keyword will retrieve the first 5 rows from the CustomerName Column from the Customers Table

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

The following SELECT statement with the GROUP BY keyword will retrieve the CustomerName Column in ASCENDING order from the Customers Table

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName;
```

The following SELECT statement with the GROUP BY keyword will retrieve the CustomerName Column in DESCENDING order from the Customers Table

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName DESC;
```

#### Sorting by Multiple Columns

- It is often neccessary to sort by multiple columns. For example, if you want to retireve a list of customer names and their countries in ASCENDING order.
- To sort by multiple columns, specify the column names seperated by commas

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

The following SELECT statement with the WHERE keyword will retrieve the CustomerName Column where their Country field is EQUAL to Canda

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
    <td>Greather than</td>
</tr>
<tr>
    <td>>=</td>
    <td>Greather than or equal to</td>
</tr>
<tr>
    <td>!></td>
    <td>Not greater than</td>
</tr>
<tr>
    <td>BETWEEN</td>
    <td>Between two specificed values</td>
</tr>
<tr>
    <td>IS NULL</td>
    <td>Is a NULL value</td>
</tr>
</table>

#### Example:

The following SELECT statement with the WHERE keyword will retrieve the CustomerName Column where their Country field is NOT EQUAL to Canda

```sql
SELECT CustomerName
FROM Customers
WHERE Country <> "Canada";
```

#### Note:

!= and <> can usually be used interchangeablly, However, not all database management systems support both forms of the non-equality operator

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
WHERE NOT Country = "Canada";
```

---

## Wildcard Filtering

### The LIKE keyword

- **Wildcards:** Special characters used to match parts of a value
- **Search pattern:** A seach condition made up o fliteral text, wildcard characters, or any combination of the above.
- Using wildcards, you can create search patterns that can be compared against your data
- To use wildcards in search claues, the LIKE operator must be used.

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
  - City, State, and ZIP codes are stored in separate columns, but your mailing lable needs them retireved as one correctly formatted field.
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

- Another frequent use of calculated fileds is performing mathematical calculations on retrieved data.
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

- NULL Values - Column rows with NULL values in them are ignored by the COUNT() function if a column name is specified, but not if the asterik (\*) is used.

### The MAX() / MIN() Function

- MAX() returns the highest value in a specified column.
- MIN() returns the lowest value in a specificied column.
- MAX() & MIN() require that the column name be specified.

#### Example:

```sql
SELECT MIN(Price) As min_price
FROM Products
```

### The SUM() Function

- SUM() is used to return the sum (total) of the values in a specific column.

#### Example:

```sql
SELECT MIN(Price) As total_price
FROM Products
```

---

## Grouping Data

### Creating Groups

- Grouping lets you divide data into logical sets so that you can perform aggregate calculaitons on each group.
- Groups are created using the GROUP BY clause in your SELECT statement.
