````markdown
# Student Course Management System

A web-based Java application developed using Servlets, JSP, JDBC, and MySQL to manage students, courses, and registrations efficiently.

---

## Technologies Used

- Java
- Servlets
- JSP
- JDBC
- MySQL
- Apache Tomcat 9
- Maven
- HTML
- CSS

---

## Features

### Admin Module
- Admin Login
- Session Management
- Logout Functionality
- Remember Username using Cookies

### Student Module
- Add Student
- View Students
- Update Student
- Delete Student

### Course Module
- Add Course
- View Courses
- Update Course
- Delete Course

### Registration Module
- Register Student to Course
- View Registrations
- Update Registration Status
- Delete Registration

---

## Project Structure

StudentCourseManagement
│
├── src/main/java
│ └── com.studentcourse
│ ├── controller
│ ├── dao
│ ├── model
│ └── util
│
├── src/main/webapp
│ ├── WEB-INF
│ │ ├── views
│ │ └── web.xml
│ └── css
│
├── pom.xml
└── database_setup.sql

---

## Database Configuration

### Database Name

```sql
student_course_db
````

### Update Database Credentials

Update database username and password inside:

```text
DBConnection.java
```

Example:

```java
DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/student_course_db",
    "root",
    "root"
);
```

---

## How to Run the Project

1. Clone the repository

```bash
git clone <repository-url>
```

2. Import the project as an Existing Maven Project in Eclipse

3. Configure Apache Tomcat 9 Server

4. Create MySQL database

5. Import `database_setup.sql`

6. Update database credentials in `DBConnection.java`

7. Run the project on Tomcat Server

8. Open browser and visit:

```text
http://localhost:8080/StudentCourseManagement/login
```

---

## Default Admin Credentials

```text
Username: admin
Password: admin123
```

---

## Concepts Implemented

* MVC Architecture
* CRUD Operations
* JDBC Connectivity
* Session Handling
* Cookies
* RequestDispatcher
* Servlet Lifecycle
* Form Validation

---

## Author

Harshit Mishra

```
```
