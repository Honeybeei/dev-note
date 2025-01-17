# 😉 Type Hints (Type Annotation)

- [😉 Type Hints (Type Annotation)](#-type-hints-type-annotation)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🤷 Why Use Type Hints?](#-why-use-type-hints)
  - [📚 Basic Syntax](#-basic-syntax)
  - [🔤 Simple Types](#-simple-types)
  - [🚀 Advanced Types (Generic Types)](#-advanced-types-generic-types)
    - [📋 List](#-list)
    - [🔗 Tuple and Set](#-tuple-and-set)
    - [📖 Dict](#-dict)
    - [🔀 Union](#-union)
    - [❓ Optional (Possibly None)](#-optional-possibly-none)
    - [🐍 Let's just stick to the Newest Python Version (3.10+)](#-lets-just-stick-to-the-newest-python-version-310)

## 🔑 Key Words

- Type Hints(Type Annotation)
- Basic Types
- Advanced Types(Generic Types)

## 👀 Fast Lookup

- **Type Hints** are used to specify the type of variables, function arguments, and return values.
- **Basic Types**: `int`, `float`, `str`, `bool`
- **Advanced Types**: `List`, `Dict`, `Tuple`, `Set`, `Union`, `Optional`
- **Just Stick to Python 3.10+**: `list`, `dict`, `tuple`, `set`, `|` for Union and Optional

## 🤷 Why Use Type Hints?

- **Improve Code Readability**
  - Type hints make the code easier to read and understand
  - It helps to understand the function signature and return type
- **Better Tooling Support**
  - Type hints help IDEs to provide better code completion and error checking
- **Easier Maintenance**
  - Type hints reduces ambiguity when working in large projects
- **Static Analysis**
  - Tools like `mypy` can analyze type errors without running the code

## 📚 Basic Syntax

```python
# Function with type hints
def greet(name: str) -> str:
    return f"Hello, {name}!"

def add(a: int, b: int) -> int:
    return a + b

# Type hints for variables
name: str = "Alice"
age: int = 30
```

These are the basic examples of using type hints in Python.

## 🔤 Simple Types

- `int`
- `float`
- `str`
- `bool`

## 🚀 Advanced Types (Generic Types)

Before we dive in, there are some difference in the type hints between Python versions. For example, you need to import `List` and `Dict` from `typing` module. But from Python 3.9, you can use them directly without importing.

> Types which are imported from `typing` module will start with a capital letter. For example, `List`, `Dict`, `Tuple`, etc.
> But the types which are built-in will start with a lowercase letter. For example, `list`, `dict`, `tuple`, etc.

### 📋 List

Python 3.8+

```python
from typing import List

def double_list(lst: List[int]) -> List[int]:
    return [2 * x for x in lst]
```

Python 3.9+

```python
def double_list(lst: list[int]) -> list[int]:
    return [2 * x for x in lst]
```

### 🔗 Tuple and Set

Tuples are immutable lists. Sets are unordered collections of unique elements.

Python 3.8+

```python
from typing import Tuple, Set

def get_first_two(t: Tuple[int, int]) -> Tuple[int, int]:
    return t[:2]

def unique_elements(s: Set[int]) -> Set[int]:
    return s
```

Python 3.9+

```python
def get_first_two(t: tuple[int, int]) -> tuple[int, int]:
    return t[:2]

def unique_elements(s: set[int]) -> set[int]:
    return s
```

### 📖 Dict

Python 3.8+

```python
from typing import Dict

def get_value(d: Dict[str, int], key: str) -> int:
    return d[key]
```

Python 3.9+

```python
def get_value(d: dict[str, int], key: str) -> int:
    return d[key]
```

### 🔀 Union

Union is used to specify that a variable can have multiple types. (this or that or ...)

Python 3.8+

```python
from typing import Union

def this_or_that(x: Union[int, str]) -> str:
    return str(x)
```

Python 3.10+

You can use `|` operator to specify Union types.

```python
def this_or_that(x: int | str) -> str:
    return str(x)
```

### ❓ Optional (Possibly None)

Optional is used to specify that a variable can have a specific type or `None`.

> However, it is recommended to use `Union` instead of `Optional`.

Python 3.8+

```python
from typing import Optional, Union

def bad_practice(x: Optional[str] = None) -> str:
    if x is None:
        return "None"
    return x

def good_practice(x: Union[str, None] = None) -> str:
    if x is None:
        return "None"
    return x
```

Python 3.10+

```python
def good_practice(x: str | None = None) -> str:
    if x is None:
        return "None"
    return x
```

### 🐍 Let's just stick to the Newest Python Version (3.10+)

Sorry 😅 but I will just stick to the newest Python version. Because it is easier to remember and it is the future.

- `list`
- `tuple`
- `set`
- `dict`
- `|` for Union and Optional

[🔙 Back to the main page]( README)
