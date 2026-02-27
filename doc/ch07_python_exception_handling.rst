.. _ch07:

==================================
Chapter 7: Python Exception Handling
==================================

Python Exceptions
++++++++++++++++++

1. What is an Exception
=======================

An exception is an error that occurs during program execution and disrupts normal program flow:

.. code-block:: python

    print(10 / 0)  # Raises ZeroDivisionError

Without handling, the program terminates immediately.


2. Basic try...except Block
===========================

The try block contains risky code; except handles the error gracefully:

.. code-block:: python

    try:
        result = 10 / 0
    except ZeroDivisionError:
        print("Cannot divide by zero")


3. Handling Multiple Exceptions
================================

Different exception types can be handled separately:

.. code-block:: python

    try:
        value = int("abc")
    except ValueError:
        print("Invalid conversion")
    except ZeroDivisionError:
        print("Division error")


4. Using else with try...except
================================

The else block executes only if no exception is raised:

.. code-block:: python

    try:
        num = int("10")
    except ValueError:
        print("Conversion failed")
    else:
        print("Conversion successful:", num)


5. Using finally Block
======================

finally always executes, whether an exception occurs or not:

.. code-block:: python

    try:
        file = open("data.txt", "r")
    except FileNotFoundError:
        print("File not found")
    finally:
        print("Execution completed")


6. Catching All Exceptions (Generic Exception)
===============================================

Catches any exception; useful for logging but should be used cautiously:

.. code-block:: python

    try:
        risky_operation()
    except Exception as e:
        print("Error occurred:", e)


7. Raising Custom Exceptions
=============================

The raise keyword triggers an exception manually:

.. code-block:: python

    def validate_age(age):
        if age < 0:
            raise ValueError("Age cannot be negative")

    validate_age(-5)


8. Creating Custom Exception Classes
====================================

Custom exceptions improve clarity in domain-specific logic:

.. code-block:: python

    class NegativeNumberError(Exception):
        pass

    def check_number(n):
        if n < 0:
            raise NegativeNumberError("Negative numbers are not allowed")

    check_number(-3)


9. Using Assertions (assert)
=============================

Assertions are used for debugging and validation during development:

.. code-block:: python

    age = 15
    assert age >= 18, "User must be at least 18 years old"


10. Best Practice: Structured Exception Handling
================================================

Encapsulating exception logic improves reliability and user experience:

.. code-block:: python

    def divide(a, b):
        try:
            return a / b
        except ZeroDivisionError:
            return "Division by zero error"
        except TypeError:
            return "Invalid input type"

    print(divide(10, 0))


Python Exception Handling
++++++++++++++++++++++++++

1. Purpose of Exception Handling
=================================

Exception handling prevents abrupt program termination and allows controlled recovery from runtime errors:

.. code-block:: python

    try:
        result = 10 / 0
    except ZeroDivisionError:
        print("Handled division by zero safely")

Ensures stable application behavior.


2. Basic try...except Structure
===============================

Separates risky code from error-handling logic:

.. code-block:: python

    try:
        number = int("abc")
    except ValueError:
        print("Invalid number format")


3. Handling Multiple Exceptions
================================

Different exception types can be managed independently:

.. code-block:: python

    try:
        value = int("10")
        result = value / 0
    except ValueError:
        print("Conversion error")
    except ZeroDivisionError:
        print("Division error")


4. Using try...except...else
=============================

else executes only if no exception occurs:

.. code-block:: python

    try:
        num = int("50")
    except ValueError:
        print("Conversion failed")
    else:
        print("Conversion successful:", num)


5. Using try...except...finally
================================

finally always runs, making it ideal for resource cleanup:

.. code-block:: python

    try:
        file = open("data.txt", "r")
    except FileNotFoundError:
        print("File not found")
    finally:
        print("Cleanup operations executed")


6. Nested Exception Handling
=============================

Allows granular control over layered risky operations:

.. code-block:: python

    try:
        try:
            x = int("abc")
        except ValueError:
            print("Inner exception handled")
    except Exception:
        print("Outer exception handler")


7. Catching Generic Exceptions
===============================

Catches all exceptions; useful for logging but should be used carefully:

.. code-block:: python

    try:
        risky_operation()
    except Exception as e:
        print("Error:", e)


