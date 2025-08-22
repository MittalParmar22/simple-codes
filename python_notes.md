# Python Programming Notes 🐍

My comprehensive Python learning reference

## Table of Contents
- [Basics](#basics)
- [Data Types](#data-types)
- [Control Structures](#control-structures)
- [Functions](#functions)
- [Object-Oriented Programming](#object-oriented-programming)
- [File Handling](#file-handling)
- [Libraries & Modules](#libraries--modules)
- [Best Practices](#best-practices)
- [Common Patterns](#common-patterns)
- [Useful Resources](#useful-resources)

---

## Basics

### Hello World
python
print("Hello, World!")


### Variables and Assignment
python
# Variable assignment
name = "Alice"
age = 20
height = 5.6
is_student = True

# Multiple assignment
x, y, z = 1, 2, 3
a = b = c = 0


### Comments
python
# Single line comment

"""
Multi-line comment
or docstring
"""


### Python Zen (import this)
- Beautiful is better than ugly
- Explicit is better than implicit
- Simple is better than complex
- Readability counts

---

## Data Types

### Numbers
python
# Integers
num = 42
big_num = 1_000_000  # Underscores for readability

# Floats
pi = 3.14159
scientific = 2.5e10  # 25,000,000,000

# Complex numbers
complex_num = 3 + 4j


### Strings
python
# String creation
single = 'Hello'
double = "World"
triple = """Multi-line
string"""

# String methods
text = "Python Programming"
print(text.upper())      # PYTHON PROGRAMMING
print(text.lower())      # python programming
print(text.split())      # ['Python', 'Programming']
print(text.replace("Python", "Java"))  # Java Programming

# String formatting
name = "Alice"
age = 20
print(f"My name is {name} and I'm {age} years old")  # f-strings (Python 3.6+)
print("My name is {} and I'm {} years old".format(name, age))  # .format()
print("My name is %s and I'm %d years old" % (name, age))  # % formatting


### Lists
python
# List creation
fruits = ["apple", "banana", "orange"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]

# List methods
fruits.append("grape")       # Add to end
fruits.insert(1, "mango")   # Insert at index
fruits.remove("banana")     # Remove first occurrence
popped = fruits.pop()       # Remove and return last item
fruits.sort()               # Sort in place
fruits.reverse()            # Reverse in place

# List comprehensions
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]


### Dictionaries
python
# Dictionary creation
person = {
    "name": "Alice",
    "age": 20,
    "city": "New York"
}

# Dictionary methods
print(person["name"])           # Access value
print(person.get("age", 0))     # Safe access with default
person["email"] = "alice@email.com"  # Add new key-value
del person["city"]              # Delete key-value
keys = person.keys()            # Get all keys
values = person.values()        # Get all values
items = person.items()          # Get key-value pairs

# Dictionary comprehension
squares_dict = {x: x**2 for x in range(5)}


### Tuples
python
# Tuple creation (immutable)
coordinates = (10, 20)
colors = ("red", "green", "blue")

# Tuple unpacking
x, y = coordinates
first, *rest = colors  # first="red", rest=["green", "blue"]


### Sets
python
# Set creation (unique elements)
unique_numbers = {1, 2, 3, 3, 4}  # {1, 2, 3, 4}
fruits_set = set(["apple", "banana", "apple"])  # {"apple", "banana"}

# Set operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1 | set2)  # Union: {1, 2, 3, 4, 5}
print(set1 & set2)  # Intersection: {3}
print(set1 - set2)  # Difference: {1, 2}


---

## Control Structures

### Conditional Statements
python
# if-elif-else
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "F"

# Ternary operator
status = "pass" if score >= 60 else "fail"

# Multiple conditions
if score >= 80 and score <= 90:
    print("Good job!")

if score < 60 or score > 100:
    print("Invalid score")


### Loops

#### For Loops
python
# Iterating over a list
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# Iterating with index
for i, fruit in enumerate(fruits):
    print(f"{i}: {fruit}")

# Range function
for i in range(5):          # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 8):       # 2, 3, 4, 5, 6, 7
    print(i)

for i in range(0, 10, 2):   # 0, 2, 4, 6, 8
    print(i)

# Iterating over dictionary
person = {"name": "Alice", "age": 20, "city": "NYC"}
for key in person:
    print(f"{key}: {person[key]}")

for key, value in person.items():
    print(f"{key}: {value}")


#### While Loops
python
# Basic while loop
count = 0
while count < 5:
    print(count)
    count += 1

# While with else
i = 0
while i < 3:
    print(i)
    i += 1
else:
    print("Loop completed normally")

# Break and continue
for i in range(10):
    if i == 3:
        continue    # Skip iteration
    if i == 7:
        break      # Exit loop
    print(i)


---

## Functions

### Basic Functions
python
# Function definition
def greet(name):
    return f"Hello, {name}!"

# Function with default parameters
def introduce(name, age=18):
    return f"I'm {name} and I'm {age} years old"

# Function with multiple return values
def calculate(a, b):
    return a + b, a - b, a * b, a / b

sum_val, diff, product, quotient = calculate(10, 5)


### Advanced Function Features
python
# *args and **kwargs
def flexible_function(*args, **kwargs):
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

flexible_function(1, 2, 3, name="Alice", age=20)

# Lambda functions
square = lambda x: x**2
numbers = [1, 2, 3, 4, 5]
squared = list(map(square, numbers))

# Filter and map
evens = list(filter(lambda x: x % 2 == 0, numbers))
doubled = list(map(lambda x: x * 2, numbers))

# Decorators (basic example)
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function call")
        result = func(*args, **kwargs)
        print("After function call")
        return result
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")


---

## Object-Oriented Programming

### Classes and Objects
python
class Student:
    # Class variable
    school_name = "Python University"
    
    def __init__(self, name, age, grade):
        # Instance variables
        self.name = name
        self.age = age
        self.grade = grade
        self.courses = []
    
    def add_course(self, course):
        self.courses.append(course)
    
    def get_info(self):
        return f"{self.name}, {self.age} years old, Grade: {self.grade}"
    
    def __str__(self):
        return f"Student: {self.name}"
    
    def __repr__(self):
        return f"Student('{self.name}', {self.age}, '{self.grade}')"

# Creating objects
student1 = Student("Alice", 20, "A")
student1.add_course("Python Programming")
print(student1.get_info())


### Inheritance
python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"I'm {self.name}, {self.age} years old"

class Student(Person):
    def __init__(self, name, age, student_id):
        super().__init__(name, age)
        self.student_id = student_id
        self.courses = []
    
    def introduce(self):  # Method overriding
        return f"I'm {self.name}, a student with ID {self.student_id}"

class Teacher(Person):
    def __init__(self, name, age, subject):
        super().__init__(name, age)
        self.subject = subject
    
    def introduce(self):
        return f"I'm {self.name}, I teach {self.subject}"


---

## File Handling

### Reading and Writing Files
python
# Writing to a file
with open('example.txt', 'w') as file:
    file.write("Hello, World!\n")
    file.write("This is a Python file.")

# Reading from a file
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)

# Reading line by line
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())

# Appending to a file
with open('example.txt', 'a') as file:
    file.write("\nAppended text")


### Working with CSV
python
import csv

# Writing CSV
data = [
    ['Name', 'Age', 'City'],
    ['Alice', 20, 'NYC'],
    ['Bob', 22, 'LA']
]

with open('people.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Reading CSV
with open('people.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)


---

## Libraries & Modules

### Standard Library Examples
python
# datetime
from datetime import datetime, date
now = datetime.now()
today = date.today()

# math
import math
print(math.pi)
print(math.sqrt(16))

# random
import random
print(random.randint(1, 10))
print(random.choice(['apple', 'banana', 'orange']))

# os
import os
print(os.getcwd())  # Current working directory
os.makedirs('new_folder', exist_ok=True)

# json
import json
data = {"name": "Alice", "age": 20}
json_string = json.dumps(data)
parsed_data = json.loads(json_string)


### Creating Your Own Module
python
# In a file called mymodule.py
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

PI = 3.14159

# In your main file
import mymodule
result = mymodule.add(5, 3)
print(mymodule.PI)

# Or
from mymodule import add, PI
result = add(5, 3)


---

## Best Practices

### Code Style (PEP 8)
python
# Good naming conventions
user_name = "alice"        # snake_case for variables
MAX_SIZE = 100             # UPPER_CASE for constants

class StudentRecord:       # PascalCase for classes
    pass

def calculate_total():     # snake_case for functions
    pass

# Proper spacing
def function_with_parameters(param1, param2, param3):
    if param1 > param2:
        return param1 + param3
    return param2 + param3

# List comprehensions vs loops
# Good: List comprehension for simple cases
squares = [x**2 for x in range(10)]

# Better: Regular loop for complex logic
result = []
for x in range(10):
    if x % 2 == 0:
        processed = complex_function(x)
        result.append(processed)


### Error Handling
python
# Try-except blocks
try:
    number = int(input("Enter a number: "))
    result = 10 / number
    print(f"Result: {result}")
except ValueError:
    print("Please enter a valid number")
except ZeroDivisionError:
    print("Cannot divide by zero")
except Exception as e:
    print(f"An error occurred: {e}")
else:
    print("No errors occurred")
finally:
    print("This always executes")

# Raising custom exceptions
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    if age > 150:
        raise ValueError("Age seems unrealistic")
    return True


---

## Common Patterns

### Working with APIs
python
# Note: Would typically use requests library
# import requests
# 
# response = requests.get('https://api.example.com/data')
# data = response.json()

# Simulating with urllib (built-in)
import urllib.request
import json

try:
    with urllib.request.urlopen('https://api.github.com/users/octocat') as response:
        data = json.loads(response.read())
        print(data['login'])
except Exception as e:
    print(f"Error fetching data: {e}")


### Data Processing
python
# Working with data
students_data = [
    {"name": "Alice", "score": 85, "subject": "Math"},
    {"name": "Bob", "score": 92, "subject": "Math"},
    {"name": "Charlie", "score": 78, "subject": "Science"},
    {"name": "Diana", "score": 96, "subject": "Math"}
]

# Filter and sort
math_students = [s for s in students_data if s["subject"] == "Math"]
sorted_by_score = sorted(math_students, key=lambda x: x["score"], reverse=True)

# Calculate average
math_scores = [s["score"] for s in math_students]
average_score = sum(math_scores) / len(math_scores)

print(f"Average Math score: {average_score:.2f}")


### Generator Functions
python
def fibonacci_generator(n):
    a, b = 0, 1
    count = 0
    while count < n:
        yield a
        a, b = b, a + b
        count += 1

# Using the generator
for num in fibonacci_generator(10):
    print(num, end=" ")


---

## Useful Resources

### Documentation and Learning
- *Official Python Docs*: https://docs.python.org/
- *PEP 8 Style Guide*: https://pep8.org/
- *Python.org Tutorial*: https://docs.python.org/3/tutorial/
- *Real Python*: https://realpython.com/

### Popular Libraries to Explore
- *requests*: HTTP library for APIs
- *pandas*: Data manipulation and analysis
- *numpy*: Numerical computing
- *matplotlib*: Data visualization
- *flask/django*: Web frameworks
- *pytest*: Testing framework

### Development Tools
- *IDEs*: PyCharm, VS Code, Jupyter Notebook
- *Package Management*: pip, conda
- *Virtual Environments*: venv, virtualenv
- *Code Formatting*: black, autopep8

---

## Quick Reference Commands

bash
# Running Python
python script.py
python3 script.py

# Installing packages
pip install package_name
pip install -r requirements.txt

# Virtual environment
python -m venv myenv
source myenv/bin/activate  # On Windows: myenv\Scripts\activate
deactivate

# Python interactive shell
python          # Start Python REPL
python -c "print('Hello')"  # Execute command directly


## Practice Projects Ideas
1. *Calculator*: Basic arithmetic operations
2. *To-Do List*: Add, remove, mark complete tasks
3. *Password Generator*: Generate secure passwords
4. *Weather App*: Fetch weather data from API
5. *File Organizer*: Sort files by extension
6. *Web Scraper*: Extract data from websites
7. *Quiz Game*: Multiple choice questions
8. *Expense Tracker*: Track personal expenses

---

Last updated: [Current Date]
Happy Coding! 🚀
