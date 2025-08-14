# advancedjava
advanced java 
12-05-2025
retrivedata-jdbc:This Java program connects to a MySQL database called school on the local machine. It uses the MySQL JDBC driver to establish the connection. After connecting, it executes a SQL query to retrieve all records from the table named class9. For each row returned, it prints the first column as an integer and the second column as a string to the console. Finally, it closes the database connection. Any errors during this process are caught and printed.
# JDBC Example – Avoiding SQL Injection with PreparedStatement

This repository contains two Java programs demonstrating how to connect to a MySQL database using JDBC and the difference between using a normal `Statement` and a `PreparedStatement`.
## Files
1. **JdbcEx_Statement.java**  
   - Uses `Statement` to execute SQL queries.  
   - Takes `username` and `password` from user input and constructs the SQL query directly.  
   - Not secure — vulnerable to SQL Injection attacks.  

2. **JdbcEx_PreparedStatement.java**  
   - Uses `PreparedStatement` with placeholders `?` to pass parameters.  
   - Inputs are bound using setter methods (`setString`, `setInt`).  
   - Secure — prevents SQL Injection by treating inputs as data, not SQL code.
## Key Learning  
- SQL Injection occurs when malicious input alters the intended SQL query.  
- PreparedStatement avoids this by separating SQL structure from input values.  
- Example of placeholder usage:  
  ```java
  String qry = "SELECT bankbalance FROM bankbalance WHERE uname = ? AND password = ?";
  PreparedStatement stmt = conn.prepareStatement(qry);
  stmt.setString(1, uname);
  stmt.setInt(2, Integer.parseInt(password));
