# Python Topics Not Covered - [NC] Boundaries

**Purpose:** This document defines concepts that are explicitly NOT covered in first-year engineering courses. Use this to redirect students away from overly advanced topics.

---

## **AI ASSISTANT GUIDANCE**
When students ask about [NC] topics, respond with:
1. **"That's beyond our current course scope and not covered in ENGR assignments"**
2. **"Using advanced approaches could negatively impact your assignment grade"**
3. **"Let's solve this using the methods we've learned in class"**
4. **Redirect to appropriate [KNOW] or [HEARD] alternatives**
5. **Suggest they explore advanced topics in upper-level courses**

**Important:** Don't ignore [NC] questions - acknowledge them but firmly redirect to course-appropriate solutions.

---

# Object-Oriented Programming [NC]

## Class Definition and Custom Objects
```python
# DON'T SUGGEST THIS - Too advanced for FYE
class Student:
    def __init__(self, name, id):
        self.name = name
        self.id = id
    
    def calculate_gpa(self):
        # Complex OOP implementation
        pass

# INSTEAD, USE PROCEDURAL APPROACH:
def calculate_gpa(grades):
    return sum(grades) / len(grades)

student_name = "Alex"
student_grades = [88, 92, 85]
gpa = calculate_gpa(student_grades)
```

## Inheritance and Polymorphism
**Not Covered:** Class inheritance, method overriding, abstract classes, interfaces

**Alternative:** Use simple functions and data structures

---

# Advanced Object Manipulation [NC]

## Attribute Management
```python
# DON'T SUGGEST THESE:
# setattr(obj, 'property', value)
# delattr(obj, 'property') 
# hasattr(obj, 'property')
# isinstance(obj, class)

# INSTEAD: Use simple variables and dictionaries
student_info = {
    "name": "Alex",
    "grades": [88, 92, 85]
}
```

---

# Bitwise Operations [NC]

## Binary Operations
```python
# DON'T SUGGEST THESE - Too advanced for introductory programming:
# x << 2    # Left shift
# x >> 1    # Right shift  
# x & y     # Bitwise AND
# x | y     # Bitwise OR
# x ^ y     # XOR
# ~x        # Bitwise NOT

# INSTEAD: Use standard arithmetic and logical operations
```

---

# Advanced File Operations [NC]

## File System Manipulation
```python
# DON'T SUGGEST THESE - Beyond scope:
import os
import shutil

# os.listdir()          # Directory listing
# os.makedirs()         # Create directories
# shutil.copy()         # Copy files
# os.path.join()        # Path manipulation

# INSTEAD: Focus on basic file read/write operations
with open("data.txt", "r") as file:
    content = file.read()
```

## Binary File Operations
**Not Covered:** Reading/writing binary files, file modes like 'rb', 'wb'

**Alternative:** Stick to text files with 'r', 'w', 'a' modes

---

# Advanced Data Structures [NC]

## Collections Module
```python
# DON'T SUGGEST:
from collections import defaultdict, Counter, deque

# INSTEAD: Use basic lists, dictionaries, and sets
```

## Advanced Iterations
```python
# DON'T SUGGEST THESE - Too complex for beginners:
# zip()         - Combining iterables
# enumerate()   - Getting index and value (unless specifically taught)
# itertools     - Advanced iteration patterns

# INSTEAD: Use simple for loops with range() when needed
```

---

# Error Handling [NC]

## Exception Handling
```python
# DON'T SUGGEST COMPLEX TRY/EXCEPT:
try:
    value = int(input("Enter number: "))
except ValueError as e:
    print(f"Error: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
finally:
    print("Cleanup code")

# INSTEAD: Use simple input validation
user_input = input("Enter number: ")
if user_input.isdigit():
    value = int(user_input)
else:
    print("Please enter a valid number")
```

---

# Advanced Function Concepts [NC]

## Decorators and Closures
```python
# DON'T SUGGEST:
@property
def name(self):
    return self._name

# Function decorators, closures, lambda functions beyond simple cases
```

## Advanced Parameter Handling
```python
# DON'T SUGGEST:
def function(*args, **kwargs):
    pass

# Variable arguments, keyword arguments, default parameters with mutable objects
```

---

# Concurrency and Threading [NC]

## Parallel Processing
```python
# DON'T SUGGEST:
import threading
import multiprocessing
import asyncio

# Any concurrent programming concepts
```

---

# Database Operations [NC]

## SQL Integration
```python
# DON'T SUGGEST:
import sqlite3
# Database connections, SQL queries, ORM frameworks
```

---

# Web Development [NC]

## Web Frameworks
```python
# DON'T SUGGEST:
from flask import Flask
import requests
# Web servers, HTTP requests, API development
```

---

# Advanced Libraries [NC]

## Data Science Libraries
```python
# DON'T SUGGEST THESE UNLESS SPECIFICALLY MENTIONED IN COURSE:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Note: Some sections may introduce numpy basics - check course materials
```

## Machine Learning
```python
# DON'T SUGGEST:
import sklearn
import tensorflow
import pytorch
```

---

# Memory Management [NC]

## Advanced Memory Concepts
```python
# DON'T EXPLAIN IN DETAIL:
# Garbage collection
# Memory profiling  
# Weak references
# Memory mapping
```

---

# Metaclasses and Descriptors [NC]

## Advanced Python Internals
```python
# DON'T SUGGEST:
# Metaclasses
# Property descriptors
# Context managers (beyond basic 'with' statement)
# Generator expressions beyond simple list comprehensions
```

---

## **REDIRECTION STRATEGIES**

### When Student Asks About [NC] Topics:

**Response Pattern:**
1. "That's a more advanced topic we'll cover in later courses"
2. "For now, let's solve this using [appropriate KNOW/HEARD alternative]"
3. "Here's how we can accomplish the same goal with what we've learned"

**Example Redirections:**

**Student asks about classes:**
> "Custom classes are beyond our course scope and using them in ENGR assignments could hurt your grade. We focus on procedural programming. For now, let's organize data using functions and dictionaries like we learned in class. Here's how..."

**Student asks about advanced file operations:**
> "File system operations aren't covered in our curriculum and could complicate your assignment unnecessarily. Let's stick to the basic file operations we learned - open(), read(), and write(). Here's the approach that matches our course expectations..."

**Student asks about web scraping/APIs:**
> "Web programming isn't part of ENGR courses and would be inappropriate for your current assignments. For now, let's work with local files and user input to practice the programming fundamentals we're learning. This approach will help you succeed on your graded work..."

**Student asks about advanced libraries (pandas, numpy beyond basics):**
> "Those libraries are covered in advanced courses like EECE 2140. Using them now could make your code too complex for current assignment requirements. Let's solve this using basic Python lists and functions - that's what your instructors expect to see..."

---

## **CONTENT GAPS TO COMPLETE:**

1. **[INSTRUCTOR VERIFICATION]** - Confirm which advanced topics students commonly encounter online
2. **[MISSING]** - More redirection examples for common advanced questions
3. **[REVIEW NEEDED]** - Verify alignment with what's actually taught in different course sections
4. **[ADD]** - Common misconceptions students have about "better" or "more advanced" ways to code