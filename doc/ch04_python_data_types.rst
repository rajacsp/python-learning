.. _ch04:

==========================
Chapter 4: Python Data Types
==========================

Python Numbers and Mathematics
+++++++++++++++++++++++++++++++

1. Numeric Data Types in Python
================================

Python supports three primary numeric types: int, float, and complex:

.. code-block:: python

    integer_num = 10
    float_num = 3.14
    complex_num = 2 + 5j

    print(type(integer_num))  # <class 'int'>
    print(type(float_num))    # <class 'float'>
    print(type(complex_num))  # <class 'complex'>


2. Basic Mathematical Operations
=================================

Core arithmetic forms the foundation of all numeric computation:

.. code-block:: python

    a = 12
    b = 5

    print(a + b)   # Addition → 17
    print(a - b)   # Subtraction → 7
    print(a * b)   # Multiplication → 60
    print(a / b)   # Division → 2.4


3. Floor Division and Modulus
==============================

Used in quotient-remainder calculations:

.. code-block:: python

    x = 17
    y = 5

    print(x // y)  # Floor division → 3
    print(x % y)   # Modulus → 2


4. Power and Exponentiation
============================

The ** operator raises a number to a specified power:

.. code-block:: python

    base = 2
    exponent = 4

    result = base ** exponent
    print(result)  # Output: 16


5. Math Module Basics
=====================

The math module provides advanced mathematical functions:

.. code-block:: python

    import math

    print(math.sqrt(16))   # Square root → 4.0
    print(math.ceil(4.3))  # Ceiling → 5
    print(math.floor(4.9)) # Floor → 4


6. Trigonometric Functions
===========================

Used extensively in scientific and engineering calculations:

.. code-block:: python

    import math

    angle = math.radians(30)

    print(math.sin(angle))  # Sine of 30°
    print(math.cos(angle))  # Cosine of 30°
    print(math.tan(angle))  # Tangent of 30°


7. Rounding Numbers
===================

round() limits decimal precision for display and computation:

.. code-block:: python

    value = 3.5678

    print(round(value))      # Output: 4
    print(round(value, 2))   # Output: 3.57


8. Absolute and Sign Functions
===============================

Used for magnitude and sign manipulation:

.. code-block:: python

    import math

    number = -25

    print(abs(number))       # Output: 25
    print(math.copysign(10, -1))  # Output: -10.0


9. Random Number Generation
============================

Facilitates simulation, sampling, and stochastic processes:

.. code-block:: python

    import random

    print(random.randint(1, 10))      # Random integer between 1 and 10
    print(random.uniform(1.0, 5.0))   # Random float between 1.0 and 5.0


10. Statistical Operations
===========================

The statistics module enables descriptive data analysis:

.. code-block:: python

    import statistics

    numbers = [10, 20, 30, 40, 50]

    print(statistics.mean(numbers))   # Mean → 30
    print(statistics.median(numbers)) # Median → 30
    print(statistics.stdev(numbers))  # Standard deviation


Python String
++++++++++++++

1. Creating Strings
===================

Strings can be defined using single, double, or triple quotes:

.. code-block:: python

    single_quote = 'Hello'
    double_quote = "World"
    multi_line = """This is
    a multi-line
    string"""

    print(single_quote)
    print(double_quote)
    print(multi_line)


2. Accessing String Characters (Indexing)
==========================================

Strings support positive and negative indexing:

.. code-block:: python

    text = "Python"

    print(text[0])    # P
    print(text[-1])   # n


3. String Slicing
=================

Extracts substrings without modifying the original string:

.. code-block:: python

    word = "Programming"

    print(word[0:6])   # Output: Progra
    print(word[:4])    # Output: Prog
    print(word[4:])    # Output: ramming


4. String Immutability
======================

Strings cannot be changed once created:

.. code-block:: python

    name = "Python"

    # name[0] = "J"  # Raises TypeError
    print(name)


5. String Concatenation and Repetition
=======================================

Used to combine or duplicate strings:

.. code-block:: python

    first = "Hello"
    second = "World"

    print(first + " " + second)  # Hello World
    print(first * 3)             # HelloHelloHello


6. String Length and Membership
================================

Performs validation and search checks:

.. code-block:: python

    message = "Data Science"

    print(len(message))         # Output: 12
    print("Data" in message)    # True
    print("AI" not in message)  # True


7. Common String Methods
=========================

Used for formatting and transformation:

.. code-block:: python

    text = "  python programming  "

    print(text.upper())     # PYTHON PROGRAMMING
    print(text.lower())     # python programming
    print(text.strip())     # python programming
    print(text.replace("python", "Java"))  # Java programming


8. Splitting and Joining Strings
=================================

Essential for text processing and parsing:

.. code-block:: python

    sentence = "Python is powerful"

    words = sentence.split(" ")
    print(words)  # ['Python', 'is', 'powerful']

    joined = "-".join(words)
    print(joined)  # Python-is-powerful


9. String Formatting
====================

Dynamic and readable string construction techniques:

.. code-block:: python

    name = "Alice"
    score = 95

    print(f"{name} scored {score} marks.")                # f-string
    print("{} scored {} marks.".format(name, score))      # format method


10. Iterating Through a String
===============================

Strings are iterable character by character:

.. code-block:: python

    word = "Code"

    for char in word:
        print(char)


Python List
++++++++++++

1. Creating a List
==================

Lists are ordered, mutable collections that can store heterogeneous data:

.. code-block:: python

    empty_list = []
    numbers = [1, 2, 3, 4, 5]
    mixed = [10, "Python", True, 5.5]

    print(empty_list)
    print(numbers)
    print(mixed)


2. Accessing List Elements (Indexing)
======================================

Lists support both positive and negative indexing:

.. code-block:: python

    fruits = ["apple", "banana", "orange"]

    print(fruits[0])   # First element
    print(fruits[-1])  # Last element


3. Slicing Lists
================

Extracts a sublist using slice notation:

.. code-block:: python

    numbers = [0, 1, 2, 3, 4, 5]

    print(numbers[1:4])   # Output: [1, 2, 3]
    print(numbers[:3])    # Output: [0, 1, 2]
    print(numbers[3:])    # Output: [3, 4, 5]


4. Modifying List Elements
===========================

Lists are mutable and allow in-place updates:

.. code-block:: python

    items = ["pen", "pencil", "eraser"]
    items[1] = "marker"

    print(items)  # Output: ['pen', 'marker', 'eraser']


5. Adding Elements to a List
=============================

append() adds at the end, insert() adds at a specific index:

.. code-block:: python

    numbers = [1, 2, 3]

    numbers.append(4)
    numbers.insert(1, 10)

    print(numbers)  # Output: [1, 10, 2, 3, 4]


6. Removing Elements from a List
=================================

remove() deletes by value, pop() deletes by index (default last):

.. code-block:: python

    data = [10, 20, 30, 40]

    data.remove(20)
    last = data.pop()

    print(data)  # Output: [10, 30]
    print(last)  # Output: 40


7. List Length and Membership
==============================

Used for validation and condition checks:

.. code-block:: python

    values = [5, 10, 15]

    print(len(values))       # Output: 3
    print(10 in values)      # Output: True
    print(100 not in values) # Output: True


8. List Iteration
=================

Lists are iterable and commonly used with loops:

.. code-block:: python

    cities = ["New York", "London", "Tokyo"]

    for city in cities:
        print(city)


9. List Comprehension
=====================

Concise way to generate lists using expressions:

.. code-block:: python

    squares = [x**2 for x in range(5)]
    print(squares)  # Output: [0, 1, 4, 9, 16]


10. Sorting and Reversing Lists
================================

Used to reorder list elements in-place:

.. code-block:: python

    numbers = [4, 1, 3, 2]

    numbers.sort()
    print(numbers)  # Output: [1, 2, 3, 4]

    numbers.reverse()
    print(numbers)  # Output: [4, 3, 2, 1]


Python Tuple
+++++++++++++

1. Creating a Tuple
===================

Tuples are ordered, immutable collections used to store fixed data:

.. code-block:: python

    empty_tuple = ()
    single_element = (10,)   # Comma required for single-element tuple
    numbers = (1, 2, 3, 4)
    mixed = (10, "Python", True)

    print(empty_tuple)
    print(single_element)
    print(numbers)
    print(mixed)


2. Accessing Tuple Elements
============================

Like lists, tuples support indexing:

.. code-block:: python

    colors = ("red", "green", "blue")

    print(colors[0])    # First element
    print(colors[-1])   # Last element


3. Slicing Tuples
=================

Tuple slicing returns a new tuple:

.. code-block:: python

    values = (0, 1, 2, 3, 4)

    print(values[1:4])   # Output: (1, 2, 3)
    print(values[:3])    # Output: (0, 1, 2)


4. Tuple Immutability
=====================

Tuple elements cannot be modified after creation:

.. code-block:: python

    coords = (10, 20)

    # coords[0] = 30  # This will raise TypeError
    print(coords)


5. Tuple Packing and Unpacking
===============================

Convenient for multiple assignments:

.. code-block:: python

    person = ("Alice", 25, "Engineer")

    name, age, profession = person

    print(name)        # Alice
    print(age)         # 25
    print(profession)  # Engineer


6. Nested Tuples
================

Tuples can contain other tuples:

.. code-block:: python

    data = ((1, 2), (3, 4), (5, 6))

    print(data[1])       # Output: (3, 4)
    print(data[1][0])    # Output: 3


7. Tuple Length and Membership
===============================

Supports standard sequence operations:

.. code-block:: python

    numbers = (10, 20, 30)

    print(len(numbers))     # Output: 3
    print(20 in numbers)    # Output: True


8. Iterating Through a Tuple
=============================

Tuples are iterable like lists:

.. code-block:: python

    languages = ("Python", "Java", "Go")

    for lang in languages:
        print(lang)


9. Converting Between Tuples and Lists
=======================================

Used when mutability is required temporarily:

.. code-block:: python

    values = (1, 2, 3)

    list_version = list(values)
    tuple_again = tuple(list_version)

    print(list_version)   # [1, 2, 3]
    print(tuple_again)    # (1, 2, 3)


10. Tuple as a Return Value
============================

Functions can return multiple values as tuples:

.. code-block:: python

    def get_coordinates():
        return (40.7128, -74.0060)

    lat, lon = get_coordinates()

    print(lat)
    print(lon)


Python Set
+++++++++++

1. Creating a Set
=================

Sets are unordered collections of unique elements:

.. code-block:: python

    empty_set = set()
    unique_numbers = {1, 2, 3, 4}
    mixed_set = {1, "Python", 3.5, True}

    print(empty_set)
    print(unique_numbers)
    print(mixed_set)


2. Automatic Removal of Duplicates
===================================

Duplicate values are automatically discarded:

.. code-block:: python

    numbers = {1, 2, 2, 3, 3, 4}
    print(numbers)  # Output: {1, 2, 3, 4}


3. Adding Elements to a Set
============================

Use add() to insert a single new element:

.. code-block:: python

    fruits = {"apple", "banana"}

    fruits.add("orange")
    print(fruits)


4. Adding Multiple Elements with update()
==========================================

update() allows batch insertion from iterables:

.. code-block:: python

    colors = {"red", "green"}
    colors.update(["blue", "yellow"])

    print(colors)


5. Removing Elements from a Set
================================

remove() raises an error if missing, discard() fails silently:

.. code-block:: python

    numbers = {10, 20, 30, 40}

    numbers.remove(20)
    numbers.discard(50)  # No error if element doesn't exist

    print(numbers)


6. Set Length and Membership
=============================

Efficient for membership testing:

.. code-block:: python

    data = {5, 10, 15}

    print(len(data))       # Output: 3
    print(10 in data)      # True
    print(100 not in data) # True


7. Iterating Through a Set
===========================

Iteration order is not guaranteed:

.. code-block:: python

    languages = {"Python", "Java", "Go"}

    for lang in languages:
        print(lang)


8. Mathematical Set Operations
===============================

Supports standard mathematical set logic:

.. code-block:: python

    A = {1, 2, 3, 4}
    B = {3, 4, 5, 6}

    print(A | B)  # Union → {1, 2, 3, 4, 5, 6}
    print(A & B)  # Intersection → {3, 4}
    print(A - B)  # Difference → {1, 2}
    print(A ^ B)  # Symmetric Difference → {1, 2, 5, 6}


9. Subset and Superset Checks
==============================

Used for hierarchical relationship validation:

.. code-block:: python

    A = {1, 2, 3}
    B = {1, 2}

    print(B.issubset(A))     # True
    print(A.issuperset(B))   # True


10. Converting Sets to Other Types
===================================

Conversion enables ordered or indexed operations when needed:

.. code-block:: python

    values_set = {1, 2, 3}

    list_version = list(values_set)
    tuple_version = tuple(values_set)

    print(list_version)   # [1, 2, 3]
    print(tuple_version)  # (1, 2, 3)


Python Dictionary
++++++++++++++++++

1. Creating a Dictionary
========================

Dictionaries store data as key–value pairs and are optimized for fast lookups:

.. code-block:: python

    empty_dict = {}
    student = {"name": "Alice", "age": 22, "grade": "A"}

    print(empty_dict)
    print(student)


2. Accessing Dictionary Values
===============================

[] raises KeyError if missing, get() safely returns None by default:

.. code-block:: python

    employee = {"id": 101, "name": "John", "role": "Developer"}

    print(employee["name"])        # Output: John
    print(employee.get("role"))    # Output: Developer


3. Adding and Updating Dictionary Entries
==========================================

Assigning a value to a key adds or updates it:

.. code-block:: python

    profile = {"username": "admin"}

    profile["email"] = "admin@example.com"
    profile["username"] = "administrator"

    print(profile)


4. Removing Items from a Dictionary
====================================

Used to delete keys and retrieve values:

.. code-block:: python

    data = {"a": 1, "b": 2, "c": 3}

    removed_value = data.pop("b")
    del data["a"]

    print(data)         # {'c': 3}
    print(removed_value)  # 2


5. Dictionary Length and Membership
====================================

Checks existence of keys only:

.. code-block:: python

    settings = {"theme": "dark", "version": 1.0}

    print(len(settings))        # Output: 2
    print("theme" in settings)  # True


6. Iterating Through Dictionaries
==================================

Supports iteration over keys, values, or both:

.. code-block:: python

    user = {"name": "Alice", "age": 30, "city": "London"}

    for key in user:
        print(key, ":", user[key])

    for key, value in user.items():
        print(key, "=>", value)


7. Dictionary Methods
=====================

Useful for introspection and transformation:

.. code-block:: python

    data = {"x": 10, "y": 20}

    print(data.keys())     # dict_keys(['x', 'y'])
    print(data.values())   # dict_values([10, 20])
    print(data.items())    # dict_items([('x', 10), ('y', 20)])


8. Merging Dictionaries
=======================

Introduced in Python 3.9 for clean dictionary merging:

.. code-block:: python

    dict1 = {"a": 1, "b": 2}
    dict2 = {"c": 3, "d": 4}

    merged = dict1 | dict2
    print(merged)


9. Nested Dictionaries
======================

Allows structured data modeling:

.. code-block:: python

    employee = {
        "id": 101,
        "personal": {
            "name": "John",
            "email": "john@example.com"
        }
    }

    print(employee["personal"]["name"])  # Output: John


10. Dictionary Comprehension
=============================

Efficient way to generate dictionaries dynamically:

.. code-block:: python

    squares = {x: x**2 for x in range(5)}
    print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
