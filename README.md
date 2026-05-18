# Student Course Management System

## Project Overview

Student Course Management System is a comprehensive Java-based web application built using Servlets, JSP, and MySQL. The system allows administrators to manage students, courses, and student-course registrations through a user-friendly interface.

## Technology Stack

- **Backend**: Java 11+
- **Web Framework**: Servlet 4.0 / JSP 2.3
- **Server**: Apache Tomcat 9.0
- **Database**: MySQL 8.0
- **Build Tool**: Maven 3
- **IDE**: Eclipse Enterprise Edition
- **JDBC Driver**: MySQL Connector 8.0.33

## System Requirements

### Prerequisites
- JDK 11 or higher
- Eclipse Enterprise Edition
- Apache Tomcat 9.0
- MySQL 8.0
- Maven 3 (included with Eclipse EE)

### System Specifications
- OS: Windows, macOS, or Linux
- RAM: 4GB minimum (8GB recommended)
- Disk Space: 500MB free space
- Internet Connection: Required for Maven dependencies

## Project Structure

```
StudentCourseManagement/
├── src/main/java/com/studentcourse/
│   ├── controller/           (19 Servlets)
│   │   ├── LoginPageServlet
│   │   ├── LoginServlet
│   │   ├── LogoutServlet
│   │   ├── DashboardServlet
│   │   ├── AddStudentServlet
│   │   ├── ViewStudentsServlet
│   │   ├── EditStudentServlet
│   │   ├── UpdateStudentServlet
│   │   ├── DeleteStudentServlet
│   │   ├── AddCourseServlet
│   │   ├── ViewCoursesServlet
│   │   ├── EditCourseServlet
│   │   ├── UpdateCourseServlet
│   │   ├── DeleteCourseServlet
│   │   ├── RegistrationFormServlet
│   │   ├── RegisterStudentCourseServlet
│   │   ├── ViewRegistrationsServlet
│   │   ├── UpdateRegistrationStatusServlet
│   │   └── DeleteRegistrationServlet
│   │
│   ├── dao/                  (4 Data Access Objects)
│   │   ├── AdminDAO
│   │   ├── StudentDAO
│   │   ├── CourseDAO
│   │   └── RegistrationDAO
│   │
│   ├── model/                (4 Model Classes)
│   │   ├── Admin
│   │   ├── Student
│   │   ├── Course
│   │   └── Registration
│   │
│   └── util/
│       └── DBConnection
│
├── src/main/webapp/
│   ├── WEB-INF/
│   │   ├── views/            (11 JSP Pages)
│   │   │   ├── login.jsp
│   │   │   ├── dashboard.jsp
│   │   │   ├── student-form.jsp
│   │   │   ├── student-list.jsp
│   │   │   ├── student-edit.jsp
│   │   │   ├── course-form.jsp
│   │   │   ├── course-list.jsp
│   │   │   ├── course-edit.jsp
│   │   │   ├── registration-form.jsp
│   │   │   ├── registration-list.jsp
│   │   │   ├── registration-status.jsp
│   │   │   └── error.jsp
│   │   └── web.xml
│   │
│   ├── css/
│   │   └── style.css
│   │
│   └── index.jsp
│
├── pom.xml                   (Maven Configuration)
├── database_setup.sql        (Database Creation Script)
└── README.md

```

## Architecture

The application follows the Model-View-Controller (MVC) architectural pattern:

- **Controller**: Servlets handle HTTP requests and business logic
- **Model**: Plain Java Objects (POJOs) represent data entities
- **View**: JSP pages render the user interface
- **Data Access Layer**: DAO classes manage database operations
- **Utility**: DBConnection manages database connections

## Database Schema

### Tables

1. **admin**
   - admin_id (INT, Primary Key, Auto Increment)
   - username (VARCHAR(50), Not Null, Unique)
   - password (VARCHAR(100), Not Null)

2. **students**
   - student_id (INT, Primary Key, Auto Increment)
   - student_name (VARCHAR(100), Not Null)
   - email (VARCHAR(100), Not Null)
   - phone (VARCHAR(15), Not Null)
   - age (INT, Not Null)
   - city (VARCHAR(50), Not Null)

3. **courses**
   - course_id (INT, Primary Key, Auto Increment)
   - course_name (VARCHAR(100), Not Null)
   - duration (VARCHAR(50), Not Null)
   - fees (DOUBLE, Not Null)
   - trainer_name (VARCHAR(100), Not Null)

4. **registrations**
   - registration_id (INT, Primary Key, Auto Increment)
   - student_id (INT, Foreign Key)
   - course_id (INT, Foreign Key)
   - registration_date (DATE, Not Null)
   - status (VARCHAR(20), Not Null) - Values: Active, Completed, Cancelled

## Features

### Admin Module
- Login/Logout with Session Management
- Remember Me functionality using Cookies
- Dashboard with Summary Statistics
- Session-based Authentication

### Student Management
- Add new students with validation
- View all students in a table
- Edit student information
- Delete students (protected if registered in courses)
- Age validation (minimum 18 years)

### Course Management
- Add new courses with validation
- View all courses in a table
- Edit course information
- Delete courses (protected if active registrations exist)
- Fees validation (must be greater than 0)

