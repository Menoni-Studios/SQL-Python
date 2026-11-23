# MySQLAlchemy or Cursor

### ➡️MySQLAlchemy

This method uses **SQLAlchemy** as a connector to allow **Pandas** to talk directly to the database.

Best for: Data Science, ETL (Extract, Transform, Load), and quick analysis.

How it works: You create an engine object. Pandas uses this engine to automatically generate SQL commands (CREATE TABLE, INSERT) and read data into DataFrames.

*   Pros:
    *   Very little code to write (e.g., df.to\_sql()).
    *   Automatically handles data types and column names.
    *   Great for loading CSVs and reporting.
*   Cons:
    *   Less control over the specific SQL syntax.
    *   Can be slower for very complex, custom queries.
    *   Requires installing sqlalchemy and a driver (like pymysql).

Steps:

**☑️.to\_sql()** =>Here in the code are all first septs to load a CSV file to MySQL. I super easy this way you do not have to create the table and load the data on the tables.

☑️**.read\_sql() =>**Alows you to retrive stuff from the DB like =>df2 = pd**.read\_sql**("SELECT \* FROM census\_data", engine).

```python
1. Read the CSV
df = pd.read_csv("CSVfile/census_data.csv")
2. Strip whitespace from ALL column names
df.columns = df.columns.str.strip()
Optional: Replace spaces with underscores for cleaner SQL names
df.columns = df.columns.str.replace(' ', '_')
3. Create the engine and write to SQL
engine = create_engine('mysql+pymysql://root:MySQL13333920!@localhost/MarceloDB')
4. Write the DataFrame to the SQL table. This will send the csv file to the MySQL database.
If the table already exists, it will be replaced.
df.to_sql('census_data', con=engine, if_exists='replace', index=False)
print("✅ Data loaded successfully!")
```

### ➡️Cursor

This method uses the MySQL Connector directly to send SQL commands as strings.

Best for: Web applications, complex database management, stored procedures, and precise control.

How it works: You connect, create a cursor, and manually write every SQL statement (e.g., cursor.execute("INSERT INTO...")).

*   Pros:
    *   Full control over SQL syntax and performance.
    *   No extra dependencies (just the connector).
    *   Better for executing DDL (CREATE, ALTER) or DML (UPDATE, DELETE) with specific conditions.
*   Cons:
    *   More verbose code (you have to manage connections, cursors, and transactions manually).
    *   You must manually convert results to Python lists or dicts.

Steps:

1️⃣**connect()** is use to connect to MySQL database. You have to use your credentials to access MySQL.

*   *   import mysql.connector
        
    *   connection = mysql.connector.**connect**(
        
        *   host="localhost",
            
        *   user="root",
            
        *   password="MySQL13333920!" )

2️⃣ **cursor()** is use to execute SQL statements and fech result from SQL queries.

*   *   cursor = connection.**cursor**()--->Note here you create a var cursor and use the var = connection created before and call .coursor on it to make stuff.
    *   cursor.**execute**("SHOW DATABASES")
    *   for db in cursor:
    *   print(db)

3️⃣ **execute()** allows to perform SQL commands, including retrieving data from a table using a query like "Select \* from table\_name." When you execute this command, the result is obtained as a collection of table data stored in an object, typically in the form of a list of lists.

*   *   cursor.**execute**("CREATE DATABASE MarceloDB")--->This will create a new data base.
        
    *   cursor.**execute**("SHOW DATABASES")--->Show all the DB
        
    *   for db in cursor:
        
    *   print(db)--->All the DB + the new one should be show.
        
    *   **tables** can be created with **.execute()**, look 8\_DataAnalysis.ipynb for more.

4️⃣ **fetchmany()** method retrieves the subsequent group of rows from the result set of a query rather than just a single row. To fetch a few rows from the table, use fetchmany(numberofrows) and mention how many rows you want to fetch.

5️⃣ **fetchall()** method in Python retrieves all the rows from the result set of a query and presents them as a list of tuples.

6️⃣ from **tabulate** import **tabulate:** This code uses the tabulate library to format the output of the SQL query results into a nicely formatted table.

7️⃣ **close()** is a method used to close the connection to a MySQL database. When called, it terminates the connection, releasing any associated resources and ensuring the connection is no longer active. This is important for managing database connections efficiently and preventing resource leaks in your MySQL database interactions.
