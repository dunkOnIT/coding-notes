# General

- **VIRTUAL ENVIRONMENTS**
    - good article: https://realpython.com/intro-to-pyenv/#specifying-your-python-version
    - stackexchange: https://stackoverflow.com/questions/52731543/how-to-use-properly-pyenv-and-venv
- **PIP**
    - install from requirements.txt: `pip install -r requirements.txt`  
    - create requirements.txt: pipreqs
        - `pip install pipreqs` if that doesn't work
- **CLASSES**
    ```python
    # Create class
    
    class DogClass:
    	# Use init to set up stuff when the class is initialised
    	def __init__(self, breed) #Specify args in the init class which can be passed when 
    														#the class is called
    		self.breed = breed
    		self.some_value = self.class_function_1 # Always specify self. when referencing
    																						# a class function
    
    	def class_function_1(self) # You always need to specify self as an argument
    		return "a"
    ```
    - [Here’s something on docstrings](https://www.programiz.com/python-programming/docstrings)
- **ENVIRONMENT VARIABLES**
    - [Artcile on how to set environment variables with python](https://able.bio/rhett/how-to-set-and-get-environment-variables-in-python--274rgt5) 
    - NB: Install `python-decouple`, NOT `decouple`
- **LOGGING**
    - [Socratica video explaning the basics](https://www.youtube.com/watch?v=g8nQ90Hk328)
    - [Documentation](https://docs.python.org/3/howto/logging.html#logging-basic-tutorial)
        - [A simple example](https://docs.python.org/3/howto/logging.html#a-simple-example)
        - [Logging to a file](https://docs.python.org/3/howto/logging.html#logging-to-a-file)
        - [Logging from multiple modules](https://docs.python.org/3/howto/logging.html#logging-from-multiple-modules)
            - [StackExchange Thread](https://stackoverflow.com/questions/15727420/using-logging-in-multiple-modules)
        - [Logging variable data](https://docs.python.org/3/howto/logging.html#logging-variable-data)
        - [Changing the format of displayed messages](https://docs.python.org/3/howto/logging.html#changing-the-format-of-displayed-messages)
            - [Full list of format variables](https://docs.python.org/3/library/logging.html#logrecord-attributes)
        - [Displaying the date/time in messages](https://docs.python.org/3/howto/logging.html#displaying-the-date-time-in-messages)
- **STRING MANIPULATION**
    - string formatting
        - f-strings:
            ```python
            name = 'Tushar'
            age = 23
            print(f"Hello, My name is {name} and I'm {age} years old.")
            ```

    - string.find(”string”)
        - `string.find(value, start, end)`
            - *`start` and `end` are optional, default to 0 and end of string respectively*
        - returns
            - first occurrence of “string”
            - -1 if not found
        - alternative: string.index(), but index() raises an exception if value not found
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/44d251ed-f780-438b-9d77-b2ea6ce1a84b/Untitled.png)
        
    - string.replace(”target”, “replace_value”)
- **DATETIME**
    - String formatting
        
        Format a datetime object as follows:
        
        ```python
        from datetime import datetime
        
        now = datetime.now()
        now_string = now.strftime("%Y-%m-%d %H.%M.%S") # gives "2022-01-06 13.25.22"
        ```
        
    - Get current time
        
        ```python
        from datetime import datetime
        
        now = datetime.now()
        ```
        

        
- **WORKING WITH FILES**
    - [Moving files](ons/8858008/how-to-move-a-file-in-python): `shutil.move(current_path, new_path)`
        - Note that filename must be included in the path, and if it is changed in new path then file will also be renamed
    - [Listing contents of a directory:](https://stackoverflow.com/questions/3207219/how-do-i-list-all-files-of-a-directory) **`[os.listdir()](https://docs.python.org/2/library/os.html#os.listdir)`**
        - Narrow down to just files using `os.path.isfile(path)`
            ```python
            import os
            
            my_path = "example/path"
            
            directory_contents = os.listdir(my_path)
            files_only = []
            
            for contents in directory_contents:
            	combined_path = os.path.join(my_path, contents)
            	if(os.path.isfile(combined_path)):
            		files_only.append(combined_path)
            
            ```
    - Writelines with newlines: `writelines("%s\n" % t for t in texts)`

- **RAISING EXCEPTIONS**
    - raise generic error: `raise Exception("Error description text")` 
    - raise specific error type: `raise <ErrorName>("Error description text")`
    - list of error types: https://www.tutorialsteacher.com/python/error-types-in-python
        |  Exception           | Description                                                                                             |
        |----------------------|---------------------------------------------------------------------------------------------------------|
        | AssertionError       | Raised when the assert statement fails.                                                                 |
        | AttributeError       | Raised on the attribute assignment or reference fails.                                                  |
        | EOFError             | Raised when the input() function hits the end-of-file condition.                                        |
        | FloatingPointError   | Raised when a floating point operation fails.                                                           |
        | GeneratorExit        | Raised when a generator's close() method is called.                                                     |
        | ImportError          | Raised when the imported module is not found.                                                           |
        | IndexError           | Raised when the index of a sequence is out of range.                                                    |
        | KeyError             | Raised when a key is not found in a dictionary.                                                         |
        | KeyboardInterrupt    | Raised when the user hits the interrupt key (Ctrl+c or delete).                                         |
        | MemoryError          | Raised when an operation runs out of memory.                                                            |
        | NameError            | Raised when a variable is not found in the local or global scope.                                       |
        | NotImplementedError  | Raised by abstract methods.                                                                             |
        | OSError              | Raised when a system operation causes a system-related error.                                           |
        | OverflowError        | Raised when the result of an arithmetic operation is too large to be represented.                       |
        | ReferenceError       | Raised when a weak reference proxy is used to access a garbage collected referent.                      |
        | RuntimeError         | Raised when an error does not fall under any other category.                                            |
        | StopIteration        | Raised by the next() function to indicate that there is no further item to be returned by the iterator. |
        | SyntaxError          | Raised by the parser when a syntax error is encountered.                                                |
        | IndentationError     | Raised when there is an incorrect indentation.                                                          |
        | TabError               | Raised when the indentation consists of inconsistent tabs and spaces.                                                      |
        | SystemError            | Raised when the interpreter detects internal error.                                                                        |
        | SystemExit             | Raised by the sys.exit() function.                                                                                         |
        | TypeError              | Raised when a function or operation is applied to an object of an incorrect type.                                          |
        | UnboundLocalError      | Raised when a reference is made to a local variable in a function or method, but no value has been bound to that variable. |
        | UnicodeError           | Raised when a Unicode-related encoding or decoding error occurs.                                                           |
        | UnicodeEncodeError     | Raised when a Unicode-related error occurs during encoding.                                                                |
        | UnicodeDecodeError     | Raised when a Unicode-related error occurs during decoding.                                                                |
        | UnicodeTranslateError  | Raised when a Unicode-related error occurs during translation.                                                             |
        | ValueError             | Raised when a function gets an argument of correct type but improper value.                                                |
        | ZeroDivisionError      | Raised when the second operand of a division or module operation is zero.                                                  |
- **PATHLIB**
    - documentation: https://docs.python.org/3/library/pathlib.html#concrete-paths
    - `import pathlib`
    - create a path object with `p = Path("filename.py") 
        - paths don't have to be full paths or have slashes or anything
    - joining: 
        - `Path.joinpath(path_object)` joins paths in the order they are specified (can be given either a path object or a string, and supports multiple arguments) 
        ```bash
        PurePosixPath('/etc').joinpath('init.d', 'apache2')
        PurePosixPath('/etc/init.d/apache2')
        ```
    - passing as an argument:

- **DESIGN PRINCIPLES**
    - When to use functions vs a class: Basically, if they share state/data
        
        > Note that there might be good reasons that all (or perhaps some groups) of your [functions] should be in a class, perhaps some shared state for a set of related operations, or other reasons. I'd probably *start* with just functions, and then be on the lookout for collection of functions that commonly operate on the same data in some way.
        > 
    - When to split stuff up into multiple files: Basically, when a file or a class has too many responsibilities.
- ~ RANDOM NOTES ~
    - sys.stdout is basically just the console - but I think it can be provided as a file-like object (ie, in place of a file path). But I’m not 100% sure on that.
    - For checking type you can use either type() to get the type, and then isinstance(test_obj, type) to check if something is/isn’t the given object type. To specify the object type, import the given module and then specify the path to the class, as in the below code:
        
        ```python
        import requests
        
        type(requests.PreparedRequest)
        ```
        
    - this is a cool wiki: [https://geekfeminism.fandom.com/wiki/Nonsexist_language](https://geekfeminism.fandom.com/wiki/Nonsexist_language)
        
        
- **JSON**
    - To load a dict from json:
    
    ```python
    f = open('data.json',)
       
    # returns JSON object as 
    # a dictionary
    data = json.load(f)
    ```
    
    - To save to a file already formatted, use “indent=4” like this:
    
    ```python
    with open("json_dump, "w+") as outfile:
    	json.dump(some_dict, outfile, indent=4) # "indent=4" stops it from saving as one line
    ```
    
- **SELENIUM**
    - WebDriver docs: https://developer.mozilla.org/en-US/docs/Web/WebDriver
    - [WebElement docs](https://www.selenium.dev/selenium/docs/api/py/webdriver_remote/selenium.webdriver.remote.webelement.html?highlight=webelement#selenium.webdriver.remote.webelement)
    - Get an element: `driver.find_element_by_<method>`
    - Get element’s text: `element.text`

# HTTP/Web Stuff

- **REQUESTS**
    - [PreparedRequest docs](https://docs.python-requests.org/en/latest/api/#requests.PreparedRequest)
        ```python
        import requests
        
        req = requests.Request('GET', 'https://httpbin.org/get')
        r = req.prepare()
        
        s = requests.Session()
        s.send(r)
        ```
        
    - [Response object docs](https://www.w3schools.com/python/ref_requests_response.asp)
        - Use response.status_code to get the status code as an int
- **FLASK (TODO)**
    - [Documentation on flask.Request object](https://flask.palletsprojects.com/en/2.0.x/api/#flask.Request.args)
        - Note that the type of flask.Request will be werkzeug.local.LocalProxy
            - This is basically just a proxy object (exists for some complicated reasons), but basically it just passes on whatever you ask it to do to the flask.Request object - so you can treate it as flask.Request for all intents and purposes
    - [Execute function after sending response](https://stackoverflow.com/questions/48994440/execute-a-function-after-flask-returns-response)
- .**WEBSERVER (WAITRESS)**
    - to start waitress server, run: `"waitress-serve --port=8080 app:app"`


# Testing

## **== GENERAL ==**
- Terminology 
  - Unit test: Testing a single component/function at a time
  - Integration test: Testing multiple components together/simultaneously
  - Test runner: Tool that helps to run multiple tests at once and summarise/report the results. `unittest` in Python standard library.
- built-in assert statement: `assert <function output> == <expected output>`
  - Returns an Error if false, and nothing if true

## **== UNIT TESTS==**

- **UNITTEST (DON'T USE THIS - PYTEST INSTEAD!**
  - `import unittest`
  - tests go into a class as methods
    - uses `assertEqual(<test_statement>, <expected_result>, <error text>)`
    ```python
    import unittest

    class TestSum(unittest.TestCase):

        def test_sum(self):
            self.assertEqual(sum([1, 2, 3]), 6, "Should be 6")

        def test_sum_tuple(self):
            self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")

    if __name__ == '__main__':
        unittest.main()
    ```
  - Failure indicated by `F`, success indicated by `.`.
  - Note use of `unittest.main()` in main function - this causes tests to  run if script called from commandline
  - Testing whether an exception is raised:
    ```python
    with self.assertRaises(TypeError):
        sum() 
    ```



## **== PYTEST ==**

- Parameterising: Let's you define what is basically a dictionary/list of inputs that can be passed as an argument to a function - essentially letting you run the same test code with multiple inputs. This is huge.
    - NB: Values are passed as-is to tests, not multiple copies of the original. So if you have a dict for the first iteration of a test and that dict gets modified, the modified version (ie, the original reference) will be used for the subsequent (second and on) tests.
- Fixtures: 
    - Fixtures can be overridden, leading to flexible behaviour? still need to see an example of this.
    - Fixtures can also be parameterised, which sounds wild/powerful/confusing

- 5x best practices: https://www.nerdwallet.com/blog/engineering/5-pytest-best-practices/
    - **Prefer mocker over mock**: I already do this, just need to document how to do it lol.
    - **Parametrize the same behavior, have different tests for different behaviors**:
        - If I expect a bunch of tests to all fail, those should be parameterised and run together. 
        - Don't try and parameterise things that will give different results.
    - **Don’t modify fixture values in other fixtures**
        - Modifying fixtures can lead to dependent fixtures returning unexpected results.
        - "Use `deepcopy` instead" - look into deepcopy if I find myself needing to do this
    - **Prefer responses over mocking outbound HTTP requests**
        - Might be worth checking out for Anuva
    - **Prefer tmpdir over global test artifacts**
        - Pytest module that seems really useful instead of having billions of different files lying around: https://docs.pytest.org/en/6.2.x/tmpdir.html
        - Syntax example:
            ```python
            import pytest

            def process_file(fp):
                """Toy function that returns an array of line lengths."""
                return [len(l.strip()) for l in fp.readlines()]


            @pytest.mark.parametrize("filename, expected", [
                ("first.txt", [3, 3, 3]),
                ("second.txt", [5, 5]),
            ])
            def test_antipattern(filename, expected):
                with open("resources/" + filename) as fp:
                    assert process_file(fp) == expected


            @pytest.mark.parametrize("contents, expected", [
                ("foo\nbar\nbaz", [3, 3, 3]),
                ("hello\nworld", [5, 5]),
            ])
            def test_pattern(tmpdir, contents, expected):
                tmp_file = tmpdir.join("testfile.txt")
                tmp_file.write(contents)
                with tmp_file.open() as fp:
                    assert process_file(fp) == expected
            ```


## **== MOCKING ==**
- pytest_mock
    - resources
        - this post giving an overview: https://changhsinlee.com/pytest-mock/
        - this post showing how to mock a class with a method: https://myadventuresincoding.wordpress.com/2011/02/26/python-python-mock-cheat-sheet/
    - mocking a class
        - 







# Error Troubleshooting

- **PYTHON GENERAL**
    - `[Errno 2] No such file or directory:` in response to:
        
        ```python
        logging.basicConfig(filename="logs/" + log_filename)
        ```
        
        This was because I had to create the logs subfolder in my current directory before a file could be created in there. Issue WASN’T that the script couldn’t create a new file (ie, removing `“logs/”` gives working code.