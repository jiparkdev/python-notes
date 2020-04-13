# Namespaces and Scopes

## 1.0 Introduction to Namespaces

### 1.1 General Description

A **namespace** is a group of names. A name in namespace *A* can be the same as a name in namespace *B*. The name in each of the namespaces can be uniquely identified by referring to its namespace.

### 1.2 Namespace Analogy #1

Imagine that there are a total of eight people in a neighborhood with two families of four where each family lives in a house. The first is the *Andersons family* and the second is the *Smiths family*. Every person in the neighborhood has a first name, as well as a family name shared only with their family members. Coincidentally, the two families have the same first names.

**Neighborhood**

*   **Andersons family house:** John Anderson, Jane Anderson, Johnny Anderson, Jenny Anderson
*   **Smiths family house:** John Smith, Jane Smith, Johnny Smith, Jenny Smith

Every single person in the neighborhood can be uniquely identified by the combination of their first name and the family name; there is only one Jane Anderson, and there is only one Jane Smith. Within the **namespace** of *Andersons family house*, just "Jane" is enough to refer to the person unambiguously. In the same line of thinking, within the **namespace** of the *neighborhood*, we can call a person by their full name to avoid ambiguity.

In summary, we have a namespace called **Neighborhood**, and within it, we have two namespaces called **Andersons family house** and **Smiths family house**. If you were a person in one of the families, you can refer to your family members by their first names, and you can call the other family's members by their full names.

### 1.3 Namespace Analogy #2

Imagine that we created a folder named **neighborhood**, and within it, we created two folders named **andersons** and **smiths**. The three folders are just regular folders that we would normally create on our computer for various reasons. After creating the folders, we created the files called **john.py**, **jane.py**, **johnny.py**, and **jenny.py** within *andersons* and *smiths* folders. Afterward, we created another file, but this time, called **mailman.py** in the **neighborhood** folder.

*   **neighborhood** *(folder)*
    *   **andersons** *(folder)*
        *   **john.py** *(file)*
        *   **jane.py** *(file)*
        *   **johnny.py** *(file)*
        *   **jenny.py** *(file)*
    *   **smiths** *(folder)*
        *   **john.py** *(file)*
        *   **jane.py** *(file)*
        *   **johnny.py** *(file)*
        *   **jenny.py** *(file)*
    *   **mailman.py** *(file)*

Every folder is a separate namespace. **jenny** in the **smiths** folder can say "**johnny**" to simply refer to her brother. However, if she wants to refer to *johnny* in the *andersons folder*, she can say "**andersons.johnny**". The **mailman** passing through the neighborhood can refer to every person in the neighborhood by their folder and name; he can say for instance, "**smiths.john**" or "**andersons.john**" to uniquely refer to a person.

### 1.4 Summary

The **namespaces** as presented above are used for the purpose of grouping the *individual objects* (people) around their *relatedness* to avoid name collisions between them when *some objects* share the *same names*. For instance, a person (**object**) in the smiths family house (**namespace**) is named "John" (**name**), and we can say "John Smith" to refer to that person, and "John Anderson" to refer to the other person in andersons family house.

>   A **namespace** is where **names** exist, and each name is associated with an **object**.

## 2.0 Python Namespaces

### 2.1 Introduction

In Python, **namespaces** are used for the purpose of grouping **objects** around a particular **functionality** to avoid **name** collisions between them when they share the same names.

>   In Python, a **package** is an object, a **module** is an object, a **class** is an object, a **function** is an object, and **values** such as **strings**, **integers**, **floats**, and **booleans** are all objects, and each of them has an associated name.

There are several different types of Python namespaces. We will go through them in the following sections.

### 2.2 Package Namespace

A **package namespace** is used for the purpose of grouping modules and its sub-packages around a particular functionality to avoid name collisions between them when they share the same names.

We will learn how to use two different modules with the same name and two different functions with the same name. Let us first create a package named **pack**.

*   ***pack***
    *   `__init__.py`
    *   `pack.py`
    *   ***sub1***
        *   `__init__.py`
        *   `m.py`
    *   ***sub2***
        *   `__init__.py`
        *   `m.py`

The above example has three folders: a top-level folder called **pack** and two sub-folders called **sub1** and **sub2**.

