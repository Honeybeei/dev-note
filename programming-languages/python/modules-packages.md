# 📦 Modules and Packages

- [📦 Modules and Packages](#-modules-and-packages)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🤔 What is Module and Package in Python?](#-what-is-module-and-package-in-python)
  - [📝 Example](#-example)
  - [🚀 `__init__.py`](#-__init__py)
    - [What to include in `__init__.py`?](#what-to-include-in-__init__py)
  - [📮 Distributing the Package](#-distributing-the-package)

## 🔑 Key Words

## 👀 Fast Lookup

## 🤔 What is Module and Package in Python?

- **Module**: A module is a .py file that contains Python code.
- **Package**: A package is a directory that contains a collection of modules and an `__init__.py` file.

> **Package** = Directory + `__init__.py` file + **modules**(`.py` files)

## 📝 Example

```plaintext
.
├── main.py
├── my_package1         # Package 1
│   ├── __init__.py     # Initialization code for the package
│   ├── module1.py      # Module 1
│   │   ├── function1
│   │   ├── class1
│   │   └── variable1
│   ├── module2.py      # Module 2
│   │   ├── function2
│   │   ├── class2
│   │   └── variable2
│   └── sub_package1    # Subpackage 1
│       ├── __init__.py # Initialization code for the subpackage
│       ├── module5.py  # Module 5
│       └── module6.py  # Module 6
└── my_package2
    ├── __init__.py     # Initialization code for the package
    └── module3.py      # Module 3
        ├── function3
        ├── class3
        └── variable3
```

Let's break down the above example:

- `main.py` is the main script.
- `my_package1` and `my_package2` are packages. They are directories containing modules and an `__init__.py` file.
- `module1.py`, `module2.py`, `module3.py`, `module5.py`, and `module6.py` are modules. They are `.py` files containing Python code.
- `__init__.py` files are used to mark directories as Python package directories and can contain initialization code for the package.

## 🚀 `__init__.py`

- The `__init__.py` file is used to mark a directory as a Python package directory.
- It can be an **empty** file or it can contain Python code that is executed when the package is imported.

### What to include in `__init__.py`?

- **Initialization code**

```python
# my_package1/__init__.py
print("Initializing my_package1")
```

- **Variable and Function definitions**

```python
# my_package1/__init__.py
version = "1.0"
def greet():
    print("Hello from my_package1")
```

- **Sub-modules and Sub-packages imports**

```python
# my_package1/__init__.py
from . import module1
from . import module2
from .sub_package1 import module5
from .sub_package1 import module6
```

or

```python
# my_package1/__init__.py
from .module1 import function1, class1, variable1
from .module2 import function2, class2, variable2
from .sub_package1.module5 import function5
from .sub_package1.module6 import function6
```

- **Package `__all__` variable**

```python
# my_package1/__init__.py
__all__ = ["module1", "module2", "sub_package1"]
```

## 📮 Distributing the Package

... Not Now ... Maybe Later 😅

[🔙 Back to the main page](README.md)