8. Re-raising Exceptions
=========================

Preserves the original traceback while adding contextual handling:

.. code-block:: python

    try:
        value = int("xyz")
    except ValueError:
        print("Logging error before re-raising")
        raise


9. Custom Exception Handling Strategy
======================================

Allows domain-specific error control:

.. code-block:: python

    class InvalidAgeError(Exception):
        pass

    def validate_age(age):
        if age < 18:
            raise InvalidAgeError("Age must be 18 or above")

    try:
        validate_age(16)
    except InvalidAgeError as e:
        print(e)


10. Production-Grade Exception Handling Pattern
===============================================

Combines graceful handling, error reporting, and guaranteed execution logic:

.. code-block:: python

    def safe_divide(a, b):
        try:
            return a / b
        except ZeroDivisionError as e:
            return f"Error: {e}"
        except Exception as e:
            return f"Unexpected error: {e}"
        finally:
            print("Operation attempted")

    print(safe_divide(10, 0))


Python Custom Exceptions
+++++++++++++++++++++++++

1. Why Use Custom Exceptions
=============================

Custom exceptions improve clarity, maintainability, and semantic accuracy by representing domain-specific error conditions:

.. code-block:: python

    class InvalidInputError(Exception):
        pass

Defines a new exception type tailored to your application logic.


2. Basic Custom Exception Example
==================================

Raises a user-defined exception with a meaningful message:

.. code-block:: python

    class NegativeValueError(Exception):
        pass

    def process_value(value):
        if value < 0:
            raise NegativeValueError("Negative values are not allowed")

    process_value(-10)


3. Extending Exception with Custom Message
===========================================

Adds dynamic context to error messages:

.. code-block:: python

    class AgeLimitError(Exception):
        def __init__(self, age):
            super().__init__(f"Age {age} is below allowed limit")

    def validate_age(age):
        if age < 18:
            raise AgeLimitError(age)

    validate_age(15)


4. Catching Custom Exceptions
==============================

Handled like any built-in exception:

.. code-block:: python

    class AuthenticationError(Exception):
        pass

    try:
        raise AuthenticationError("Invalid credentials")
    except AuthenticationError as e:
        print("Login failed:", e)


5. Creating Hierarchy of Custom Exceptions
===========================================

Facilitates organized error taxonomy and layered handling:

.. code-block:: python

    class ApplicationError(Exception):
        pass

    class DatabaseError(ApplicationError):
        pass

    class NetworkError(ApplicationError):
        pass


6. Custom Exception with Additional Attributes
===============================================

Carries structured metadata for better diagnostics:

.. code-block:: python

    class TransactionError(Exception):
        def __init__(self, code, message):
            self.code = code
            self.message = message
            super().__init__(f"[{code}] {message}")

    raise TransactionError(403, "Unauthorized action")


7. Using Custom Exceptions in Functions
========================================

Enforces logical validation constraints:

.. code-block:: python

    class FileMissingError(Exception):
        pass

    def load_config(filename):
        if not filename.endswith(".json"):
            raise FileMissingError("Only JSON configuration files supported")

    load_config("config.txt")


8. Custom Exception with Logging
=================================

Useful for application-level logging and audit trails:

.. code-block:: python

    class DataValidationError(Exception):
        pass

    try:
        raise DataValidationError("Invalid CSV column format")
    except DataValidationError as e:
        print("Validation Error Logged:", e)


9. Chaining Custom Exceptions
==============================

Preserves original error context using exception chaining:

.. code-block:: python

    class InitialError(Exception):
        pass

    class DerivedError(Exception):
        pass

    try:
        try:
            raise InitialError("Initial failure")
        except InitialError as e:
            raise DerivedError("Follow-up failure") from e
    except DerivedError as final_error:
        print(final_error)


10. Best Practice: Naming and Design Pattern
=============================================

Follow naming conventions:

- Use meaningful names
- Inherit from Exception
- Include descriptive docstrings

.. code-block:: python

    class InvalidOrderStateError(Exception):
        """Raised when an order is in an invalid processing state"""
        pass

    def process_order(status):
        if status != "confirmed":
            raise InvalidOrderStateError("Order must be confirmed before processing")

    process_order("draft")
