.. _ch09:

==================================
Chapter 9: Python Advanced Topics
==================================

List Comprehension
++++++++++++++++++

Python List Comprehension is a high-performance, declarative construct for generating lists through compact expressions. It replaces verbose iterative patterns with expressive, memory-efficient, and semantically rich syntax.

Basic List Comprehension
=========================

.. code-block:: python

    squares = [x**2 for x in range(5)]
    # Equivalent to:
    squares = []
    for x in range(5):
        squares.append(x**2)


Conditional Filtering
======================

.. code-block:: python

    even_numbers = [x for x in range(10) if x % 2 == 0]


Nested List Comprehensions
===========================

.. code-block:: python

    matrix = [[i * j for j in range(3)] for i in range(3)]


List Comprehension with Function Calls
=======================================

.. code-block:: python

    def transform(x):
        return x * 10

    result = [transform(x) for x in range(5)]


Multiple Conditions
===================

.. code-block:: python

    result = [x for x in range(20) if x > 5 if x % 2 == 0]


If-Else Expressions
====================

.. code-block:: python

    status = ["even" if x % 2 == 0 else "odd" for x in range(5)]


Advanced Pattern: Flattening Lists
===================================

.. code-block:: python

    nested = [[1, 2], [3, 4], [5]]
    flat = [item for sublist in nested for item in sublist]


Data Cleaning Pipeline Example
===============================

.. code-block:: python

    raw = ["  apple ", " Banana", "cherry "]
    cleaned = [item.strip().lower() for item in raw]


Combining with zip()
====================

.. code-block:: python

    pairs = [(x, y) for x, y in zip([1,2], [3,4])]


Dictionary Creation via List Comprehension
===========================================

.. code-block:: python

    keys = ["a", "b"]
    values = [1, 2]
    data = {k: v for k, v in zip(keys, values)}


Python Lambda / Anonymous Function
++++++++++++++++++++++++++++++++++++

1. What is a Lambda Function
=============================

A lambda function is a small anonymous function defined using the lambda keyword:

.. code-block:: python

    square = lambda x: x ** 2
    print(square(5))  # Output: 25

Lambda functions are used for concise, one-line operations.


2. Lambda with Multiple Arguments
==================================

.. code-block:: python

    add = lambda a, b: a + b
    print(add(10, 5))  # Output: 15


3. Lambda Without Assignment (Inline Usage)
============================================

.. code-block:: python

    print((lambda x, y: x * y)(4, 5))  # Output: 20


4. Lambda with map()
====================

.. code-block:: python

    numbers = [1, 2, 3, 4]

    squares = list(map(lambda x: x ** 2, numbers))
    print(squares)  # Output: [1, 4, 9, 16]


5. Lambda with filter()
=======================

.. code-block:: python

    numbers = [1, 2, 3, 4, 5, 6]

    even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
    print(even_numbers)  # Output: [2, 4, 6]


6. Lambda with reduce()
=======================

.. code-block:: python

    from functools import reduce

    numbers = [1, 2, 3, 4]

    total = reduce(lambda x, y: x + y, numbers)
    print(total)  # Output: 10


7. Lambda for Sorting Key
==========================

.. code-block:: python

    students = [("Alice", 85), ("Bob", 72), ("Charlie", 90)]

    students.sort(key=lambda x: x[1])
    print(students)


8. Lambda in List Comprehension Context
========================================

.. code-block:: python

    multipliers = [(lambda x: x * n) for n in range(1, 4)]

    print(multipliers)


9. Lambda vs Normal Function
=============================

.. code-block:: python

    def square_func(x):
        return x ** 2

    square_lambda = lambda x: x ** 2

    print(square_func(4))     # 16
    print(square_lambda(4))   # 16


10. Real-World Lambda Example
=============================

.. code-block:: python

    employees = [
        {"name": "Alice", "salary": 5000},
        {"name": "Bob", "salary": 3000},
        {"name": "Charlie", "salary": 7000}
    ]

    highest_paid = max(employees, key=lambda emp: emp["salary"])
    print(highest_paid)


Python Iterators
++++++++++++++++

1. What is an Iterator
======================

An iterator is an object that allows traversal through all elements of a collection, one element at a time:

.. code-block:: python

    numbers = [1, 2, 3, 4]
    iterator = iter(numbers)

    print(next(iterator))  # 1
    print(next(iterator))  # 2

