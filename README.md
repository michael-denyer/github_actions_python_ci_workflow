# Python GitHub Actions Reusable Workflows for CI
Python GitHub Actions Reusable Workflows for CI (Continuous Integration) 

These reusable workflows currently run on python 3.10.

## How to use the workflow in a specific project

example.yml shows how to reference the 3 workflows (black.yml, ci.yml and lizard.yml) ***when they have been placed in a
public repository or shared privately in an enterprise repository***. In this example I used my own GitHub repository michael_denyer and the default GitHub branch main.
These three workflows all function independently of each other. The example.yml script must be placed in the folder 
.github/workflows in your project to run. It is configured to run on merges to master or main branches or if a branch is
tagged with ci_xxx.

The testing in the ci.yml pipeline requires there to be a folder called test, in the project root, containing all your 
tests and also a requirements.txt file in that folder containing the required packages to be installed for testing
(excluding flake8, bandit, pylint, pylint-mccabe, ochrona, pytest, pytest-benchmark, pytest-sugar).

## CI pipeline purpose

The purpose of a continuous integration pipeline is to improve the quality of existing code through consistent 
formatting, code styles, testing, etc. Ensuring that people can be certain what to expect and make changes to the code 
with confidence.

## CI pipeline components

### 1. Black (.github/workflows/black.yml)

Black is the uncompromising Python code formatter. By using it, you agree to cede control over minutiae of 
hand-formatting. In return, Black gives you speed, determinism, and freedom from pycodestyle nagging about formatting. 
You will save time and mental energy for more important matters.

### 2. Lizard (.github/workflows/lizard.yml)

Lizard is an extensible Cyclomatic Complexity Analyzer. It counts the NLOC (lines of code without comments) and 
CCN (cyclomatic complexity number) to flag functions with high complexity. Generally these functions have many tasks
rather than the recommended single task which makes them harder to test and understand.

### 3. flake8  (.github/workflows/ci.yml)
Flake8 is a Python library that wraps PyFlakes and  pycodestyle. It is a great toolkit for checking your code 
base against coding style (PEP8) and programming errors (like “library imported but unused” and “Undefined name”) 

### 4. Bandit [![security: bandit](https://img.shields.io/badge/security-bandit-yellow.svg)](https://github.com/PyCQA/bandit)

Bandit is a tool designed to find common security issues in Python code. To do this Bandit processes each file, builds 
an AST from it, and runs appropriate plugins against the AST nodes. Once Bandit has finished scanning all the files it 
generates a report.

### 5. Ochrona [![Ochrona](https://img.shields.io/badge/secured_by-ochrona-blue)](https://ochrona.dev)

Ochrona is an Application Security solution that carries out software composition analysis (SCA). Ochrona utilises an 
automatically updated vulnerability database to assess your project dependencies, identifying any 
known vulnerabilities.

### 6. Pylint / McCabe (.github/workflows/ci.yml)

Pylint is a Python static code analysis tool which looks for programming errors, helps enforcing a coding standard, 
sniffs for code smells and offers simple refactoring suggestions. McCabe is another measure of code complexity.

### 7. Pytest / Pytest-benchmark (.github/workflows/ci.yml)

The pytest framework makes it easy to write individual unit tests, yet scales to support complex functional testing for 
applications and libraries helping you to write code with fewer bugs. Pytest-benchmark allows you to test how long 
given tests take to run to see if any changes improve or adversely effect performance.
