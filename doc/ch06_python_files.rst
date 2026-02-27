.. _ch06:

====================
Chapter 6: Python Files
====================

Python Directory and Files Management
++++++++++++++++++++++++++++++++++++++

1. Getting Current Working Directory
====================================

Returns the directory from which the Python script is executed:

.. code-block:: python

    import os

    current_dir = os.getcwd()
    print(current_dir)


2. Changing the Working Directory
==================================

Changes the active working directory for file operations:

.. code-block:: python

    import os

    os.chdir("C:/Projects")
    print(os.getcwd())


3. Listing Files and Directories
=================================

Returns all files and folders in the specified directory:

.. code-block:: python

    import os

    items = os.listdir(".")
    print(items)


4. Creating a Directory
=======================

mkdir() creates a single directory, makedirs() creates nested directories:

.. code-block:: python

    import os

    os.mkdir("new_folder")
    os.makedirs("parent/child/grandchild")


5. Checking File or Directory Existence
=======================================

Essential for safe file operations:

.. code-block:: python

    import os

    print(os.path.exists("data.txt"))      # True or False
    print(os.path.isfile("data.txt"))     # Checks file
    print(os.path.isdir("new_folder"))    # Checks directory


6. Creating and Writing to a File
==================================

Creates the file if it does not exist and writes content:

.. code-block:: python

    with open("sample.txt", "w") as file:
        file.write("Hello, Python File System")


7. Reading from a File
======================

Reads the entire content of the file into a string:

.. code-block:: python

    with open("sample.txt", "r") as file:
        content = file.read()

    print(content)


8. Renaming and Deleting Files
===============================

Used to manage file lifecycle:

.. code-block:: python

    import os

    os.rename("sample.txt", "renamed.txt")
    os.remove("renamed.txt")


9. Copying and Moving Files
============================

Provides advanced file handling capabilities:

.. code-block:: python

    import shutil

    shutil.copy("source.txt", "backup.txt")
    shutil.move("backup.txt", "archive/backup.txt")


10. Modern File Handling with pathlib
=====================================

pathlib offers an object-oriented and cleaner approach for file and directory manipulation:

.. code-block:: python

    from pathlib import Path

    file_path = Path("example.txt")

    file_path.write_text("Using pathlib module")
    print(file_path.read_text())

    print(file_path.exists())
    print(file_path.parent)


Python CSV: Read and Write CSV files
+++++++++++++++++++++++++++++++++++++

1. What is a CSV File
=====================

A CSV (Comma-Separated Values) file stores tabular data in plain text, where each line represents a row and values are separated by commas:

.. code-block:: python

    name,age,city
    Alice,25,New York
    Bob,30,London


2. Reading a CSV File Using csv.reader
=======================================

Reads each row as a list of values:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.reader(file)
        for row in reader:
            print(row)


3. Skipping Header Row
======================

Useful when the first row contains column names:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.reader(file)
        next(reader)  # Skip header
        for row in reader:
            print(row)


4. Reading CSV as Dictionary (csv.DictReader)
==============================================

Each row is read as an ordered dictionary mapped to column headers:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            print(row["name"], row["age"])


5. Writing to a CSV File Using csv.writer
==========================================

Creates and writes rows to a CSV file:

