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

6. Features Implemented
   
### R1 — Account Creation

The system allows new users to register by entering their name, email address, password, and password confirmation.

Before creating an account, the application checks that all required information has been provided. Passwords are hashed using bcrypt before they are saved in the database.

### R2 — Registration Error Handling

The registration process includes validation to prevent incomplete or invalid account creation. The system checks for missing fields, mismatched passwords, and email addresses that are already registered.

If an email address is already in use, the application informs the user with the message:

`Email Already Exists`

### R3 — User Authentication

Existing users can access their accounts by entering their email address and password.

The application retrieves the user's stored password hash and uses bcrypt to verify the entered password. If the login information is incorrect, the system displays the following message:

`Invalid email or password`

This message appears whether the email is not registered or the password is incorrect.

### R4 — Session Handling

Once a user successfully logs in or registers, the application saves their user ID and name in the session. The user ID stored in the session is then used to identify the authenticated user when accessing protected features.

The logout function clears the session and redirects the user to the login page.

### R5 — Personal To-Do List

After authentication, users can access their own task list. The application retrieves tasks from the database according to the user ID stored in the session.

This ownership-based filtering helps prevent users from viewing tasks belonging to other accounts.

### R6 — Creating Tasks

Users can add new tasks through the to-do page. The application checks that the task title is not blank and does not exceed 200 characters.

When a task is created, it is linked to the ID of the currently authenticated user.

### R7 — Updating Tasks

Users can modify the titles of their existing tasks and change their completion status.

Before applying an update, the database query checks both the task ID and the authenticated user's ID. This ensures that the update applies only to a task owned by that user.

### R8 — Task Completion

The application allows users to mark tasks as completed or reopen them by changing the completion checkbox.

The task's status is stored in the database in the `is_done` field, allowing the application to retrieve its current state later.

### R9 — Removing Tasks

Users can delete tasks from their personal lists. The deletion query checks both the task ID and the user's ID before removing a record.

This ownership check prevents a user from deleting a task belonging to another account through the application's normal task-management route.

### R10 — Security and Input Checks

Several security and validation techniques are used in the application:

- **Password protection:** bcrypt hashes passwords before they are stored.
- **SQL injection prevention:** parameterized SQL queries are used for database operations.
- **Authentication:** sessions are used to identify logged-in users.
- **Access control:** task updates and deletions check task ownership.
- **Input validation:** required fields and task-title length are checked on the server.
- **Configuration management:** environment variables are used to load database credentials and the Flask session secret.

The `.env` file should be excluded from Git so that database credentials and the session secret are not exposed in the repository.
