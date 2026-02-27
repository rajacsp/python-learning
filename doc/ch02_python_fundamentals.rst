.. _ch02:

=======================
Chapter 2: Python Fundamentals
=======================

Python Variables and Literals
++++++++++++++++++++++++++++++

1. Declaring and Assigning Variables
=====================================

Variable assignment in Python is straightforward. Variables are dynamically typed and do not require explicit type declaration.

.. code-block:: python

    # Variable assignment
    count = 10
    price = 99.99
    name = "Python"

    print(count)   # Output: 10
    print(price)   # Output: 99.99
    print(name)    # Output: Python


2. Multiple Variable Assignment
================================

You can assign multiple variables in a single statement:

.. code-block:: python

    a, b, c = 1, 2, 3

    print(a)  # Output: 1
    print(b)  # Output: 2
    print(c)  # Output: 3

This allows simultaneous assignment in a single statement.


3. Reassigning Variables
=========================

Python variables can reference different data types at different times:

.. code-block:: python

    value = 100
    print(value)  # Output: 100

    value = "Reassigned"
    print(value)  # Output: Reassigned


4. Numeric Literals
====================

Python supports integer, floating-point, and complex number literals:

.. code-block:: python

    integer_literal = 42
    float_literal = 3.14
    complex_literal = 2 + 3j

    print(integer_literal)  # Output: 42
    print(float_literal)    # Output: 3.14
    print(complex_literal)  # Output: (2+3j)


5. String Literals
==================

String literals can be defined using single, double, or triple quotes:

.. code-block:: python

    single_quote = 'Hello'
    double_quote = "World"
    multi_line = """This is
    a multi-line
    string"""

    print(single_quote)  
    print(double_quote)  
    print(multi_line)


6. Boolean Literals
===================

Boolean literals are True and False (case-sensitive):

.. code-block:: python

    is_active = True
    is_logged_in = False

    print(is_active)      # Output: True
    print(is_logged_in)   # Output: False


7. Special Literal: None
========================

None represents the absence of a value:

.. code-block:: python

    result = None

    if result is None:
        print("No value assigned yet")


8. Collection Literals
======================

Python supports literal syntax for all major built-in collections:

.. code-block:: python

    list_literal = [1, 2, 3]
    tuple_literal = (4, 5, 6)
    set_literal = {7, 8, 9}
    dict_literal = {"a": 1, "b": 2}

    print(list_literal)   # Output: [1, 2, 3]
    print(tuple_literal)  # Output: (4, 5, 6)
    print(set_literal)    # Output: {7, 8, 9}
    print(dict_literal)   # Output: {'a': 1, 'b': 2}


9. Binary, Octal, and Hexadecimal Literals
===========================================

Numeric literals can be expressed in different number systems:

.. code-block:: python

    binary = 0b1010
    octal = 0o12
    hexadecimal = 0xA

    print(binary)       # Output: 10
    print(octal)        # Output: 10
    print(hexadecimal)  # Output: 10


10. Using Variables in Expressions
===================================

Variables participate directly in arithmetic and logical expressions:

.. code-block:: python

    x = 5
    y = 3

    sum_result = x + y
    product_result = x * y

    print(sum_result)      # Output: 8
    print(product_result)  # Output: 15


Python Type Conversion
++++++++++++++++++++++

1. Implicit Type Conversion (Type Coercion)
============================================

Python automatically converts types in certain situations:

.. code-block:: python

    integer_value = 10       # int
    float_value = 3.5       # float

    result = integer_value + float_value  # int + float → float

    print(result)           # Output: 13.5
    print(type(result))     # Output: <class 'float'>

Python automatically promotes int to float in mixed numeric expressions.


2. Explicit Type Conversion to Integer (int())
===============================================

Use int() to convert compatible values to integers. Fractions are truncated, not rounded:

.. code-block:: python

    float_value = 9.99
    string_value = "42"

    int_from_float = int(float_value)
    int_from_string = int(string_value)

    print(int_from_float)    # Output: 9   (fraction truncated)
    print(int_from_string)   # Output: 42


3. Explicit Type Conversion to Float (float())
===============================================

float() converts integers and numeric strings to floating-point numbers:

.. code-block:: python

    int_value = 7
    string_value = "3.14"

    float_from_int = float(int_value)
    float_from_string = float(string_value)

    print(float_from_int)      # Output: 7.0
    print(float_from_string)   # Output: 3.14


4. Explicit Type Conversion to String (str())
==============================================

str() provides a readable string representation of most Python objects:

.. code-block:: python

    int_value = 100
    float_value = 25.5
    bool_value = True

    str_int = str(int_value)
    str_float = str(float_value)
    str_bool = str(bool_value)

    print(str_int)    # Output: '100'
    print(str_float)  # Output: '25.5'
    print(str_bool)   # Output: 'True'


5. Converting to Boolean (bool())
==================================

By convention, "empty" values are False and non-empty values are True:

