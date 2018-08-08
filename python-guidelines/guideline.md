# 1. Indentation <sup><a href="https://www.python.org/dev/peps/pep-0008/?#indentation">1</a></sup>

### 1.1 **Tabs or spaces**

Use four spaces per indentation level; as mentioned in pep8.

### 1.2 **Maximum line length**

Limit all the lines to a maximum of 80 characters per line
The preferred way of wrapping long lines when inside parentheses, brackets and braces are explained below in section 1.3.

For lines not having these above mentioned characteristics, backslashes are acceptable. There should be one extra indentation level of four spaces if statement requires multiline and should be indented with another level of 4 spaces if it has an indentation level continued as sub-part of that statement. e.g.,
```python
    with open('/path/to/some/file/you/want/to/read') as file_1, \
        open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())
```

### 1.3 **Hanging indents**

#### 1.3.1 **Function calls, etc.**

If the statement is too big to accommodate in single line then we should add only one extra indentation level of four spaces wherein there should be no parameters on the first line and the extra indentation should be used to clearly distinguish itself as a continuation line.

```python
    foo = long_function_name(
        var_one, var_two,
        var_three, var_four
        var_five, var_six
    )
```

If there is an indentation level to the function already then an extra indentation level should be added to the params compared to the further indentation required making it clearly distinguishable.

```python
    def long_function_name(
            var_one, var_two, var_three,
            var_four, var_five):
        print(var_one)
```


#### 1.3.2 **Conditional statements**

When using conditional statements if it requires to be written on multiple lines, it should use only one extra indentation level for the next lines of the condition.

```python
    if (this_is_one_thing and
            that_is_another_thing):
        do_something()
```

If using same indentation level, add a comment to make it distinguishable and make sure the indent line never starts with a binary operator but can end in one.

```python
    if (this_is_one_thing and
            that_is_another_thing):
        # Add a comment here to justify the condition and distinguish
        do_something()
```

#### 1.3.3 **Lists/Dictionaries**

When using lists/dictionaries if it requires to be written on multiple lines, it should be lined up under the first character of the line that starts the multiline construct

```python
    my_list = [
        1, 2, 3,
        4, 5, 6,
    ]
```

```python
    result = some_function_that_takes_arguements(
        ‘a’, ‘b’, ‘c’,
        ‘d’, ‘e’, ‘f’
    )
```


# 2. Naming

While naming any python file in Systers' Open Source projects, follow these guidelines for naming.

### 2.1 **Modules and Packages**

Modules should have short, all-lowercase names. Underscores can be used in the module name if it improves readability.

Python packages should also have short, all-lowercase names, although the use of underscores is discouraged.

### 2.2 **File**

Files should have all _mixedCase_ name convention as

```python
    urls.py

    jobSearch.py
```

For naming the test files append a prefix  _test\__ to the mixedCase as:

```python
    test_jobSearch.py
```

### 2.3 **Class**

Class names should use the _CamelCase_ convention as:

```python
    class Admin(Object):
        pass
```

For naming the test classes append the suffix _Test_ to the CamelCase as:

```python
    class AdminTest(Object):
        pass
```

### 2.4 **Variables**

Variable names should be lowercase, with words separated by underscores as necessary to improve readability.

```python
    temp_variable_for_example = some_random_thing()
```

If a function or method returns some value, it is encouraged to catch it even if the value is not being used anywhere. For naming such unused variables append a prefix _unused\__ to the variable name to make it distinguishable.

```python
    unused_temp_variable = function_returning_value()
```

### 2.5 **Functions and Methods**

Function names should be lowercase, with words separated by underscores as necessary to improve readability.

```python
    def dummy_function_for_example(self):
        pass
```

Use one leading underscore only for non-public methods -

```python
    def _some_non_public_function(self):
        pass
```

### 2.6 **Arguments or Parameters**

Arguments or parameters should be all lower-case letters separated by underscores.
If the name of any such arguments or parameters clashes with a reserved keyword append a _single__underscore_ to it.

`class_ instead of class or clss.`

### 2.7 **Constants**

Constants should be all upper-case letters separated by underscores as necessary.

```python
    JOB_NOT_FOUND = 'No jobs available.'
```

# 3. Imports <sup><a href="https://www.python.org/dev/peps/pep-0008/?#imports">3</a></sup>

Import only what needs to be used, never import a whole module when everything(function) in it would not be used. In case a module or submodule would be used fully, import all of it instead of importing individual functions or methods.

Also make sure that the modules imported always follow alphabetical order.

```python
    import os                             # GOOD : if entire os module is required
    import os                             # BAD  : if entire os module is not required
    from os import getcwd                 # GOOD : if getcwd (or few functions) is the only function required
    from os import (getcwd, system,       # BAD  : if entire os module is required
                    environ, getpid)
```

Imports should usually be on separate lines:

Good:
```python
    import os
    import sys
```

Bad:
```python
    import sys, os
```

Though it is okay to use this

```python
    from subprocess import Popen, PIPE
```

Imports should always be at the top of the file and should follow the following order:

- Standard library imports.
- Related third party imports.
- Local application/library specific imports.

Implicit relative imports should _never_ be used, always use absolute _imports._

Under any circumstances, never use _Wildcard Imports_ i.e. `from <module> import *`


# **4.** Docstrings <sup><a href="http://www.python.org/dev/peps/pep-0257/">4</a></sup>

Use only triple quotes for docstrings since it reserves use of single quotes for commenting large chunks of code.

