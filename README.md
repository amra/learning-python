Tasks for colleges to learn python

<!--ts-->
   * [Tools](#tools)
      * [Editor](#editor)
      * [Git](#git)
      * [Python](#python)
         * [Reading exceptions](#reading-exceptions)
         * [Virtualenv](#virtualenv)
         * [Pip](#pip)
   * [Basic](#basic)
      * [Basic 01 - Hello world](#basic-01---hello-world)
      * [Basic 02 - Read file](#basic-02---read-file)
      * [Basic 03 - Count lines](#basic-03---count-lines)
   * [XML](#xml)
      * [XML 01 - Find surnames](#xml-01---find-surnames)
      * [XML 02 - List surnames only](#xml-02---list-surnames-only)

<!-- Added by: amra, at: St dub  3 15:18:44 CEST 2019 -->

<!--te-->

# Tools
## Editor
Edit your code in editor like PyCharm (Community edition) or IntelliJ Idea (Community edition) because of context documentation and code completion.  

*Code completion*. Shortcut `ctrl + space`.

![](./images/pycharm-completion-default.png)

source: https://realpython.com/python-ides-code-editors-guide/

*Context documentation*. Shortcut `ctrl + q`.

![](./images/pycharm-documentation3.png)

source: https://realpython.com/python-ides-code-editors-guide/ 

## Git
Use git to backup and share your project with others. Atlassian company has awesome git explanation: https://www.atlassian.com/git

- What is git about: https://www.atlassian.com/git/tutorials/what-is-version-control
- Basic commands: https://www.atlassian.com/git/tutorials/setting-up-a-repository

## Python
### Reading exceptions
It's important to orient in reading python exceptions. See this example
```
/home/develop/learning-python/venv/bin/python /home/develop/learning-python/test.py
Traceback (most recent call last):
  File "/usr/lib/python3.5/xml/etree/ElementPath.py", line 263, in iterfind
    selector = _cache[cache_key]
KeyError: ('//record/surname', None)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/develop/learning-python/test.py", line 4, in <module>
    filtered = root.findall('//record/surname')
  File "/usr/lib/python3.5/xml/etree/ElementPath.py", line 304, in findall
    return list(iterfind(elem, path, namespaces))
  File "/usr/lib/python3.5/xml/etree/ElementPath.py", line 268, in iterfind
    raise SyntaxError("cannot use absolute path on element")
SyntaxError: cannot use absolute path on element
```


Key information is:
- `KeyError: ('//record/surname', None)` traslated: there is something wrong with `//record/surname`
- `SyntaxError: cannot use absolute path on element` translated: wrong syntax, detail is 'cannot use absolute path on element'. You can google it.
- `File "/home/develop/learning-python/test.py", line 4, in <module>` translated: the error happend in file `test.py` on line 4

### Virtualenv
`virtualenv` is a tool to create isolated Python environments. `virtualenv` creates a folder which contains all the necessary executables to use the packages that a Python project would need.

Links:
- https://docs.python-guide.org/dev/virtualenvs/#lower-level-virtualenv
- https://virtualenv.pypa.io/en/latest/

Commands:
- `virtualenv venv`
- `source ./venv/bin/activate`

TODO

### Pip
`pip` is the package installer for Python.

Links:
- https://pip.pypa.io/en/stable/

Commands:
- `pip install -r requirements.txt`

TODO

# Basic
## Basic 01 - Hello world

Your first task is to create a hello word script in python. So your script has to print "hello word".
 
Hints:
- print function: https://www.w3schools.com/python/ref_func_print.asp
- execute the script: https://askubuntu.com/questions/244378/running-python-file-in-terminal
 
## Basic 02 - Read file
Read file `./files/everything-is-awesome.txt` and output the first row on the screen.

Hints:
- read file: https://www.w3schools.com/python/python_file_open.asp
- types of opening files: https://www.w3schools.com/python/python_file_handling.asp

## Basic 03 - Count lines
Read file `./files/everything-is-awesome.txt` and print count of all lines in the file.

Hint:
- create an integer variable and set it to zero: https://www.w3schools.com/python/python_numbers.asp
- loop through the line of the file and each increase the variable by one: https://www.w3schools.com/python/python_file_open.asp

## Basic 04 - split string
Split `Everything Is AWESOME!!!` and print each word on separate line.

Hints:
- https://www.w3schools.com/python/python_strings.asp

<!--
## Task 04 - Split string
- https://docs.python.org/2/library/stdtypes.html#str.split
- https://www.pythonforbeginners.com/dictionary/python-split

## Read file and print each word on separate lin

## Task 05 - Case

## Dictionary

## Count 'and' word in whole file

-->
<!--
https://raw.githubusercontent.com/zhiwehu/Python-programming-exercises/master/100%2B%20Python%20challenging%20programming%20exercises.txt
-->

# XML

There are several approaches to XML programming in Python. We will start with XML analysis using python ElementTree and XPath.

Learn about XPath:
- https://www.w3schools.com/xml/xml_xpath.asp
- https://www.w3schools.com/xml/xpath_intro.asp

Core example:
```python
import xml.etree.ElementTree as ET

# Parse XML file and get its root element
root = ET.parse('./files/people.xml').getroot()

# Filter using XPath. 
filtered = root.findall('.//record[firstname="John"]')

for element in filtered:
    print(ET.tostring(element).decode('utf-8'))
```

## XML 01 - Find surnames
Change the example to find all users with surname `Doe`.


## XML 02 - List surnames only
Print surnames to output, one surname per line. ElementTree class has limitations in xpath functionality. 

Hint:
- Select surname elements with xpath. Output will containe lines like `<surname>Puckett</surname>`.
- Take a look on ElementTree.tostring documentation: https://docs.python.org/3/library/xml.etree.elementtree.html#xml.etree.ElementTree.tostring
- Set tostring parameter to `method="text"`.

