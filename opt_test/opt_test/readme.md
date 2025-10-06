# 📘 School Timetable Optimization using OR-Tools CP-SAT

**Author:** Blessing Mvana Nhlozi
**Language:** Python
**Library:** [Google OR-Tools](https://developers.google.com/optimization)

---

## Overview

This project uses **Constraint Programming (CP-SAT)** to automatically generate an optimal **school timetable** that satisfies a set of logical and practical constraints.
The solver ensures that no teacher or student is double-booked, lessons are evenly distributed, and daily schedules are balanced.

---

## Methodology

### 1. Data Loading

All timetable-related information (classes, teachers, students, lessons, and weekdays) is loaded from CSV files using the `load_data()` function.

### 2. Model Building

The `build_model()` function defines:

* **Decision variables** for assigning lessons to time slots.
* **Constraints** to ensure valid scheduling, such as:

  * Teachers and students are not assigned to two classes at the same time.
  * Required number of lessons per subject are met.
  * Classes are not overloaded per day.

### 3. Optimization

The **CP-SAT solver** searches for feasible and optimal solutions that minimize constraint violations while maximizing schedule balance.

### 4. Output Formatting

The final timetable is formatted and merged with timeslot information using `format_output()`.
Results are exported as a CSV file (`timetable.csv`).

### 5. Profiling

The **`Profiler`** context manager is used to monitor execution time and memory usage for performance tracking.

---

## Components

| Function              | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| **`Profiler`**        | Tracks time and memory usage for performance optimization. |
| **`load_data()`**     | Loads all CSV files into DataFrames.                       |
| **`build_model()`**   | Defines CP-SAT variables, constraints, and objectives.     |
| **`solve_model()`**   | Runs the solver and extracts the timetable.                |
| **`format_output()`** | Prepares and exports the final CSV timetable.              |

---

## Folder Structure

```

├── opt_test/
    │
    ├── __MACOSX/
    │   └── ..........
    │
    ├── opt_test/
    │   ├── 000_Functions.ipynb
    │   ├── 001_Main.ipynb
    │   │
    │   ├── class_list.csv
    │   ├── timeslots.csv
    │   ├── lessons_required.csv
    │   ├── weekdays.csv
    │   ├── teacher_classes.csv
    │   ├── student_classes.csv
    │   ├── teacher_list.csv
    │   │
    │   ├── timetable.csv
    │   │
    │   ├── README.md
    │   └── requirements.txt
```
---

## Example Usage

```bash
python 001_Main.py
```

or in Jupyter Notebook:

```python
%run 001_Main.ipynb
```

The solution file `timetable.csv` will be saved automatically in the working directory.

---

## Dependencies

* Python ≥ 3.8
* pandas
* ortools
* logging

Install all dependencies using:

```bash
pip install -r requirements.txt
```