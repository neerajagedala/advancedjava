## Servlet Example – RequestDispatcher & Attribute Passing  
**Date:** 18 August 2025  
This example demonstrates how to use **Servlets in Java** to handle client requests, pass data between servlets using **RequestDispatcher** and `setAttribute()`, and generate a dynamic response.  

## Complete Code Example  

### 1. `index.html`
```html
<!DOCTYPE html>
<html>
<body>
  <form action="add" method="get">
    Enter 1 number: <input type="text" name="num1"><br>
    Enter 2 number: <input type="text" name="num2"><br>
    <input type="submit">
  </form>
</body>
</html>
package com.servlet;

import java.io.IOException;
import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class AddServlet extends HttpServlet {
    public void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException, ServletException {
        int i = Integer.parseInt(req.getParameter("num1"));
        int j = Integer.parseInt(req.getParameter("num2"));
        int k = i + j;

        req.setAttribute("k", k);

        RequestDispatcher rd = req.getRequestDispatcher("sq");
        rd.forward(req, res);
    }
}
package com.servlet;

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class SqServelet extends HttpServlet {
    public void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException {
        int k = (int) req.getAttribute("k");
        k = k * k;

        PrintWriter out = res.getWriter();
        out.println("Result is " + k);
    }
}
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
         xmlns="http://xmlns.jcp.org/xml/ns/javaee" 
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee 
         http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" 
         id="WebApp_ID" version="4.0">

  <servlet>
    <servlet-name>abc</servlet-name>
    <servlet-class>com.servlet.AddServlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>abc</servlet-name>
    <url-pattern>/add</url-pattern>
  </servlet-mapping>  

  <servlet>
    <servlet-name>pqr</servlet-name>
    <servlet-class>com.servlet.SqServelet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>pqr</servlet-name>
    <url-pattern>/sq</url-pattern>
  </servlet-mapping>  

</web-app>


## Servlet Example – RequestDispatcher & Attribute Passing  
**Date:** 16 August 2025  
This example demonstrates how to use **Servlets in Java** to handle client requests, pass data between servlets using **RequestDispatcher** and `setAttribute()`, and generate a dynamic response.  

## Flow of the Program
1. **HTML Form (`index.html`)**  
   - Takes two numbers as input from the user.  
   - Submits data to the `/add` servlet using the **GET** method

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
RequestDispatcher → forwards same request, data lasts only for that request.
HttpSession → stores data for the session, survives across requests.
HttpSession session = req.getSession();
int k = (int) session.getAttribute("k");
sendRedirect() → sends a new request, URL changes in the browser.

