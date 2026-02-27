.. _ch10:

================================
Chapter 10: Python Date and Time
================================

Python datetime
+++++++++++++++

1. Overview of the datetime Module
===================================

The datetime module is used for handling date and time operations with high precision and reliability:

.. code-block:: python

    import datetime

    print(datetime.datetime.now())

It supports full timestamping, scheduling, comparisons, and formatting.


2. Current Date and Time
=========================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    print(now)

Returns the current system date and time including microseconds.


3. Extracting Date Components
==============================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print(now.year)
    print(now.month)
    print(now.day)
    print(now.hour)
    print(now.minute)
    print(now.second)


4. Using date and time Objects
===============================

.. code-block:: python

    from datetime import date, time

    d = date(2025, 6, 15)
    t = time(14, 30, 45)

    print(d)
    print(t)


5. Formatting with strftime()
=============================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    print(now.strftime("%d-%m-%Y"))
    print(now.strftime("%A, %B %d %Y"))


6. Parsing Strings with strptime()
===================================

.. code-block:: python

    from datetime import datetime

    date_string = "15-06-2025"
    dt = datetime.strptime(date_string, "%d-%m-%Y")
    print(dt)


7. Time Difference using timedelta
===================================

.. code-block:: python

    from datetime import datetime, timedelta

    start = datetime.now()
    end = start + timedelta(hours=5, minutes=30)

    print("Start:", start)
    print("End:", end)


8. Timezone Handling with zoneinfo
==================================

.. code-block:: python

    from datetime import datetime
    from zoneinfo import ZoneInfo

    ny_time = datetime.now(ZoneInfo("America/New_York"))
    tokyo_time = datetime.now(ZoneInfo("Asia/Tokyo"))

    print("New York:", ny_time)
    print("Tokyo:", tokyo_time)


9. ISO Format Conversion
=========================

.. code-block:: python

    from datetime import datetime

    dt = datetime.now()
    print(dt.isoformat())


10. Practical Example: Scheduling Logic
========================================

.. code-block:: python

    from datetime import datetime, timedelta

    meeting_time = datetime.now() + timedelta(days=2)

    if datetime.now() < meeting_time:
        print("Meeting scheduled")
    else:
        print("Meeting overdue")


Python strftime()
++++++++++++++++++

1. What is strftime()
=====================

strftime() converts a datetime object into a formatted string based on specified format codes:

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    formatted = now.strftime("%Y-%m-%d")
    print(formatted)  # e.g., 2025-11-24


2. Basic Date Formatting
=========================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print(now.strftime("%d/%m/%Y"))  # Day/Month/Year
    print(now.strftime("%m-%d-%Y"))  # Month-Day-Year


3. Time Formatting
===================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print(now.strftime("%H:%M:%S"))  # 24-hour format
    print(now.strftime("%I:%M %p"))  # 12-hour format with AM/PM


4. Including Day and Month Names
=================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print(now.strftime("%A"))  # Full weekday name
    print(now.strftime("%a"))  # Short weekday name
    print(now.strftime("%B"))  # Full month name
    print(now.strftime("%b"))  # Short month name


5. Combining Date and Time
===========================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print(now.strftime("%Y-%m-%d %H:%M:%S"))


6. Using strftime() for File Naming
====================================

.. code-block:: python

    from datetime import datetime

    filename = "backup_" + datetime.now().strftime("%Y%m%d_%H%M%S") + ".zip"
    print(filename)


7. ISO 8601 Format Using strftime
==================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    iso_format = now.strftime("%Y-%m-%dT%H:%M:%S")
    print(iso_format)


8. Custom Human-Readable Format
================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print(now.strftime("Today is %A, %d %B %Y at %I:%M %p"))


9. Formatting Specific datetime Object
=======================================

.. code-block:: python

    from datetime import datetime

    custom_date = datetime(2025, 12, 25, 18, 30)

    print(custom_date.strftime("%A, %d %B %Y - %H:%M"))


10. Enterprise Use Case: Log Timestamp
=======================================

.. code-block:: python

    from datetime import datetime

    def log_message(message):
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        print(f"[{timestamp}] {message}")

    log_message("Server started")
    log_message("User authenticated")


Python strptime()
++++++++++++++++++

1. What is strptime()
=====================

strptime() converts a date/time string into a datetime object using a specified format pattern:

