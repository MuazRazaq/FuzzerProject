# This Project is aimed at doing "Directed Fuzzing."
This document describes how the provided Python script performs directed fuzzing on the SQL Injection vulnerability page of the Damn Vulnerable Web Application (DVWA).
This fuzzing code is "directed" because it targets specific SQL injection vulnerabilities by using both known problematic input patterns and variations of them. 
The 

## Overview
1. Directed fuzzing is a testing technique where the fuzzer has some knowledge of the structure of the input and targets specific parts of the system with crafted input. The script uses this technique to interact with the DVWA, targeting its SQL Injection vulnerability.
2. Input Patterns: The script defines a set of SQL injection patterns (sql_patterns list) that are known to be problematic in SQL query contexts. This is a crucial aspect of directed fuzzing - it uses input that is crafted to exploit known vulnerabilities rather than completely random input.
3. Input Mutation: In addition to the exact patterns, the script introduces some randomness by using mutation functions (delete_random_character, insert_random_character, change_random_character). It means the script is not just using known patterns but also variants of them, which makes it more likely to find edge cases.
4. Updating Priorities: The script uses a priority dictionary to keep track of which input patterns have caused unexpected behavior. Inputs that cause unusual behavior have their priority increased. This is another characteristic of directed fuzzing: the script is learning and adapting its input selection based on feedback from the application.


# Fuzzer Project

This Project is an automation script designed to perform security testing on the Damn Vulnerable Web Application (DVWA). 
It tests DVWA against various SQL injection patterns and analyzes the application's response to identify potential security vulnerabilities.

## Prerequisites

To get started with the Fuzzer Project, you need the following installed on your system:

- Python 3.x
- WAMP (Windows, Apache, MySQL, PHP)
- Google Chrome Browser
- ChromeDriver
- DVWA

## Installation Steps

### Step 1: Install Python

If you do not have Python installed, download and install Python 3 from the [official website](https://www.python.org/downloads/).

### Step 2: Install WAMP

1. Go to the [WAMP download page](https://www.wampserver.com/en/) and download the latest version.
2. Run the installer and follow the on-screen instructions to install WAMP.
3. Once installed, start the WAMP server.

### Step 3: Set Up DVWA

1. Download DVWA from its [GitHub repository](https://github.com/digininja/DVWA).
2. Extract the DVWA folder and move it to the `www` directory of your WAMP installation (usually `C:\wamp64\www`).
3. Open your browser and navigate to `http://localhost/phpmyadmin`. Log in using username `root` and no password.
4. Create a new database called `dvwa`.
5. In your browser, navigate to `http://localhost/dvwa/setup.php` and click on the 'Create / Reset Database' button.
6. Navigate to `http://localhost/dvwa/login.php`. Use the default credentials `admin` / `password` to log in.

### Step 4: Install ChromeDriver

1. Download the appropriate version of ChromeDriver for your version of Google Chrome from the [official site](https://sites.google.com/a/chromium.org/chromedriver/downloads).
2. Extract the `chromedriver.exe` file and place it in a directory that's in your system's PATH, for example, `C:\Windows\System32`.

### Step 5: Install Required Python Libraries

install the necessary Python libraries using pip in the notebook first:

pip install selenium
pip install coverage

### How the Fuzzer Works
The Fuzzer Project automates a Chrome browser to interact with DVWA. The script will:
1. Log in to DVWA using default credentials.
2. Navigate to the security page and set the security level to low.
3. Navigate to the SQL Injection page.
4. Inject a series of SQL injection patterns into the input field.
5. Record and analyze the application's response for each pattern.
6. Maintain a priority dictionary to prioritize patterns that cause unexpected responses.
7. Generate a report at the end to display the total number of crashes, data breaches, crash rate, and input coverage.

### Running the Fuzzer
Before running the script, make sure WAMP server is running and DVWA is accessible at http://localhost/dvwa/login.php.
Then you can run the fuzzer in Notebook.
