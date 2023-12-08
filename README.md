# Java-ORM 


## This repository provides a Database.java to connect to databse, execute SQL statements, and other interaction with the SQLITE3 Database using the JDBC Sqlite Driver. 






<br><br><br>

# Requirements 

1. SQLITE JDBC Driver
# 

<br><br>


Database Class API Documentation
================================

Package
-------

    package com.example; // Change this to your current package
    

Class: Database
---------------

### Fields

    public Connection conn = null;
    

### Methods

#### `connect(String database_name)`

Establishes a connection to the specified SQLite database.

**Parameters:**

*   `database_name` (String): The name of the SQLite database.

**Example:**

    Database database = new Database();
    database.connect("example_database.db");
    

---
<br><br>
#### `executeStatement(String sql)`

Executes a SQL statement that does not return a result set.

**Parameters:**

*   `sql` (String): The SQL statement to be executed.

**Example:**

    Database database = new Database();
    database.connect("example_database.db");
    database.executeStatement("CREATE TABLE IF NOT EXISTS students (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)");
    

---
<br><br>
#### `executeSearch(String sql) : ResultSet`

Executes a SQL query and returns a `ResultSet` containing the result.

**Parameters:**

*   `sql` (String): The SQL query to be executed.

**Returns:**

*   `ResultSet`: The result set containing the query result.

**Example:**

    Database database = new Database();
    database.connect("example_database.db");
    ResultSet result = database.executeSearch("SELECT * FROM students");
    

---
<br><br>
#### `loopThroughResultSet(ResultSet resultSet)`

Prints the content of a `ResultSet` by looping through its rows and columns.

**Parameters:**

*   `resultSet` (ResultSet): The result set to be looped through.

**Example:**

    Database database = new Database();
    database.connect("example_database.db");
    ResultSet result = database.executeSearch("SELECT * FROM students");
    database.loopThroughResultSet(result);
    

---
<br><br>
#### `replaceWildcards(String query, String... keyValues) : String`

Replaces wildcard placeholders in a query with specified values.

**Parameters:**

*   `query` (String): The query containing wildcard placeholders.
*   `keyValues` (String...): Key-value pairs for replacement.

**Returns:**

*   `String`: The query with replaced values.

**Example:**

    Database database = new Database();
    String query = "SELECT * FROM students WHERE name = {name} AND age = {age}";
    String replacedQuery = database.replaceWildcards(query, "{name}", "John", "{age}", "25");
    

---
<br><br><br>
### Usage Example

    public class ExampleUsage {
        public static void main(String[] args) {
            Database database = new Database();
            database.connect("example_database.db");
    
            // Execute statements or queries as needed
            database.executeStatement("CREATE TABLE IF NOT EXISTS students (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)");
    
            // Search and loop through the result set
            ResultSet result = database.executeSearch("SELECT * FROM students");
            database.loopThroughResultSet(result);
    
            // Replace wildcards in a query
            String query = "SELECT * FROM students WHERE name = {name} AND age = {age}";
            String replacedQuery = database.replaceWildcards(query, "{name}", "John", "{age}", "25");
            System.out.println("Replaced Query: " + replacedQuery);
        }
    }
    


\`\`\`
