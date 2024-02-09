# ServletAPI

Below is a simple tutorial on how to create a JSP servlet:

### 1. **Setup Your Development Environment:**
   Make sure you have Java and a servlet container like Apache Tomcat installed on your system.

### 2. **Create a Dynamic Web Project:**
   Start a new dynamic web project in your preferred IDE (Eclipse, IntelliJ IDEA, or others). Configure your project to include the necessary servlet container libraries.

### 3. **Create a JSP File:**
   Create a new JSP file (e.g., `index.jsp`) in the `WebContent` directory of your project. This file will contain the HTML and JSP code.

   ```jsp
   <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="UTF-8">
       <title>JSP Servlet Tutorial</title>
   </head>
   <body>
       <h1>Hello, <%= request.getParameter("name") %></h1>
   </body>
   </html>
   ```

   This simple JSP file displays a greeting message with the value of the "name" parameter from the request.

### 4. **Create a Servlet Class:**
   Create a servlet class (e.g., `HelloServlet.java`) that handles the logic and forwards the request to the JSP page.

   ```java
   import java.io.IOException;
   import javax.servlet.ServletException;
   import javax.servlet.annotation.WebServlet;
   import javax.servlet.http.HttpServlet;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;

   @WebServlet("/HelloServlet")
   public class HelloServlet extends HttpServlet {
       private static final long serialVersionUID = 1L;

       protected void doGet(HttpServletRequest request, HttpServletResponse response)
               throws ServletException, IOException {
           // Set the content type
           response.setContentType("text/html");

           // Forward the request to the JSP page
           request.getRequestDispatcher("/index.jsp").forward(request, response);
       }
   }
   ```

### 5. **Configure Servlet in `web.xml` (Optional for Servlet 3.0+):**
   If you are not using Servlet 3.0 annotations, configure your servlet in the `web.xml` file.

   ```xml
   <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
            version="3.1">

       <servlet>
           <servlet-name>HelloServlet</servlet-name>
           <servlet-class>com.example.HelloServlet</servlet-class>
       </servlet>

       <servlet-mapping>
           <servlet-name>HelloServlet</servlet-name>
           <url-pattern>/HelloServlet</url-pattern>
       </servlet-mapping>

   </web-app>
   ```

### 6. **Run Your Application:**
   Deploy your web application to a servlet container, start the server, and access your servlet (e.g., http://localhost:8080/your-web-app-context/HelloServlet?name=John).

### 7. **Explore JSP Features:**
   Explore additional JSP features, such as JSP expressions, declarations, and directives. You can use Java code directly in your JSP pages.

This is a basic tutorial to get you started with JSP and servlets. As you progress, you can explore more advanced topics such as session management, JSP custom tags, and MVC patterns for building robust web applications.