*   We created the `__init__.py` files in each of the folders to tell Python that the folders represent packages.

*   We then created `pack.py` under the *pack* folder.
*   Afterward, we created `m.py` in *sub1* and *sub2* folders.

***Note*** that the modules in **sub1** and **sub2** packages have the same name (i.e. `m`).

Let us imagine for a moment that all `.py` files are currently empty; they do not contain any code.

Now, we decide to write some code in `sub1/m.py` and `sub2/m.py` like so:

***sub1/m.py***

```python
def func():
    """print hi"""
    print("hi")
```

***sub2/m.py***

```python
def func():
    """print bye"""
    print("bye")
```

***Notice*** that the functions in the two modules have the same name.

We then write some code in `pack/pack.py`.

***pack/pack.py***

```python
import sub1.m
import sub2.m

if __name__ == "__main__":
    sub1.m.func()
    sub2.m.func()
```

There is a function called `func` in ***sub1/m.py*** and there is a function with exactly the same name `func` in ***sub2/m.py***. Since we wanted to use `func` from the two modules, we had to import the modules first by writing `import sub1.m` and `import sub2.m`. We then called the functions by writing `sub1.m.func` and `sub2.m.func`. When we execute ***pack.py***, we will see "hi" and "bye" printed out on the command prompt.

Note that there are two functions (**objects**) with the same **name** (i.e. `func`). We can uniquely call each of them in **pack.py** by specifying which package and module they belong to. It is possible for us to uniquely refer to the functions with the same names in this example, because the names of the functions exist in different namespaces.

Note that there are two modules (**objects**) with the same **name** (i.e. `m`). We can uniquely access each of them in **pack.py** by specifying which sub-package they belong to. It is possible for us to uniquely refer to the modules with the same names in this example, because the names of the modules exist in different namespaces (i.e. in **sub1** and **sub2**).

The **pack** package has its own namespace. Its namespace has the names of its own modules (e.g. **pack.py**) and sub-packages (e.g. **sub1** and **sub2**). The sub-packages **sub1** and **sub2** have their own namespaces. Their namespaces have the names of their modules (e.g. **m.py**).

The module **m.py** in each of the sub-packages has its own namespace. Its namespace has the name of the function `func`, in other words, the name `func`.

***Note*** that in the previous two sentences we have introduced a new namespace which we call the **Module Namespace**. We will learn about the **module namespaces** in the next section.

### 2.3 Module Namespace (Global Namespace)

A **module namespace** is commonly called the **global namespace** in Python. If we hear the phrase "module namespace" or "module-level namespace" or "global namespace", they are all talking about the same thing. We will use the phrase "global namespace" throughout the rest of this document.

**Global namespace** exists only in a module and it contains the names of the globally defined variables, the names of globally defined functions, and the names of globally defined classes. We will look at what it means for variables, functions, and classes to be globally defined. Let us have a look at an example of a module. Create a file called **foo.py** and write the code as shown below.

***foo.py***

```python
GLO1 = 1
GLO2 = 2

def top_func():
    print("top")
    def sub_func():
        print("sub")

class TopClass:
    class SubClass:
        pass

if __name__ == "__main__":
    GLO3 = 3
```

We can see that there are three global variables in **foo.py**. The names of the global variables `GLO1`, `GLO2`, and `GLO3`, namely, the names "GLO1", "GLO2", and "GLO3" are in the **global namespace**. Also, the names of the globally defined function and class are in the global namespace: `top_func` and `TopClass` are in the global namespace, whereas `sub_func` and `SubClass` are not in the global namespace.

As we can see in **foo.py**, a function can be defined inside another function and a class can be defined inside another class. They are called nested/inner functions and nested/inner classes. We will not come across nested functions or classes in stability test scripts, but we introduce them here lightly for the purpose of learning about Python namespaces.

>   **Global namespace** exists only in a module, and it has the names of the globally defined variables, globally defined functions, and globally defined classes.

### 2.4 Local Namespace

A **local namespace** exists only in a function, and it contains the names of the local variables and the names of the inner functions. The local namespace of a function is created only at the time the function is called and only lasts **until the function *returns*** (when the function completes its execution). If we do not write any `return` statements in a function, a `None` value will be returned by default.

>   **All** Python functions return either `None` or some value specified through the `return` statement.

