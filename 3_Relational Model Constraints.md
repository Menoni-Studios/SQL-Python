## Types of relational model constraints

### ✅Entity integrity constraint

This constraint ensures that every table in a relational database has a PRIMARY KEY. A primary key uniquely identifies each row in the table. A primary key column(s):

*   must not contain NULL values
*   must be unique across all rows

This constraint guarantees that each record (or entity) in a table is DISTINCT and IDENTIFICABLE, preventing duplication and missing identifiers.

*   EXAMPLE:
    *   CREATE TABLE BookShop (
        *   BOOK\_ID INT PRIMARY KEY,
        *   TITLE VARCHAR(100),
        *   AUTHOR\_ID INT
        *   );
*   EXPALNATION:
    *   Here, BOOK\_ID is the primary key. It must be:
        *   Unique (no two books can have the same ID)
        *   Not NULL (every book must have an ID)
        *   Note: Every table in a relational database should have a primary key to satisfy entity integrity.

### ✅Referential integrity constraint

This constraint ensures that a FOREING KEY in one table always refers to a valid PRIMARY KEYprimary key in another table. This maintains consistent and meaningful relationships between tables.

It enforces the **logical link between related data** in different tables, preventing the existence of invalid or "orphaned" references.

*   EXAMPLE:
    *   CREATE TABLE BookShop\_AuthorDetails (
        *   AUTHOR\_ID INT **PRIMARY KEY**,
        *   AUTHOR\_NAME VARCHAR(100)
        *   );
    *   CREATE TABLE BookShop (
        *   BOOK\_ID INT **PRIMARY KEY**,
        *   TITLE VARCHAR(100),
        *   AUTHOR\_ID INT, **FOREIGN KEY (AUTHOR\_ID) REFERENCES BookShop\_AuthorDetails(AUTHOR\_ID)** );
*   EXPLANATION:
    *   AUTHOR\_ID in BookShop references AUTHOR\_ID in BookShop\_AuthorDetails.
    *   This means every AUTHOR\_ID in BookShop must exist in BookShop\_AuthorDetails.
    *   Trying to insert a book with an AUTHOR\_ID that doesn't exist in BookShop\_AuthorDetails will fail.

### ✅Domain integrity constraint

This constraint ensures that all values stored in a column fall within a defined domain. This includes rules about:

*   data type
    
*   formant
    
*   allowed values
    
*   nullability
    
*   EXAMPLE:
    
    *   CREATE TABLE BookShop (
        *   BOOK\_ID INT PRIMARY KEY,
        *   TITLE VARCHAR(100) NOT NULL,
        *   PRICE DECIMAL(5, 2) CHECK (PRICE >= 0),
        *   PUBLISHED\_DATE DATE
        *   );
*   EXPLANATION:
    
    *   Two standard mechanisms used to enforce domain integrity are the **CHECK** and **NOT NULL** constraints:
    *   CHECK:
        *   The CHECK constraint enforces rules about the range or pattern of acceptable values within a column. It ensures that the data entered meets specific logical conditions.
            *   The PRICE column in the example above has a CHECK constraint to ensure it's not negative
    *   NOT NULL:
        *   The NOT NULL constraint enforces nullability rules, ensuring that a column must contain a value and cannot be left empty (NULL).
            *   TITLE is NOT NULL. A title must be provided.
