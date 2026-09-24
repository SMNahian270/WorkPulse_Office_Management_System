# WorkPulse – Office Management System

A full-stack, role-based office management system built with **PHP, JavaScript, HTML, CSS, and MySQL**, designed to be hosted on an **Apache** server. WorkPulse streamlines task delegation and progress tracking across four user roles: **Admin, Manager, Team Leader, and Employee**.

---

## 📌 Table of Contents

1. [Features](#-features)
2. [Tech Stack](#-tech-stack)
3. [Project Structure](#-project-structure)
4. [Database Schema](#-database-schema)
5. [User Roles & Permissions](#-user-roles--permissions)
6. [Installation & Setup](#️-installation--setup)
7. [How to Run with Apache](#️-how-to-run-with-apache)
8. [Default Login Credentials](#-default-login-credentials)
9. [How the System Works](#-how-the-system-works)
10. [Security Notes](#-security-notes)
11. [Known Limitations](#️-known-limitations)
12. [Author](#️-author)

---

## 🚀 Features

- **Role-Based Access Control (RBAC)** — Admin, Manager, Team Leader, and Employee each get a dedicated dashboard and set of actions.
- **Hierarchical Task Assignment** — Managers assign tasks to Team Leaders, who further break them into subtasks for Employees.
- **Task Lifecycle Tracking** — Every task moves through `pending → in_progress → completed`.
- **Deadline Management** — Filter tasks by *Due Today*, *Overdue*, and *No Deadline*.
- **Status Dashboard** — Live counters for total tasks, pending, in-progress, completed, overdue, and due today.
- **In-App Notifications** — Automatic alerts when a task is assigned, reassigned, or its status is updated.
- **User Management (Admin)** — Add, edit, delete users, reset passwords, and manage roles.
- **Profile Management** — All users can update their full name and password.
- **AJAX Username Availability Check** — Real-time feedback during registration.
- **Session-Based Authentication** — Secure login/logout with role-based redirects.
- **Responsive Sidebar UI** — Collapsible navigation using pure CSS (checkbox toggle).

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | HTML5, CSS3, JavaScript (DOM, AJAX) |
| Backend | PHP (OOP, MVC-inspired structure) |
| Database | MySQL (PDO with prepared statements) |
| Server | Apache (XAMPP) |
| Icons | Font Awesome 4.7 |
| Fonts | Google Fonts (Libre Baskerville, Poppins, etc.) |

---

## 📁 Project Structure

```
WorkPulse/
│
├── Common/
│   ├── Controller/
│   │   ├── HandleAjax.php
│   │   ├── LoginController.php
│   │   ├── LogoutController.php
│   │   └── RegistrationController.php
│   ├── Model/
│   │   ├── Database.php
│   │   └── User.php
│   └── View/
│       ├── css/style.css
│       ├── checkUsername.js
│       ├── reg.js
│       ├── login.php
│       └── registration.php
│
├── Admin/
│   ├── Controller/
│   │   ├── AddTaskController.php
│   │   ├── AddUserController.php
│   │   ├── ChangePasswordController.php
│   │   ├── DeleteTaskController.php
│   │   ├── DeleteUserController.php
│   │   ├── UpdateProfileController.php
│   │   ├── UpdateTaskController.php
│   │   └── UpdateUserController.php
│   ├── Model/
│   │   ├── NotificationModel.php
│   │   ├── TaskModel.php
│   │   └── UserModel.php
│   └── View/
│       ├── css/style.css
│       ├── img/user.png
│       ├── add-user.php
│       ├── create-task.php
│       ├── dashboard.php
│       ├── edit-profile.php
│       ├── edit-task.php
│       ├── edit-user.php
│       ├── header.php
│       ├── nav.php
│       ├── notifications.php
│       ├── profile.php
│       ├── tasks.php
│       └── user.php
│
├── Manager/
│   ├── Mcontroller/
│   │   ├── DashboardController.php
│   │   ├── TaskController.php
│   │   └── taskValidation.js
│   ├── Mmodel/
│   │   ├── Monitor.php
│   │   └── Task.php
│   └── Mview/
│       ├── style.css
│       ├── create-task.php
│       ├── dashboard.php
│       ├── edit-profile.php
│       ├── edit-task.php
│       └── task-list.php
│
├── Team_Leader/
│   ├── Controller/
│   │   ├── ProfileController.php
│   │   └── TaskController.php
│   ├── Model/
│   │   ├── Notification.php
│   │   ├── Task.php
│   │   └── User.php
│   └── View/
│       ├── css/style.css
│       ├── img/user.png
│       ├── create-subtask.php
│       ├── dashboard.php
│       ├── edit-profile.php
│       ├── edit-subtask.php
│       ├── header.php
│       ├── nav.php
│       ├── notifications.php
│       ├── profile.php
│       ├── tasks.php
│       └── team-tasks.php
│
├── Employee/
│   ├── Controller/
│   │   ├── UpdateProfileController.php
│   │   └── UpdateTaskStatusController.php
│   ├── Model/
│   │   ├── NotificationModel.php
│   │   ├── TaskModel.php
│   │   └── UserModel.php
│   └── View/
│       ├── css/style.css
│       ├── img/user.png
│       ├── dashboard.php
│       ├── edit_profile.php
│       ├── edit-task-employee.php
│       ├── header.php
│       ├── my_task.php
│       ├── nav.php
│       ├── notifications.php
│       └── profile.php
│
└── taskflow_db.sql
```

## 👥 User Roles & Permissions

### 🔴 Admin
- Manage all users (add, edit, delete, reset password)
- Create tasks and assign to any user
- View all tasks across the system
- View full system activity log (all notifications)
- Edit own profile & change password

### 🟠 Manager
- Create tasks and assign to Team Leaders
- View all tasks they created
- Edit / delete their own tasks
- Dashboard with statistics (total, pending, in-progress, completed, overdue, due today)
- Edit own profile

### 🟡 Team Leader
- View tasks assigned by Managers
- Break down manager tasks into subtasks for Employees
- Edit / delete their own subtasks
- Monitor employee progress with filters (Due Today, Overdue, No Deadline)
- Receive notifications on new assignments
- Edit own profile & password

### 🟢 Employee
- View tasks assigned to them
- Update task status (`pending → in_progress → completed`)
- Filter their tasks (Due Today, Overdue, No Deadline)
- Receive notifications when tasks are assigned or reassigned
- Edit own profile & password

---

## ⚙️ Installation & Setup

### Prerequisites
- **XAMPP** (or WAMP / LAMP) with **Apache** and **MySQL** installed
- **PHP 7.4+** (PHP 8.x recommended)
- **MySQL 5.7+**
- A modern web browser (Chrome, Firefox, Edge)

## ▶️ How to Run with Apache

Once the above setup is done, open your browser and navigate to:

```
http://localhost/WorkPulse/Common/View/login.php
```

You will see the **WorkPulse login page**. Log in with one of the credentials below based on the role you want to test.

> **Note:** Each role lands on a different dashboard automatically after login, thanks to the role-based redirect inside `LoginController.php`.

---


You can also register a new account as **Manager**, **Team Leader**, or **Employee** from the registration page (Admin accounts can only be created by an existing Admin).

---

## 🔄 How the System Works

1. **Registration / Login**
   - New users register via `registration.php`. Username availability is checked live via AJAX (`checkUsername.js` → `HandleAjax.php`).
   - On successful login, `LoginController.php` stores session data (`role`, `id`, `username`, `full_name`) and redirects the user to their role-specific dashboard.

2. **Task Creation Flow**
   - **Admin** or **Manager** creates a task → task stored in `tasks` table with `parent_task_id = NULL`.
   - A notification is inserted for the assignee.

3. **Subtask Delegation Flow**
   - **Team Leader** opens *Assigned Tasks* → clicks **Assign to Employee** → creates a subtask with `parent_task_id` pointing to the manager's task.
   - Employee gets a notification.

4. **Progress Update Flow**
   - **Employee** opens *My Tasks* → clicks **Update Status** → changes status to `pending`, `in_progress`, or `completed`.
   - The system notifies the person who assigned the task.

5. **Monitoring Flow**
   - **Admin** sees system-wide stats.
   - **Manager** sees stats for tasks they created.
   - **Team Leader** sees stats for subtasks they assigned.
   - **Employee** sees stats for their own tasks.
   - All roles can filter by *Due Today*, *Overdue*, and *No Deadline*.

6. **Notifications**
   - Each role has a `notifications.php` page.
   - Employees and Team Leaders see only their own notifications.
   - Admin sees all notifications (system-wide activity log).

---

## 🔒 Security Notes

This project was built for **academic purposes** and includes the following security measures:

- ✅ PDO **prepared statements** for all database queries (prevents SQL injection).
- ✅ `htmlspecialchars()` and `stripslashes()` used on user inputs and outputs (prevents XSS).
- ✅ Session-based authentication with role checks on every protected page.
- ✅ Ownership checks before edit/delete operations (users can only modify their own records).
- ✅ Server-side + client-side validation on all forms.

⚠️ **Important:** Passwords are currently stored in **plain text** in the database to keep the project simple for demonstration. In a real production system, you should use `password_hash()` and `password_verify()`.

---

## ⚠️ Known Limitations

- Passwords are stored in plain text (see above).
- No email verification or password reset via email.
- No file uploads or attachments for tasks.
- No pagination on tables (fine for small datasets).
- Admin cannot delete their own account (by design).
- Tasks with subtasks cannot be deleted until subtasks are removed or reassigned.

---

## ✍️ Author

**WorkPulse** — Office Management System
Developed as a **Web Technology** course project at **AIUB**.
**Timeline:** August 2026 – September 2026

---

## 📜 License

This project is intended for **educational use only**. Feel free to fork, modify, and learn from it.