Let us look at an example. Create a file called **bar.py** and write the code as shown below.

**bar.py**

```python
def top_func():
    """outer function"""
    a = "top"
    def sub_func():
        """inner function"""
        a = "what"
    sub_func()
    print(a)

if __name__ == "__main__":
    top_func()
```

*Sidenote:* Notice that `top_func` does not have a `return` statement. Python functions return `None` by default when there are no `return` statements. The point we want to make here is that whether or not we write the `return` statements in a function, the function will still return something, which means that the local namespace of the function will be discarded once the call to the function has completed its execution.

Let us break down the **bar.py** example shown above.

1.  `top_func` is a globally defined function, **and its local namespace:**
    *   Has the name of the variable `a`, namely, the name "a" that has the string "top".
    *   Has the name of the function `sub_func`, namely, the name "sub_func".
    *   Does not have the name of the variable `a` defined inside the `sub_func` function.
1.  `sub_func` is a locally defined function, **and its own local namespace:**
    *   Has the name of the variable `a`, namely, the name "a" that has the string "what".
1.  We call `sub_func` on line #7.
    *   The local namespace gets created as soon as the function is called.
    *   The assignment statement `a = "what"` does not overwrite the `top_func`'s variable `a` because `sub_func` is not allowed to assign a new object to the variables defined in `top_func`. Instead, the assignment statement `a = "what"` in `sub_func` creates a local variable for `sub_func`. The name of the local variable `a` in `sub_func`, namely, the name "a" will be stored in `sub_func` function's own local namespace.
    *   The local namespace gets destroyed as soon as the function returns.
1.  We then print out variable `a` on line #8.
    *   We notice that the word "top" gets printed out (not the word "what"). This is due to the fact that assigning "what" to variable `a` from `sub_func` creates a new variable with the name "a" inside the `sub_func` function's own local namespace, and it has no relation to the variable `a` defined in the outer function `top_func`.

**Rules of Assigning, Mutating, and Reading Objects of Variables in the Context of Inner & Outer Functions:**

1.  From the perspective of the inner function (i.e. `sub_func`) we ***cannot* assign a new object** (i.e. `"what"`) to a variable (i.e. `a`) that was originally defined in the outer function (i.e. `top_func`).
1.  From the perspective of the inner function (i.e. `sub_func`) we ***can* mutate the object itself** of a variable that was originally defined in the outer function (i.e. `top_func`) *only if the object is mutable*.
1.  From the perspective of the inner function (i.e. `sub_func`) we ***can* read the object** of a variable that was originally defined in the outer function (i.e. `top_func`) *only if the inner function does not attempt to assign a new object to the variable*.

>   **Local namespace** exists only in a function, and it has the names of the local variables and nested functions.

### 2.5 Enclosing Namespace

An **enclosing namespace** exists in the context of a nested function. Let us look back at **bar.py** for a moment.

**bar.py**

```python
def top_func():
    """outer function"""
    a = "top"
    def sub_func():
        """inner function"""
        a = "what"
    sub_func()
    print(a)

if __name__ == "__main__":
    top_func()
```

The **bar.py** example here is exactly the same as the one we showed in the *Local Namespaces* section. We can refer to the *Local Namespace* section for a detailed description of the code.

If we look closely at line #3, we see that variable `a` is defined in `top_func`; it is a variable that is local to `top_func`; the name of the variable `a`, namely, the name "a" is in `top_func`'s local namespace. In the perspective of the inner function `sub_func`, the name of the variable `a` defined in `top_func` is in an **enclosing namespace**. Essentially, an enclosing namespace and a local namespace of an outer function refer to the same thing. If  `sub_func` looks at the variable `a` (which is defined in `top_func`), it is essentially looking inside its **enclosing namespace**, whereas if `top_func` looks at the same variable, it is looking at its own **local namespace**. Let us have a look at another example for a moment. Please create a file called **boobar.py**.

**boobar.py**

```python
def func1():
    one = 1
    def func2():
        two = 2
        def func3():
            pass
```

`func1`'s local namespace has the names of `one` and `func2`. `func2`'s local namespace has the names of `two` and `func3`. `func3` sees that `two` is in its **enclosing namespace**, and `func2` sees that `one` is in its **enclosing namespace**.

