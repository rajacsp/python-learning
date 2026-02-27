.. _ch05:

=======================
Chapter 5: Python Functions
=======================

Python Functions
++++++++++++++++

1. Defining a Basic Function
=============================

A function is defined using the def keyword followed by the function name and parentheses:

.. code-block:: python

    def greet():
        print("Hello, Python!")

    greet()


2. Function with Parameters
============================

Parameters allow functions to accept external input:

.. code-block:: python

    def greet_user(name):
        print(f"Hello, {name}!")

    greet_user("Alice")


3. Function with Return Value
==============================

The return statement sends a value back to the caller:

.. code-block:: python

    def add(a, b):
        return a + b

    result = add(5, 3)
    print(result)  # Output: 8


4. Default Parameters
=====================

Default values are used when no argument is provided:

.. code-block:: python

    def greet(name="Guest"):
        print(f"Hello, {name}!")

    greet()
    greet("Bob")


5. Keyword Arguments
====================

Arguments can be passed by name for clarity:

.. code-block:: python

    def student_info(name, age):
        print(f"Name: {name}, Age: {age}")

    student_info(age=20, name="Alice")


6. *Variable-Length Arguments (args)
====================================

Allows passing multiple positional arguments:

.. code-block:: python

    def sum_numbers(*args):
        return sum(args)

    print(sum_numbers(1, 2, 3, 4))  # Output: 10


7. **Keyword Variable-Length Arguments (kwargs)
===============================================

Accepts arbitrary keyword arguments:

.. code-block:: python

    def display_profile(**kwargs):
        for key, value in kwargs.items():
            print(f"{key}: {value}")

    display_profile(name="Alice", role="Engineer")


8. Function with Both *args and kwargs
=======================================

Supports flexible function signatures:

.. code-block:: python

    def complete_profile(*args, **kwargs):
        print("Positional:", args)
        print("Keyword:", kwargs)

    complete_profile("Python", level="Advanced", year=2025)


9. Lambda (Anonymous) Functions
================================

Used for short, inline function definitions:

.. code-block:: python

    square = lambda x: x ** 2
    print(square(5))  # Output: 25


10. Recursive Functions
=======================

A function calling itself to solve repetitive problems:

.. code-block:: python

    def factorial(n):
        if n == 0:
            return 1
        return n * factorial(n - 1)

    print(factorial(5))  # Output: 120


Python Function Arguments
++++++++++++++++++++++++++

1. Positional Arguments
=======================

Arguments are passed in the order defined by the function:

.. code-block:: python

    def display_info(name, age):
        print(f"Name: {name}, Age: {age}")

    display_info("Alice", 25)


2. Keyword Arguments
====================

Arguments are passed using parameter names, improving readability and flexibility:

.. code-block:: python

    def display_info(name, age):
        print(f"Name: {name}, Age: {age}")

    display_info(age=25, name="Alice")


3. Default Arguments
====================

Default values are used when arguments are not supplied:

.. code-block:: python

    def greet(name="Guest"):
        print(f"Hello, {name}")

    greet()
    greet("Bob")


4. Required Arguments
=====================

Arguments without defaults must be provided:

.. code-block:: python

    def login(username, password):
        print(f"User: {username}")

    login("admin", "1234")
    # login("admin")  # Raises TypeError


5. *Variable-Length Positional Arguments (args)
===============================================

*args collects extra positional arguments into a tuple:

.. code-block:: python

    def calculate_sum(*numbers):
        return sum(numbers)

    print(calculate_sum(1, 2, 3))      # 6
    print(calculate_sum(5, 10, 15, 5)) # 35


6. **Variable-Length Keyword Arguments (kwargs)
===============================================

**kwargs collects extra keyword arguments into a dictionary:

.. code-block:: python

    def user_profile(**details):
        for key, value in details.items():
            print(f"{key}: {value}")

    user_profile(name="Alice", role="Developer", level="Senior")