.. code-block:: python

    print(bool(0))        # Output: False
    print(bool(1))        # Output: True
    print(bool(""))       # Output: False
    print(bool("text"))   # Output: True
    print(bool([]))       # Output: False
    print(bool([1, 2]))   # Output: True


6. Converting Between Strings and Lists
========================================

list() splits a string into characters; "separator".join() combines a list of strings:

.. code-block:: python

    text = "python"

    # String to list of characters
    char_list = list(text)
    print(char_list)  # Output: ['p', 'y', 't', 'h', 'o', 'n']

    # List of strings to single string
    words = ["Python", "Type", "Conversion"]
    joined = " ".join(words)
    print(joined)     # Output: Python Type Conversion


7. Converting Between Tuples, Lists, and Sets
==============================================

Collection types can be converted between each other as long as the elements are compatible:

.. code-block:: python

    numbers_list = [1, 2, 2, 3]

    numbers_tuple = tuple(numbers_list)
    numbers_set = set(numbers_list)

    print(numbers_tuple)  # Output: (1, 2, 2, 3)
    print(numbers_set)    # Output: {1, 2, 3}


8. Converting to Dictionary (dict())
====================================

dict() can convert an iterable of key–value pairs into a dictionary:

.. code-block:: python

    pairs_list = [("a", 1), ("b", 2)]
    pairs_tuple = (("x", 10), ("y", 20))

    dict_from_list = dict(pairs_list)
    dict_from_tuple = dict(pairs_tuple)

    print(dict_from_list)   # Output: {'a': 1, 'b': 2}
    print(dict_from_tuple)  # Output: {'x': 10, 'y': 20}


9. Handling Conversion Errors with try / except
================================================

Invalid conversions raise exceptions (e.g., ValueError) that can be handled gracefully:

.. code-block:: python

    def safe_int_convert(value: str) -> int:
        try:
            return int(value)
        except ValueError:
            print(f"Cannot convert '{value}' to int. Defaulting to 0.")
            return 0

    print(safe_int_convert("123"))   # Output: 123
    print(safe_int_convert("abc"))   # Output: Cannot convert 'abc' to int. Defaulting to 0.
                                     #         0


10. Custom Type Conversion via __str__ and __int__
==================================================

Custom classes can define how they convert to built-in types by implementing special methods like __str__ and __int__:

.. code-block:: python

    class Score:
        def __init__(self, points: int):
            self.points = points

        def __str__(self) -> str:
            return f"Score: {self.points}"

        def __int__(self) -> int:
            return self.points

    player_score = Score(95)

    print(str(player_score))  # Output: Score: 95
    print(int(player_score))  # Output: 95


Python Basic Input and Output
++++++++++++++++++++++++++++++

1. Using print() for Standard Output
====================================

The print() function displays text and values to the standard output (console):

.. code-block:: python

    print("Hello, Python!")
    print(100)
    print(3.14)


2. Printing Multiple Values
============================

Multiple values can be printed in a single call, separated by spaces by default:

.. code-block:: python

    name = "Alice"
    age = 30

    print(name, age)  
    # Output: Alice 30


3. Customizing Output with sep and end
=======================================

sep defines the separator between values. end defines what is printed at the end (default is newline):

.. code-block:: python

    print("Python", "is", "powerful", sep=" - ", end="!")
    # Output: Python - is - powerful!


4. Formatted Output using f-strings
====================================

f-strings provide a readable and efficient way to format strings:

.. code-block:: python

    name = "Bob"
    score = 88

    print(f"Student {name} scored {score} marks.")
    # Output: Student Bob scored 88 marks.


5. Using str.format() Method
=============================

An alternative formatting approach, useful for older Python versions:

.. code-block:: python

    product = "Laptop"
    price = 1200

    print("The price of {} is ${}".format(product, price))
    # Output: The price of Laptop is $1200


6. String Formatting with Old-Style % Operator
===============================================

Legacy formatting style, still seen in legacy codebases:

.. code-block:: python

    item = "Book"
    quantity = 5

    print("You bought %d %s(s)." % (quantity, item))
    # Output: You bought 5 Book(s).


7. Using input() to Receive User Input
=======================================

input() always returns data as a string:

.. code-block:: python

    name = input("Enter your name: ")
    print("Hello,", name)


8. Converting Input to Required Data Type
==========================================

Explicit conversion is required when numeric operations are needed:

.. code-block:: python

    age = int(input("Enter your age: "))

    print(f"You will be {age + 1} next year.")


9. Reading Multiple Inputs in One Line
=======================================

Useful for command-line programs requiring space-separated values:

.. code-block:: python

    numbers = input("Enter two numbers: ").split()

    num1 = int(numbers[0])
    num2 = int(numbers[1])

    print(num1 + num2)


10. Redirecting Output to a File
=================================

The print() function can send output to files using the file parameter:

.. code-block:: python

    with open("output.txt", "w") as file:
        print("This text goes into the file.", file=file)

    print("Data successfully written to output.txt")
