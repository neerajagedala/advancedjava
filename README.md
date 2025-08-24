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
Servlet Example – FirstServlet (Hello World)

## Servlet Example – FirstServlet (Hello World)  
**Date:** 17 August 2025  
This is the first simple **Servlet program** that demonstrates how to create, configure, and run a **Hello World servlet** in Eclipse using Apache Tomcat.  

## Flow of the Program
1. **Create Dynamic Web Project (Eclipse)**  
   - Go to **File → New → Dynamic Web Project**.  
   - Enter a project name (e.g., `FirstServletProject`).  
   - Configure the target runtime with **Apache Tomcat**.  

2. **Create Servlet Class (`FirstServlet.java`)**  
   - Extend the `HttpServlet` class.  
   - Override the `doGet()` method.  
   - Use `PrintWriter` to send `"Hello World"` as a response to the client.  

3. **Configure `web.xml` (Deployment Descriptor)**  
   - Define the servlet name and mapping.  
   - Example: Map the URL `/hello` to the `FirstServlet` class.  

4. **Run the Application**  
   - Right-click the project → **Run on Server** → Choose **Tomcat Server**.  
   - Access the servlet in the browser at:  
     ```
     http://localhost:8080/FirstServletProject/hello
     ```
## Key Points
- `HttpServlet` is the base class for creating servlets.  
- `doGet()` handles **GET requests** from the client (browser).  
- `PrintWriter` is used to send output (HTML/text) to the response.  
- `web.xml` maps servlet URLs to servlet classes.


  **Servlets are the foundation of Java web applications.**
  ## Servlet Example – RequestDispatcher & Attribute Passing
**Date:** 18 August 2025  
This example demonstrates how to use **Servlets in Java** to handle client requests, pass data between servlets using **RequestDispatcher** and `setAttribute()`, and generate a dynamic response.  

## Flow of the Program
1. **HTML Form (`index.html`)**  
   - Takes two numbers as input from the user.  
   - Submits data to the `/add` servlet using the **GET** method.  
   - [View Code](index.html)  

2. **`AddServlet.java`**  
   - Reads input parameters (`num1`, `num2`) from the request.  
   - Adds the two numbers.  
   - Stores the result (`k`) as a request attribute.  
   - Forwards the request to the `SqServlet` using **RequestDispatcher**.  
3. **`SqServlet.java`**  
   - Retrieves the attribute (`k`) from the request.  
   - Squares the result.  
   - Sends the final output back to the client (browser).  
4. **`web.xml` (Deployment Descriptor)**  
   - Maps URLs (`/add` and `/sq`) to their respective servlet classes.  
   - Ensures the correct servlet is called based on the incoming request.  
## Key Points
- **RequestDispatcher** is used to forward the request from one servlet to another.  
- `setAttribute()` and `getAttribute()` are used to share data between servlets.  
- `web.xml` acts as a central configuration file for servlet mapping in the web application.  
- This example demonstrates **Servlet communication** and how to generate **dynamic responses**.
- Summary for this change:

**RequestDispatcher** → forwards same request, data lasts only for that request.
**HttpSession** → stores data for the session, survives across requests.
**sendRedirect()** → sends a new request, URL changes in the browser.


## Servlet Example – Using Cookies to Share Data Between Servlets
**Date:** 18 August 2025

It demonstrates how to use **Cookies** in Java Servlets to share data between multiple servlets. In this example, one servlet (`AddServlet`) adds two numbers and stores the result in a **cookie**, which is then read and squared by another servlet (`SqServlet`).
### What is a Cookie in Servlets?
- A **Cookie** is a small piece of data stored on the **client’s browser**.
- It is used to maintain **state** or **share information** between multiple requests or servlets.
- Unlike **HttpSession**, cookies can persist even after the browser is closed (if given a max age).
### How Cookies Work in This Example
1. **AddServlet**
   - Receives two numbers from the user via `request.getParameter()`.
   - Adds the numbers and stores the sum in a **cookie** named `"k"`.
   - Sends the cookie to the client using `res.addCookie(cookie)`.
   - Redirects the client to `SqServlet` using `res.sendRedirect("sq")`.
2. **SqServlet**
   - Retrieves all cookies from the request using `req.getCookies()`.
   - Finds the cookie named `"k"` and reads its value.
   - Squares the value and displays the result to the user.
   - Prints a message `"sq called"` on the server console for debugging.
