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

## 4. Project Directory Structure

The application is organized into separate folders for database files, static resources, HTML templates, and configuration.

```text
project-root/
│
├── database/
│   └── schema.sql
│
├── screenshots/
│   ├── login page.png
│   ├── one marked as done.png
│   ├── phone screenshot.png
│   └── register page error.png
│
├── static/
│   └── style.css
│
├── templates/
│   ├── login.html
│   ├── register.html
│   └── todos.html
│
├── .env
├── .env.example
├── .gitignore
├── README.md
├── app.py
├── requirements.txt
└── setup.py
```

The `app.py` file contains the Flask routes and application logic. The `templates` directory stores the pages rendered by Flask, while `static/style.css` defines their appearance. The database directory contains the SQL schema used to create the application's tables.

The `.env` file stores configuration settings, including database connection details and the Flask session secret. The `.env.example` file can provide a template for configuring the application on another computer.

**Security note:** The actual `.env` file should not be published in a public repository because it may contain sensitive credentials. The repository should use `.gitignore` to exclude it.

---

## 5. Installation and Execution Guide

### Step 1 — Verify Python

Install Python if it is not already available. Open a terminal and check the installed version:

```bash
python --version
```

### Step 2 — Install Dependencies

Navigate to the project's root directory and install the packages listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

### Step 3 — Prepare the MySQL Database

Make sure the MySQL server is running. Create the database and tables using the project's SQL schema:

```bash
mysql -u root -p < database/schema.sql
```

Enter the MySQL password when prompted. This command assumes that the schema file contains the necessary database creation statements.

### Step 4 — Configure the Environment

Create a local `.env` file using `.env.example` as a template. On Windows, copy `.env.example` and rename the copy to `.env`.

Update the configuration values to match your MySQL installation:

```text
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_database_password
DB_NAME=registration
SESSION_SECRET=your_secret_key
```

Use your own database credentials and a strong, randomly generated session secret. Do not publish real passwords or secret values in the repository.

### Step 5 — Start the Application

From the project root, launch the Flask application:

```bash
python app.py
```

Open the local address displayed in the terminal in your browser to access the application.

# 6. Features Implemented

## R1 — Account Creation

The system allows new users to register by entering their name, email address, password, and password confirmation.

Before creating an account, the application checks that all required information has been provided. Passwords are hashed using bcrypt before they are saved in the database.

---

## R2 — Registration Error Handling

The registration process includes validation to prevent incomplete or invalid account creation. The system checks for missing fields, mismatched passwords, and email addresses that are already registered.

If an email address is already in use, the application displays the message:

`Email Already Exists`

---

## R3 — User Authentication

Existing users can access their accounts by entering their email address and password.

The application retrieves the stored password hash and uses bcrypt to verify the entered password. If the login information is incorrect, the system displays the following message:

`Invalid email or password`

This message is used whether the email is not registered or the password is incorrect.

---

## R4 — Session Handling

After a successful login or registration, the application stores the user's ID and name in the session. The user ID is then used to identify the authenticated user when accessing protected features.

The logout function clears the session and redirects the user to the login page.

---

## R5 — Personal To-Do List

After logging in, users can access their own task lists. The application retrieves tasks from the database using the user ID stored in the session.

This filtering helps prevent users from viewing tasks that belong to other accounts.

---

## R6 — Creating Tasks

Users can add new tasks through the to-do page. The application checks that the task title is not empty and does not exceed 200 characters.

Each new task is associated with the ID of the currently logged-in user.

---

## R7 — Updating Tasks

Users can edit the titles of their tasks and change their completion status.

Before updating a task, the database query checks both the task ID and the authenticated user's ID. This ensures that users can modify only their own tasks.

---

## R8 — Task Completion

Users can mark tasks as completed or change them back to incomplete using the completion checkbox.

The task's status is stored in the database in the `is_done` field, allowing the application to retrieve the current status later.

---

## R9 — Removing Tasks

Users can delete tasks from their personal lists. The deletion query checks both the task ID and the user's ID before removing the record.

This ownership check prevents users from deleting tasks belonging to other accounts through the application's normal task-management route.

---

## R10 — Security and Input Validation

The application uses several security measures and validation techniques:

- **Password protection:** bcrypt hashes passwords before they are stored.
- **SQL injection prevention:** parameterized SQL queries are used for database operations.
- **Session authentication:** sessions identify users who have logged in.
- **Access control:** task updates and deletions verify task ownership.
- **Input validation:** the application checks required fields and task-title length on the server.
- **Configuration management:** environment variables store database connection settings and the Flask session secret.

The `.env` file should be excluded from Git to protect database credentials and other sensitive configuration values.
