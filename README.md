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
  
# JDBC PreparedStatement Example – Insert Data into MySQL  
**Date:** 14 August 2025  
This program demonstrates how to use JDBC with a PreparedStatement to insert data into a MySQL database table securely.
## File
- **JdbcEx.java**
  - Connects to a MySQL database using JDBC.
  - Prompts the user to enter `id` and `name`.
  - Uses a PreparedStatement to insert values into the `class9` table.
  - Prevents SQL Injection by using placeholders (`?`) instead of concatenating input directly.
## Key Points
- **PreparedStatement** keeps SQL structure and data separate.
- Parameters are bound using methods:
  ```java
  stmt.setInt(1, Integer.parseInt(ID));
  stmt.setString(2, name);
  
# JDBC CallableStatement Example – Call Stored Procedure in MySQL  
**Date:** 16 August 2025  
This program demonstrates how to use JDBC with a CallableStatement to call a stored procedure from a MySQL database.
## File
- **JdbcEx.java**
  - Connects to a MySQL database using JDBC.
  - Prompts the user to enter a student `id`.
  - Calls a stored procedure `getname1` using a CallableStatement.
  - Retrieves and displays the student's name for the given ID.
## Key Points
- **CallableStatement** is used to call stored procedures from the database.  
- Parameters are set using methods such as:
  ```java
  stmt.setInt(1, ID);

  
## MVC Architecture – Simple Explanation  
**Date:** 17 August 2025  
This document explains the **MVC (Model-View-Controller)** architecture in a simple way, commonly used in Java, Spring Boot, and other frameworks to build structured applications.
## What is MVC?
- **MVC** stands for **Model – View – Controller**.
- It is a **design pattern** that separates an application into three main components:
  1. **Model** – Represents the data and business logic.
  2. **View** – Represents the user interface (what the user sees).
  3. **Controller** – Acts as a bridge between Model and View, handling user input and coordinating responses.
## Components
1. **Model**
   - Manages the application data.
   - Interacts with the database.
   - Contains business logic (rules, calculations, operations).
   - Example: `Student.java`, `StudentDAO.java`
2. **View**
   - Displays data to the user.
   - Represents the front-end (HTML, JSP, Thymeleaf, etc.).
   - Example: `student.jsp`, `student.html`
3. **Controller**
   - Handles requests from the user.
   - Calls the Model to process data.
   - Sends processed data to the View.
   - Example: `StudentController.java`
## How MVC Works (Flow)
1. The **user sends a request** (e.g., clicking a button or entering data).  
2. The **Controller** receives the request and decides what to do.  
3. The **Model** processes the request (fetches data, applies logic).  
4. The **Controller** sends the data to the **View**.  
5. The **View** displays the result to the user.  
## Example (Student Application)
- **Model**: `Student.java` stores student data like id, name, marks.  
- **View**: `student.jsp` displays student details.  
- **Controller**: `StudentController.java` gets the student info from the database through the Model and sends it to the View for display.
## Key Points
- MVC makes applications easier to **maintain**, **test**, and **scale**.  
- It separates **business logic** (Model), **user interface** (View), and **control flow** (Controller).  
- Used in frameworks like **Spring MVC**, **Struts**, and **ASP.NET MVC**.  

  
