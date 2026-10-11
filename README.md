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