An iterator follows two core methods: __iter__() and __next__().


2. Iterable vs Iterator
=======================

.. code-block:: python

    data = [10, 20, 30]

    print(iter(data))     # Iterable converted to iterator
    print(isinstance(data, list))  # Iterable

- Iterable → Can be looped over
- Iterator → Produces values one-by-one


3. Using next() with Iterators
===============================

.. code-block:: python

    items = ["A", "B", "C"]
    it = iter(items)

    print(next(it))
    print(next(it))
    print(next(it))


4. StopIteration Exception
===========================

.. code-block:: python

    items = [1, 2]
    it = iter(items)

    print(next(it))
    print(next(it))
    # print(next(it))  # Raises StopIteration


5. Iterators in for Loops
==========================

.. code-block:: python

    colors = ["red", "green", "blue"]

    for color in colors:
        print(color)


6. Creating Custom Iterator Class
==================================

.. code-block:: python

    class CountUp:
        def __init__(self, limit):
            self.limit = limit
            self.current = 0

        def __iter__(self):
            return self

        def __next__(self):
            if self.current < self.limit:
                self.current += 1
                return self.current
            raise StopIteration

    counter = CountUp(3)

    for number in counter:
        print(number)


7. Infinite Iterator Example
=============================

.. code-block:: python

    class InfiniteNumbers:
        def __iter__(self):
            self.num = 0
            return self

        def __next__(self):
            self.num += 1
            return self.num


8. Iterator from Built-in Functions
====================================

.. code-block:: python

    data = "Python"

    it = iter(data)
    print(list(it))  # ['P', 'y', 't', 'h', 'o', 'n']


9. Checking if an Object is an Iterator
========================================

.. code-block:: python

    from collections.abc import Iterator

    numbers = iter([1, 2, 3])
    print(isinstance(numbers, Iterator))  # True


10. Real-World Iterator Example
================================

.. code-block:: python

    class FileLineReader:
        def __init__(self, filename):
            self.file = open(filename, "r")

        def __iter__(self):
            return self

        def __next__(self):
            line = self.file.readline()
            if line:
                return line.strip()
            self.file.close()
            raise StopIteration

    for line in FileLineReader("data.txt"):
        print(line)


Python Generators
++++++++++++++++++

1. What is a Generator
======================

A generator is a special type of function that returns an iterator and yields values one at a time using the yield keyword:

.. code-block:: python

    def simple_generator():
        yield 1
        yield 2
        yield 3

    gen = simple_generator()
    print(next(gen))  # 1
    print(next(gen))  # 2

Generators produce values lazily, improving memory efficiency.


2. Generator vs Normal Function
================================

.. code-block:: python

    def normal_function():
        return 10
        return 20

    def generator_function():
        yield 10
        yield 20

    print(normal_function())          # 10
    print(list(generator_function())) # [10, 20]


3. Iterating Over a Generator
==============================

.. code-block:: python

    def count_up(n):
        for i in range(1, n + 1):
            yield i

    for num in count_up(5):
        print(num)


4. Generator State Preservation
================================

.. code-block:: python

    def demo():
        print("Start")
        yield 1
        print("Resume")
        yield 2

    g = demo()
    print(next(g))
    print(next(g))


5. Memory Efficiency of Generators
===================================

.. code-block:: python

    def large_numbers():
        for i in range(1000000):
            yield i

    gen = large_numbers()
    print(next(gen))
    print(next(gen))


6. Generator Expression
=======================

.. code-block:: python

    squares = (x ** 2 for x in range(5))
    print(list(squares))  # [0, 1, 4, 9, 16]


7. Using Generators with next()
================================

.. code-block:: python

    def alpha_generator():
        yield "A"
        yield "B"
        yield "C"

    gen = alpha_generator()
    print(next(gen))
    print(next(gen))


8. Infinite Generator
=====================

.. code-block:: python

    def infinite_counter():
        num = 1
        while True:
            yield num
            num += 1

    counter = infinite_counter()
    print(next(counter))
    print(next(counter))


9. Generator with try...finally
================================

.. code-block:: python

    def resource_handler():
        try:
            yield "Using resource"
        finally:
            print("Resource released")

    gen = resource_handler()
    print(next(gen))


10. Real-World Generator Example
=================================