.. code-block:: python

    import csv

    with open("output.csv", "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["name", "age", "city"])
        writer.writerow(["Alice", 25, "New York"])
        writer.writerow(["Bob", 30, "London"])


6. Writing Multiple Rows at Once
=================================

Efficient for bulk data writing:

.. code-block:: python

    import csv

    data = [
        ["John", 28, "Toronto"],
        ["Emma", 35, "Berlin"]
    ]

    with open("people.csv", "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerows(data)


7. Writing Dictionaries Using csv.DictWriter
=============================================

Ensures structured column mapping:

.. code-block:: python

    import csv

    fieldnames = ["name", "age", "city"]

    with open("users.csv", "w", newline="") as file:
        writer = csv.DictWriter(file, fieldnames=fieldnames)
        writer.writeheader()
        
        writer.writerow({"name": "Alice", "age": 25, "city": "Paris"})
        writer.writerow({"name": "Bob", "age": 30, "city": "Rome"})


8. Custom Delimiters and Quoting
=================================

CSV supports configurable delimiters for complex data formats:

.. code-block:: python

    import csv

    with open("custom.csv", "w", newline="") as file:
        writer = csv.writer(file, delimiter="|")
        writer.writerow(["Name", "Age", "Country"])
        writer.writerow(["Alice", 25, "India"])


9. Appending Data to an Existing CSV
====================================

"a" mode appends data without overwriting existing rows:

.. code-block:: python

    import csv

    with open("users.csv", "a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["Charlie", 40, "USA"])


10. Reading CSV Using pandas (Advanced)
=======================================

Pandas provides high-level, efficient CSV data manipulation for analytics and ML workflows:

.. code-block:: python

    import pandas as pd

    df = pd.read_csv("data.csv")
    print(df.head())


Reading CSV files in Python
++++++++++++++++++++++++++++

1. Basic CSV Reading with csv.reader
====================================

Reads each row as a list of string values:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.reader(file)
        for row in reader:
            print(row)


2. Skipping Header Row
======================

Useful when the first row contains column names:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.reader(file)
        header = next(reader)
        print("Header:", header)

        for row in reader:
            print(row)


3. Reading CSV as Dictionary (DictReader)
==========================================

Each row is returned as an ordered dictionary mapped to column headers:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            print(row)


4. Accessing Specific Columns
==============================

Enables column-based data processing:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            print(row["name"], row["age"])


5. Reading CSV with Custom Delimiter
====================================

Handles CSV files that use non-standard separators:

.. code-block:: python

    import csv

    with open("data_pipe.csv", "r") as file:
        reader = csv.reader(file, delimiter="|")
        for row in reader:
            print(row)


6. Reading Large CSV Files Efficiently
=======================================

Iterative reading avoids loading the entire file into memory:

.. code-block:: python

    import csv

    with open("large_data.csv", "r") as file:
        reader = csv.reader(file)
        for row in reader:
            process = row  # Lazy iteration prevents memory overload


7. Converting CSV Data Types
=============================

CSV values are strings by default and often require type casting:

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            age = int(row["age"])
            salary = float(row["salary"])
            print(age, salary)


8. Reading CSV with Error Handling
==================================

Ensures robustness in production code:

.. code-block:: python

    import csv

    try:
        with open("data.csv", "r") as file:
            reader = csv.reader(file)
            for row in reader:
                print(row)
    except FileNotFoundError:
        print("CSV file not found.")


9. Reading CSV into a List
===========================

Loads the entire CSV into memory (use cautiously for large files):

.. code-block:: python

    import csv

    with open("data.csv", "r") as file:
        reader = csv.reader(file)
        data = list(reader)

    print(data)


10. Reading CSV Using pandas (Structured Approach)
==================================================

Pandas offers a high-level interface for complex data analysis and transformations:

.. code-block:: python

    import pandas as pd

    df = pd.read_csv("data.csv")

    print(df)
    print(df["name"])


Writing CSV files in Python
++++++++++++++++++++++++++++

1. Basic CSV Writing with csv.writer
====================================

Creates a CSV file and writes rows as lists:

.. code-block:: python

    import csv

    with open("output.csv", "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["name", "age", "city"])
        writer.writerow(["Alice", 25, "New York"])


2. Writing Multiple Rows at Once
=================================

Efficient approach for bulk row insertion:

.. code-block:: python

    import csv

    data = [
        ["Bob", 30, "London"],
        ["Emma", 28, "Berlin"],
    ]

    with open("people.csv", "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerows(data)


3. Writing CSV with Custom Delimiter
====================================

Allows CSV generation beyond comma-separated formatting:

.. code-block:: python

    import csv

    with open("data_pipe.csv", "w", newline="") as file:
        writer = csv.writer(file, delimiter="|")
        writer.writerow(["Name", "Age", "Country"])
        writer.writerow(["John", 35, "India"])


4. Writing CSV with Quoting
============================

Ensures consistent quoting of all fields:

.. code-block:: python

    import csv

    with open("quotes.csv", "w", newline="") as file:
        writer = csv.writer(file, quoting=csv.QUOTE_ALL)
        writer.writerow(["Alice", "Software Engineer", "New York"])


5. Appending Data to Existing CSV
==================================

Appends without overwriting existing data:

.. code-block:: python

    import csv

    with open("users.csv", "a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["Charlie", 40, "Canada"])


6. Writing Dictionaries with DictWriter
========================================

Maps keys directly to column headers:

.. code-block:: python

    import csv

    fieldnames = ["name", "age", "city"]

    with open("users.csv", "w", newline="") as file:
        writer = csv.DictWriter(file, fieldnames=fieldnames)
        writer.writeheader()
        writer.writerow({"name": "Alice", "age": 25, "city": "Paris"})


7. Validating Data Before Writing
==================================

Prevents invalid or incomplete data from being written:

.. code-block:: python

    import csv

    def validate_row(row):
        return all(row)

    data = [
        ["John", 28, "Toronto"],
        ["", 35, "Berlin"]
    ]

    with open("validated.csv", "w", newline="") as file:
        writer = csv.writer(file)
        for row in data:
            if validate_row(row):
                writer.writerow(row)


8. Writing CSV with UTF-8 Encoding
==================================

Ensures proper handling of international characters:

.. code-block:: python

    import csv

    with open("unicode.csv", "w", encoding="utf-8", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["Name", "City"])
        writer.writerow(["José", "München"])


9. Generating CSV from List of Dictionaries
============================================

Ideal for exporting structured datasets:

.. code-block:: python

    import csv

    records = [
        {"name": "Alice", "age": 25, "city": "Rome"},
        {"name": "Bob", "age": 30, "city": "Madrid"}
    ]

    with open("records.csv", "w", newline="") as file:
        writer = csv.DictWriter(file, fieldnames=records[0].keys())
        writer.writeheader()
        writer.writerows(records)


10. Writing CSV Using pandas (Advanced Workflow)
================================================

Pandas simplifies CSV creation in data-intensive applications:

.. code-block:: python

    import pandas as pd

    data = {
        "name": ["Alice", "Bob"],
        "age": [25, 30],
        "city": ["Paris", "London"]
    }

    df = pd.DataFrame(data)
    df.to_csv("data.csv", index=False)
