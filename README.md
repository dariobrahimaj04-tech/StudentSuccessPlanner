# Student Success Planner

## Project Overview
Student Success Planner is a JavaFX desktop application designed to help students organize and manage their academic tasks, track grades, and calculate course averages. The application demonstrates object-oriented programming principles including inheritance, polymorphism, and encapsulation.

## Features

### ✨ Core Functionality
- **Add Tasks**: Create assignments, exams, or projects with course name, task name, grade, and due date
- **Task Management**: View all tasks in an organized list with detailed information
- **Grade Tracking**: Automatically calculate and display average grades
- **Task Deletion**: Remove individual tasks with success confirmation
- **Clear All**: Bulk delete all tasks with a safety confirmation dialog
- **File Operations**: Save and load tasks to/from `tasks.txt`

### 🛡️ Input Validation
- **Empty Field Checks**: Prevents blank course names, task names, or due dates
- **Grade Validation**: Ensures grades are valid numbers between 0-100
- **Date Format Validation**: Enforces MM/DD/YYYY format using regex patterns
- **Robust Error Handling**: Clear, user-friendly error messages for all validation failures

### 💾 File Handling
- **Safe Loading**: Gracefully handles corrupted or missing data in `tasks.txt`
- **Malformed Line Skipping**: Continues loading valid tasks even if some lines are invalid
- **Error Reporting**: Displays success count and number of skipped lines to the user
- **Data Persistence**: All tasks saved in CSV format for easy portability

### 📊 Automatic Updates
- Average grade updates automatically after adding, deleting, or loading tasks
- Task count updates in real-time
- No manual recalculation needed

### 🎨 Professional GUI Design
- Modern, clean interface with intuitive layout
- Color-coded buttons (blue primary, gray secondary, red danger)
- Responsive design with appropriate spacing and typography
- Professional styling with rounded corners and shadows

## Project Structure

```
studentsuccessplanner/
├── StudentSuccessPlanner.java  (Main GUI application)
├── SchoolTask.java            (Base class for all tasks)
├── Assignment.java            (Assignment subclass)
├── Exam.java                  (Exam subclass)
├── ProjectTask.java           (Project subclass)
└── README.md                  (This file)
```

## Object-Oriented Design

### Inheritance Hierarchy
```
SchoolTask (abstract parent)
├── Assignment
├── Exam
└── ProjectTask
```

### Key Classes

**SchoolTask** (Parent Class)
- Protected fields: courseName, taskName, grade, dueDate
- Provides common functionality for all task types
- Defines template methods: `getTaskType()`, `getPriorityMessage()`

**Assignment, Exam, ProjectTask** (Child Classes)
- Extend SchoolTask with specialized implementations
- Override methods to provide task-specific behavior
- Demonstrate polymorphism through different priority messages

## Getting Started

### Requirements
- Java 11 or higher
- JavaFX SDK (included in most NetBeans distributions)
- Apache NetBeans IDE (recommended)

### Running the Application

1. **In NetBeans:**
   - Create a new JavaFX project
   - Copy all `.java` files to the project source folder
   - Set up JavaFX libraries in project properties
   - Run `StudentSuccessPlanner.java`

2. **From Command Line:**
   ```bash
   javac --module-path /path/to/javafx-sdk/lib --add-modules javafx.controls *.java
   java --module-path /path/to/javafx-sdk/lib --add-modules javafx.controls StudentSuccessPlanner
   ```

## Usage Guide

### Adding a Task
1. Enter course name (e.g., "CIS 115")
2. Enter task name (e.g., "Final Project")
3. Enter grade (0-100)
4. Enter due date in MM/DD/YYYY format
5. Select task type from dropdown
6. Click "Add Task"

### Saving and Loading
- **Save to File**: Stores all tasks in `tasks.txt` in CSV format
- **Load from File**: Retrieves tasks from `tasks.txt` (skips corrupted entries)

### Managing Tasks
- **Calculate Average**: Updates the displayed average grade
- **Delete Selected**: Remove a specific task from the list
- **Clear All Tasks**: Remove all tasks after confirmation
- **Clear Fields**: Reset input fields to defaults

## Data Format

Tasks are saved in CSV format with the following structure:
```
courseName,taskName,grade,dueDate,taskType
```

Example:
```
CIS 115,Final Project,95.5,05/15/2026,Project
CIS 101,Midterm Exam,88.0,04/20/2026,Exam
CIS 120,Lab 5,92.3,04/25/2026,Assignment
```

## Code Highlights

### Input Validation with Regex
```java
private static final Pattern DATE_PATTERN = 
    Pattern.compile("^(0[1-9]|1[0-2])/(0[1-9]|[12]\\d|3[01])/\\d{4}$");
```

### Robust File Loading
```java
try {
    // Validate and parse with error handling
} catch (NumberFormatException ex) {
    failCount++;
    continue;  // Skip malformed lines
}
```

### Polymorphic Task Creation
```java
SchoolTask schoolTask = switch (type) {
    case "Exam" -> new Exam(course, task, grade, dueDate);
    case "Project" -> new ProjectTask(course, task, grade, dueDate);
    default -> new Assignment(course, task, grade, dueDate);
};
```

## Learning Outcomes

This project demonstrates:
- ✅ Object-Oriented Programming (OOP) principles
- ✅ Inheritance and polymorphism
- ✅ Input validation and error handling
- ✅ File I/O operations
- ✅ JavaFX GUI development
- ✅ ArrayList collections
- ✅ Professional code documentation (Javadoc)
- ✅ Software design patterns

## Future Enhancements

- Database integration for persistent storage
- Task priority levels (Low, Medium, High)
- Due date reminders and notifications
- Filtering and sorting options
- Dark mode toggle
- Task categories/tags
- Grade distribution analytics

## Author
Dario Brahimaj

## Date
April 2026

## License
Open source - feel free to use and modify for educational purposes
