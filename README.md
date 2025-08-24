# 📚 SL Tech EdTech Backend System

🔗 **GitHub Repository:** [mlordjames/edtech_backend_system](https://github.com/mlordjames/edtech_backend_system)

A lightweight, object-oriented backend system designed for **EdTech platforms**.  
This project implements user management, course management, and enrollments in a structured, extensible way.  
It also includes a **command-line interface (CLI)** for interacting with the system.

---

## 🚀 Features

- **User Management**
  - Create Learners and Instructors.
  - Update user email and password securely.
  - Validate login credentials.

- **Learner Functionalities**
  - Enroll in courses.
  - Drop courses.
  - View enrolled courses.

- **Instructor Functionalities**
  - Add and remove courses they teach.
  - View courses they are assigned to.

- **Course Management**
  - Create and delete courses.
  - Assign instructors to courses.
  - List learners enrolled in a course.

- **Enrollment Management**
  - Track learner enrollments with unique IDs.
  - Handle active, dropped, and completed enrollments.

- **Interactive CLI**
  - Add users, courses, and enrollments through a user-friendly terminal menu.
  - Generate reports and summaries of the system state.

---

## 🏗️ Project Structure

```bash
.
├── edtech_backend.py   # Main script with all classes and CLI menu
├── README.md           # Project documentation (this file)
```

Key Classes:
- `User` → Base class for all users (attributes: `id`, `name`, `email`, `role`).
- `Learner(User)` → Inherits from `User`; supports enrollment actions.
- `Instructor(User)` → Inherits from `User`; supports course management.
- `Course` → Represents a course with instructor and learner registry.
- `Enrollment` → Tracks learner enrollment in a course with status.
- `SLTechBackend` → Core orchestrator managing all users, courses, and enrollments.

---

## 🛠️ Installation & Setup

### 1. Clone Repository
```bash
git clone https://github.com/mlordjames/edtech_backend_system.git
cd edtech-backend-system
```

### 2. Run Script
Ensure you have **Python 3.8+** installed.

```bash
python edtech_backend.py
```

---

## 💻 Usage (Interactive Menu)

Once you run the script, you’ll see:

```
=== SL Tech EdTech Backend (In-Memory) ===

Select an option:
 1) Add Learner
 2) Add Instructor
 3) Add Course
 4) Assign Instructor to Course
 5) Enroll Learner in Course
 6) Drop Learner from Course
 7) List Enrolled Learners (by Course)
 8) List Courses for Learner
 9) List Courses for Instructor
10) Find User by Email & Validate Login
11) Update User Email
12) Update User Password
13) Show Summary
 0) Exit
```

Example flow:
1. Add an **Instructor**.  
2. Add a **Course** (and optionally assign that instructor).  
3. Add a **Learner**.  
4. Enroll the learner in the course.  
5. List learners in that course.  

---

## 📖 Example Walkthrough

```bash
1) Add Instructor
Instructor Name: Dr. Ada Lovelace
Instructor Email: ada@example.com
Password (hidden): ****
Created Instructor: Dr. Ada Lovelace | id=123e4567

2) Add Learner
Learner Name: John Doe
Learner Email: john@example.com
Password (hidden): ****
Created Learner: John Doe | id=456e7890

3) Add Course
Course Title: Introduction to Python
Course Description: Learn Python basics.
Instructor ID: 123e4567
Created Course: Introduction to Python | id=course123

5) Enroll Learner in Course
Learner ID: 456e7890
Course ID: course123
Enrolled. enrollment_id=enroll567

7) List Enrolled Learners (by Course)
Learners in course course123:
 - John Doe (456e7890)
```

---

## 🧪 Testing the System Programmatically

Instead of the CLI, you can use the classes directly in Python:

```python
from edtech_backend import SLTechBackend

backend = SLTechBackend()

# Add users
inst = backend.add_instructor("Ada Lovelace", "ada@example.com", "password123")
learner = backend.add_learner("John Doe", "john@example.com", "pass456")

# Add course
course = backend.add_course("Intro to Python", "Learn the basics", inst.user_id)

# Enroll learner
enrollment = backend.enroll(learner.user_id, course.course_id)

print(backend.summary())
# Output: Users: 2 (Learners=1, Instructors=1) | Courses: 1 | Enrollments: 1
```

---

## 📦 Extensibility

This project is built with **OOP principles** and can be extended with:
- 🔐 Authentication (hashed passwords, JWT tokens, etc.)
- 🗄️ Database integration (SQLite, PostgreSQL, MongoDB).
- 🌐 REST API layer (Flask/Django/FastAPI).
- 🧑‍💻 Admin dashboard with analytics.

---

## 📋 Requirements

- Python 3.8+
- No external dependencies (pure standard library).  
- Optional: `reportlab` if you want to export results or code to PDF.

---

## 👨‍💻 Author

**Etiese James**  
- 🌐 GitHub: [@mlordjames](https://github.com/mlordjames)  
- ✉️ Email: jamesetiese@gmail.com  

---

## 📜 License

This project is licensed under the **MIT License** – you’re free to use, modify, and distribute.