>   **Enclosing namespace** exists only in a function in the context of nested functions, and it has the names of the local variables and nested functions. It is in essence, the **local namespace** of a function that is directly one level up in a nest from the perspective of a nested function.

### 2.6 Built-in Namespace

**Built-in namespace** exists in a Python program as a whole, for the lifetime of the program, and it ceases to exist when the program terminates. A **built-in namespace** has the names of the built-in functions & variables such as `id`, `range`, `len`, and `__name__`.

More accurate way to describe a built-in namespace is the following: a built-in namespace exists in an actively running Python interpreter; therefore it gets created when the Python interpreter starts, and it gets destroyed when the Python interpreter terminates.

*What does it mean for the Python interpreter to start and terminate?* Whenever we are running a Python module, we are starting a Python interpreter. The Python interpreter is the thing that interprets our Python code into a language that the computer can understand. When the computer finishes running a Python module and there are no more modules that it is told to run, then the Python interpreter terminates.

To put this into perspective, imagine writing a module that imports another module. All the code inside each of the two modules is in either global namespace, local namespace, or enclosing namespace. The built-in namespace lives above the global namespace and it can be accessed by the two modules that are running within the same Python interpreter.

Let us have a look at an example for a moment.

**x.py**

```python
def func():
    pass
```

**y.py**

```python
import x
if __name__ == "__main__":
    x.func()
```

In the above example, we have two modules **x.py** and **y.py**. **y.py** imports the **x** module. Imagine that we execute **y.py** on the command prompt. As soon as we execute the file, Python interpreter starts, and during the run-time of **y.py**, **x** module gets imported. In this entire process, there exists only a single **built-in namespace**, where as there are two different global namespaces; one for each module. When the module **y.py** finishes running, the Python iterpreter terminates. When the Python interpreter terminates, the **built-in namespace** gets destroyed.

>   **Built-in namespace** exists only in an actively running Python interpreter, and it contains the names of the built-in functions. It is created when the Python interpreter starts. It is destroyed when the Python interpreter terminates.

### 2.7 Conclusion

We have discussed all **five** Python namespaces:

*   Package Namespace
*   Global Namespace (Module Namespace)
*   Local Namespace
*   Enclosing namespace
*   Built-in Namespace

A **namespace** is where **names** exist, and each name is associated with an **object**. In Python, a **package** is an object, a **module** is an object, a **class** is an object, a **function** is an object, and **values** such as **strings**, **integers**, **floats**, and **booleans** are all objects, and each of them has an associated name.

### ⚠ Caution

>   The terminology "**namespace**" and "**scope**" are often used interchangeably, but it is not because they have the same definition; it is because the words that surround the terminology overlap in discussions that reason about which namespace a name belongs to or which portion of the code can a name be accesssed.

## 3.0 Python Scopes

### 3.1 General Description

A **scope** is a ***textual region of a program*** where a namespace is ***directly accessible***.

In Python, there are a total of four **scopes**:

*   Built-in Scope
*   Global Scope
*   Enclosing Scope
*   Local Scope

In Python, there are a total of five **namespaces**:

*   Package Namespace
*   Built-in Namespace
*   Global Namespace
*   Enclosing Namespace
*   Local Namespace

As you can see from the above two lists for Python scopes and namespaces, there are several words that look the same, namely, the words "built-in", "global", "enclosing", and "local". This is where things can get a little bit tricky. However, there are crucial differences between a scope and a namespace.

**Namespace**

>   A **namespace** is where **names** exist, and each name is associated with an **object**.

**Scope**

>   A **scope** is a property of a name itself.
>   A **scope** is a ***textual region of a program*** where a namespace is ***directly accessible***.
>   A **scope** informs Python which namespace to search for a name when the name is being used.

***Directly accessing*** a namespace means that you do not have to prefix a name with a namespace to refer to a name. Here are some examples of prefixing a name with its namespace:  `random.shuffle`, `math.pow`, and `uiautomator.Device`. In the examples, `random` is a namespace of `shuffle`, `math` is the namespace of `pow`, and `uiautomator` is the namespace of `Device`. When we can directly access a name in a namespace, we do not have to include any namespace prefixes. For example, if we had a variable assignment like `x = 1` and we tried to print out `x` in the next line of code, we simply use the variable's name `x` to do so. We do not have to prefix it with a namespace like we did for `random.shuffle` or `math.pow` above.

