# A Quick Start Guide to Learning SQL

### Index:

1. [Defining SQL](#Defining-SQL)
2. [Retrieving Data](#Retrieving-Data)
3. [Sorting Data](#Sorting-Data)
4. [Filtering Data](#Filtering-Data)
5. [Advance Filtering](#Advance-Filtering)
6. [Wildcard Filtering](#Wildcard-Filtering)

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

- Using wildcards, you can create search patterns that can be compared against your data
- The wildcards themselves are actually characters that have special meanings wihtin SQL WHERE clauses, and SQL supports several different wildcard types.
- To use wildcards in search claues, the LIKE operator must be used.

---
