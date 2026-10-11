# Login and To-Do Management System

A web-based Login and To-Do Management System developed for **Database Systems Lab 2**. The project provides user registration and authentication, allowing users to create, update, complete, and delete their personal tasks. The application connects to a MySQL database through a Flask backend and ensures that task operations are associated with the currently logged-in user.

---

## 1. Team Members

| Name | Student ID | Responsibilities |
|---|---|---|
| Dina Ibrahim Ebeid | 2304144 | Backend development, user authentication, task management, input validation, and application integration. |
| Mohab Mohamed | 2304077 | Database design, frontend development, interface styling, testing, and project documentation. |

*The responsibilities above are a suggested division. Adjust them to reflect the work each team member actually completed.*

---

## 2. Technologies and Tools

### Backend Technologies
- **Python:** Implements the application's main logic.
- **Flask:** Handles HTTP requests, routes, sessions, and page rendering.
- **PyMySQL:** Connects the Flask application to the MySQL database.
- **bcrypt:** Hashes passwords and verifies login credentials.
- **python-dotenv:** Loads configuration values from environment variables.

### Frontend Technologies
- **HTML:** Defines the structure of the web pages.
- **CSS:** Controls the layout, colors, and visual appearance.
- **Jinja2:** Generates dynamic HTML pages using data supplied by Flask.

### Database
- **MySQL:** Stores user account information and to-do items.

---

## 3. Main Application Features

- User registration and login.
- Secure password hashing.
- Individual task lists for each user.
- Adding new tasks.
- Editing task titles.
- Marking tasks as completed or incomplete.
- Deleting tasks.
- Validation of required fields and task title length.
- A responsive, customized user interface.