7. Combining Normal, *args, and kwargs
=======================================

Order of parameters must follow: normal → *args → kwargs

.. code-block:: python

    def full_profile(name, *skills, **info):
        print("Name:", name)
        print("Skills:", skills)
        print("Details:", info)

    full_profile("Alice", "Python", "ML", age=30, city="Toronto")


8. Positional-Only Arguments (Python 3.8+)
===========================================

Parameters before / must be positional-only:

.. code-block:: python

    def divide(a, b, /):
        return a / b

    print(divide(10, 2))
    # divide(a=10, b=2)  # Raises TypeError


9. Keyword-Only Arguments
==========================

Parameters after * must be specified as keyword arguments:

.. code-block:: python

    def configure(*, mode="light"):
        print(f"Mode: {mode}")

    configure(mode="dark")


10. Argument Unpacking
======================

* and ** can unpack tuples/lists and dictionaries directly into function arguments:

.. code-block:: python

    def multiply(a, b, c):
        return a * b * c

    values = (2, 3, 4)
    print(multiply(*values))  # Output: 24

    data = {"a": 1, "b": 2, "c": 3}
    print(multiply(**data))   # Output: 6


Python Variable Scope
+++++++++++++++++++++

1. Local Scope
==============

Local variables exist only within the function where they are declared:

.. code-block:: python

    def show_value():
        x = 10  # Local variable
        print(x)

    show_value()
    # print(x)  # NameError: x is not defined


2. Global Scope
===============

Global variables are accessible throughout the module:

.. code-block:: python

    x = 20  # Global variable

    def display():
        print(x)

    display()
    print(x)


3. Local vs Global Variable Conflict
====================================

Local variables override global variables within function scope:

.. code-block:: python

    value = 50

    def update():
        value = 10  # Local variable shadows global
        print("Inside function:", value)

    update()
    print("Outside function:", value)


4. Using the global Keyword
============================

The global keyword allows modification of global variables inside functions:

.. code-block:: python

    count = 0

    def increment():
        global count
        count += 1

    increment()
    print(count)  # Output: 1


5. Enclosing Scope (Nested Functions)
=====================================

Nested functions can access variables from their enclosing scope:

.. code-block:: python

    def outer():
        message = "Hello"

        def inner():
            print(message)  # Accessing enclosing variable

        inner()

    outer()


6. Using the nonlocal Keyword
=============================

nonlocal allows modification of variables from the enclosing (but not global) scope:

.. code-block:: python

    def outer():
        count = 0

        def inner():
            nonlocal count
            count += 1
            print(count)

        inner()
        inner()

    outer()


7. LEGB Rule (Scope Resolution Order)
======================================

Python resolves variables using the LEGB rule:

- Local
- Enclosing
- Global
- Built-in

.. code-block:: python

    x = "Global"

    def outer():
        x = "Enclosing"

        def inner():
            x = "Local"
            print(x)

        inner()

    outer()


8. Built-in Scope
=================

Built-in functions and exceptions reside in the built-in scope:

.. code-block:: python

    print(len([1, 2, 3]))  # Built-in function


9. Scope Inside Loops
=====================

Unlike some languages, Python loop variables are not block-scoped:

.. code-block:: python

    for i in range(3):
        loop_var = i

    print(loop_var)  # Accessible outside loop


10. Practical Example of Scope Management
==========================================

Demonstrates coordinated use of local, enclosing, and global scopes:

.. code-block:: python

    total = 100

    def calculate():
        total = 50

        def adjust():
            nonlocal total
            total += 10

        adjust()
        return total

    print(calculate())  # Output: 60
    print(total)        # Output: 100


Python Global Keyword
+++++++++++++++++++++

1. Basic Use of Global Variables
=================================

Global variables are declared outside functions and are readable within functions by default:

.. code-block:: python

    count = 10

    def display():
        print(count)

    display()  # Output: 10


2. Modifying Global Variable Without global (Error Case)
========================================================

