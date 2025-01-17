# 📜 DocStrings

- [📜 DocStrings](#-docstrings)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🧐 What is a Docstring?](#-what-is-a-docstring)
  - [🔤 Basic Syntax](#-basic-syntax)
  - [🔍 Google Style Docstring](#-google-style-docstring)
    - [⚙️ Function Docstring](#️-function-docstring)
    - [🗂️ Class Docstring](#️-class-docstring)
    - [📦 Module Docstring](#-module-docstring)

## 🔑 Key Words

- Docstring
- String Literal
- `__doc__`
- `help()`
- Google Style Docstring

## 👀 Fast Lookup

- **Docstrings** are a way of documenting your Python code.
- They are a **string literal** that occurs as the first statement in a module, function, class, or method definition.
- They can be accessed using the `__doc__` attribute or the `help()` function at runtime.
- I will use **Google Style Docstring** for my Python projects.

## 🧐 What is a Docstring?

- Docstrings are a way of documenting your Python code.
- They are a **string literal** that occurs as the first statement in a module, function, class, or method definition.
- They can be accessed using the `__doc__` attribute or the `help()` function at runtime.

```python
def my_function():
    """This is a docstring."""
    pass

print(my_function.__doc__)        # Output: This is a docstring.
print(help(my_function))          # Output: This is a docstring.
print(type(my_function.__doc__))  # Output: <class 'str'>
```

## 🔤 Basic Syntax

- Docstrings are enclosed in triple quotes (`""" """` or `''' '''`).
- Use `r""" """` if the docstring contains backslashes.
- They are placed directly after the **function**, **method**, **class**, or **module** definition.

```python
def my_function():
    """This is a docstring."""
    pass

class MyClass:
    r"""Backslashes (\) are ignored in raw triple double quotes."""

    def my_method(self):
        """This is a method docstring."""
        pass
```

## 🔍 Google Style Docstring

I will use this style for my Python projects.

### ⚙️ Function Docstring

```python
def add_numbers(a, b):
    """Adds two numbers together.

    Args:
        a (int or float): The first number.
        b (int or float): The second number.

    Returns:
        int or float: The sum of `a` and `b`.

    Raises:
        TypeError: If `a` or `b` is not an integer or float.

    Examples:
        >>> add_numbers(2, 3)
        5
        >>> add_numbers(2.5, 3.5)
        6.0
    """
    if not isinstance(a, (int, float)) or not isinstance(b, (int, float)):
        raise TypeError("Both arguments must be numbers.")
    return a + b

```

### 🗂️ Class Docstring

```python
class Rectangle:
    """Represents a rectangle shape.

    Attributes:
        width (float): The width of the rectangle.
        height (float): The height of the rectangle.
    """

    def __init__(self, width, height):
        """Initializes a new Rectangle instance.

        Args:
            width (float): The width of the rectangle.
            height (float): The height of the rectangle.

        Raises:
            ValueError: If `width` or `height` is negative.
        """
        if width < 0 or height < 0:
            raise ValueError("Width and height must be non-negative.")
        self.width = width
        self.height = height

    def area(self):
        """Calculates the area of the rectangle.

        Returns:
            float: The area calculated as `width * height`.

        Examples:
            >>> rect = Rectangle(3, 4)
            >>> rect.area()
            12
        """
        return self.width * self.height
```

### 📦 Module Docstring

Create a `geometry.py` file with the following content:

```python
"""Geometry module for shape calculations.

This module provides classes and functions to perform calculations on different geometric shapes like rectangles and circles.

Classes:
    Rectangle
    Circle

Functions:
    calculate_distance(point1, point2)
"""

import math

class Rectangle:
    """Represents a rectangle shape."""
    # Class implementation...

class Circle:
    """Represents a circle shape."""
    # Class implementation...

def calculate_distance(point1, point2):
    """Calculates the Euclidean distance between two points.

    Args:
        point1 (tuple): The first point as (x, y).
        point2 (tuple): The second point as (x, y).

    Returns:
        float: The distance between `point1` and `point2`.

    Examples:
        >>> calculate_distance((0, 0), (3, 4))
        5.0
    """
    return math.hypot(point2[0] - point1[0], point2[1] - point1[1])
```

[🔙 Back to the main page](./README.md)
