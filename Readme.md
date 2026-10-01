# 🐧 Linux Students Portal

<p align="center">
  <img src="https://img.shields.io/badge/Shell-Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white" alt="Bash"/>
  <img src="https://img.shields.io/badge/Platform-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux"/>
  <img src="https://img.shields.io/badge/Course-COMP311-blue?style=for-the-badge" alt="COMP311"/>
</p>

<p align="center">
  A modular Bash-based student management system — add, modify, search, and
  list student records stored in a plain text file.
</p>

---

## 📖 About the Project

Linux Students Portal is a command-line admin tool built entirely with
**Bash shell scripting**. It manages a flat-file "database" of students,
with full input validation (ID format, date format, duplicate checks) and
auto-generated email addresses — all without any external language or
database engine, as part of a Linux systems/scripting course.

---

## ✨ Features

- ➕ **Add Student**
  - Enforces a unique 4-digit student ID (rejects duplicates and malformed input)
  - Validates date of birth format (`dd/mm/yyyy`)
  - Auto-generates an email address from the first name + last two ID digits
    (e.g. `ahmad_34@birzeit.edu`)
- ✏️ **Modify Student**
  - Delete a student by ID
  - Update a student's full name or date of birth (with the same validation rules)
- 🔍 **Search Student**
  - Search by exact ID
  - Search by full or partial first/last name, with results sorted by first name
- 📋 **List Students**
  - Sorted by ID
  - Sorted by full name
  - Sorted by date of birth (duplicates collapsed to one entry)

---

## 🗂️ Project Structure

```
LinuxStudentsPortal/
├── StudentsPortal        # Main menu — entry point of the program
├── addStudent            # Handles adding new student records
├── modifyStudent         # Handles deleting/updating student records
├── searchStudent         # Handles searching by ID or name
├── listStudents          # Handles listing/sorting students
├── students.sample       # Sample data file (plain-text records)
└── README.md
```

Each student record is stored as a single line in the data file, in the
format:
```
id:Full Name:dd/mm/yyyy:email@birzeit.edu
```

---

## 🛠️ Technologies Used

- **Bash** (shell scripting)
- Core Unix text-processing tools: `grep`, `cut`, `sort`, `case`
- Plain-text file storage (no database)

---

## ▶️ How to Run

> Requires a Unix-like environment (Linux, macOS, or WSL/Git Bash on Windows).

1. **Clone the repository**
   ```bash
   git clone https://github.com/A7mcdd/LinuxStudentsPortal.git
   cd LinuxStudentsPortal
   ```

2. **Make the scripts executable**
   ```bash
   chmod +x StudentsPortal addStudent modifyStudent searchStudent listStudents
   ```

3. **Run the main menu**
   ```bash
   ./StudentsPortal
   ```

4. Follow the on-screen menu to add, modify, search, or list students.
   All data is read from and written to the local `students` data file in
   the same directory (copy `students.sample` to `students` to try it out
   with sample data).

---

## 🧠 Notes on Design

- The project is split into **four independent scripts** (one per core
  feature) called from a single main menu script, keeping each piece of
  logic modular and easy to maintain/test on its own.
- Input validation uses Bash `case` pattern matching to enforce exact
  formats (4-digit IDs, `dd/mm/yyyy` dates) and re-prompts the user until
  valid input is given.
- `students.sample` contains placeholder/test data only — no real personal
  information.