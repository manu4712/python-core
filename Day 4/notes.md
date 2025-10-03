# Python Fundamentals: Complete Notes

## Comments in Python

Comments are essential for code documentation and readability. Python provides several ways to create comments:

### Single-line Comments
- Use the `#` symbol to create single-line comments[1][4][16]
- Everything after `#` on the same line is ignored by the interpreter
- Can be placed at the beginning of a line or after code on the same line

```python
# This is a single-line comment
print("Hello World")  # This is an inline comment
```

### Multi-line Comments
Python doesn't have a dedicated multi-line comment syntax, but there are two approaches[1][7][10]:

**Method 1: Multiple Single-line Comments (Preferred)**
```python
# This is a multi-line comment
# Each line starts with #
# This method is efficient and preferred
```

**Method 2: Triple Quotes (String Literals)**
```python
"""
This is a multi-line comment using triple quotes.
It's technically a string literal, not a comment.
If not assigned to a variable, it's ignored by Python.
"""

'''
You can also use triple single quotes
for multi-line comments.
'''
```

**Important Note**: Triple quotes create string literals, not true comments. They're commonly used for docstrings but can function as comments when not assigned to variables[1][4][7].

## Variables in Python

### What are Variables?
Variables in Python are **references** or **pointers** to objects in memory, not containers that store values directly[22][28][33]. When you assign a value to a variable, Python:
1. Creates an object in memory containing the value
2. Assigns the variable name as a reference to that object's memory address

```python
x = 42  # Creates an integer object with value 42
print(id(x))  # Shows the memory address/object ID
```

### Variable Naming Rules
Variables must follow specific naming conventions[11]:

**Rules:**
- Must start with a letter (a-z, A-Z) or underscore (_)
- **Cannot** start with a digit
- Can contain letters, digits, and underscores only
- Case-sensitive (age, Age, and AGE are different variables)
- Cannot use Python keywords

**Valid Examples:**
```python
myvar = "John"
my_var = "John"
_my_var = "John"  # Valid but not recommended to start with underscore
myVar = "John"
MYVAR = "John"
myvar2 = "John"
```

**Invalid Examples:**
```python
2myvar = "John"    # Cannot start with digit
my-var = "John"    # Cannot contain hyphen
my var = "John"    # Cannot contain spaces
```

### Underscore Conventions
Understanding underscore usage is important for Python conventions[2][5][8]:

- **Single leading underscore (_var)**: Indicates "internal use" - a naming convention suggesting the variable is for internal use within a class or module
- **Single trailing underscore (var_)**: Used to avoid conflicts with Python keywords (e.g., `class_` instead of `class`)
- **Double leading underscore (__var)**: Triggers name mangling in classes for pseudo-private attributes
- **Double leading and trailing underscore (__var__)**: Reserved for special methods (dunder methods) - avoid for your own variables

**Best Practice**: While starting with underscore is technically allowed, it's not recommended unless you understand the conventions[2][5].

## Data Types in Python

### Dynamic Typing
Python is **dynamically typed**[24][30][32], meaning:
- Variable types are determined at **runtime** based on assigned values
- Variables can change types during execution
- No need to declare variable types explicitly
- Type checking occurs when code runs, not when it's written

```python
x = 42          # x is int
print(type(x))  # <class 'int'>

x = "Hello"     # x is now str  
print(type(x))  # <class 'str'>

x = 3.14        # x is now float
print(type(x))  # <class 'float'>
```

### Primitive Data Types
Python has several built-in primitive data types[6][9][12]:

#### Numeric Types

**1. Integer (int)**
- Represents whole numbers (positive, negative, or zero)
- No limit to how long an integer can be in Python
- Examples: `5`, `-10`, `0`, `1000000`

```python
num1 = 5
print(type(num1))  # <class 'int'>
```

**2. Float (float)**
- Represents real numbers with decimal points
- Accurate up to 15 decimal places
- Examples: `3.14`, `-2.5`, `0.0`

```python
num2 = 3.14
print(type(num2))  # <class 'float'>
```

**3. Complex (complex)**
- Represents complex numbers with real and imaginary parts
- Format: `a + bj` where `a` is real part, `bj` is imaginary part
- Use `j` (not `i`) for the imaginary unit
- Examples: `3+4j`, `2j`, `5+0j`

```python
num3 = 3 + 4j
print(type(num3))  # <class 'complex'>
print(num3.real)   # 3.0 (real part)
print(num3.imag)   # 4.0 (imaginary part)
```

#### Boolean Type

**Boolean (bool)**
- Represents truth values: `True` or `False`
- Subclass of int (True = 1, False = 0)
- Case-sensitive: must be `True` and `False`, not `true` and `false`

```python
is_active = True
is_complete = False
print(type(is_active))  # <class 'bool'>
```

#### String Type

**String (str)**
- Represents textual data (sequences of characters)
- **No separate character type** in Python[23][26][29][37]
- Single characters are strings of length 1
- Immutable (cannot be changed after creation)
- Can use single quotes, double quotes, or triple quotes

```python
text1 = "Hello"
text2 = 'World'
char = 'A'  # This is a string of length 1, not a character type
print(type(char))  # <class 'str'>
print(len(char))   # 1
```

**Important**: Unlike languages like Java or C++, Python has no `char` data type. Everything textual is a string[26][29].

## Object Reference System

### How Python Manages Objects
Python uses a reference-based system for managing objects[22][28][33]:

1. **Object Creation**: When you assign a value, Python creates an object in memory
2. **Variable Assignment**: The variable stores the object's ID/memory address, not the value itself
3. **Object ID**: Each object has a unique identifier accessible via `id()` function

```python
a = 50
b = a
c = 50

print(id(a))  # Same memory address
print(id(b))  # Same memory address  
print(id(c))  # Same memory address (for small integers)

# When we reassign
a = 60
print(id(a))  # Different memory address
print(id(b))  # Still original address
```

### Garbage Collection
Python automatically manages memory through garbage collection[22][25][31]:

- **Reference Counting**: Primary method - when an object's reference count reaches zero, it's immediately deleted
- **Cyclic Garbage Collection**: Secondary method for handling circular references
- **Automatic Process**: Happens automatically when objects are no longer referenced

```python
x = [1, 2, 3]  # Object created, reference count = 1
y = x          # Reference count = 2
del x          # Reference count = 1
y = None       # Reference count = 0, object is garbage collected
```

## Key Corrections and Clarifications

### Misconceptions Corrected:

1. **Triple Quotes**: These create string literals, not true comments. They function as comments only when not assigned to variables[1][4][7].

2. **Underscore Usage**: While starting with underscore is technically allowed, it's not recommended unless you understand Python naming conventions[2][5].

3. **Character Type**: Python has NO character data type. Single characters are strings with length 1[23][26][29].

4. **Variable Storage**: Variables don't store values directly - they store references/pointers to objects in memory[22][28][33].

5. **Dynamic Typing**: Type determination happens at runtime, not compile time. Python performs type checking as code executes[24][30][32].

## Summary

- **Comments**: Use `#` for single-line, multiple `#` for multi-line (preferred), or triple quotes for docstring-style comments
- **Variables**: References to objects in memory, following specific naming rules
- **Data Types**: int, float, complex, bool, str - all determined dynamically at runtime  
- **No char type**: Everything textual is a string
- **Object Management**: Python handles memory automatically through reference counting and garbage collection
- **Dynamic Nature**: Types can change during program execution, providing flexibility but requiring runtime type checking

This foundation provides the essential understanding needed to work effectively with Python's variable and type system.