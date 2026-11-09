# Practical workbook

Try the tasks first. Python examples use Python 3. SQL uses SQLite, with notes for courses using other database systems. All names and marks are invented.

## Tasks

1. **Foundation — even or odd:** Write a function returning whether an integer is even. Test 0, 7, and -4.
2. **Foundation — marks average:** Write a function returning an average for a non-empty list of marks from 0 to 100. Reject an empty list and out-of-range marks. Test [70, 80, 90], [0], and invalid input.
3. **Foundation — vowel counter:** Count English vowel letters, ignoring case. Test 'India', 'SCHOOL', and an empty string.
4. **Progression — stack:** Push 'Maths' and 'CS'; pop once. Predict the removed item and the remaining stack. Explain what happens if pop is called on an empty list.
5. **Progression — file:** Write two subject names to a disposable text file, read them back, and count the lines. Use a temporary directory so no existing file is overwritten.
6. **Progression — SQL:** Run the dataset below. Find students with at least 75 marks, the mean of known marks, the count per class, and each student's class label.

## Python solutions

The assertions are executable checks. A failed assertion means the observed result differs from the stated expectation.

```python
def is_even(n):
    return n % 2 == 0


def average_marks(marks):
    if not marks:
        raise ValueError("At least one mark is required")
    if any(mark < 0 or mark > 100 for mark in marks):
        raise ValueError("Marks must be between 0 and 100")
    return sum(marks) / len(marks)


def count_vowels(word):
    count = 0
    for character in word.lower():
        if character in "aeiou":
            count += 1
    return count


assert is_even(0) is True
assert is_even(7) is False
assert is_even(-4) is True
assert average_marks([70, 80, 90]) == 80
assert average_marks([0]) == 0
assert average_marks([100, 100]) == 100
for invalid in ([], [-1], [101]):
    try:
        average_marks(invalid)
    except ValueError:
        pass
    else:
        raise AssertionError("Invalid marks were accepted")
assert count_vowels("India") == 3
assert count_vowels("SCHOOL") == 2
assert count_vowels("") == 0

stack = []
stack.append("Maths")
stack.append("CS")
assert stack.pop() == "CS"
assert stack == ["Maths"]
# pop() on an empty list raises IndexError.

from pathlib import Path
from tempfile import TemporaryDirectory

with TemporaryDirectory() as folder:
    path = Path(folder) / "subjects.txt"
    with path.open("w", encoding="utf-8") as file:
        file.write("Maths\nCS\n")
    with path.open("r", encoding="utf-8") as file:
        subjects = [line.strip() for line in file]
    assert subjects == ["Maths", "CS"]
    assert len(subjects) == 2

print("Python exercises passed")
```

The average function assumes numeric inputs. An interactive version must also catch invalid text conversion and explain the error to the user. Zero is a valid mark; an empty list is not a zero average.

## SQL dataset and solutions

Run this script in SQLite. It uses a fresh in-memory database in the verification example below.

```sql
CREATE TABLE Class (
    class_id INTEGER PRIMARY KEY,
    label TEXT NOT NULL
);
CREATE TABLE Student (
    student_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    class_id INTEGER NOT NULL REFERENCES Class(class_id),
    marks INTEGER CHECK (marks BETWEEN 0 AND 100)
);
INSERT INTO Class VALUES (11, 'Class 11'), (12, 'Class 12');
INSERT INTO Student VALUES
    (1, 'Asha', 11, 80),
    (2, 'Ravi', 11, 70),
    (3, 'Meera', 12, 90),
    (4, 'Kabir', 12, NULL);

SELECT name FROM Student WHERE marks >= 75 ORDER BY name;
-- Asha, Meera (two rows)

SELECT AVG(marks) FROM Student;
-- 80.0: (80 + 70 + 90) / 3; NULL is excluded.

SELECT class_id, COUNT(*) FROM Student
GROUP BY class_id ORDER BY class_id;
-- (11, 2), (12, 2); COUNT(*) includes Kabir's row.

SELECT s.name, c.label FROM Student AS s
INNER JOIN Class AS c ON s.class_id = c.class_id
ORDER BY s.student_id;
-- Asha: Class 11; Ravi: Class 11; Meera: Class 12; Kabir: Class 12.

SELECT name FROM Student WHERE marks IS NULL;
-- Kabir
```

SQLite needs `PRAGMA foreign_keys = ON;` on each connection to enforce foreign keys. The verification script enables it. SQL data types and enforcement details vary across databases; use your course's DBMS when preparing for its practical assessment.

## Run SQL with Python

Save the SQL block above as `practice.sql`, then run this Python script from the same folder. Use only the fictional dataset.

```python
import sqlite3
from pathlib import Path

with sqlite3.connect(":memory:") as connection:
    connection.execute("PRAGMA foreign_keys = ON")
    connection.executescript(Path("practice.sql").read_text(encoding="utf-8"))
    assert connection.execute(
        "SELECT name FROM Student WHERE marks >= 75 ORDER BY name"
    ).fetchall() == [("Asha",), ("Meera",)]
    assert connection.execute(
        "SELECT AVG(marks) FROM Student"
    ).fetchone() == (80.0,)
    assert connection.execute(
        "SELECT class_id, COUNT(*) FROM Student GROUP BY class_id ORDER BY class_id"
    ).fetchall() == [(11, 2), (12, 2)]
    assert connection.execute(
        "SELECT s.name, c.label FROM Student AS s "
        "INNER JOIN Class AS c ON s.class_id = c.class_id ORDER BY s.student_id"
    ).fetchall() == [
        ("Asha", "Class 11"), ("Ravi", "Class 11"),
        ("Meera", "Class 12"), ("Kabir", "Class 12")
    ]
    assert connection.execute(
        "SELECT name FROM Student WHERE marks IS NULL"
    ).fetchall() == [("Kabir",)]
print("SQL exercises passed")
```

## Self-check and mini-project

Without looking up answers, explain why range excludes its stop value, why a student name is a weak primary key, and why HTTPS alone does not prove a site is honest. Review the matching questions if you cannot explain them with an example.

Build a fictional marks summary: accept three numeric marks, validate the range, calculate the mean, and display it to two decimal places. Test non-numeric text, 0, 100, and out-of-range values. Extension: store invented names and marks in CSV using the csv module.

Assess your work by checking correctness, clear names, validation, boundary cases, and your ability to explain every line.