Assigning to a variable inside a function makes it local unless explicitly declared global:

.. code-block:: python

    value = 5

    def update():
        value = value + 1  # UnboundLocalError


3. Using global to Modify Global Variables
===========================================

The global keyword allows direct modification of a global variable:

.. code-block:: python

    counter = 0

    def increment():
        global counter
        counter += 1

    increment()
    print(counter)  # Output: 1


4. Global Variable Across Multiple Functions
=============================================

A global variable can be shared and updated across multiple functions:

.. code-block:: python

    status = "inactive"

    def activate():
        global status
        status = "active"

    def show_status():
        print(status)

    activate()
    show_status()  # Output: active


5. Global Keyword Inside Nested Functions
==========================================

global always refers to the module-level scope, even when used inside nested functions:

.. code-block:: python

    x = 100

    def outer():
        def inner():
            global x
            x = 200

        inner()

    outer()
    print(x)  # Output: 200


6. Difference Between global and nonlocal
==========================================

- global → Refers to module-level variable
- nonlocal → Refers to nearest enclosing function scope

.. code-block:: python

    x = 50

    def outer():
        x = 10
        
        def inner():
            global x
            x = 99

        inner()
        print("Outer x:", x)

    outer()
    print("Global x:", x)


7. Tracking State Using Global Variables
=========================================

Used for maintaining application-wide counters or shared state:

.. code-block:: python

    requests = 0

    def handle_request():
        global requests
        requests += 1

    handle_request()
    handle_request()
    print(requests)  # Output: 2


8. Global Variable with Conditional Logic
==========================================

Global variables often manage configuration state:

.. code-block:: python

    mode = "light"

    def toggle_mode():
        global mode
        if mode == "light":
            mode = "dark"
        else:
            mode = "light"

    toggle_mode()
    print(mode)  # Output: dark


9. Avoiding Global Abuse (Best Practice Warning)
================================================

Mutable objects can be modified without global, reducing global keyword dependency:

.. code-block:: python

    config = {"theme": "dark"}

    def update_config(new_theme):
        config["theme"] = new_theme  # No global keyword needed


10. Best Practice: Encapsulation Instead of Global
==================================================

Encapsulation is preferred over global variables in production systems for maintainability and testability:

.. code-block:: python

    class Counter:
        def __init__(self):
            self.value = 0

        def increment(self):
            self.value += 1

    counter = Counter()
    counter.increment()
    print(counter.value)  # Output: 1


Python Recursion
++++++++++++++++

1. Basic Recursive Function
============================

A recursive function calls itself to solve a smaller instance of the same problem:

.. code-block:: python

    def print_numbers(n):
        if n == 0:
            return
        print(n)
        print_numbers(n - 1)

    print_numbers(5)


2. Base Case and Recursive Case
================================

Every recursive function must define a base case to prevent infinite calls:

.. code-block:: python

    def factorial(n):
        if n == 0:          # Base case
            return 1
        return n * factorial(n - 1)  # Recursive case

    print(factorial(5))  # Output: 120


3. Recursive Sum of Numbers
============================

Demonstrates problem decomposition through recursion:

.. code-block:: python

    def sum_n(n):
        if n == 1:
            return 1
        return n + sum_n(n - 1)

    print(sum_n(5))  # Output: 15


4. Recursive Fibonacci Series
==============================

Classic example of overlapping subproblems in recursion:

.. code-block:: python

    def fibonacci(n):
        if n <= 1:
            return n
        return fibonacci(n - 1) + fibonacci(n - 2)

    print(fibonacci(6))  # Output: 8


5. Recursion vs Iteration Comparison
====================================

Iteration often provides better performance and memory efficiency than deep recursion:

.. code-block:: python

    def factorial_iterative(n):
        result = 1
        for i in range(1, n + 1):
            result *= i
        return result

    print(factorial_iterative(5))  # 120


6. Recursive Traversal of List
===============================

