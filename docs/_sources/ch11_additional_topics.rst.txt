.. _ch11:

================================
Chapter 11: Additional Topics
================================

Precedence and Associativity of Operators in Python
++++++++++++++++++++++++++++++++++++++++++++++++++++

1. What is Operator Precedence
===============================

Operator precedence determines the order in which operators are evaluated in an expression.

.. code-block:: python

    result = 10 + 5 * 2
    print(result)  # 20, not 30

Multiplication (*) has higher precedence than addition (+).


2. What is Operator Associativity
==================================

Associativity determines the direction of evaluation when operators have the same precedence.

.. code-block:: python

    result = 100 / 10 / 2
    print(result)  # 5.0

Division is left-to-right associative: (100 / 10) / 2


3. Using Parentheses to Override Precedence
=============================================

.. code-block:: python

    result = (10 + 5) * 2
    print(result)  # 30

Parentheses explicitly control evaluation order.


4. Arithmetic Operator Precedence
==================================

.. code-block:: python

    result = 2 + 3 * 4 - 5
    print(result)  # 9

Evaluation order: * → + → -


5. Comparison and Logical Precedence
=====================================

.. code-block:: python

    result = 10 > 5 and 5 > 2
    print(result)  # True

Order: Comparison (>) → Logical AND (and)


6. Logical Operator Hierarchy
==============================

.. code-block:: python

    result = True or False and False
    print(result)  # True

Order: not → and → or


7. Assignment Precedence
=========================

.. code-block:: python

    x = y = 10 + 5
    print(x, y)  # 15 15

Assignment (=) has lower precedence than arithmetic operators.


8. Exponentiation Associativity (Right to Left)
================================================

.. code-block:: python

    result = 2 ** 3 ** 2
    print(result)  # 512

Evaluated as: 2 ** (3 ** 2) = 2 ** 9


9. Bitwise Operator Precedence
===============================

.. code-block:: python

    result = 5 & 3 | 2
    print(result)

Bitwise operations follow strict precedence for predictable results.


10. Complex Expression Evaluation Example
==========================================

.. code-block:: python

    result = 5 + 2 ** 3 * 4 > 20 and not False
    print(result)  # True

Step-by-step: Exponentiation → Multiplication → Addition → Comparison → Logical NOT → AND


Python Keywords and Identifiers
+++++++++++++++++++++++++++++++++

1. What are Python Keywords
============================

Keywords are reserved words in Python with predefined meanings that cannot be used as variable or function names.

.. code-block:: python

    import keyword
    print(keyword.kwlist)

These words define Python's syntax and control structures.


2. List of Python Keywords (Core Examples)
===========================================

.. code-block:: python

    import keyword
    for word in keyword.kwlist:
        print(word)

Common keywords:

- Control Flow: if, elif, else, for, while, break, continue
- Function & Class: def, return, class, lambda
- Exception Handling: try, except, finally, raise
- Logical: and, or, not, is, in


3. What are Identifiers
=======================

Identifiers are names used to identify variables, functions, classes, modules, or objects.

.. code-block:: python

    total = 100
    def calculate_sum():
        pass
    class User:
        pass

Here, total, calculate_sum, and User are identifiers.


4. Rules for Identifiers
=========================

An identifier must:

- Start with a letter (a-z, A-Z) or underscore _
- Not start with a digit
- Contain letters, digits, or underscores only
- Not be a Python keyword

.. code-block:: python

    valid_name = 10
    _invalid = 20
    # 1value = 30  # Invalid


5. Case Sensitivity in Identifiers
===================================

Python identifiers are case-sensitive.

.. code-block:: python

    value = 10
    Value = 20
    print(value)  # 10
    print(Value)  # 20

value and Value are treated as two distinct identifiers.


6. Invalid Identifier Examples
===============================

Python enforces strict syntax rules for naming.

.. code-block:: python

    # data = 100      # Starts with digit (Invalid)
    # class = 10       # Keyword (Invalid)
    # my-name = 5      # Special character (Invalid)


7. Naming Conventions (PEP 8 Standard)
=======================================

Standard practices:

- Variables & functions → snake_case
- Classes → PascalCase
- Constants → UPPER_CASE

.. code-block:: python

    # Variable
    total_price = 500

    # Function
    def calculate_total():
        pass

    # Class
    class UserAccount:
        pass


8. Difference Between Keywords and Identifiers
===============================================

Keywords are reserved words in Python, while identifiers are user-defined names.

- Keywords: if, class, return
- Identifiers: count, UserData, my_function


9. Checking if a Word is a Keyword
===================================

.. code-block:: python

    import keyword
    print(keyword.iskeyword("if"))      # True
    print(keyword.iskeyword("value"))   # False

Useful for compilers, linters, and code validators.


10. Real-World Naming Example
==============================

.. code-block:: python

    class OrderProcessor:
        def calculate_tax(self, amount):
            tax_rate = 0.18
            return amount * tax_rate

    processor = OrderProcessor()
    print(processor.calculate_tax(1000))