### 3.2 Scope Example #1

**neighborhood.py**

```python
you = "me"

def andersons_house():
    print(you) # this is valid, you can print you because you is in the global scope.
    john = "John Anderson"
    print(jenny) # this is invalid because jenny is in smiths_house's local scope.

def simiths_house():
    print(you) # this is valid, you can print you because you is in the global scope.
    jenny = "Jenny Smith"
    print(john) # this is invalid because john is in andersons_house's local scope.
```

1.  The variable `you` is a globally defined variable.
    *   The name "you" exists in the global namespace.
2.  The function `andersons_house` is a globally defined function.
    *   The name "andersons_house" exists in the global namespace.
    *   The `print` statement prints `you`. `you` has a global scope.
    *   The variable `john` is a locally defined variable.
        *   The name "john" exists in the local namespace.
    *   The `print` statement cannot print `jenny` because it is in `smiths_house`'s local scope.
3.  The function `smiths_house` is a globally defined function.
    *   The name "smiths_house" exists in the global namespace.
    *   The `print` statement prints `you`. `you` has a global scope.
    *   The variable `jenny` is a locally defined variable.
        *   The name "jenny" exists in the local namespace.
    *   The `print` statement cannot print `john` because it is in `andersons_house`'s local scope.

### 3.3 Scope Example #2

**module1.py**

```python
global_var = 1

def outer_func():
    outer_var = 1
    print(outer_var)
    def inner_func():
        inner_var = 2
        print(global_var)
        print(outer_var)
        print(inner_var)
    inner_func()

if __name__ == "__main__":
    outer_func()
```

1.  The variable `global_var` is a globally defined variable; a global variable.
    *   The name "global_var" exists in the global namespace of **module1**.
2.  The function `outer_func` is a globally defined function.
    *   The name "outer_func" exists in the global namespace.
    *   The variable `outer_var` is a locally defined variable; a local variable.
        *   The name "outer_var" exists in the local namespace of `outer_func`.
    *   The `print` statement prints `outer_var`. `outer_var` has a local scope.
    *   The function `inner_func` is a locally defined function; a nested function.
        *   The name "inner_func" exists in the local namespace of `outer_func`.
        *   The variable `inner_var` is a locally defined variable; a local variable.
            *   The name "inner_var" exists in the local namespace of `inner_func`.
        *   The `print` statement prints `global_var`. `global_var` has a global scope.
        *   The `print` statement prints `outer_var`. `outer_var` has an enclosing scope.
        *   The `print` statement prints `inner_var`. `inner_var` has a local scope.
3.  The function call `inner_func()` calls `inner_func`. `inner_func` has a local scope.
4.  The function call `outer_func()` calls `outer_func`. `outer_func` has a global scope.

### 3.4 Local Scope

*   If a variable `x` is defined locally in a function, the name "x" gets stored in the local namespace.
*   If a variable `x` is defined locally in a function, the variable `x` **has** a local scope.

### 3.5 Enclosing Scope

*   If a variable `x` is defined locally in an outer function, the name "x" gets stored in the outer function's local namespace.
*   If there is an inner function, then from its own point of view, the name "x" is in an enclosing namespace.
*   If there is an inner function, then from its own point of view, the variable `x` **has** an enclosing scope.

### 3.6 Global Scope

*   If a variable `x` is defined globally in a module, the name "x" gets stored in the global namespace.
*   If a variable `x` is defined globally in a module, the variable `x` **has** a global scope.

### 3.7 Built-in Scope

All of the Python built-in names have the built-in scope, which means that all of our own Python modules (i.e. our own .py files) that are running under the same Python interpreter will have access to them.

## 4.0 Scope Resolution

### 4.1. General Description

At any given point in time during an execution of any Python program, there are at least three different scopes whose namespaces are directly accessible.

1.  The **local scope** of a name is searched first.
2.  The **enclosing scope** of a name is searched next.
3.  The **global scope** of a name is searched afterward.
4.  The **built-in scope** of a name is searched last.

>   Searching for a scope of a name means that Python will search for the name in a particular namespace.

### 4.2 Scope Resolution Example

Let us look at an example to discuss what it means to search a scope of a name.

