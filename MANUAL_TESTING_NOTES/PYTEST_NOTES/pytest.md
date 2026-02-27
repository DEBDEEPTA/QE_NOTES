### 1. _What is pytest?_
 * pytest is a third-party testing framework that makes testing in Python:
 * Simple (no boilerplate)
 * Readable
 * Scalable
 * Extremely powerful
___
### 2. _pytest vs unittest_
| Feature         | unittest        | pytest              |
| --------------- | --------------- | ------------------- |
| Test style      | Class-based     | Function-based      |
| Assertions      | Special methods | Plain `assert`      |
| Fixtures        | Verbose         | Powerful & reusable |
| Parametrization | Limited         | Native & clean      |
| Plugins         | Limited         | Huge ecosystem      |
| Failure output  | Less readable   | Excellent           |
___
### 3. _Installation_
```python
   pip install pytest   # <- Install Library
```
```python
   pytest --version     # <- Check Version
```
### 4. _Commonly used command Flags_
```markdown
    pytest                  # run all tests
    pytest -v               # verbose
    pytest -q               # quiet
    pytest test_math.py     # specific file
    pytest -k add           # run tests matching name
    pytest --maxfail=1      # stop after first failure
    pytest -x               # exit on first failure
    pytest -s               # used to run tests while disabling stdout/stderr capture
```
___
### 5. _Test Discovery Rules_
 * pytest `auto-discovers` tests. 
 * _**Rules**_ :
   1. _File Names_
      ```python
        test_*.py   # <- module name shoud start with test
        *_test.py   # <- or, module name should end with test
      ```
   2. _Functions Names_
      ```python
        def test_something():      # <- Should start with test
      ```
   3. _Class Names_
      ```python
        class TestSomething:         # <- Should start with test      
      ```
      ```python
        ⚠️ No __init__ in test classes.
      ```
### 6. _Testing Types_
   1. _Function Based Testing_
   2. _Class Based Testing_ 
   
   * _Function Based Testing_
     ```python
       # src/function_based_testing/calc.py
       def add(a,b):
           return a+b
        
       def mul(a,b):
           return a*b
        
       def sub(a,b):
           return a-b
        
       def div(a,b):
           return a/b
        
       def rem(a,b):
           return a%b 
     ```
     ```python
       # src/function_based_testing/greet.py
       def greet(message = "Hello"):
           return message
     ```
     ```python
       # tests/function_tests/test_calc.py
       from src.function_based_testing import calc, greet
      
       def test_add():
           result_add = calc.add(5,2)
           assert result_add == 7
      
       def test_mul():
           result_mul = calc.mul(5,5)
           assert result_mul == 20    # 25
      
       def test_div():
           result_div = calc.div(5,2)
           assert result_div == 3     # 2.5
      
       def test_rem():
           result_rem = calc.rem(3,2)
           assert result_rem == 1
      
       def test_sub():
           result_sub = calc.sub(5,2)
           assert result_sub == 3
        
       def test_greet():
           message = "Hello Dev!"
           greet_message = greet.greet()
           assert greet_message == message   # "Hello Dev!"
     ```
     * Output Trace
       ```markdown
           test_add    ✅
           test_mul    ❌
           test_div    ❌
           test_rem    ✅
           test_sub    ✅
           test_greet  ❌
       ```
     * Terminal Output
       ```terminaloutput
           .FF..F
           ================================ FAILURES ================================
           ... 
           ================ 3 failed, 3 passed ==================
       ```

   * _Class Based Testing_

### 7. Setup & Teardown Methods
| Feature             | Function-Level                | Method-Level                    | Class-Level            | Module-Level              |
| ------------------- | ----------------------------- | ------------------------------- | ---------------------- | ------------------------- |
| Applies To          | Standalone functions          | Methods inside class            | Entire class           | Entire Python file        |
| Runs Before         | Each test function            | Each test method                | First method in class  | First test in module      |
| Runs After          | Each test function            | Each test method                | Last method in class   | Last test in module       |
| Setup Name          | `setup_function(function)`    | `setup_method(self, method)`    | `setup_class(cls)`     | `setup_module(module)`    |
| Teardown Name       | `teardown_function(function)` | `teardown_method(self, method)` | `teardown_class(cls)`  | `teardown_module(module)` |
| Needs Decorator     | ❌                             | ❌                               | ✅ `@classmethod`       | ❌                         |
| Parameter Passed    | function object               | method object                   | class object           | module object             |
| Scope               | Per function                  | Per method                      | Per class              | Entire file               |
| Execution Frequency | Every function                | Every method                    | Once per class         | Once per file             |
| Works Without Class | ✅                             | ❌                               | ❌                      | ✅                         |
| Can Use self        | ❌                             | ✅                               | ❌                      | ❌                         |
| Fixture Injection   | ❌                             | ❌                               | ❌                      | ❌                         |
| Performance         | Slowest                       | Slow                            | Faster                 | Fastest                   |
| Typical Use Case    | Simple isolated tests         | Logical grouping                | Shared class resources | Global setup (DB, config) |
| Recommended Today   | ❌                             | ❌                               | ❌                      | ❌ (Use fixtures instead)  |

