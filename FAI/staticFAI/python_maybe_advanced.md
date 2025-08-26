# python_maybe_advanced.md - Advanced/optional content for [MAYBE] topics
# [SYSTEM FILE - DO NOT REMOVE]

# Python Advanced/Optional Content - [MAYBE] Topics

**Note:** These topics are covered in some sections or may be pursued by students independently in projects. Not required for all students.

---

# Advanced String Methods [MAYBE]

## String Replacement and Splitting [MAYBE]
```python
course_list = "ENGR101,MATH102,COMP150,PHYS101"

# Split string into list
courses = course_list.split(",")
print(courses)  # ['ENGR101', 'MATH102', 'COMP150', 'PHYS101']

# Replace content
updated = course_list.replace("COMP150", "COMP160")
print(updated)

# Join list back to string
new_course_list = " | ".join(courses)
print(new_course_list)  # ENGR101 | MATH102 | COMP150 | PHYS101
```

## String Testing Methods [MAYBE]
```python
user_input = "12345"
if user_input.isnumeric():
    grade = int(user_input)
    print(f"Valid grade: {grade}")

# Check string properties
text = "   "
if text.isspace():
    print("Input is empty or whitespace only")
    
course_code = "ENGR101"
if course_code.startswith("ENGR"):
    print("Engineering course")
if course_code.endswith("101"):
    print("Introductory level")
```

## String Formatting [MAYBE]
```python
template = "Student: {name}, Grade: {grade}, Status: {status}"
result = template.format(
    name="Alex",
    grade=85,
    status="Passing"
)
print(result)

# Find and index methods
student_email = "alex.smith@northeastern.edu"
at_position = student_email.find("@")  # Returns position of @
domain_start = student_email.index("@") + 1
domain = student_email[domain_start:]
print(f"Domain: {domain}")  # northeastern.edu
```

---

# Advanced Variable Types [MAYBE]

## Tuples [MAYBE]
```python
departments = ("ENGR", "MATH", "COMP")  # Ordered, unchangeable
print(departments[0])  # Access by index
# departments[0] = "PHYS"  # This would cause an error - tuples are immutable

# Common use: returning multiple values from functions
def get_course_info():
    return "ENGR101", "Dr. Smith", 4  # Returns tuple

course, instructor, credits = get_course_info()  # Unpack tuple
```

## Sets [MAYBE]
```python
majors = {"Engineering", "Math", "CS"}  # Unordered, unique values only
majors.add("Physics")  # Add item
print(majors)  # Duplicates automatically removed

# Set operations for comparing groups
engr_students = {"Alex", "Jamie", "Taylor"}
math_students = {"Jamie", "Taylor", "Casey"}
both_courses = engr_students & math_students  # Intersection
print(f"Taking both: {both_courses}")
```

---

# Advanced File Operations [MAYBE]

## Multiple File Operations [MAYBE]
```python
# Read all lines into a list
with open("grades.txt", "r") as file:
    all_lines = file.readlines()  # Returns list of lines
    
for line in all_lines:
    print(line.strip())  # Remove newline characters

# Write multiple lines at once
course_data = ["ENGR101\n", "MATH102\n", "COMP150\n"]
with open("courses.txt", "w") as file:
    file.writelines(course_data)

# File positioning
with open("grades.txt", "r") as file:
    position = file.tell()  # Get current position
    first_line = file.readline()
    file.seek(0)  # Go back to beginning
    all_content = file.read()
```

---

# Basic Error Handling [MAYBE]

## Simple Input Validation [MAYBE]
```python
def get_valid_grade():
    """Get a valid grade between 0-100 with error handling"""
    while True:
        try:
            grade_input = input("Enter grade (0-100): ")
            grade = int(grade_input)
            if 0 <= grade <= 100:
                return grade
            else:
                print("Grade must be between 0 and 100")
        except ValueError:
            print("Please enter a valid number")

# Use the function
student_grade = get_valid_grade()
print(f"Valid grade entered: {student_grade}")
```

## Basic Exception Handling [MAYBE]
```python
# Simple file handling with error checking
def read_course_file(filename):
    try:
        with open(filename, "r") as file:
            content = file.read()
            return content
    except FileNotFoundError:
        print(f"File {filename} not found")
        return None
    except Exception as e:
        print(f"Error reading file: {e}")
        return None

# Try to read a course file
course_data = read_course_file("course_schedule.txt")
if course_data:
    print("Course data loaded successfully")
else:
    print("Using default course schedule")
```

---

# Advanced List Methods [MAYBE]

## List Manipulation [MAYBE]
```python
grades = [88, 92, 85, 90, 75]

# Insert at specific position
grades.insert(2, 95)  # Insert 95 at index 2
print(grades)

# Remove specific value
grades.remove(75)  # Remove first occurrence of 75

# Remove and return item by index
last_grade = grades.pop()     # Remove and return last item
first_grade = grades.pop(0)   # Remove and return first item

# Reverse and sort
grades.reverse()  # Reverse in place
grades.sort()     # Sort in place
grades.sort(reverse=True)  # Sort descending
```

---

# Advanced Control Flow [MAYBE]

## Continue Statement [MAYBE]
```python
grades = [88, 45, 92, 30, 85, 90]

print("Passing grades only:")
for grade in grades:
    if grade < 60:
        continue  # Skip failing grades
    print(f"Grade: {grade}")
```

## Else with Loops [MAYBE]
```python
# Search for a specific grade
target_grade = 95
grades = [88, 92, 85, 90]

for grade in grades:
    if grade == target_grade:
        print(f"Found grade: {target_grade}")
        break
else:
    print(f"Grade {target_grade} not found")  # Executes if no break
```

---

# Boolean Functions [MAYBE]

## any() and all() [MAYBE]
```python
# Check if all students passed
student_grades = [85, 92, 78, 88, 91]
passing_grades = [grade >= 70 for grade in student_grades]

if all(passing_grades):
    print("All students in ENGR101 passed!")
else:
    print("Some students need additional support")

# Check if any student got an A  
a_grades = [grade >= 90 for grade in student_grades]
if any(a_grades):
    print("At least one student earned an A in the course")
```