**scope.py**

```python
def outer_func():
    def inner_func():
        missing_func()
    inner_func()

if __name__ == "__main__":
    outer_func()
```

*   **Line #1:** The function `outer_func` is a globally defined function.
*   **Line #2:** The function `inner_func` is a locally defined function.
*   **Line #3:** The function call `missing_func()` is not defined anywhere in the module.
*   **Line #4:** The function call `inner_func()` calls `inner_func`. `inner_func` has a local scope.
*   **Line #7:** The function call `outer_func()` calls `outer_func`. `outer_func` has a global scope.

When you execute **scope.py**, you will get an error like the following:

```
Traceback (most recent call last):
  File "C:\Users\j.park.cnt\Desktop\test.py", line 7, in <module>
    outer_func()
  File "C:\Users\j.park.cnt\Desktop\test.py", line 4, in outer_func
    inner_func()
  File "C:\Users\j.park.cnt\Desktop\test.py", line 3, in inner_func
    missing_func()
NameError: global name 'missing_func' is not defined
```

### 4.3 The LEGB Rule

The LEGB rule is a scope resolution rule. It is a rule that the Python interpreter follows in order to search for the names that you are using in your Python code.

1.  Local
2.  Enclosing
3.  Global
4.  Built-in

Look closely at **Line #8** of the error message in **Section 4.2**, it says `NameError`. This is due to the fact that `missing_func` was not defined anywhere in the module. However, a question still remains, what steps did Python interpreter go through to conclude that `missing_func` was missing?

