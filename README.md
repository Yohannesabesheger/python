
# 🔹 `*args` and `**kwargs` in Python – Simplified Summary

## ✅ What are they?
- `*args` and `**kwargs` let you pass **a variable number of arguments** to functions.
- The names (`args`, `kwargs`) are just conventions; you can use any name with the `*` and `**`.

---

## 🔸 `*args` – Non-keyword Arguments
Used to pass **multiple positional arguments**.

```python
def test_var_args(f_arg, *argv):
    print("First:", f_arg)
    for arg in argv:
        print("Another arg:", arg)

test_var_args('one', 'two', 'three')
```

**Output:**
```
First: one
Another arg: two
Another arg: three
```

---

## 🔸 `**kwargs` – Keyword Arguments
Used to pass **multiple named arguments** (as a dictionary).

```python
def greet_me(**kwargs):
    for key, value in kwargs.items():
        print(f"{key} = {value}")

greet_me(name="Yasoob")
```

**Output:**
```
name = Yasoob
```

---

## 🔸 Calling a Function with `*args` / `**kwargs`

```python
def test_args_kwargs(arg1, arg2, arg3):
    print(arg1, arg2, arg3)

# Using *args
args = ("one", 2, 3)
test_args_kwargs(*args)

# Using **kwargs
kwargs = {"arg1": "one", "arg2": 2, "arg3": 3}
test_args_kwargs(**kwargs)
```

---

## 🔸 Argument Order in Function Definition

```python
def some_func(fixed_arg, *args, **kwargs):
    pass
```

---

## 🔸 When to Use?
- Commonly used in:
  - **Function decorators**
  - **Flexible APIs**
  - **Monkey patching** (modifying functions at runtime)

**Example (monkey patching):**

```python
def get_info(self, *args):
    return "Test data"

someclass.get_info = get_info
```

---