.. code-block:: python

    def read_large_file(filename):
        with open(filename, "r") as file:
            for line in file:
                yield line.strip()

    for line in read_large_file("data.txt"):
        print(line)


Python Namespace and Scope
+++++++++++++++++++++++++++

1. What is a Namespace
======================

A namespace is a container that holds identifiers (variables, functions, objects) and maps them to their corresponding values:

.. code-block:: python

    a = 10

Here, a resides in a namespace and points to the value 10.

Types of namespaces:

- Built-in namespace
- Global namespace
- Local namespace


2. Built-in Namespace
=====================

.. code-block:: python

    print(len([1, 2, 3]))
    print(type(100))

These functions belong to the built-in namespace and are always available.


3. Global Namespace
===================

.. code-block:: python

    x = 50  # Global variable

    def show():
        print(x)

    show()

Global variables are accessible throughout the module.


4. Local Namespace
==================

.. code-block:: python

    def calculate():
        y = 20  # Local variable
        print(y)

    calculate()
    # print(y)  # NameError


5. Accessing Namespace Using globals()
=======================================

.. code-block:: python

    x = 100

    print(globals()["x"])  # Output: 100


6. Accessing Namespace Using locals()
======================================

.. code-block:: python

    def demo():
        a = 10
        b = 20
        print(locals())

    demo()


7. LEGB Rule (Scope Resolution Order)
======================================

Python resolves variable names in the following order:

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


8. Enclosing Namespace
======================

.. code-block:: python

    def outer():
        message = "Hello"
        def inner():
            print(message)
        inner()

    outer()


9. Modifying Enclosing Variables with nonlocal
===============================================

.. code-block:: python

    def counter():
        value = 0
        def increment():
            nonlocal value
            value += 1
            return value
        return increment

    count = counter()
    print(count())
    print(count())


10. Namespace Lifecycle Demonstration
======================================

.. code-block:: python

    x = "Global"

    def test():
        x = "Local"
        print("Inside:", x)

    test()
    print("Outside:", x)


Python Closures
++++++++++++++++

1. What is a Closure
====================

A closure is a function that remembers and has access to variables from its enclosing scope even after the outer function has finished execution:

.. code-block:: python

    def outer():
        message = "Hello"
        
        def inner():
            return message

        return inner

    func = outer()
    print(func())  # Output: Hello


2. Basic Closure Structure
===========================

.. code-block:: python

    def multiplier(x):
        def multiply(y):
            return x * y
        return multiply

    times2 = multiplier(2)
    print(times2(5))  # Output: 10


3. Closure Retaining State
===========================

.. code-block:: python

    def counter():
        count = 0

        def increment():
            nonlocal count
            count += 1
            return count

        return increment

    c = counter()
    print(c())  # 1
    print(c())  # 2


4. nonlocal in Closures
=======================

.. code-block:: python

    def power(base):
        exponent = 2

        def calculate():
            nonlocal exponent
            exponent += 1
            return base ** exponent

        return calculate

    p = power(2)
    print(p())
    print(p())


5. Closure vs Global Variable
==============================

.. code-block:: python

    def using_closure():
        factor = 10
        return lambda x: x * factor

    print(using_closure()(5))


6. Multiple Closures from Same Function
========================================

.. code-block:: python

    def make_adder(x):
        def adder(y):
            return x + y
        return adder

    add5 = make_adder(5)
    add10 = make_adder(10)

    print(add5(3))    # 8
    print(add10(3))   # 13


7. Inspecting Closure Variables
================================

.. code-block:: python

    def outer():
        value = 42

        def inner():
            return value

        return inner

    func = outer()
    print(func.__closure__[0].cell_contents)  # 42


8. Closures as Function Factories
==================================

.. code-block:: python

    def logger(prefix):
        def log(message):
            print(f"{prefix}: {message}")
        return log

    info_logger = logger("INFO")
    error_logger = logger("ERROR")

    info_logger("System started")
    error_logger("System failed")


9. Closure in Decorators (Foundation Pattern)
==============================================

.. code-block:: python

    def my_decorator(func):
        def wrapper(*args, **kwargs):
            print("Before execution")
            return func(*args, **kwargs)
        return wrapper


10. Real-World Closure Example
===============================

.. code-block:: python

    def threshold_checker(threshold):
        def check(value):
            return value > threshold
        return check

    high_temp = threshold_checker(40)

    print(high_temp(35))  # False
    print(high_temp(45))  # True


