# Intermediate CS Questions and Answers

Original practice material for Indian Intermediate / Class 11–12 students. Python 3 is used for programming; SQL examples use the sample schema in [the practical workbook](PRACTICE.md). All student data is fictional.

These are learning stages, not official class or board assignments. State boards and CBSE differ in languages, topics, and assessment. Compare with your school's current syllabus; this guide does not claim complete exam coverage.

## How to study

Attempt each question before reading its answer. Explain the idea in your own words, dry-run examples, and then complete the workbook. Foundation sections can be studied first; progression sections assume basic Python familiarity.

## Contents

1. Computer fundamentals · Foundation (10 questions)
2. Python basics and control flow · Foundation (15 questions)
3. Strings and collections · Foundation to progression (10 questions)
4. Functions, files, and debugging · Progression (7 questions)
5. Databases and SQL · Progression (10 questions)
6. Networks and responsible computing · Foundation to progression (8 questions)

## Computer fundamentals · Foundation

### 1. What are hardware and software?

Hardware is the physical equipment, such as a keyboard or processor. Software is the instructions it runs, such as an operating system or a Python program.

### 2. What does the CPU do?

The central processing unit fetches and executes instructions. Its arithmetic and logic unit performs calculations and comparisons; its control unit coordinates operations.

### 3. How do RAM and secondary storage differ?

RAM holds working data and is normally volatile: its contents are lost when power is removed. SSDs and hard disks retain files without power. Save your work to storage.

### 4. What is an operating system?

It manages hardware resources, files, memory, and running programs, and provides services for applications. Windows, Linux, and Android are examples.

### 5. What are input, processing, output, and storage?

For a marks calculator, entering marks is input, calculating an average is processing, displaying it is output, and saving the result is storage.

### 6. What are a bit and a byte?

A bit is a binary digit, 0 or 1. A byte contains 8 bits. A KiB is 1,024 bytes; a decimal kB is 1,000 bytes. Check which unit a question uses.

### 7. Convert binary 1011 to decimal.

Use place values 8, 4, 2, 1: 1×8 + 0×4 + 1×2 + 1×1 = 11.

### 8. Convert decimal 13 to binary.

13 = 8 + 4 + 1, so the bits for 8, 4, 2, 1 are 1, 1, 0, 1. The result is 1101.

### 9. What do AND, OR, and NOT do?

AND is true only when both inputs are true. OR is true when at least one input is true. NOT reverses a Boolean value. For A=True and B=False: A AND B=False, A OR B=True, NOT A=False.

### 10. Why do computers need character encodings?

They map characters to numeric representations. Unicode assigns code points to characters, including Indian scripts; UTF-8 encodes them as bytes. One character need not occupy one byte.

## Python basics and control flow · Foundation

### 11. What is an algorithm?

A finite sequence of clear steps for solving a problem. To find the larger of two numbers, read both, compare them, and report the larger; if equal, report equality.

### 12. Why use a dry run?

A dry run follows a program by hand, recording changing values and output. It helps find logic mistakes before execution.

### 13. What are variables and common Python types?

A variable name refers to an object. Examples: count=3 is int, average=72.5 is float, name='Asha' is str, and passed=True is bool.

### 14. What does input() return?

It returns a string. Use int(input()) for an integer when the entered text is valid. Invalid integer text raises ValueError.

### 15. How do = and == differ?

= assigns a value to a name; == compares values. score = 80 assigns; score == 80 evaluates to True.

### 16. What are /, //, and %?

/ is division, // is floor division, and % gives the remainder. With positive integers: 17/5 = 3.4, 17//5 = 3, 17%5 = 2. Floor division rounds down, so -7//2 = -4.

### 17. What is the result of 2 + 3 * 4?

14, because multiplication is evaluated before addition. (2 + 3) * 4 gives 20.

### 18. Why does indentation matter?

Python uses indentation to group statements into blocks, such as the body of an if or for. Use consistent indentation, conventionally four spaces.

### 19. How do you test whether an integer n is even?

Use n % 2 == 0. This also works for zero and negative even integers.

### 20. What values does range(1, 5) produce?

1, 2, 3, 4. The stop value is excluded. range(5) produces 0 through 4.

### 21. When should you use for or while?

Use for to iterate through items or a known range. Use while to repeat while a condition remains true; ensure the condition can eventually become false.

### 22. How do break and continue differ?

break exits the nearest loop. continue skips the remainder of the current iteration and proceeds to the next iteration.

### 23. Predict: total=0, then add n for each n in range(1, 4).

The values of n are 1, 2, 3. The running totals are 1, 3, 6, so the final total is 6.

### 24. How do syntax, runtime, and logic errors differ?

A missing colon can cause a syntax error. Dividing by zero causes a runtime exception. Using the wrong formula can produce an incorrect result without an exception: a logic error.

### 25. How can a function help?

A function groups reusable work under a name. Parameters receive inputs; return sends a result to the caller. print displays a value and does not substitute for returning it.

## Strings and collections · Foundation to progression

### 26. What are indexing and slicing?

For s='INDIA', s[0] is 'I', s[-1] is 'A', and s[1:4] is 'NDI'. A slice excludes its stop index.

### 27. Can a string be changed in place?

No. Strings are immutable. s.lower() returns a new string; assign it if you want to keep the result.

### 28. How do lists and tuples differ?

Both are ordered sequences. A list is mutable, such as [70, 80]; a tuple is immutable, such as (70, 80). A tuple may still contain a mutable object.

### 29. What is a dictionary?

A mapping from unique, hashable keys to values. marks={'Asha': 85}; marks['Asha'] gives 85. Use marks.get('Ravi', 0) when a missing name should produce 0.