All non-trivial methods should have docstrings. Docstrings should follow [PEP257](http://www.python.org/dev/peps/pep-0257/)

There exists two types of docstrings, long-form and short-form.
A short-form docstring fits entirely on one line, including the triple quotes. It is used for simple functions, especially (though by no means exclusively) ones that are not part of a public API:

```python
    """Return short-form docstring."""
```

If the description spills past one line, use long-form docstring:
A summary line (one physical line) , terminated by a period, question mark, or exclamation point, followed by a blank line, followed by the rest of the doc string starting at the same cursor position as the first quote of the first line. Even though BDFL suggests in PEP 257, do not put a blank line before the ending quotes.

```python
    """This comment serves to demonstrate the format of a docstring.
    
    Note that the summary line is always at most one line long, and
    on the same line as the opening triple-quote, and with no spaces
    between the triple-quote and the text.
    """
```
The docstring should describe the function calling syntax and its semantics, not its implementation.

The docstring should contain the following sections after description unless empty in which case that particular section can be skipped:

- **Parameters:** List each parameter by name, and a description of it. The description can span several lines (use a hanging indent if so).
- **Returns or Yields** : Describe the type and semantics of the return value. If the function only returns None, this section is not required.
- **Raises** : List all exceptions that are relevant to the interface.

Example:

```python
    def some_random_function(self, a):
        """
        This function is just for example purposes
        :param a: Explain about parameter a here
        :return: Explain what this function returns
        """
        a = call_something()
        ...
        return Result
```

# 5. Testing

### 5.1 **Automated testing**

The QA process is divided as follows:

- Continuous Integration: Used Travis CI to setup CI for Project
- Automated Testing: Used Selenium to write UI tests from an end-users perspective. (black-box tests)
- Unit Testing: Unit-tests have been written for services in the codebase. (white-box tests)


##### Few important points regarding CI:

- `.travis.yml` is the config file to run the travis build
- Build can be viewed at `https://travis-ci.org/systers/<project_name>`
- Status would be reflected in the badge in `README.md`

#### 5.1.1 Structure of tests


- Selenium, a browser automation tool is used to simulate the functionality. Python APIs for selenium are used in the automated tests.

- Django provides a class `LiveServerTestCase`. What this does is that, It setups a Virtual Django Sever in the background which can be used by selenium to run tests.

- So, each testcase Class inherits `LiveServerTestCase`, Contains a `setUp` and `tearDown` method to instantiate and end live-server respectively. Each testcase in the class begins with `test`.

- Each Test Class covers a view. Class name represents the name of the view in nav-bar. Test suite for a view is contained in `tests` folder of the app containing the view. For Ex: `Volunteer Search` tab in the nav-bar of an admin user redirects to `http://127.0.0.1:8000/volunteer/search/`, so  the corresponding tests for this view would be in `VolunteerSearch` class in `tests` folder of `volunteer` app.

- Each app contains a `tests` folder containing the unit-tests and automated
  tests and an `__init__.py` to let django consider it as a package.

- For pure python repositories which do not use a framework, the tests should be created in the root of the project preferably in the same directory which contains the code source. This test directory must contain an `__init__.py` for making it a python package. 

#### 5.1.2 Design of tests (POM design)

##### Few important points regarding design pattern for Selenium tests:


- The tests follow the page object model design. Pages in vms have been broken into 
  objects which model their behaviour. The `pom` folder contains the architecture setup
  for this design.

- Each test file interacts with respective page objects and reuses their methods.
  To locate elements on the page both pages and tests use static locators defined in 
  `pom/locators` folder. `pom/pages` folder contains the pages mapping to vms.

- To follow up changes in UI with changes in tests, the modifications need to be made only
  in the relevant locators/urls/page file.

- Addition of any new view implies that a pom `page` and `locator` need to be created.

- Similarly, modifying any view implies that the corresponding `page` and `locator` will
  also need to be modified.
  

#### 5.1.3 Creating new test classes

##### Important points regarding creation of new Test Class:

- As mentioned earlier, each test class corresponds to a view which has a corresponding
  pom page and locator.

- When creating a new test class, first identify the view the class is being created for,
  and create corresponding pom page and locator.
  
- Similarly, if you are modifying the existing templates make sure you update the corresponding
  pom page and locators.

- Each Test Class has `setUpClass` and `tearDownClass` class methods which should initiate and
  quit the WebDriver objects respectively.

- POM page should be linked to the Test Class in the `setUpClass` method itself and WebDriverWait
  if needed in the tests should also be initiated in this method only.

- If in the tests you are logging in as admin or volunteer make sure to `logout` in the `tearDown`
  method of the Test Class.

- Use of implicit waits should always be avoided unless needed in an extreme case and has the
  approval of a maintainer. If wait is needed use explicit waits instead.

- Tests in normal mode might fail if all are executed at once, but if a test is fails in
  `HEADLESS` mode then the test is wrong and should be corrected accordingly.


# 6. Tutorial (Automated Testing)

To get started with automated testing, a tutorial has been documented and can be found here:
[Tutorial](https://github.com/systers/vms/blob/develop/aut_docs/Tutorial.md)


# 7. Flake8 config (setup.cfg)

A common setup.cfg is to be used throughout Systers Open Source to maintain consistency,
it has already been implemented in VMS and can be viewed here:

[https://github.com/systers/vms/blob/develop/vms/setup.cfg](https://github.com/systers/vms/blob/develop/vms/setup.cfg)