Recursion is useful for navigating hierarchical or nested data:

.. code-block:: python

    def print_list(lst):
        if not lst:
            return
        print(lst[0])
        print_list(lst[1:])

    print_list([1, 2, 3, 4])


7. Recursive String Reversal
=============================

Illustrates recursive manipulation of sequences:

.. code-block:: python

    def reverse_string(text):
        if len(text) == 0:
            return text
        return reverse_string(text[1:]) + text[0]

    print(reverse_string("Python"))  # Output: nohtyP


8. Recursion Limit Error
=========================

Python enforces a recursion limit to prevent stack overflow:

.. code-block:: python

    def infinite_recursion():
        return infinite_recursion()

    # infinite_recursion()  # Raises RecursionError


9. Checking Recursion Depth
============================

System recursion limits can be queried and adjusted cautiously:

.. code-block:: python

    import sys

    print(sys.getrecursionlimit())  # Default ~1000


10. Optimizing Recursion with Memoization
==========================================

Memoization dramatically improves performance by caching results:

.. code-block:: python

    from functools import lru_cache

    @lru_cache(maxsize=None)
    def fibonacci(n):
        if n <= 1:
            return n
        return fibonacci(n - 1) + fibonacci(n - 2)

    print(fibonacci(30))  # Optimized recursion


Python Modules
++++++++++++++

1. What is a Module
===================

A module is a file containing Python code (functions, variables, classes) that can be imported and reused in other programs:

.. code-block:: python

    # file: math_utils.py
    def add(a, b):
        return a + b


2. Importing a Module
=====================

The import keyword loads the entire module and accesses its content using dot notation:

.. code-block:: python

    import math

    print(math.sqrt(25))  # Output: 5.0


3. Importing Specific Functions from a Module
==============================================

Imports only selected items, reducing namespace clutter:

.. code-block:: python

    from math import sqrt, pow

    print(sqrt(16))     # Output: 4.0
    print(pow(2, 3))    # Output: 8.0


4. Renaming a Module using as
==============================

Useful for improving readability or avoiding name conflicts:

.. code-block:: python

    import math as m

    print(m.pi)     # Output: 3.141592653589793


5. Creating and Using a Custom Module
======================================

Custom modules help organize reusable logic:

.. code-block:: python

    # file: calculator.py
    def multiply(a, b):
        return a * b

    # main.py
    import calculator

    print(calculator.multiply(4, 5))  # Output: 20


6. Using __name__ in Modules
=============================

Ensures code runs only when the file is executed directly, not when imported:

.. code-block:: python

    # file: demo.py
    def main():
        print("Main function executed")

    if __name__ == "__main__":
        main()


7. Built-in Modules Example
============================

Python provides rich built-in modules like os, sys, math, datetime, and random:

.. code-block:: python

    import datetime

    today = datetime.date.today()
    print(today)


8. Exploring Module Content with dir()
=======================================

Lists all available attributes and methods inside a module:

.. code-block:: python

    import math

    print(dir(math))


9. Using help() for Module Documentation
=========================================

Displays detailed documentation of a module and its components:

.. code-block:: python

    import math

    help(math)


10. Module Search Path (sys.path)
=================================

Shows directories Python searches to locate modules, including:

- Current directory
- Standard library path
- Site-packages

.. code-block:: python

    import sys

    print(sys.path)


Python Package
++++++++++++++

1. What is a Package
====================

A package is a collection of Python modules organized in a directory hierarchy, enabling structured and scalable code organization:

.. code-block:: python

    my_package/
    │── __init__.py
    │── module1.py
    │── module2.py

The presence of __init__.py indicates that the directory is a Python package.


2. Creating a Basic Package
===========================

Packages allow logical grouping of related modules:

.. code-block:: python

    # my_package/module1.py
    def greet():
        return "Hello from module1"

    # main.py
    import my_package.module1

    print(my_package.module1.greet())


3. Importing from a Package
============================

