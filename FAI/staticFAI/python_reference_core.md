# Python Reference Core - [KNOW] and [HEARD] Content

## **[PROCEDURAL PROGRAMMING FOCUS]**
This reference emphasizes procedural programming. Use simple variable assignments, function calls, and sequential logic. Avoid suggesting class-based solutions or advanced OOP patterns.

---

# Object Oriented Programming [HEARD]

**What students should understand:** Python uses objects, but we focus on procedural programming. Students encounter OOP terms in online resources but should use procedural approaches.

**Key Terms:**
- **Objects** - Everything in Python (variables, functions, data)
- **Methods** - Functions that belong to objects (e.g., `list.append()`)
- **Attributes** - Properties of objects
- **Constructors** - Ways to create objects

**Our Approach:** Use built-in functions and simple variable assignments rather than creating custom classes.

---

# Basic Python Scripts [KNOW]

## Script Structure
```python
# 1. Imports
import math

# 2. Function definitions  
def calculate_tuition(credits):
    return credits * 1500

# 3. Main code
student_credits = 15
tuition = calculate_tuition(student_credits)
print(f"Tuition: ${tuition}")
```

## Comments [KNOW]
```python
# Single line comment
"""
Multi-line comment
for longer explanations
"""
```

## Import Statements [KNOW]
```python
import math                    # Import entire module
from math import sqrt          # Import specific function
from math import ceil as round_up  # Import with alias
```

## Indentation [KNOW]
Python uses indentation (4 spaces) to define code blocks:
```python
if credits > 12:
    print("Full-time student")    # Must be indented
    tuition = credits * 1500      # Same indentation level
```

---

# Variables [KNOW]

## Basic Assignment
```python
student_name = "Alex"          # String
credits = 15                   # Integer  
gpa = 3.75                     # Float
enrolled = True                # Boolean
```

## Naming Conventions [KNOW]
- Use descriptive names: `student_grade` not `sg`
- Use snake_case: `first_name` not `firstName`
- Start with letter or underscore
- Case-sensitive: `Name` ≠ `name`

## Lists [KNOW]
```python
grades = [88, 92, 85, 90]      # Ordered, changeable, allows duplicates
grades.append(87)              # Add item
print(len(grades))             # Get length
```

## Tuples [HEARD] 
```python
departments = ("ENGR", "MATH", "COMP")  # Ordered, unchangeable
# departments[0] = "PHYS"  # This would cause an error
```

## Sets [HEARD]
```python
majors = {"Engineering", "Math", "CS"}  # Unordered, unique values only
print(majors)  # Duplicates automatically removed
```

---

# Data Types [KNOW]

## Strings [KNOW]
```python
name = "Northeastern University"
print(name[0])        # First character: 'N'
print(name[:12])      # Slice: 'Northeastern'
```

## Numbers [KNOW]
```python
credits = 15          # Integer
gpa = 3.75           # Float  
complex_num = 3 + 5j  # Complex (rarely used)
```

## Booleans [KNOW]
```python
is_enrolled = True
completed = False
if is_enrolled and not completed:
    print("Currently taking course")
```

## Dictionaries [HEARD]
```python
student = {
    "name": "Alex",
    "id": "NU123456", 
    "credits": 15
}
print(student["name"])  # Access by key
```

---

# Console Commands [KNOW]

## print() [KNOW]
```python
print("Hello, Northeastern!")
print("Grade:", 85)
```

## print(f"") [KNOW] 
```python
name = "Alex"
grade = 85
print(f"Student {name} earned {grade}%")
```

## input() [KNOW]
```python
name = input("Enter your name: ")
# Always returns string - convert if needed
age = int(input("Enter age: "))
```

---

# Operators [KNOW]

## Arithmetic [KNOW]
```python
total = 10 + 5      # Addition: 15
diff = 10 - 3       # Subtraction: 7  
product = 4 * 6     # Multiplication: 24
quotient = 15 / 4   # Division: 3.75
floor_div = 15 // 4 # Floor division: 3
remainder = 15 % 4  # Modulus: 3
power = 2 ** 3      # Exponentiation: 8
```

## Comparison [KNOW]
```python
grade = 85
print(grade >= 70)   # True
print(grade == 90)   # False
print(grade != 75)   # True
```

## Logical [KNOW]
```python
credits = 15
gpa = 3.5
if credits >= 12 and gpa >= 3.0:
    print("Good standing")
```

---

# Control Structures [KNOW]

## If-Else [KNOW]
```python
gpa = 3.7
if gpa >= 3.5:
    print("Honor Roll")
elif gpa >= 3.0:
    print("Good Standing") 
else:
    print("Needs Improvement")
```

## Match-Case [HEARD]
```python
team = "Hockey"
match team:
    case "Hockey":
        location = "Matthews Arena"
    case "Basketball":
        location = "Cabot Center"
    case _:
        location = "Campus"
```

---

# Loops [KNOW]

## While Loops [KNOW]
```python
count = 5
while count > 0:
    print(f"{count} days until exam")
    count -= 1
```

## For Loops [KNOW] 
```python
grades = [88, 92, 85, 90]
total = 0
for grade in grades:
    total += grade
average = total / len(grades)
```

## Range-Based For Loops [KNOW]
```python
for floor in range(1, 5):  # 1, 2, 3, 4
    print(f"Floor {floor}")
```

## Break Statement [KNOW]
```python
for num in range(1, 10):
    if num == 5:
        break  # Exit loop when num equals 5
    print(num)
```