.. code-block:: python

    from datetime import datetime

    date_string = "2025-11-24"
    dt = datetime.strptime(date_string, "%Y-%m-%d")
    print(dt)


2. Parsing Basic Date Format
=============================

.. code-block:: python

    from datetime import datetime

    date_string = "24/11/2025"
    parsed = datetime.strptime(date_string, "%d/%m/%Y")
    print(parsed)


3. Parsing Date and Time Together
==================================

.. code-block:: python

    from datetime import datetime

    datetime_string = "2025-11-24 18:45:30"
    dt = datetime.strptime(datetime_string, "%Y-%m-%d %H:%M:%S")
    print(dt)


4. Parsing with Month and Day Names
====================================

.. code-block:: python

    from datetime import datetime

    date_string = "Monday, November 24 2025"
    dt = datetime.strptime(date_string, "%A, %B %d %Y")
    print(dt)


5. Parsing 12-Hour Clock Format
================================

.. code-block:: python

    from datetime import datetime

    time_string = "07:30 PM"
    dt = datetime.strptime(time_string, "%I:%M %p")
    print(dt.time())


6. Using strptime() for File Data Processing
=============================================

.. code-block:: python

    from datetime import datetime

    log_entry = "2025-11-24 10:15:00 - Server Started"
    timestamp = log_entry.split(" - ")[0]

    dt = datetime.strptime(timestamp, "%Y-%m-%d %H:%M:%S")
    print(dt)


7. Handling Incorrect Format Errors
====================================

.. code-block:: python

    from datetime import datetime

    try:
        dt = datetime.strptime("24-11-2025", "%Y-%m-%d")
    except ValueError as e:
        print("Parsing failed:", e)


8. Converting User Input Safely
================================

.. code-block:: python

    from datetime import datetime

    user_input = "15-06-2025"

    try:
        parsed_date = datetime.strptime(user_input, "%d-%m-%Y")
        print("Valid date:", parsed_date)
    except ValueError:
        print("Invalid date format")


9. Combining strptime() and strftime()
======================================

.. code-block:: python

    from datetime import datetime

    raw = "2025/11/24"
    dt = datetime.strptime(raw, "%Y/%m/%d")
    formatted = dt.strftime("%d-%m-%Y")

    print(formatted)  # 24-11-2025


10. Enterprise Use Case: API Timestamp Parsing
===============================================

.. code-block:: python

    from datetime import datetime

    api_timestamp = "2025-11-24T14:35:59"
    dt = datetime.strptime(api_timestamp, "%Y-%m-%dT%H:%M:%S")

    print("Parsed API Timestamp:", dt)


How to Get Current Date and Time in Python
++++++++++++++++++++++++++++++++++++++++++++

1. Using datetime.now() (Most Common Method)
=============================================

.. code-block:: python

    from datetime import datetime

    current_datetime = datetime.now()
    print(current_datetime)


2. Get Only Current Date
=========================

.. code-block:: python

    from datetime import date

    today = date.today()
    print(today)


3. Get Only Current Time
=========================

.. code-block:: python

    from datetime import datetime

    current_time = datetime.now().time()
    print(current_time)


4. Formatted Current Date and Time
===================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    formatted = now.strftime("%Y-%m-%d %H:%M:%S")
    print(formatted)


5. Using time Module
====================

.. code-block:: python

    import time

    current_timestamp = time.ctime()
    print(current_timestamp)


6. Using UNIX Timestamp
=======================

.. code-block:: python

    import time

    timestamp = time.time()
    print(timestamp)


7. Current UTC Date and Time
=============================

.. code-block:: python

    from datetime import datetime

    utc_now = datetime.utcnow()
    print(utc_now)


8. Current Date and Time with Timezone
=======================================

.. code-block:: python

    from datetime import datetime
    from zoneinfo import ZoneInfo

    local_time = datetime.now(ZoneInfo("America/New_York"))
    print(local_time)


9. Human-Friendly Display
===========================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    print(now.strftime("Today is %A, %d %B %Y - %I:%M %p"))


10. Enterprise Logging Example
===============================

.. code-block:: python

    from datetime import datetime

    def log_event(event):
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        print(f"[{timestamp}] {event}")

    log_event("Server Started")
    log_event("User Login Successful")


Python Get Current Time
+++++++++++++++++++++++++

