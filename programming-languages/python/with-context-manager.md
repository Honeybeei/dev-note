# 🧹 `with` Keyword

- [🧹 `with` Keyword](#-with-keyword)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [❓ What is `with` keyword in Python?](#-what-is-with-keyword-in-python)
  - [📜 Basic Syntax](#-basic-syntax)
  - [🤼 Without `with` keyword vs With `with` keyword](#-without-with-keyword-vs-with-with-keyword)
  - [ℹ️ About Context Manager](#ℹ️-about-context-manager)
  - [📚 Built-in Context Managers](#-built-in-context-managers)
    - [📂 File Handling](#-file-handling)
    - [🔒 Thread Locking](#-thread-locking)
    - [🗂️ Temporary Directory](#️-temporary-directory)

## 🔑 Key Words

- `with`
- context manager
- resource management

## 👀 Fast Lookup

- `with` keyword is used for resource management
- It works with **Context managers**

```python
with open('file.txt', 'r') as file:
    print(file.read())

# Automatically closes the file when the block is exited
```

## ❓ What is `with` keyword in Python?

- `with` is a control flow statement
- It simplifies the resource management (like file, locks, database connections, etc.)
- It works with **Context managers**
  - It is an object that takes care of setting up a resource and cleaning it up when it is no longer needed.

## 📜 Basic Syntax

```python
with expression [as variable]:
    with-block
```

- `expression` should return a context manager object
- `variable` is optional
- `with-block` is executed with the context manager object

```python
with open('file.txt', 'r') as file:
    print(file.read())
```

## 🤼 Without `with` keyword vs With `with` keyword

These are the examples of writing to a file.

- Without `with` keyword

```python
file = open('file.txt', 'w')
try:
  file.write('Hello, World!')
finally:
  file.close() # You have to close the file manually
```

- With `with` keyword

```python
with open('file.txt', 'w') as file:
    file.write('Hello, World!')

# The file is automatically closed when the block is exited
```

## ℹ️ About Context Manager

- Context manager is a class that implements `__enter__` and `__exit__` methods
  - `__enter__` method is called when the `with` block starts
    - It initializes the resource and returns it
  - `__exit__` method is called when the `with` block ends
    - It cleans up the resource

```python
class MyContextManager:
    def __enter__(self):
        print("Entering the context")
        # Setup code
        return "Resource"
    
    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting the context")
        # Cleanup code
        if exc_type:
            print(f"Exception occurred: {exc_type}, {exc_value}")
        return False  # Re-raise the exception if one occurred

# Using the custom context manager
with MyContextManager() as resource:
    print(f"Using the resource: {resource}")
    # Uncomment the next line to simulate an exception
    # raise ValueError("Something went wrong!")

# Output:
# Entering the context
# Using the resource: Resource
# Exiting the context
```

## 📚 Built-in Context Managers

### 📂 File Handling

```python
with open('file.txt', 'r') as file:
    content = file.read()
    print(content)
# The file is automatically closed when the block is exited
```

### 🔒 Thread Locking

```python
import threading

lock = threading.Lock()

with lock:
    # Critical section of code
    print("Lock acquired")
# The lock is automatically released when the block is exited
```

### 🗂️ Temporary Directory

```python
import tempfile

with tempfile.TemporaryDirectory() as tmpdirname:
    print('Created temporary directory', tmpdirname)
# The temporary directory and its contents are removed when the block is exited
```

[🔙 Back to the main page](./README.md)
