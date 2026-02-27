.. _ch03:

============================
Chapter 3: Python Flow Control
============================

Python if...else Statement
++++++++++++++++++++++++++

1. Basic if Statement
=====================

Executes the block only when the condition evaluates to True:

.. code-block:: python

    age = 20

    if age >= 18:
        print("Eligible to vote")


2. Using if...else Statement
=============================

Provides an alternative execution path when the condition is False:

.. code-block:: python

    temperature = 15

    if temperature > 25:
        print("It's warm outside")
    else:
        print("It's cold outside")


3. Using if...elif...else Chains
=================================

Allows testing multiple conditions in sequence:

.. code-block:: python

    score = 85

    if score >= 90:
        print("Grade: A")
    elif score >= 75:
        print("Grade: B")
    elif score >= 60:
        print("Grade: C")
    else:
        print("Grade: D")


4. Nested if Statements
=======================

An if block can exist inside another for complex logic:

.. code-block:: python

    username = "admin"
    password = "1234"

    if username == "admin":
        if password == "1234":
            print("Access granted")
        else:
            print("Incorrect password")


5. Using Logical Operators in Conditions
=========================================

Combine multiple conditions using and, or, and not:

.. code-block:: python

    age = 25
    is_verified = True

    if age > 18 and is_verified:
        print("User can proceed")


6. Short-Hand if Statement (Single Line)
=========================================

Useful for minimal conditional checks:

.. code-block:: python

    x = 10

    if x > 5: print("x is greater than 5")


7. Short-Hand if...else (Ternary Expression)
=============================================

Compact inline conditional assignment:

.. code-block:: python

    num = 7

    result = "Even" if num % 2 == 0 else "Odd"
    print(result)  # Output: Odd


8. Checking Multiple Values with in
====================================

Efficient alternative to chained OR conditions:

.. code-block:: python

    day = "Sunday"

    if day in ["Saturday", "Sunday"]:
        print("Weekend")
    else:
        print("Weekday")


9. Comparing Strings in Conditions
==================================

Common technique to handle case-insensitive comparisons:

.. code-block:: python

    username = "Alice"

    if username.lower() == "alice":
        print("Welcome Alice")


10. Using pass in if Statement
==============================

pass acts as a syntactic placeholder to avoid errors for empty blocks:

.. code-block:: python

    value = 5

    if value > 0:
        pass  # Placeholder for future logic

    print("Program continues...")


Python for Loop
+++++++++++++++

1. Basic for Loop with a Sequence
==================================

Iterates over each element in a sequence:

.. code-block:: python

    fruits = ["apple", "banana", "orange"]

    for fruit in fruits:
        print(fruit)


2. Using range() in for Loop
=============================

Generates numbers from 0 to 4 by default:

.. code-block:: python

    for i in range(5):
        print(i)


3. Custom Start and Step with range()
======================================

Format: range(start, stop, step)

.. code-block:: python

    for i in range(2, 10, 2):
        print(i)
    # Output: 2, 4, 6, 8


4. Iterating Through a String
==============================

Processes each character individually:

.. code-block:: python

    word = "Python"

    for char in word:
        print(char)


5. Using for with Index via enumerate()
========================================

Provides both index and value during iteration:

.. code-block:: python

    languages = ["Python", "Java", "C++"]

    for index, lang in enumerate(languages):
        print(index, lang)


6. Nested for Loops
===================

A loop inside another loop, commonly used for matrices and grids:

.. code-block:: python

    for i in range(3):
        for j in range(2):
            print(f"i={i}, j={j}")


7. Using break in for Loop
===========================

Terminates the loop when the condition is met:

.. code-block:: python

    for number in range(1, 10):
        if number == 5:
            break
        print(number)


8. Using continue in for Loop
==============================

Skips the current iteration without stopping the loop:

.. code-block:: python

    for number in range(1, 6):
        if number == 3:
            continue
        print(number)


9. for Loop with else Clause
=============================

The else block executes when the loop finishes normally (not broken):

.. code-block:: python

    for num in range(3):
        print(num)
    else:
        print("Loop completed successfully")


10. Iterating Over Dictionaries
===============================

Allows iteration over keys, values, or key–value pairs:

.. code-block:: python

    student = {"name": "Alice", "age": 22, "grade": "A"}

    for key, value in student.items():
        print(key, ":", value)


Python while Loop
+++++++++++++++++

1. Basic while Loop
===================

Executes repeatedly as long as the condition evaluates to True:

.. code-block:: python

    count = 1

    while count <= 5:
        print(count)
        count += 1


2. Decrementing Counter in while Loop
======================================

Commonly used for countdown logic:

.. code-block:: python

    number = 5

    while number > 0:
        print(number)
        number -= 1


3. Using while with User Input
===============================

Loop continues until a specific input condition is met:

.. code-block:: python

    user_input = ""

    while user_input != "exit":
        user_input = input("Type 'exit' to stop: ")


4. Infinite while Loop
======================

Creates an endless loop unless interrupted with break:

.. code-block:: python

    while True:
        print("Running...")


5. Breaking a while Loop
========================

break terminates the loop immediately:

.. code-block:: python

    count = 0

    while True:
        if count == 3:
            break
        print(count)
        count += 1