1. Using datetime.now().time() (Standard Method)
================================================

.. code-block:: python

    from datetime import datetime

    current_time = datetime.now().time()
    print(current_time)


2. Using strftime() for Formatted Time
=======================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    formatted_time = now.strftime("%H:%M:%S")
    print(formatted_time)


3. 12-Hour Format with AM/PM
=============================

.. code-block:: python

    from datetime import datetime

    time_12_hour = datetime.now().strftime("%I:%M %p")
    print(time_12_hour)


4. Using the time Module (System Clock)
========================================

.. code-block:: python

    import time

    current_time = time.strftime("%H:%M:%S")
    print(current_time)


5. Get Only Hour, Minute, Second
=================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()

    print("Hour:", now.hour)
    print("Minute:", now.minute)
    print("Second:", now.second)


6. Get Current UTC Time
=======================

.. code-block:: python

    from datetime import datetime

    utc_time = datetime.utcnow().time()
    print(utc_time)


7. Timezone-Aware Current Time
===============================

.. code-block:: python

    from datetime import datetime
    from zoneinfo import ZoneInfo

    tokyo_time = datetime.now(ZoneInfo("Asia/Tokyo")).time()
    print(tokyo_time)


8. Current Time with Microseconds
==================================

.. code-block:: python

    from datetime import datetime

    now = datetime.now()
    print(now.strftime("%H:%M:%S.%f"))


9. UNIX Time (Epoch Seconds)
=============================

.. code-block:: python

    import time

    epoch_time = time.time()
    print(epoch_time)


10. Enterprise Logging Example (Time-Only Logger)
=================================================

.. code-block:: python

    from datetime import datetime

    def log_event(event):
        current_time = datetime.now().strftime("%H:%M:%S")
        print(f"[{current_time}] {event}")

    log_event("Service initialized")
    log_event("Task executed")


Python Timestamp to datetime and Vice-Versa
++++++++++++++++++++++++++++++++++++++++++++++

1. What is a Timestamp
======================

A timestamp represents time as the number of seconds since January 1, 1970 (Unix Epoch):

.. code-block:: python

    import time

    timestamp = time.time()
    print(timestamp)  # e.g. 1732452305.4829


2. Convert Timestamp → datetime (Local Time)
=============================================

.. code-block:: python

    from datetime import datetime

    timestamp = 1732452305
    dt = datetime.fromtimestamp(timestamp)

    print(dt)


3. Convert Timestamp → UTC datetime
====================================

.. code-block:: python

    from datetime import datetime

    timestamp = 1732452305
    utc_dt = datetime.utcfromtimestamp(timestamp)

    print(utc_dt)


4. Convert datetime → Timestamp
================================

.. code-block:: python

    from datetime import datetime

    dt = datetime.now()
    timestamp = dt.timestamp()

    print(timestamp)


5. Timestamp Conversion with Formatting
========================================

.. code-block:: python

    from datetime import datetime

    timestamp = 1732452305
    dt = datetime.fromtimestamp(timestamp)

    print(dt.strftime("%Y-%m-%d %H:%M:%S"))


6. Using time Module for Conversion
====================================

.. code-block:: python

    import time

    timestamp = 1732452305
    readable = time.ctime(timestamp)

    print(readable)


7. Convert UTC Timestamp to Local Timezone
===========================================

.. code-block:: python

    from datetime import datetime
    from zoneinfo import ZoneInfo

    timestamp = 1732452305

    utc = datetime.fromtimestamp(timestamp, ZoneInfo("UTC"))
    local = utc.astimezone(ZoneInfo("Asia/Kolkata"))

    print("UTC:", utc)
    print("Local:", local)


8. Convert datetime String → Timestamp
=======================================

.. code-block:: python

    from datetime import datetime

    date_string = "2025-11-24 14:30:00"
    dt = datetime.strptime(date_string, "%Y-%m-%d %H:%M:%S")
    timestamp = dt.timestamp()

    print(timestamp)


9. Millisecond Timestamp Handling
==================================

.. code-block:: python

    from datetime import datetime

    ms_timestamp = 1732452305482  # milliseconds
    dt = datetime.fromtimestamp(ms_timestamp / 1000)

    print(dt)


10. Enterprise Example: Database Time Normalization
===================================================

