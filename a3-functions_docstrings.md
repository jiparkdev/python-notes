# Functions

## Function Definition & Docstring

### `def` keyword

The keyword `def` introduces a function definition. It **must** be followed by the function name, an open parenthesis, zero or more parameters, a closing parenthesis, and then a colon.

### `"""docstrings"""`

Triple double quotation marks `"""` indicate the start of a docstring (documentation string), and it must end with another triple double quotation marks. A docstring exists to inform the reader of your code the purpose of your code. It is used in various parts of the Python code. It is a good practice to include docstrings in your code, it is highly recommended that you make a habit of writing docstrings. In this lesson, we will focus on writing docstrings in functions.

When you write a docstring for a function, always write it just after the function's header. Do not write any code between the function header and the docstring. The first line of the docstring should be short and informative, and the rest of the docstring lines can contain more details about your function.

***func1.py***

```python
def foo_func(param):
    """This is a docstring. This function does nothing."""
    pass

def bar_func(param1, param2):
    """return the sum of two integers."""
    return param1 + param2

def docstring_example():
    """this is the first line of the docstring. make this short.
    this is the second line of the docstring, and you can have as many lines as you want,
    and you can go into the deails of this function here. Notice that if you have a multiline
    docstring for you function, the enclosing docstring quotations are on a separate line.
    """
```

## Function Parameters & Return Statement

You can have zero or more parameters for a function. You can return zero or more values from a function.

***func2.py***

```python
def func1():
    """No parameters, and no return value. Simply prints Hi"""
    print "Hi."

def func2(p1, p2, p3, p4, p5):
    """Multiple parameters, and no return value. Simply prints the parameters."""
    print p1, p2, p3, p4, p5

def func3(p1, p2):
    """Two parameters and a return value."""
    print p1 + p2
```