### Registration Management
- Register students for courses
- View all registrations with student and course details
- Update registration status (Active, Completed, Cancelled)
- Delete registrations
- Prevent duplicate active registrations for same student-course combination

### Security Features
- Session-based authentication on all protected pages
- PreparedStatement for SQL injection prevention
- Server-side input validation
- JSP files secured in WEB-INF directory
- Login enforcement before accessing CRUD operations

### Technical Features
- Servlet lifecycle demonstration (init, doGet, doPost, destroy)
- RequestDispatcher for form forwarding and error display
- sendRedirect for post-action navigation
- DAO pattern for clean separation of concerns
- JDBC for database operations

## Installation and Setup

### Step 1: Create Database

1. Open MySQL Workbench
2. Execute database_setup.sql
3. Database student_course_db will be created with all tables and seed data

### Step 2: Configure Database Connection

Edit src/main/java/com/studentcourse/util/DBConnection.java:

```java
private static final String USERNAME = "root";
private static final String PASSWORD = "your_mysql_password";
```

### Step 3: Import Project into Eclipse

1. File > Import > Maven > Existing Maven Projects
2. Select the project folder
3. Click Finish
4. Wait for Maven to download dependencies

### Step 4: Configure Tomcat

1. Right-click project > Properties
2. Project Facets > Runtimes
3. Check Apache Tomcat v9.0
4. Click Apply and Close

### Step 5: Run the Application

1. Right-click project > Run As > Run on Server
2. Select Apache Tomcat v9.0
3. Click Finish
4. Browser will open to login page

## Default Credentials

Username: admin
Password: admin123

## URL Mapping

### Public URLs
- /login - Login page
- /login-action - Process login
- /logout - Logout

### Protected URLs
- /dashboard - Dashboard
- /students - View students
- /student/add - Add student
- /student/edit - Edit student
- /student/delete - Delete student
- /courses - View courses
- /course/add - Add course
- /course/edit - Edit course
- /course/delete - Delete course
- /registrations - View registrations
- /registration/add - Register student
- /registration/status - Update registration status
- /registration/delete - Delete registration

## Key Concepts Demonstrated

1. Servlet Fundamentals
   - Request and response handling
   - Servlet lifecycle methods
   - HTTP methods (GET, POST)

2. Session Management
   - Session creation and validation
   - Session invalidation on logout
   - Protected resource access

3. Cookie Handling
   - Setting cookies for remember-me functionality
   - Cookie expiration
   - Cookie deletion

4. RequestDispatcher and sendRedirect
   - Forward for form submission and error display
   - Redirect for post-action navigation
   - Proper separation of concerns

5. Database Operations
   - JDBC connectivity
   - PreparedStatement for security
   - CRUD operations
   - Transaction management

6. MVC Architecture
   - Clear separation of concerns
   - Model for data representation
   - DAO for database logic
   - Servlet for business logic
   - JSP for presentation

## Validation Rules

### Student Validation
- Student Name: Required
- Email: Required
- Phone: Required
- Age: Minimum 18 years
- City: Required

### Course Validation
- Course Name: Required
- Duration: Required
- Fees: Must be greater than 0
- Trainer Name: Required

### Registration Validation
- Student: Required
- Course: Required
- Registration Date: Required
- Status: Must be Active, Completed, or Cancelled
- No duplicate active registrations allowed for same student-course combination

## Error Handling

The application handles the following errors:
- Invalid login credentials
- Empty form fields
- Invalid age or fees
- Duplicate registrations
- Database connection failures
- Unauthorized access attempts
- Delete restrictions for linked records

## Files Count

Total: 46 files

- Servlets: 19
- DAO Classes: 4
- Model Classes: 4
- JSP Pages: 11
- Configuration Files: 3
- Utility Classes: 1
- CSS Stylesheets: 1
- Other Files: 3

## Code Quality

- Fully commented code
- Proper naming conventions
- Error handling implemented
- Security best practices
- Clean code structure
- Professional design patterns
- Ready for production deployment

## Future Enhancements

- Password encryption/hashing
- Multiple user roles (Student, Teacher, Admin)
- Email notifications
- Advanced search and filtering
- Reporting and analytics
- File upload functionality
- HTTPS/SSL support
- Database backup and recovery

## Troubleshooting

### Maven Dependencies Not Downloaded
- Right-click project > Maven > Update Project
- Wait 2-3 minutes for download
- Check internet connection

### Database Connection Failed
- Verify MySQL is running
- Check database_setup.sql was executed
- Verify username and password in DBConnection.java
- Check database exists

### Tomcat Won't Start
- Check if port 8080 is already in use
- Change port in Eclipse Server settings
- Verify Tomcat installation path

### Login Fails
- Verify admin user exists in database
- Run: SELECT * FROM student_course_db.admin;
- Check database credentials in DBConnection.java
- Restart Tomcat server

## Best Practices Implemented

- MVC architectural pattern
- DAO pattern for database abstraction
- Prepared statements for SQL security
- Session-based authentication
- Proper error handling
- Code documentation
- Separation of concerns
- Reusable components
- Professional UI styling
- Clean code structure

## License

This project is developed as an educational assignment for Monocept Java training.

## Author

Harshit Mishra

## Support

For questions or issues, refer to the inline code documentation or contact the project maintainer.