1.  When the Python interpreter makes an initial attempt to make a call to the function `missing_func`, it first searches for the name "missing_func" in the local namespace (the name's local scope is searched), and since the interpreter does not find the name in the local namespace;
2.  The interpreter starts searching for it in the enclosing namespace (the name's enclosing scope is searched). And, since the name does not exist in the enclosing namespace;
3.  The interpreter starts searching for the name in the global namespace (the name's global scope is searched), but the name does not exist in the global namespace either, so;
4.  The interpreter searches for the name in the built-in namespace (the name's built-in scope is searched). However, the name did not exist in the built-in namespace either.

After going searching through all the namespaces (all the name's scopes), Python was not able to find the name "missing_func"; therefore, the interpreter raised a Python exception called `NameError`.

## 5.0 The `global` keyword

The keyword `global` is useful when we want to:

1.  Modify the value of an existing global variable from within a function, or
2.  Create a new global variable from within a function.

**Attempting to Access a Local Variable**

Let us first take a look at an example that attempts to access a local variable; a variable that was initially defined within a function without the `global` keyword.

**global1.py**

```python
def func1():
    """Create a local variable."""
    somevar = "foo"

if __name__ == "__main__":
    func1()
    print(somevar)
```

The above example **global1.py** will produce an exception like so:

```
Traceback (most recent call last):
  File "C:\Users\jpjhp\Desktop\global1.py", line 7, in <module>
    print(somevar)
NameError: name 'somevar' is not defined
```

The above example produces an exception, because when the Python interpreter first tries to execute the `print(somevar)`, it starts looking for the variable `somevar` starting from the global namespace, and it will never be able to find the variable because the order in which the name of the variable "somevar" is searched goes from the global namespace to the built-in namespace (which also does not have the name "somevar").

**Creating a Global Variable From a Function**

Now, if we use the `global` keyword to declare `somevar` as a global variable, we should be able to access `somevar` outside of `func2`. In the following example, notice how we did not have to **initially** define the `somevar` variable outside of `func2`; we simply used the `global` keyword from within `func2` to make it into a global variable.

**global2.py**

```python
def func2():
    """Create a global variable inside a function."""
    global somevar
    somevar = "bar"


if __name__ == "__main__":
    func2()
    print(somevar)
```

The above example **global2.py** will indeed print out the value "bar".

**Changing a Global Variable Inside a Function**

You can also change a value of an existing global variable from within/inside a function. Let's say that you have a global variable called `foo`, and if you have a function that wants to modify its value, you have to write `global foo` inside the function.

**global3.py**

```python
# We create a global variable called foo
foo = "global"


def func3():
    """This function does NOT update the global variable. This is creating a local variable called foo."""
    foo = "local"


def func4():
    """This function can UPDATE -- or assign a new object to -- the global variable."""
    global foo
    foo = "still global"


if __name__ == "__main__":
    func3()
    print(foo)  # this prints out "global"
    func4()
    print(foo)  # this prints out "still global"
```

*   **Line #2:** `foo` is a globally defined variable (global variable).
*   **Line #5:** `func3` is a globally defined function.
    *   We don't call a globally defined function -- a global function. They are just called "functions".
    *   **Line #7:** `foo` is a locally defined variable (local variable).
        *   The statement `foo = "local"` does not assign a new object "local" to the global variable `foo`.
        *   The statement `foo = "local"` creates a new local variable called `foo` that is local to `func3`.
*   **Line #10:** `func4` is a globally defined function.
    *   **Line #12:** `global foo` statement basically says that from now on, if you use `foo` variable in the `func4` function, `foo` will refer to the `foo` global variable.
    *   **Line #13:** `foo = "still global"` assigns a new object "still global" to the global variable `foo`.
*   **Line #17:** Function `func3` is called here, but the global variable `foo` is not modified.
    *   Only the local variable `foo` (local to `func3`) is created when `func3` is called.
*   **Line #18:** `print(foo)` prints out the string "global".
    *   Notice that the call to `func3` did not modify the global variable `foo`; therefore, printing `foo` here will just print out "global".
*   **Line #19:** Function `func4` is called here, and this time, the global variable `foo` gets modified.
*   **Line #20:** `print(foo)` prints out the string "still global".
    *   Notice that the call to `func4` successfully modified the global variable `foo` since `foo` was declared as a `global` variable from within the `func4` function.

## 6.0 The `nonlocal` Keyword

**Section 2.4** introduced you to a rule that says that you cannot assign a new object to a variable that was originally defined in an outer function. Let us revisit the rule here: If you have an outer function and an inner function, and a variable defined in the outer function, you cannot assign a new object to the outer function's variable from inside the inner fuction.

Python 3 fixes such limitation by introducing a new keyword called `nonlocal`; it allows you to assign a new object to an outer variable from inside an inner function. The `nonlocal` keyword, followed by the variable that you wish to use, makes it ***non-local* and *non-global***. *Non-local* & *non-global* mean that the variable has an enclosing scope but can be manipulated inside of the inner function, and at the same time, it is not a global variable since it was never defined as a global variable. Let us have a look at an example of the `nonlocal` keyword.

**nonlocal1.py**

```python
def outer():
    outer_var = "outer"
    def inner():
        nonlocal outer_var
        outer_var = "inner"
        print(outer_var)
    inner()
    print(outer_var)


if __name__ == "__main__":
    outer()
```

*   **Line #1:** `outer` is a globally defined function.
*   **Line #2:** `outer_var` is a locally defined variable. Local to the `outer` function.
    *   `outer_var` is a local variable that can only be accessed inside the `outer` function.
*   **Line #3:** `inner` is a locally defined function.
*   **Line #4:** `nonlocal` makes the variable `outer_var` a non-local & non-global variable.
    *   `outer_var` is not a local to the `inner` function.
    *   `outer_var` now refers to the variable that was initially defined in the `outer` function.

*   **Line #5:** `outer_var = "inner"` assigns the "inner" string object to `outer_var`.
*   **Line #6:** `print(outer_var)` prints the string "inner".
*   **Line #7:** `innner()` calls the inner function.
*   **Line #8:** `print(msg)` prints out the string "inner".
*   **Line #12:** `outer` function is executed.

As you can see from the above example, the `outer_var` variable is never made into a local variable that is local to the `inner` function. The `nonlocal outer_var` statement allows the code inside the `inner` function to assign new object to the `outer_var` where `outer_var` refers to the variable that was originally defined at line #2.

## 7.0 Main Takeaways

>   A **namespace** is where **names** exist, and each name is associated with an **object**. In Python, a **package** is an object, a **module** is an object, a **class** is an object, a **function** is an object, and **values** such as **strings**, **integers**, **floats**, and **booleans** are all objects, and each of them has an associated name.

>A **scope** is a property of a name itself. A **scope** is a ***textual region of a program*** where a namespace is ***directly accessible***. A **scope** informs the Python interpreter which namespace and in what order the namespaces should be looked up in order to search for the name that is being used.