Demonstrates professionalism and readability using proper identifiers.


Python Asserts
+++++++++++++++

1. What is an Assertion
=======================

An assertion is a debugging aid that tests a condition and raises an error if the condition evaluates to False.

.. code-block:: python

    x = 10
    assert x > 0

If the condition fails, Python raises an AssertionError.


2. Basic Assertion Syntax
==========================

.. code-block:: python

    assert condition

Example:

.. code-block:: python

    age = 18
    assert age >= 18

Program continues only if the condition is true.


3. Assertion with Custom Messages
==================================

.. code-block:: python

    score = 40
    assert score >= 50, "Score must be at least 50 to pass"

Provides clear contextual error information.


4. Assertion Failure Example
=============================

.. code-block:: python

    value = -5
    assert value > 0, "Value must be positive"
    # AssertionError: Value must be positive

Useful during validation and debugging phases.


5. Using Assertions in Functions
=================================

.. code-block:: python

    def calculate_square(num):
        assert isinstance(num, int), "Input must be an integer"
        return num * num

    print(calculate_square(5))

Ensures correct parameter usage.


6. Assertions for Invariant Checks
===================================

.. code-block:: python

    def withdraw(balance, amount):
        assert amount <= balance, "Insufficient balance"
        return balance - amount

    print(withdraw(500, 600))

Guarantees logical consistency during execution.


7. Assertions vs Exception Handling
====================================

Assertions are debugging aids for internal logic, while exceptions handle user input validation.

- Assertions: Can be disabled, for internal logic
- Exceptions: Always active, for user input validation


8. Disabling Assertions in Production
======================================

Assertions can be disabled by running Python with optimization flag:

.. code-block:: bash

    python -O script.py

This removes all assert statements from execution.


9. Advanced Assertion with Complex Logic
=========================================

.. code-block:: python

    def process_data(data):
        assert data is not None and len(data) > 0, "Data cannot be empty"
        return sum(data)

    print(process_data([10, 20, 30]))

Combines multiple conditions in one assertion.


10. Enterprise Use Case: Defensive Programming
===============================================

.. code-block:: python

    def process_order(order):
        assert "id" in order, "Order must contain ID"
        assert order["amount"] > 0, "Order amount must be positive"
        return "Order Processed"

    order = {"id": 101, "amount": 250}
    print(process_order(order))

Ensures internal system contracts remain valid.


Python JSON
++++++++++++

1. What is JSON
===============

JSON (JavaScript Object Notation) is a lightweight data-interchange format used for storing and exchanging structured data.

.. code-block:: python

    {
      "name": "Alice",
      "age": 30,
      "active": true
    }

In Python, JSON is handled using the built-in json module.


2. Importing the JSON Module
=============================

.. code-block:: python

    import json

Provides methods to convert between Python objects and JSON format.


3. Convert Python Object → JSON String (json.dumps)
====================================================

.. code-block:: python

    import json

    data = {"name": "Alice", "age": 30, "city": "Toronto"}
    json_string = json.dumps(data)
    print(json_string)

Serializes Python objects into a JSON-formatted string.


4. Convert JSON String → Python Object (json.loads)
====================================================

.. code-block:: python

    import json

    json_text = '{"name": "Bob", "age": 25}'
    python_obj = json.loads(json_text)
    print(python_obj)
    print(type(python_obj))  # dict

Deserializes JSON string into Python data structures.


5. Writing JSON to a File (json.dump)
======================================

.. code-block:: python

    import json

    data = {
        "product": "Laptop",
        "price": 1200,
        "in_stock": True
    }

    with open("product.json", "w") as file:
        json.dump(data, file)

Stores structured data persistently.


6. Reading JSON from a File (json.load)
========================================

.. code-block:: python

    import json

    with open("product.json", "r") as file:
        data = json.load(file)

    print(data)

Loads JSON data into Python objects.


7. Pretty Printing JSON
=======================

.. code-block:: python

    import json

    data = {"name": "Alice", "skills": ["Python", "AI", "ML"]}
    pretty_json = json.dumps(data, indent=4)
    print(pretty_json)

Improves readability for logs and debugging.


8. Handling Complex Data Types
===============================

.. code-block:: python

    import json
    from datetime import datetime

    data = {"event": "login", "time": str(datetime.now())}
    json_string = json.dumps(data)
    print(json_string)

Non-serializable objects must be converted manually.


9. Sorting JSON Keys
====================

.. code-block:: python

    import json

    data = {"b": 2, "a": 1, "c": 3}
    sorted_json = json.dumps(data, sort_keys=True)
    print(sorted_json)

Useful for consistent API responses and hashing.


10. Enterprise Example: API Response Handling
==============================================

.. code-block:: python

    import json

    def parse_api_response(response):
        try:
            data = json.loads(response)
            return data.get("status"), data.get("payload")
        except json.JSONDecodeError:
            return "error", None

    response = '{"status": "success", "payload": {"id": 101}}'
    print(parse_api_response(response))

