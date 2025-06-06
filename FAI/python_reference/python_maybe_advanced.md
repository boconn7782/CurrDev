# Python Advanced/Optional Content - [MAYBE] Topics

**Note:** These topics are covered in some sections or may be pursued by students independently in projects. Not required for all students.

---

# Advanced Variable Types [MAYBE]

## Dictionaries - Advanced Usage
```python
# Student record system
student_records = {
    "NU123456": {
        "name": "Alex Smith",
        "courses": ["ENGR101", "MATH102"],
        "gpa": 3.75
    },
    "NU654321": {
        "name": "Jamie Johnson", 
        "courses": ["COMP150", "PHYS101"],
        "gpa": 3.85
    }
}

# Accessing nested data
alex_gpa = student_records["NU123456"]["gpa"]
print(f"Alex's GPA: {alex_gpa}")

# Iterating over dictionaries
for student_id, info in student_records.items():
    print(f"Student {student_id}: {info['name']}")
```

## Set Operations
```python
engr_students = {"Alex", "Jamie", "Taylor", "Casey"}
math_students = {"Jamie", "Taylor", "Morgan", "Quinn"}

# Set operations
both_courses = engr_students & math_students    # Intersection
all_students = engr_students | math_students    # Union
only_engr = engr_students - math_students       # Difference

print(f"Taking both: {both_courses}")
```

---

# Advanced Control Flow [MAYBE]

## Continue Statement
```python
grades = [88, 45, 92, 30, 85, 90]

print("Passing grades only:")
for grade in grades:
    if grade < 60:
        continue  # Skip failing grades
    print(f"Grade: {grade}")
```

## Else with Loops
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

# Advanced Console Functions [MAYBE]

## ascii() Function
```python
name = "Café"
print(ascii(name))  # 'Caf\\xe9' - shows ASCII representation
```

## format() Method
```python
template = "Student: {name}, Grade: {grade}, Status: {status}"
result = template.format(
    name="Alex",
    grade=85,
    status="Passing"
)
print(result)
```

---

# Advanced String Methods [MAYBE]

## String Replacement and Splitting
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

## String Testing Methods
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

---

# Advanced File Operations [MAYBE]

## Multiple File Operations
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
```

---

# Advanced List Methods [MAYBE]

## List Manipulation
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

## List Comprehensions
```python
# Create new list based on existing list
grades = [88, 92, 85, 90, 75, 95]

# Get only passing grades
passing_grades = [grade for grade in grades if grade >= 80]
print(passing_grades)

# Transform grades (add curve)  
curved_grades = [grade + 5 for grade in grades]
print(curved_grades)

# Complex list comprehension
grade_status = [
    "Pass" if grade >= 70 else "Fail" 
    for grade in grades
]
print(grade_status)
```

---

# Advanced Mathematical Functions [MAYBE]

## Extended Math Operations
```python
import math

# Additional math functions that some students may encounter
numbers = [4, 9, 16, 25]

# Square roots of all numbers
sqrt_values = [math.sqrt(num) for num in numbers]
print(sqrt_values)

# Ceiling and floor
value = 3.7
print(math.ceil(value))   # Round up: 4
print(math.floor(value))  # Round down: 3

# Logarithms (for advanced projects)
print(math.log(10))       # Natural log
print(math.log10(100))    # Base-10 log: 2.0
```

## Binary and Complex Numbers
```python
# Binary representation (for computer science projects)
number = 42
binary = bin(number)      # '0b101010'
print(f"{number} in binary: {binary}")

# Complex numbers for engineering calculations
z1 = complex(3, 4)        # 3 + 4j
z2 = complex(1, 2)        # 1 + 2j
result = z1 + z2          # (4+6j)
print(f"Complex result: {result}")
```

---

# Advanced Function Concepts [MAYBE]

## Multiple Return Values
```python
def analyze_grades(grades):
    """Return multiple statistics about grades"""
    avg = sum(grades) / len(grades)
    highest = max(grades)
    lowest = min(grades)
    passing_count = len([g for g in grades if g >= 70])
    
    return avg, highest, lowest, passing_count

# Unpack multiple return values
grades = [88, 92, 65, 85, 90, 78]
average, max_grade, min_grade, num_passing = analyze_grades(grades)

print(f"Average: {average:.2f}")
print(f"Range: {min_grade} - {max_grade}")
print(f"Students passing: {num_passing}")
```

---

# Regular Expressions [MAYBE]

## Basic Pattern Matching
```python
import re

# Validate student ID format (NU followed by 6 digits)
student_ids = ["NU123456", "NU789012", "ABC123", "NU12345"]

pattern = r"NU\d{6}"  # NU followed by exactly 6 digits

for student_id in student_ids:
    if re.match(pattern, student_id):
        print(f"{student_id}: Valid format")
    else:
        print(f"{student_id}: Invalid format")
```

---

## **CONTENT GAPS TO COMPLETE:**

1. **[INSTRUCTOR REVIEW]** - Verify which [MAYBE] topics are actually used in student projects
2. **[MISSING]** - Advanced loop techniques (enumerate, zip) if used
3. **[MISSING]** - File handling with CSV data (if relevant to projects)
4. **[MISSING]** - Basic error handling (try/except) for robust code
5. **[EXPANSION NEEDED]** - More realistic project-based examples
6. **[VERIFY]** - Regular expressions - confirm if actually used in any sections