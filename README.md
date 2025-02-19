# Ex01 – Environment Setup

## Module Sevlet Application HelloWorld
Viết ứng dụng HelloWorld gồm

•	1 Java class,

•	1 page JSP nhập tên user,

•	1 JSP hiển thị lời chào (khởi tạo bởi Java class)

## Mục lục

- [Giới thiệu](#giới-thiệu)
- [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)
- [Cài đặt và sử dụng](#cài-đặt-và-sử-dụng)
- [Liên hệ](#liên-hệ)

## Giới thiệu

Bài kiểm tra Environment Setup hướng dẫn tạo Sevlet.

## Yêu cầu hệ thống

- JDK >= 17 (19,21 recommended)
- Intellij IDEA >= 2020.3 (MAX-VERSION recomended)
- Tomcat 10 recomended

## Cài đặt và sử dụng

### Với người sử dụng dự án của tôi

1. Clone Repository
   ```sh
   https://github.com/nghiabeoniamey/ex01-environment-setup.git
   ```

2. Mở project với Intellij IDEA (đợi Intellij IDEA load dự án Maven)

3. Sau khi load dự án Maven xong, nhấn liên tục 2 lần `Shift` search keyword `Edit Configuration`

4. Chọn `Add New Configuration` => chọn `Tomcat Server / Local`

5. Configuration Application Server bằng Tomcat (ở đây mh chọn Tomcat 10)

6. Chọn `Deployment`, Chọn `Artifact: war exploded`

7. Chỉnh Application context: `/`, Chọn `APPLY` => `OK` => `Run Tomcat` OR `Shift + F10`

### Start to Zero

1. Đảm bảo setup đầy đủ yêu cầu hệ thống [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)

2. Mở `IntelliJ IDEA` - `New Project`

3. Tại menu `Generators` Chọn `Jakarta EE`

4. Setup Jakarta EE
    ```txt
    Name: ...
    Location: ...
    Template: Web application
    Application Server: No application Server
    Language: Java
    Build system: Maven OR Gradle (Chọn 1 trong 2)
    Group: ...
    Artifact: ...
    JDK: Chọn JDK 17 - 19 - 21 Khuyến khích
    ```
    ```
    Chọn Next
    Chọn Jakarta EE 9.1
    Chọn Create
    ```
5. Load Project, check file pom or gradle
    ```
    jakarta.servlet-api
    junit-jupiter-api: for test
    junit-jupiter-engine: for test
    ```
6. Sau khi load dự án Maven xong, nhấn liên tục 2 lần `Shift` search keyword `Edit Configuration`

7. Chọn `Add New Configuration` => chọn `Tomcat Server / Local`

8. Configuration Application Server bằng Tomcat (ở đây mh chọn Tomcat 10)

9. Chọn `Deployment`, Chọn `Artifact: war exploded`

10. Chỉnh Application context: `/`, Chọn `APPLY` => `OK`
11. Cấu hình file code
    >HelloServlet
    ```java
    import jakarta.servlet.annotation.WebServlet;
    import jakarta.servlet.http.HttpServlet;
    import jakarta.servlet.http.HttpServletRequest;
    import jakarta.servlet.http.HttpServletResponse;

    import java.io.IOException;
    import java.io.PrintWriter;

    @WebServlet(name = "helloServlet", value = "/hello-servlet")
    public class HelloServlet extends HttpServlet {
        private String message;

        public void init() {
            message = "Hello ";
        }

        public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
            String name = request.getParameter("name");
            response.setContentType("text/html");

            // Hello
            PrintWriter out = response.getWriter();
            out.println("<html><body>");
            out.println("<h1>" + message + name + "</h1>");
            out.println("</body></html>");
        }

        public void destroy() {
        }
    }
    ```
    >index.jsp
    ```
    <%@ page contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" %>
    <!DOCTYPE html>
    <html>
    <head>
        <title>JSP - Hello World</title>
    </head>
    <body>
    <form action="/hello-servlet" method="get">
        Tên User:
        <input type="text" name="name"/>
        <button type="submit">Đăng Nhập Hệ Thống</button>
    </form>
    </body>
    </html>
    ```
12. `Run Tomcat` OR `Shift + F10`
## Liên hệ

Nếu bạn có bất kỳ câu hỏi nào, vui lòng liên hệ qua email nghiabe.dev@gmail.com.