Python Decorators
++++++++++++++++++

1. What is a Decorator
======================

A decorator is a function that modifies the behavior of another function without changing its source code:

.. code-block:: python

    def my_decorator(func):
        def wrapper():
            print("Before function execution")
            func()
            print("After function execution")
        return wrapper

    @my_decorator
    def say_hello():
        print("Hello")

    say_hello()


2. Decorator Without @ Syntax
==============================

.. code-block:: python

    def greet():
        print("Welcome")

    greet = my_decorator(greet)
    greet()


3. Decorator with Arguments
============================

.. code-block:: python

    def log_decorator(func):
        def wrapper(*args, **kwargs):
            print("Arguments:", args, kwargs)
            return func(*args, **kwargs)
        return wrapper

    @log_decorator
    def add(a, b):
        return a + b

    print(add(5, 3))


4. Chaining Multiple Decorators
================================

.. code-block:: python

    def bold(func):
        def wrapper():
            print("<b>")
            func()
            print("</b>")
        return wrapper

    def italic(func):
        def wrapper():
            print("<i>")
            func()
            print("</i>")
        return wrapper

    @bold
    @italic
    def display():
        print("Text")

    display()


5. Decorator with Return Value
===============================

.. code-block:: python

    def uppercase(func):
        def wrapper():
            result = func()
            return result.upper()
        return wrapper

    @uppercase
    def message():
        return "hello world"

    print(message())


6. Decorator Preserving Function Metadata
==========================================

.. code-block:: python

    from functools import wraps

    def my_decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            return func(*args, **kwargs)
        return wrapper


7. Decorator for Timing Execution
==================================