Standard pattern for microservices and REST APIs.


Python pip
+++++++++++

1. What is pip
===============

pip is Python's official package manager used to install, upgrade, and manage external libraries and dependencies.

.. code-block:: bash

    pip --version

It connects to the Python Package Index (PyPI) to fetch and install packages.


2. Installing a Package
========================

.. code-block:: bash

    pip install requests

Downloads and installs the requests package and its dependencies into the environment.


3. Upgrading a Package
======================

.. code-block:: bash

    pip install --upgrade requests

Ensures the latest stable version of a package is installed.


4. Uninstalling a Package
==========================

.. code-block:: bash

    pip uninstall requests

Removes the package and related files cleanly.


5. Listing Installed Packages
==============================

.. code-block:: bash

    pip list

Displays all currently installed Python packages in the environment.


6. Viewing Package Information
===============================

.. code-block:: bash

    pip show requests

Provides metadata such as version, location, dependencies, and author details.


7. Installing Specific Package Version
=======================================

.. code-block:: bash

    pip install numpy==1.24.0

Locks installation to an exact version for reproducibility.


8. Using requirements.txt
==========================

Example requirements.txt:

.. code-block:: text

    flask==2.2.3
    requests>=2.25
    numpy

Essential for dependency management in team environments.


9. Freezing Dependencies
=========================

.. code-block:: bash

    pip freeze > requirements.txt

Exports exact installed package versions for deployment or CI/CD pipelines.


10. Enterprise Deployment Example
==================================

.. code-block:: bash

    # Step 1: Create virtual environment
    python -m venv venv

    # Step 2: Activate environment
    source venv/bin/activate   # macOS/Linux
    venv\Scripts\activate      # Windows

    # Step 3: Install dependencies
    pip install -r requirements.txt

This ensures isolated, repeatable, production-grade deployments.


Python *args and **kwargs
+++++++++++++++++++++++++++

1. What are *args and **kwargs
===============================

*args and **kwargs allow a function to accept a variable number of arguments.

- *args → Variable positional arguments
- **kwargs → Variable keyword arguments (key-value pairs)

.. code-block:: python

    def demo(*args, **kwargs):
        print(args)
        print(kwargs)

    demo(1, 2, 3, name="Alice", age=30)

Enables highly flexible function signatures.


2. Using *args (Variable Positional Arguments)
===============================================

.. code-block:: python

    def add_numbers(*args):
        return sum(args)

    print(add_numbers(1, 2, 3, 4))  # 10

All positional arguments are captured as a tuple.


3. Iterating Over *args
========================

.. code-block:: python

    def display_values(*args):
        for value in args:
            print(value)

    display_values("Python", "AI", "ML")

Ideal for functions handling unknown input sizes.


4. Using **kwargs (Variable Keyword Arguments)
===============================================

.. code-block:: python

    def display_profile(**kwargs):
        for key, value in kwargs.items():
            print(f"{key}: {value}")

    display_profile(name="Alice", role="Engineer", location="Toronto")

All keyword arguments are captured as a dictionary.


5. Combining *args and **kwargs
================================

.. code-block:: python

    def process_data(*args, **kwargs):
        print("Positional:", args)
        print("Keyword:", kwargs)

    process_data(10, 20, user="CSP", status="Active")

Supports highly dynamic functions.


6. Order of Parameters
======================

.. code-block:: python

    def example(a, b, *args, c=10, **kwargs):
        print(a, b, args, c, kwargs)

    example(1, 2, 3, 4, key="value")

Correct function signature order: Normal parameters → *args → Default parameters → **kwargs


7. Unpacking Arguments with * and **
=====================================

.. code-block:: python

    def greet(name, age):
        print(f"{name} is {age} years old")

    data = ("Alice", 30)
    greet(*data)

    info = {"name": "Bob", "age": 25}
    greet(**info)

Used for data-driven function execution.


8. Forwarding Arguments to Another Function
=============================================

.. code-block:: python

    def wrapper(*args, **kwargs):
        return calculate(*args, **kwargs)

    def calculate(a, b):
        return a + b

    print(wrapper(5, 10))

Common in decorators and middleware.


9. Dynamic API Handler Example
===============================

.. code-block:: python

    def api_handler(endpoint, *args, **kwargs):
        print(f"Calling {endpoint}")
        print("Params:", args)
        print("Options:", kwargs)

    api_handler("/users", 1, 2, limit=10, sort="asc")

Used in REST clients and flexible service routers.


10. Enterprise-Grade Example
=============================

.. code-block:: python

    def log_event(event_type, *args, **kwargs):
        print(f"Event: {event_type}")
        if args:
            print("Details:", args)
        if kwargs:
            print("Metadata:", kwargs)

    log_event("LOGIN", "UserID:101", ip="192.168.1.1", status="success")

Ideal for dynamic logging, analytics, and telemetry systems.
