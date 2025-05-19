
# Advanced Python Summary: Generators, Decorators, Context Managers, and Async Programming

## Objective
Enhance Python skills by using efficient and powerful features: generators, decorators, context managers, and asynchronous programming.

---

## 1. Generators – Efficient Iterators
**Description:**  
Generators allow you to iterate over large data sets without storing everything in memory. They generate values on the fly using the `yield` keyword, which makes your program more memory-efficient and responsive.

- Use `yield` to return values one at a time.
- Memory-efficient and supports lazy evaluation.

**Example:**
```python
def firstn(n):
    num = 0
    while num < n:
        yield num
        num += 1
```

**Generator Expression:**
```python
squares = (x * x for x in range(10))
```

---

## 2. Decorators – Modify Functions/Methods
**Description:**  
Decorators provide a way to wrap a function to extend or alter its behavior without modifying the actual function code. They are widely used for logging, access control, memoization, and more.

- Add functionality to existing functions without changing their code.
- Use `@decorator_name` syntax.

**Basic Decorator:**
```python
def decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper

@decorator
def say_hello():
    print("Hello!")
```

**Decorator with Arguments:**
```python
def do_twice(func):
    def wrapper(*args, **kwargs):
        func(*args, **kwargs)
        func(*args, **kwargs)
    return wrapper

@do_twice
def greet(name):
    print(f"Hello {name}")
```

---

## 3. Context Managers – Manage Resources
**Description:**  
Context managers simplify resource management tasks like opening/closing files, acquiring/releasing locks, or managing database connections. They ensure proper setup and cleanup using `with` blocks.

- Use `with` to ensure resources (e.g., files) are properly opened/closed.

**Class-based Example:**
```python
class File:
    def __init__(self, name, mode):
        self.file = open(name, mode)
    def __enter__(self):
        return self.file
    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()

with File('demo.txt', 'w') as f:
    f.write('Hello World!')
```

**Using contextlib:**
```python
from contextlib import contextmanager

@contextmanager
def open_file(name):
    f = open(name, 'w')
    try:
        yield f
    finally:
        f.close()

with open_file('demo.txt') as f:
    f.write('Hello World!')
```

---

## 4. Asynchronous Programming – Async & Await
**Description:**  
Async programming enables concurrent execution of tasks, especially useful for IO-bound operations like web requests, file access, or database queries. Python’s `asyncio` library helps manage such tasks efficiently.

- Non-blocking execution for IO-bound tasks.
- Use `async` and `await` with the `asyncio` library.

**Basic Coroutine:**
```python
import asyncio

async def greet(name):
    print(f"Hello {name}")
    await asyncio.sleep(1)
    print(f"Goodbye {name}")

asyncio.run(greet("World"))
```

**Run Multiple Coroutines:**
```python
async def main():
    await asyncio.gather(
        greet("Alice"),
        greet("Bob"),
    )

asyncio.run(main())
```

---

## Benefits Summary

- **Generators:** Save memory, efficient for large data.
- **Decorators:** Clean, reusable modifications.
- **Context Managers:** Safe resource management.
- **Async Programming:** Handles many tasks concurrently without threads.