### Key Points
- `res.sendRedirect("sq")` sends a **new request** to `SqServlet`, so cookies are used to preserve the value across requests.
- You could also use `RequestDispatcher.forward()` for **server-side forwarding** within the same request, but cookies are necessary when using redirect.
- Cookies store **strings**, so conversion to `int` is required for arithmetic operations.

---

## Flow of the Program
1. User enters two numbers in a form and submits to `AddServlet`.
2. `AddServlet` calculates the sum, stores it in a cookie `"k"`, and redirects to `SqServlet`.
3. `SqServlet` reads the cookie, squares the value, and displays the result.

---
## Code Snippets
### AddServlet.java
```java
public class AddServlet extends HttpServlet {
    public void doGet(HttpServletRequest req, HttpServletResponse res) 
            throws IOException, ServletException {
        int i = Integer.parseInt(req.getParameter("num1"));
        int j = Integer.parseInt(req.getParameter("num2"));
        int k = i + j;

        Cookie cookie = new Cookie("k", k + "");
        res.addCookie(cookie);
        res.sendRedirect("sq");
        // Alternative: Use RequestDispatcher to forward within same request
        // RequestDispatcher rd = req.getRequestDispatcher("sq");
        // rd.forward(req, res);
    }
}


# Introduction to JSP (Java Server Pages)
**Date:** 20 August 2025  
JSP (**Java Server Pages**) is a server-side technology used to create **dynamic web content** in Java. It allows developers to write HTML pages with embedded Java code. JSP is built on top of the **Servlet API**, and during execution, JSP pages are internally converted into Servlets by the server (like Apache Tomcat).  
## Why JSP?
- Easier to write and maintain compared to raw Servlets (less Java boilerplate).
- Allows mixing **HTML + Java code** using special JSP tags.
- Good for presentation logic (UI), while Servlets handle business logic.
- Supports **Expression Language (EL)** and **JSTL** for cleaner code.
## JSP Lifecycle
1. **Translation** → JSP is converted into a Servlet by the web container.  
2. **Compilation** → The generated Servlet is compiled into bytecode.  
3. **Loading & Initialization** → Servlet class is loaded and initialized.  
4. **Execution** → The `_jspService()` method executes to handle requests.  
5. **Destroy** → The container removes JSP from memory when not needed.  


# JSP Directives Example
**Date:** 24 August 2025  
JSP Directives provide special instructions to the JSP engine.  
They do not produce output directly but affect the overall page behavior.  

There are **three main JSP Directives**:  
1. Page Directive  
2. Include Directive  
3. Taglib Directive
## 1. Page Directive (`<%@ page ... %>`)

- Defines **page-level settings** like language, imports, and encoding.  
- Common attributes: `language`, `contentType`, `pageEncoding`, `import`.  

**Example in `home.jsp`:**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8" import="java.util.Random,java.util.ArrayList" %>


# JSP Implicit Objects

**Date:** 24 August 2025  

In JSP, **implicit objects** are pre-defined objects created by the JSP engine.  
They are available in JSP pages without the need for explicit declaration or creation.  

These objects make it easier to access request data, responses, session, application data, etc.  

---

## 📑 List of JSP Implicit Objects
1. **request** – Represents the HTTP request data (parameters, headers, cookies).  
   ```jsp
   String user = request.getParameter("username");
2.  **response** – Used to send response data to the client.
response.setContentType("text/html");
response.sendRedirect("home.jsp");

3.**out** – Writes output data to the client.
out.println("Welcome to JSP!");

4.**session** – Represents the user session (stores data across multiple requests).
session.setAttribute("username", "Neeraja");
String name = (String) session.getAttribute("username");

5.**application** – Refers to the ServletContext, shared across the entire web application.
application.setAttribute("appName", "JSPDemoApp");
String app = (String) application.getAttribute("appName");

6.**config** – Provides servlet configuration details.
String servletName = config.getServletName();

7.**pageContext** – Provides access to all JSP objects within the page.7
pageContext.include("header.jsp");
out.println(page.toString());

8**exception** – Available only in error pages, represents the exception object.
ut.println("Error: " + exception.getMessage());

##Summary
JSP provides 9 implicit objects.
They simplify development by offering direct access to request/response/session/application data.
No explicit declaration is needed — JSP engine automatically provides them.



