# A Quick Start Guide to Learning SQL

<h3>Index:</h3>
<ol>
    <li><a href="#DefiningSQL">Defining SQL</a></li>
    <li><a href="#RetrievingData">Retrieving Data</a></li>
    <li><a href="#SortingData">Sorting Data</a></li>
    <li><a href="#FilteringData">Filtering Data</a></li>
</ol>

<h3>Resources:</h3>
<ul>
    <li>https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all</li>
</ul>

<a name="DefiningSQL"></a>

<h2>Defining SQL</h2>

<h3>What is SQL?</h3>
<ol>
    <li>Structured Query Language (SQL) is a domain specific language used in programming and designed for managed data held in relational database management</li>
    <li>It is particularly useful in handling STRUCTURED data, i.e. data incorporating rleations among entities and variables</li>
</ol>

<h3>Key Terms (<i>Simplified</i>):</h3>
<ul>
    <li><b>Database:</b> A container to store organized data</li>
    <li><b>Table:</b> A structured list of data of a specific type</li>
    <li><b>Column:</b> A single field in a table. All tables are made up of one or more columns</li>
    <li><b>Row:</b> A record in a table</li>
</ul>

<br>

<a name="RetrievingData"></a>

<h2>Retrieving Data</h2>

<h3>Retrieving Data from a Single Column</h3>
<p> To use the SELECT keyword to retrieve table data you must, at a minimum, specify two pieces of information</p>
<ol>
    <li> What do you want to select? (<i>e.g. CustomerName Column</i>)</li>
    <li> Where do you want to select from? (<i>e.g. Customers Table</i>)</li>
</ol>

```sql
SELECT CustomerName
FROM Customers;
```

<h4> Note: </h4>
<ul>
    <li>All extra white space within a SQL statement is ignored when the statement is processed. SQL statements can be specificed on one long line or broken up over many lines</li>
    <li>Most SQL developers find that breaking up statements over multiple lines makes it easier to read and debug.</li>
</ul>

<h4>Example:</h4>

```sql
SELECT CustomerName
FROM Customers;

SELECT CustomerName FROM Customers;

SELECT
CustomerName
FROM
Customers;
```

<br>

<h3>Retrieving Data from Multiple Columns</h3>
<p>The difference with retrieving data from multiple columns is: <p>
<ul>
    <li>Multiple column names must be specified after the SELECT keyword</li>
    <li>Each column must be seperated by a comma</li>
</ul>

<h4>Example:</h4>
<p>The following SELECT statement will retrieve three columns from the Customers table</p>

```sql
SELECT CustomerName, Address, Country
FROM Customers;
```

<br>

<h3>Retrieving Data from all Columns</h3>
<p>This In addition to being able to specify column(s), the SELECT keyword can be used to request all columns without having to list them out individually.This can be done by using the asterik (*) wildcard</p>

<h4>Example:</h4>

```sql
SELECT *
FROM Customers;
```

<h3>Limiting Results</h3>
<p>What if you only wanted to return the first row or a set number of rows?</p>
<p>This can be done by specifying the quantity with the LIMIT keyword</p>

<h4>Example:</h4>
<p>The following SELECT statement with the LIMIT keyword will retrieve the first 5 rows from the CustomerName Column from the Customers Table</p>

```sql
SELECT CustomerName
FROM Customers
LIMIT 5;
```

<br>

<a name="SortingData"></a>

<h2>Sorting Data</h2>

<h3>Order By</h3>
<ul>
    <li>To explicitly sort data retrieved using a SELECT statement, the ORDER BY keyword is used.</li>
    <li>ORDER BY takes the name of one or more columns by which to sort the output</li>
    <li>To sort by descending order, ensure to include the DESC keyword</li>
</ul>

<h4>Example</h4>
<p>The following SELECT statement with the GROUP BY keyword will retrieve the CustomerName Column in ASCENDING order from the Customers Table</p>

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName;
```

<p>The following SELECT statement with the GROUP BY keyword will retrieve the CustomerName Column in DESCENDING order from the Customers Table</p>

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName DESC;
```

<h4>Sorting by Multiple Columns</h4>
<ul>
    <li>It is often neccessary to sort by multiple columns. For example, if you want to retireve a list of customer names and their countries in ASCENDING order.</li>
    <li>To sort by multiple columns, specify the column names seperated by commas</li>
</ul>

<h4>Example:</h4>

```sql
SELECT CustomerName
FROM Customers
ORDER BY CustomerName, Country;
```

<h4>Note:</h4>
<ul>
    <li>The DESC keyword only applies to the column name that directly precedes it.</li>
    <li>If you want to sort descending on multiple columns, be sure each column has its own DESC keyword.</li>
</ul>

<br>

<a name="FilteringData"></a>

<h2>Filtering Data</h2>