.. code-block:: python

    import time
    from functools import wraps

    def timer(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            start = time.time()
            result = func(*args, **kwargs)
            print("Execution Time:", time.time() - start)
            return result
        return wrapper

    @timer
    def process():
        for _ in range(1000000):
            pass

    process()


8. Decorator with Parameters
=============================

.. code-block:: python

    def repeat(n):
        def decorator(func):
            def wrapper(*args, **kwargs):
                for _ in range(n):
                    func(*args, **kwargs)
            return wrapper
        return decorator

    @repeat(3)
    def greet():
        print("Hello")

    greet()


9. Class-Based Decorator
=========================

.. code-block:: python

    class Logger:
        def __init__(self, func):
            self.func = func

        def __call__(self, *args, **kwargs):
            print("Calling function...")
            return self.func(*args, **kwargs)

    @Logger
    def show():
        print("Processing data")

    show()


10. Real-World Decorator Example
=================================

.. code-block:: python

    def require_login(func):
        def wrapper(user):
            if not user.get("authenticated"):
                return "Access Denied"
            return func(user)
        return wrapper

    @require_login
    def view_profile(user):
        return f"Welcome {user['name']}"

    user = {"name": "Alice", "authenticated": True}
    print(view_profile(user))


Python @property Decorator
++++++++++++++++++++++++++++

1. What is @property
====================

The @property decorator allows a method to be accessed like an attribute while still providing controlled logic behind the scenes:

.. code-block:: python

    class Person:
        def __init__(self, name):
            self._name = name

        @property
        def name(self):
            return self._name

    p = Person("Alice")
    print(p.name)  # Alice


2. Encapsulation Using @property
=================================

.. code-block:: python

    class Product:
        def __init__(self, price):
            self._price = price

        @property
        def price(self):
            return self._price

    item = Product(100)
    print(item.price)


3. Read-Only Property
=====================

.. code-block:: python

    class Circle:
        def __init__(self, radius):
            self._radius = radius

        @property
        def area(self):
            return 3.14 * self._radius ** 2

    c = Circle(5)
    print(c.area)


4. Using @property with Setter
===============================

.. code-block:: python

    class Employee:
        def __init__(self, salary):
            self._salary = salary

        @property
        def salary(self):
            return self._salary

        @salary.setter
        def salary(self, value):
            if value < 0:
                raise ValueError("Salary cannot be negative")
            self._salary = value

    e = Employee(5000)
    e.salary = 6000
    print(e.salary)


5. @property with Deleter
==========================

.. code-block:: python

    class Account:
        def __init__(self, balance):
            self._balance = balance

        @property
        def balance(self):
            return self._balance

        @balance.deleter
        def balance(self):
            del self._balance

    acc = Account(1000)
    del acc.balance


6. Computed Property Example
=============================

.. code-block:: python

    class Rectangle:
        def __init__(self, length, width):
            self.length = length
            self.width = width

        @property
        def area(self):
            return self.length * self.width

    rect = Rectangle(10, 5)
    print(rect.area)  # 50


7. Difference: @property vs Normal Method
==========================================

.. code-block:: python

    class User:
        def __init__(self, name):
            self._name = name

        def get_name(self):
            return self._name

        @property
        def name(self):
            return self._name

    u = User("Bob")
    print(u.get_name())  # Method call
    print(u.name)        # Property access


8. Enforcing Data Integrity
============================

.. code-block:: python

    class Temperature:
        def __init__(self, celsius):
            self._celsius = celsius

        @property
        def celsius(self):
            return self._celsius

        @celsius.setter
        def celsius(self, value):
            if value < -273.15:
                raise ValueError("Temperature below absolute zero")
            self._celsius = value


9. Lazy Evaluation with @property
==================================

.. code-block:: python

    class DataLoader:
        def __init__(self):
            self._data = None

        @property
        def data(self):
            if self._data is None:
                print("Loading data...")
                self._data = [1, 2, 3]
            return self._data

    loader = DataLoader()
    print(loader.data)
    print(loader.data)


10. Enterprise-Style Implementation
===================================

.. code-block:: python

    class BankAccount:
        def __init__(self, owner, balance):
            self.owner = owner
            self._balance = balance

        @property
        def balance(self):
            return self._balance

        @balance.setter
        def balance(self, amount):
            if amount < 0:
                raise ValueError("Balance cannot be negative")
            self._balance = amount

    account = BankAccount("Alice", 1000)
    account.balance = 1500
    print(account.balance)


Python RegEx
+++++++++++++

1. What is RegEx
================

Regular Expressions (RegEx) provide a powerful way to search, match, and manipulate text patterns:

.. code-block:: python

    import re

    text = "Python is powerful"
    match = re.search("Python", text)
    print(match.group())  # Python


2. Using re.match()
===================

.. code-block:: python

    import re

    text = "Python Programming"
    result = re.match("Python", text)

    print(result.group())  # Python

match() checks for a pattern at the start of the string only.


3. Using re.search()
====================

.. code-block:: python

    import re

    text = "Learn Python Programming"
    result = re.search("Python", text)

    print(result.group())  # Python

search() scans the entire string for the first match.


4. Using re.findall()
=====================

.. code-block:: python

    import re

    text = "The rain in Spain"
    matches = re.findall("ai", text)

    print(matches)  # ['ai', 'ai']


5. Using re.sub() (Replace Text)
=================================

.. code-block:: python

    import re

    text = "I love Java"
    new_text = re.sub("Java", "Python", text)

    print(new_text)  # I love Python


6. Using Character Classes
===========================

.. code-block:: python

    import re

    text = "abc123"
    result = re.findall("[a-z]", text)

    print(result)  # ['a', 'b', 'c']

Common patterns:

- [a-z] → lowercase letters
- [A-Z] → uppercase letters
- [0-9] → digits


7. Metacharacters and Special Sequences
========================================

.. code-block:: python

    import re

    text = "Email: test123@gmail.com"
    pattern = r"\w+@\w+\.\w+"

    match = re.search(pattern, text)
    print(match.group())

Common sequences:

- \d → digit
- \w → alphanumeric
- \s → whitespace


8. Using Quantifiers
====================

.. code-block:: python

    import re

    text = "Helloooo"
    pattern = r"o+"

    print(re.findall(pattern, text))  # ['oooo']

Quantifiers:

- \* → 0 or more
- \+ → 1 or more
- ? → 0 or 1
- {n} → exact count


9. Grouping with Parentheses
=============================

.. code-block:: python

    import re

    text = "John Doe"
    pattern = r"(John) (Doe)"

    match = re.search(pattern, text)
    print(match.groups())  # ('John', 'Doe')


10. Real-World RegEx Example
=============================

.. code-block:: python

    import re

    def validate_phone(phone):
        pattern = r"^\+?\d{10,13}$"
        return bool(re.match(pattern, phone))

    print(validate_phone("+911234567890"))  # True
    print(validate_phone("12345"))          # False