6. Using continue in while Loop
================================

Skips the current iteration and proceeds to the next cycle:

.. code-block:: python

    number = 0

    while number < 5:
        number += 1
        if number == 3:
            continue
        print(number)


7. while Loop with else Clause
===============================

The else block runs if the loop ends without encountering break:

.. code-block:: python

    x = 0

    while x < 3:
        print(x)
        x += 1
    else:
        print("Loop completed normally")


8. Simulating do-while Loop Behavior
====================================

Python does not have a native do-while, but this pattern replicates it:

.. code-block:: python

    count = 0

    while True:
        print("Executing at least once")
        count += 1
        if count == 3:
            break


9. Nested while Loops
=====================

A while loop inside another while loop:

.. code-block:: python

    i = 1

    while i <= 3:
        j = 1
        while j <= 2:
            print(f"i={i}, j={j}")
            j += 1
        i += 1


10. Using while for Input Validation
====================================

Ensures user input meets required constraints before proceeding:

.. code-block:: python

    age = -1

    while age < 0:
        age = int(input("Enter a positive age: "))

    print("Valid age entered:", age)


Python break and continue
+++++++++++++++++++++++++

1. Using break to Exit a Loop Early
===================================

The loop stops immediately when the break statement is encountered:

.. code-block:: python

    for number in range(1, 10):
        if number == 5:
            break
        print(number)


2. Using continue to Skip an Iteration
=======================================

The current iteration is skipped, and the loop proceeds with the next cycle:

.. code-block:: python

    for number in range(1, 6):
        if number == 3:
            continue
        print(number)


3. break in a while Loop
========================

Demonstrates breaking out of an infinite loop:

.. code-block:: python

    count = 0

    while True:
        if count == 3:
            break
        print(count)
        count += 1


4. continue in a while Loop
===========================

Illustrates bypassing specific values:

.. code-block:: python

    num = 0

    while num < 5:
        num += 1
        if num == 2:
            continue
        print(num)


5. Using break in Nested Loops
===============================

break exits only the inner loop:

.. code-block:: python

    for i in range(3):
        for j in range(5):
            if j == 2:
                break
            print(f"i={i}, j={j}")


6. Using Flag with break for Controlled Exit
=============================================

Flag variables help manage complex exit logic:

.. code-block:: python

    found = False

    for number in range(10):
        if number == 7:
            found = True
            break

    print("Found:", found)


7. break + else Interaction
===========================

The else executes only if the loop does not terminate via break:

.. code-block:: python

    for n in range(5):
        if n == 10:
            break
    else:
        print("Loop completed without break")


8. continue for Input Filtering
================================

Useful for skipping unwanted values during iteration:

.. code-block:: python

    for char in "python123":
        if char.isdigit():
            continue
        print(char)


9. Breaking Based on User Input
================================

Common pattern for controlled loop termination:

.. code-block:: python

    while True:
        user_input = input("Enter 'q' to quit: ")
        if user_input.lower() == 'q':
            break


10. Performance Use Case with continue
=======================================

Prevents unnecessary processing for invalid data, improving loop efficiency:

.. code-block:: python

    numbers = [1, -2, 3, -4, 5]

    for num in numbers:
        if num < 0:
            continue
        print(num)


Python pass Statement
+++++++++++++++++++++

1. Basic Usage of pass
======================

The pass statement acts as a placeholder where a statement is syntactically required but no action is needed:

.. code-block:: python

    if True:
        pass

    print("Program continues running")


2. Using pass in an Empty Function
===================================

Commonly used when defining function stubs during development:

.. code-block:: python

    def future_feature():
        pass


3. Using pass in a Class Definition
====================================

Allows declaration of a class structure without immediate implementation:

.. code-block:: python

    class User:
        pass


4. Using pass in a Loop
=======================

Maintains structural correctness without altering control flow:

.. code-block:: python

    for i in range(5):
        if i == 3:
            pass
        else:
            print(i)


5. Using pass in Conditional Blocks
====================================

Useful when logic for a condition will be implemented later:

.. code-block:: python

    score = 85

    if score > 90:
        print("Excellent")
    elif score > 80:
        pass
    else:
        print("Needs Improvement")


6. pass vs continue vs break
=============================

Key differences:

- pass → Does nothing
- continue → Skips iteration
- break → Terminates loop

.. code-block:: python

    for i in range(5):
        if i == 2:
            pass      # Does nothing
        print(i)


7. Using pass as Placeholder in Exception Handling
==================================================

Temporarily suppresses exception handling during development (use cautiously in production):

.. code-block:: python

    try:
        risky_operation()
    except Exception:
        pass


8. Using pass in Abstract Method Design
========================================

Used when defining interface-like structures before concrete implementations:

.. code-block:: python

    class Shape:
        def draw(self):
            pass


9. pass in Function Control Flow Planning
==========================================

Helps structure logic flow before final code integration:

.. code-block:: python

    def validate_user(user):
        if not user:
            pass
        else:
            print("User is valid")


10. Real-World Use Case: Iterative Development
===============================================

Facilitates staged development in agile environments without breaking code execution:

.. code-block:: python

    def api_handler(request):
        # Feature under construction
        pass