Enables direct access to specific functions or classes within a package:

.. code-block:: python

    from my_package.module1 import greet

    print(greet())


4. Using init.py for Initialization
====================================

__init__.py controls what gets exposed when the package is imported:

.. code-block:: python

    # my_package/__init__.py
    from .module1 import greet


5. Sub-packages Structure
=========================

Packages can contain nested sub-packages for large systems:

.. code-block:: python

    my_package/
    │── __init__.py
    │── analytics/
    │   ├── __init__.py
    │   └── stats.py


6. Relative Imports Inside a Package
====================================

Relative imports use:

- . current package
- .. parent package

Ensures internal module cohesion:

.. code-block:: python

    from my_package.analytics.stats import calculate_mean


7. Absolute Imports in Packages
================================

Preferred in production for clarity and maintainability:

.. code-block:: python

    from my_package.analytics.stats import calculate_mean


8. Installing External Packages with pip
=========================================

External packages extend Python's functionality:

.. code-block:: python

    pip install requests

    import requests

    response = requests.get("https://api.example.com")
    print(response.status_code)


9. Viewing Installed Packages
==============================

Displays all packages installed in the Python environment:

.. code-block:: bash

    pip list


10. Packaging a Custom Project (Setup File)
============================================

This enables distribution and installation of your package via PyPI or internal repositories:

.. code-block:: python

    # setup.py
    from setuptools import setup, find_packages

    setup(
        name="mypackage",
        version="1.0",
        packages=find_packages()
    )


Python Main Function
++++++++++++++++++++

1. Purpose of the Main Function
================================

In Python, the "main function" is a conventional entry point that controls program execution flow:

.. code-block:: python

    def main():
        print("Program started")

    main()

This provides a clear structure and separation of execution logic.


2. Using if __name__ == "__main__"
==================================

This ensures the main logic runs only when the file is executed directly, not when imported:

.. code-block:: python

    def main():
        print("Main function executed")

    if __name__ == "__main__":
        main()


3. Why __name__ Works
=====================

- When run directly → __main__
- When imported → module name

This enables safe reusability of scripts as modules:

.. code-block:: python

    print(__name__)


4. Main Function with Parameters
=================================

The main function can accept arguments like any other function:

.. code-block:: python

    def main(name):
        print(f"Welcome, {name}")

    if __name__ == "__main__":
        main("Alice")


5. Main Function for Program Flow Control
==========================================

The main function orchestrates program execution in a clean, readable order:

.. code-block:: python

    def process_data():
        print("Processing data...")

    def main():
        print("Initializing system...")
        process_data()

    if __name__ == "__main__":
        main()


6. Using Main with Command-Line Arguments
==========================================

Allows integration with command-line tools and automation workflows:

.. code-block:: python

    import sys

    def main():
        print("Arguments received:", sys.argv)

    if __name__ == "__main__":
        main()


7. Separating Business Logic from Entry Point
==============================================

Improves modularity and testability:

.. code-block:: python

    def calculate_total(a, b):
        return a + b

    def main():
        result = calculate_total(10, 20)
        print("Total:", result)

    if __name__ == "__main__":
        main()


8. Main Function in Large Applications
=======================================

Supports structured application life-cycle management:

.. code-block:: python

    def initialize():
        print("System initialized")

    def run():
        print("Application running")

    def shutdown():
        print("System shutdown")

    def main():
        initialize()
        run()
        shutdown()

    if __name__ == "__main__":
        main()


9. Main Function with Error Handling
====================================

Encapsulates exception handling at the entry level:

.. code-block:: python

    def main():
        try:
            print("Executing task...")
        except Exception as e:
            print("Error occurred:", e)

    if __name__ == "__main__":
        main()


10. Production-Ready Main Template
==================================

Standard best practice for scalable, maintainable Python applications:

.. code-block:: python

    def main():
        """Application entry point"""
        print("Application started")

    if __name__ == "__main__":
        main()