.. code-block:: python

    from datetime import datetime

    def normalize_timestamp(input_value):
        if isinstance(input_value, (int, float)):
            return datetime.fromtimestamp(input_value)
        elif isinstance(input_value, str):
            dt = datetime.strptime(input_value, "%Y-%m-%d %H:%M:%S")
            return dt.timestamp()

    print(normalize_timestamp(1732452305))
    print(normalize_timestamp("2025-11-24 14:30:00"))


Python time Module
+++++++++++++++++++

1. What is the time Module
===========================

The time module provides low-level time-related functions for:

- Timestamps
- Delays
- Performance measurement
- System clock interactions

.. code-block:: python

    import time

    print(time.time())


2. Get Current Time as Readable String
=======================================

.. code-block:: python

    import time

    current_time = time.ctime()
    print(current_time)


3. Get Current Time Components
===============================

.. code-block:: python

    import time

    t = time.localtime()
    print("Hour:", t.tm_hour)
    print("Minute:", t.tm_min)
    print("Second:", t.tm_sec)


4. Sleep / Delay Execution
===========================

.. code-block:: python

    import time

    print("Start")
    time.sleep(2)
    print("End after 2 seconds")


5. Measure Execution Time (Performance Timing)
==============================================

.. code-block:: python

    import time

    start = time.time()
    time.sleep(1)
    end = time.time()

    print("Execution Time:", end - start, "seconds")


6. High-Precision Timer with perf_counter()
============================================

.. code-block:: python

    import time

    start = time.perf_counter()
    time.sleep(0.5)
    end = time.perf_counter()

    print("Precise Time:", end - start)


7. Formatting Time with strftime()
===================================

.. code-block:: python

    import time

    formatted = time.strftime("%Y-%m-%d %H:%M:%S")
    print(formatted)


8. Parsing Time with strptime()
================================

.. code-block:: python

    import time

    parsed = time.strptime("24-11-2025 10:30:00", "%d-%m-%Y %H:%M:%S")
    print(parsed)


9. Convert Timestamp to Readable Time
======================================

.. code-block:: python

    import time

    timestamp = time.time()
    readable = time.ctime(timestamp)

    print(readable)


10. Enterprise Use Case: Rate Limiting Logic
=============================================

.. code-block:: python

    import time

    last_request = time.time()

    def can_execute():
        global last_request
        current = time.time()
        if current - last_request >= 5:
            last_request = current
            return True
        return False

    print(can_execute())


Python sleep()
+++++++++++++++

1. What is sleep()
===================

sleep() is a function from the time module that pauses program execution for a specified number of seconds:

.. code-block:: python

    import time

    print("Start")
    time.sleep(2)
    print("Resumed after 2 seconds")


2. Basic Delay in Seconds
==========================

.. code-block:: python

    import time

    time.sleep(5)
    print("Executed after 5 seconds")


3. Sleep with Float Values (Sub-second Precision)
==================================================

.. code-block:: python

    import time

    time.sleep(0.5)
    print("Executed after 0.5 seconds")


4. Using sleep() in Loops
==========================

.. code-block:: python

    import time

    for i in range(3):
        print("Processing", i)
        time.sleep(1)


5. Sleep for Countdown Timer
=============================

.. code-block:: python

    import time

    for i in range(5, 0, -1):
        print("Countdown:", i)
        time.sleep(1)
    print("Go!")


6. Sleep in Retry Mechanism
=============================

.. code-block:: python

    import time

    def retry_operation():
        for attempt in range(3):
            print("Attempt", attempt + 1)
            time.sleep(2)

    retry_operation()


7. Sleep in API Rate Limiting
==============================

.. code-block:: python

    import time

    def api_request():
        print("Request sent")
        time.sleep(1)

    for _ in range(5):
        api_request()


8. Sleep for Background Task Simulation
========================================

.. code-block:: python

    import time

    print("Task started...")
    time.sleep(3)
    print("Task completed.")


9. Non-blocking Alternative (asyncio.sleep)
============================================

.. code-block:: python

    import asyncio

    async def task():
        print("Waiting...")
        await asyncio.sleep(2)
        print("Done")

    asyncio.run(task())


10. Enterprise Use Case: Controlled Batch Processing
====================================================

.. code-block:: python

    import time

    def process_batches():
        for batch in range(1, 4):
            print(f"Processing batch {batch}")
            time.sleep(2)

    process_batches()
