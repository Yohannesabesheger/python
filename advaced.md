# Advanced Python Summary: Generators, Decorators, Context Managers, and Async Programming

## Objective
Enhance Python skills by using efficient and powerful features: generators, decorators, context managers, and asynchronous programming.

---

## 1. Generators – Efficient Iterators
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
## Generator Expression:

``` python
Copy
Edit
squares = (x * x for x in range(10))