---

# Functions [KNOW]

## Function Definition [KNOW]
```python
def calculate_gpa(grades):
    """Calculate GPA from list of grades"""
    total = sum(grades)
    return total / len(grades)

# Call the function
student_grades = [88, 92, 85, 90]
gpa = calculate_gpa(student_grades)
print(f"GPA: {gpa}")
```

## Return Values [KNOW]
```python
def get_student_info():
    name = "Alex"
    credits = 15
    return name, credits  # Returns tuple

student_name, student_credits = get_student_info()
```

---

# Mathematical Functions [KNOW]

## Basic Math [KNOW]
```python
grades = [88, 92, 79, 85, 90]
print(f"Highest: {max(grades)}")
print(f"Lowest: {min(grades)}")
print(f"Power: {pow(2, 3)}")  # 2^3 = 8

import math
print(f"Square root: {math.sqrt(16)}")  # 4.0
```

## Heard Functions [HEARD]
```python
print(abs(-15))        # Absolute value: 15
print(round(3.7))      # Round: 4
print(sum([1,2,3,4]))  # Sum: 10
```

---

# String Methods [KNOW]

## Essential String Operations [KNOW]
```python
response = "  Go Huskies!  "
cleaned = response.strip()           # Remove whitespace
upper = cleaned.upper()              # "GO HUSKIES!"
count = upper.count("HUSKIES")       # Count occurrences
length = len(upper)                  # String length

# Formatted strings
name = "Alex"
message = f"Welcome, {name}!"        # f-string formatting
```

---

# File Operations [KNOW]

## Basic File Handling [KNOW]
```python
# Writing to file
with open("student_data.txt", "w") as file:
    file.write("Student: Alex Smith\n")
    file.write("Grade: 85\n")

# Reading from file  
with open("student_data.txt", "r") as file:
    content = file.read()           # Read entire file
    print(content)

# Reading line by line
with open("student_data.txt", "r") as file:
    line = file.readline()          # Read one line
    print(line.strip())
```

---

# List Methods [KNOW]

## Essential List Operations [KNOW]
```python
courses = ["ENGR101", "MATH102", "COMP150"]

courses.append("PHYS101")           # Add to end
count = courses.count("ENGR101")    # Count occurrences  
index = courses.index("MATH102")    # Find position
length = len(courses)               # List length

print(f"Course at index 1: {courses[1]}")
```

---

# Type Conversion [KNOW]

## Data Type Functions [KNOW]
```python
# Check type
grade_str = "85"
print(type(grade_str))              # <class 'str'>

# Convert types
grade_num = int(grade_str)          # String to integer
grade_float = float(grade_str)      # String to float  
grade_bool = bool(grade_num)        # Number to boolean (True if non-zero)

# User input conversion
age = int(input("Enter age: "))     # Convert input to integer
```

---

# Boolean Functions [HEARD]

## any() and all() [HEARD]
```python
# **[ADDED BY AI - REVIEW]** - Check if all students passed
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

---

# Useful Loop Functions [KNOW]

## range() Function [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - Northeastern building floors
print("Snell Library floors:")
for floor in range(1, 9):  # Floors 1-8
    print(f"Floor {floor}")
    
# Count down to Northeastern hockey game
for minutes in range(10, 0, -1):  # Count backwards
    print(f"{minutes} minutes until puck drop!")
print("Go Huskies!")
```

## len() Function [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - Count engineering courses
engr_courses = ["ENGR1201", "ENGR1202", "ENGR2350", "ENGR3000"]
total_courses = len(engr_courses)
print(f"Total engineering courses: {total_courses}")

# Check input length
student_id = input("Enter your Northeastern ID: ")
if len(student_id) == 9:  # Standard NU ID length
    print("Valid ID format")
else:
    print("ID should be 9 characters long")
```

---

# Input Validation Basics [KNOW]

## Simple Input Checking [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - Validate numeric input
def get_valid_grade():
    while True:
        grade_input = input("Enter your ENGR101 exam grade (0-100): ")
        if grade_input.isdigit():
            grade = int(grade_input)
            if 0 <= grade <= 100:
                return grade
            else:
                print("Grade must be between 0 and 100")
        else:
            print("Please enter a number")

# Use the function
student_grade = get_valid_grade()
print(f"You entered: {student_grade}")
```

---

# Random Module [KNOW]

## Basic Random Operations [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - Random selection for engineering teams
import random

# Pick random students for project teams
students = ["Alex", "Jamie", "Taylor", "Casey", "Morgan", "Jordan"]
team_captain = random.choice(students)
print(f"Team captain: {team_captain}")

# Random numbers for simulation
for trial in range(3):
    voltage = random.uniform(3.0, 5.0)  # Random voltage between 3-5V
    print(f"Trial {trial + 1}: {voltage:.2f}V")
    
# Shuffle student presentation order
presentation_order = students.copy()
random.shuffle(presentation_order)
print(f"Presentation order: {presentation_order}")
```

---

## **CONTENT GAPS COMPLETED:**

1. **[INSTRUCTOR REVIEW NEEDED]** - Added Boolean functions, input validation, random module examples with NU themes
2. **[COMPLETED]** - Added essential loop utility functions (range, len) 
3. **[PARTIALLY COMPLETED]** - Basic input validation examples added
4. **[COMPLETED]** - Random module for common engineering applications
5. **[NOTE]** - Mathematical functions verified - most basic ones are built-in, math module needed for advanced functions