### 30. What does append do?

For a=[1, 2], a.append(3) changes a to [1, 2, 3]. append mutates the list and returns None; do not write a=a.append(3).

### 31. What is aliasing?

If a=[1, 2] and b=a, both names refer to the same list. b.append(3) also changes what a sees. a.copy() creates a separate outer list.

### 32. How can you count vowels in a word?

Start a counter at zero. Visit each character in word.lower(); increment when the character is in 'aeiou'. This rule counts English vowel letters.

### 33. What is linear search?

Check items one by one until a match is found or the sequence ends. It works on unsorted lists and takes up to n comparisons for n items.

### 34. What condition does binary search require?

The searchable sequence must be sorted under the same ordering used by the search. Repeatedly inspect the middle and discard half the remaining interval.

### 35. What is a stack?

A last-in, first-out collection, like a pile of books. In a Python list, append pushes and pop removes the last item. Check for an empty stack before popping.

## Functions, files, and debugging · Progression

### 36. What is local scope?

A name assigned inside a function is normally local to that function. Pass required inputs as parameters and return results instead of depending on changing global variables.

### 37. What is a default argument?

It supplies a value when a caller omits an argument. In def greet(name='Student'): the default is 'Student'. Avoid mutable defaults such as [] for a fresh list per call.

### 38. What does try/except do?

It handles selected exceptions. For example, catch ValueError when converting text to an integer so the program can request valid input.

### 39. Why use with when opening a file?

A with open(...) block closes the file when the block ends, including when an exception occurs. Choose the correct mode and an encoding for text.

### 40. How do file modes r, w, and a differ?

r reads an existing file. w writes and truncates an existing file, so previous contents can be lost. a appends at the end. Practice only on disposable files.

### 41. What is CSV?

Comma-separated values is a text format for records and fields. Fields can contain quoted commas, so use Python's csv module instead of simply splitting every line at commas.

### 42. What test cases should a marks-average program include?

Try ordinary marks, all zeroes, all maximum marks, boundary marks, invalid marks, and no marks. Decide how the program handles an empty input before dividing.

## Databases and SQL · Progression

### 43. What are a database and a DBMS?

A database is an organised collection of data. A database management system stores, retrieves, and manages it. A school might store student and course records.

### 44. What are rows and columns?

In a relational table, a row represents a record, such as one student. A column represents an attribute, such as student_id or name.

### 45. What is a primary key?

A column or set of columns chosen to uniquely identify each row. It must be unique and non-null. Student names are poor keys because different students may share a name.

### 46. What is a foreign key?

It relates rows to a referenced key in another table (or the same table). For example, Student.class_id can refer to Class.class_id.

### 47. How do SELECT and WHERE work?

SELECT chooses output columns; WHERE filters rows. SELECT name FROM Student WHERE marks >= 75; returns names of students with marks at least 75.

### 48. Why use ORDER BY?

It requests sorted results. SELECT name, marks FROM Student ORDER BY marks DESC, name ASC; sorts highest marks first, then names alphabetically for tied marks.

### 49. How do COUNT(*) and AVG(marks) differ?

COUNT(*) counts rows. AVG(marks) calculates the mean of non-null marks. NULL represents a missing or unknown value; it is not the number zero.

### 50. How do WHERE and HAVING differ?

WHERE filters rows before grouping. HAVING filters groups after aggregation. Example: SELECT class_id, COUNT(*) FROM Student GROUP BY class_id HAVING COUNT(*) >= 2;

### 51. How do you check for a missing mark?

Use WHERE marks IS NULL, not marks = NULL. Ordinary equality with NULL does not evaluate to true.

### 52. What is an INNER JOIN?

It combines matching rows from tables. SELECT s.name, c.label FROM Student AS s INNER JOIN Class AS c ON s.class_id = c.class_id; matches each student to the corresponding class.

## Networks and responsible computing · Foundation to progression

### 53. How do a LAN and the Internet differ?

A local area network connects devices over a limited area, such as a school lab. The Internet connects many networks globally.

### 54. How do a switch and a router differ?

A switch typically forwards frames within a local network. A router forwards packets between IP networks.

### 55. What does DNS do?

The Domain Name System resolves domain names to records such as IP addresses. It helps a browser locate a service using a readable name.

### 56. How do a browser and a search engine differ?

A browser is an application used to access web content. A search engine is a service that indexes and helps find content.

### 57. What does HTTPS provide?

It protects data in transit using TLS and authenticates the server for the requested hostname through certificates. It does not guarantee that a site's claims or downloads are trustworthy.

### 58. What is phishing?

A deceptive message or site tries to make you reveal information or take an unsafe action. Verify the sender through a trusted route and avoid unexpected login links.

### 59. How should students protect accounts and privacy?

Use unique passwords or passphrases and multi-factor authentication where available. Never share passwords, OTPs, addresses, or student records in public code. Use invented data for projects.

### 60. What is responsible use of digital material and AI?

Credit sources, respect licences, and submit work you understand. Check AI-generated answers against trusted sources and your own tests; do not upload classmates' personal information.

## References

- [Python tutorial: control flow](https://docs.python.org/3/tutorial/controlflow.html)
- [Python tutorial: data structures](https://docs.python.org/3/tutorial/datastructures.html)
- [Python tutorial: files](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
- [SQLite SELECT reference](https://www.sqlite.org/lang_select.html) — runnable workbook dialect; school courses may use MySQL.
- [CBSE curriculum portal, 2026–27](https://cbseacademic.nic.in/curriculum_2027.html) — check the relevant subject and year; state-board students should consult their own board.

Edition: 9 November 2026. Existing interview notes are preserved separately as optional advanced reading.