* _Execution Flow_
  ```markdown
    setup_module
        setup_class
            setup_method
                test
            teardown_method
        teardown_class
    teardown_module
  ```

### 8. _Fixtures_
* A fixture is a reusable function that:
    * ✔ Sets up test data / environment
    * ✔ Provides it to test functions 
    * ✔ Optionally cleans up after execution
* _Execution Flow_
    ```markdown
      Call fixture → return value → inject into test → run test
    ```
* _🧪 Pytest Fixtures – Complete Overview Diagram_
    ```markdown
        Fixtures
        │
        ├── 1️⃣ Fixture Scope
        │   │
        │   ├── function (default)
        │   ├── class
        │   ├── module
        │   ├── package
        │   └── session
        │
        ├── 2️⃣ Types of Fixtures
        │   │
        │   ├── Simple Fixture
        │   │     └── return value
        │   │
        │   ├── Fixture with yield
        │   │     ├── setup (before yield)
        │   │     └── teardown (after yield)
        │   │
        │   ├── Parameterized Fixture
        │   │     ├── params=[]
        │   │     └── request.param
        │   │
        │   ├── Autouse Fixture
        │   │     └── autouse=True
        │   │
        │   └── Chained Fixtures (Dependency Injection)
        │         └── fixture depends on another fixture
        │
        ├── 3️⃣ Fixture Execution Flow
        │   │
        │   ├── Setup Phase
        │   ├── Test Execution
        │   └── Teardown Phase
        │
        ├── 4️⃣ Fixture Injection Mechanism
        │   │
        │   ├── Passing fixture as test argument
        │   ├── Passing fixture to another fixture
        │   └── request object usage
        │
        ├── 5️⃣ Advanced Fixture Concepts
        │   │
        │   ├── Indirect Parametrization
        │   ├── Dynamic Fixture Creation
        │   ├── Factory as Fixture
        │   ├── Fixture Finalizers (addfinalizer)
        │   └── Fixture Caching Behavior
        │
        ├── 6️⃣ conftest.py Usage
        │   │
        │   ├── Shared Fixtures
        │   ├── Folder-level Fixtures
        │   └── Auto Discovery
        │
        └── 7️⃣ Common Real-Time Use Cases
            │
            ├── WebDriver Setup
            ├── Database Connection
            ├── API Client Setup
            ├── Login Session Setup
            └── Test Data Setup
    ```
* 1️⃣ Fixture Scope 

    | Scope                  | Lifetime          | Created When               | Destroyed When             | Use Case                   | Performance             | Example                 |
    | ---------------------- | ----------------- | -------------------------- | -------------------------- | -------------------------- | ----------------------- | ----------------------- |
    | **function** (default) | Per test function | Before each test           | After each test            | Isolated tests             | ❌ Slow (repeated setup) | DB connection per test  |
    | **class**              | Per test class    | Before first test in class | After last test in class   | Shared setup in class      | ⚡ Medium                | Login session per class |
    | **module**             | Per file (.py)    | Before first test in file  | After all tests in file    | Shared resource per module | ⚡ Faster                | API client              |
    | **package**            | Per folder        | Before tests in package    | After all tests in package | Rarely used                | ⚡ Faster                | Large test suites       |
    | **session**            | Entire test run   | Once at start              | At end of pytest run       | Global setup               | 🚀 Fastest              | Browser / DB engine     |

    ```python
        session
         └── package
              └── module
                   └── class
                        └── function
         # -> Inner scopes run more frequently
         # -> Outer scopes run less frequently (more efficient)
    
    ```
* 
---

### X.  _Industry Standard Directory Structure For Writing Test Scripts_
   1. _General Directory Structure_
      ```python
         project_root/
         │
         ├── src/
         │   └── my_project/
         │       ├── __init__.py
         │       ├── circle.py
         │       ├── rectangle.py
         │
         ├── tests/
         │   ├── unit/
         │   │   ├── test_circle.py
         │   │   ├── test_rectangle.py
         │   │
         │   ├── integration/
         │   │   └── test_api.py
         │   │
         │   ├── conftest.py
         │
         ├── pytest.ini
         ├── requirements.txt
         ├── README.md
      ```
   2._pytest.ini_