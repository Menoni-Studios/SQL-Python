# SELECT statement

SELECT is classified as a Database Query command used to retrieve information from a database table.

### There are various forms in which a SELECT statement is used.

1.  The general syntax of a SELECT statement retrieves the data under the listed columns from Table\_1. The code is:
    1.  **SELECT COLUMN1, COLUMN2, ... FROM TABLE\_1** ;
        1.  Example = SELECT ID, Name FROM TABBLE\_1
2.  To retrieve all columns from a table, use " \* " instead of specifying individual column names. The code below retrieves the entire table
    1.  **SELECT \* FROM TABLE\_1 ;**
3.  Use the **WHERE** clause to filter the required data based on a predicate. The code below filters the response to only the entries that match the predicate.
    1.  **SELECT \<COLUMS> <columns>FROM TABLE_1 WHERE &lt;predicate&gt;<predicate>; predicate =&gt; "column (operator) value"</predicate></columns>**
        1.  Example = SELECT FROM TABLE\_1 WHERE ID<=5
        2.  Retrieves all columns from the "COUNTRY" table where the value in the "ID" column is less than or equal to 5.
        3.  **SELECT Title, ProductionCompany, Locations, ReleaseYear FROM FilmLocations WHERE Writer<>"James Cameron"**;

# COUNT statement

1.  Count retivre the number of row of a specific criteria:
    1.  Example get the total of rows in a table:
        1.  **SELECT COUNT(\*) from TABLE\_1**
    2.  Example get the total rows in a column:
        1.  **SELECT COUNT(column\_1) from TABLE\_1 WHERE column\_1 = "condicional"**

# **DISTINCT statement**

1.  Retrieves unique values in a column.
    1.  **SELECT DISTINCT column\_1 from TABLE\_1**
2.  List of unique values in a column\_1 where medaltype is gold\*\*.\*\*
    1.  **SELECT DISTINCT column\_1 from TABLE\_1 WHERE medaltype = "Gold"**

# **LIMIT statement**

1.  Restrict the number of rows retrieved from the dataset.
    1.  Example get the first 10 rows
        1.  **SELECT \* FROM TABLE\_1 LIMIT 10**
    2.  Example get the 5 rows in column\_1 for a particular year.
        1.  **SELECT \* FROM column\_1 WHERE year = 2026 LIMIT 5**

# **EXAMPLES:**

1.  **COUNT & DISTINCT combination**:
    1.  We want to retrieve the count of release years of the films produced by a specific company so that duplicate release years of those films will be discarded in the count. Will get the count of row with this criteria.
        1.  **SELECT COUNT(DISTINCT ReleaseYear) FROM FilmLocations WHERE ProductionCompany="Warner Bros. Pictures";**
2.  LIMIT
    1.  We want to retrieve 15 rows from the table starting from row 11.
        1.  **SELECT \* FROM FilmLocations LIMIT 15 OFFSET 10;**

# **INSERT statement**

1.  Insert into columns 1 and 2 values:\\
    1.  **INSERT INTO table\_name (column\_name\_1, column\_name\_2,...) VALUES ("value\_1", "value\_2",...)**
2.  Insert multiple rows in one column. This 3 values will be insterted in the column\_name\_1. You can specify several columns and add multiple values to them.
    1.  **INSERT INTO table\_name (column\_name\_1) VALUES**
        1.  **("value\_1", "value\_2", "value\_3")**

# UPDATE , INSERT, DELETE statements

1.  **UPDATE table\_name SET column\_name = "value" WHERE condition =<>!= "something"**
    1.  When using the UPDATE statement, if you do not specify the WHERE clause, all the rows in the table are updated.
2.  **INSERT INTO table\_1(ins\_id, lastname, firstname, city, country) VALUES(4, 'Saha', 'Sandip', 'Edmonton', 'CA');**
3.  **DELETE FROM table\_1 WHERE conditon =<>!= "something"**
    1.  If you do not specify the WHERE clause, all the rows in the table are updated.

# Operators

1.  \=
2.  \>
3.  <
4.  \>=
5.  <=
6.  <>

# ORDER BY

1.  It is use to order data in ascending or descending order:
    1.  This will arrange the table by price in ascendign order by default.
        1.  SELECT \* FROM table\_1 ORDER BY price
    2.  This will order in a descending.
        1.  SELECT \* FROM table\_1 ORDER BY price DESC
    3.  Can also sort by more than one column:
        1.  SELECT \* FROM table\_1 ORDER BY country, ID

# NOT operator

1.  NOT will give you the negative result:
    1.  SELECT \* FROM table\_1 WHERE NOT country="Ireland"
        1.  Return all the customer except from Ireland.
    2.  SELECT \* FROM table\_1 WHERE NOT salary < 50k
        1.  Return all the emploee over 50K.

# NULL VALUES

1.  To find nulls values we use: **IS NULL** OR **IS NOT NULL:**
    1.  **SELECT customerID, customerName, Address**
    2.  **FROM table\_1**
    3.  **WHERE Address IS NOT NULL**
        1.  Return the customer that Address has values.

# AND/OR

1.  It is useful to filter based on multiple conditions:
2.  AND: display records if ALL condition are true.
3.  OR: display records if ANY condition are true.\
    1.  SELECT cloumn\_1, column\_2....
    2.  FROM table\_1
    3.  WHERE condition\_1 **AND** condition\_2 **AND** conditon\_3
