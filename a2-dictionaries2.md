## Dictionary

Like a `list`, a `dictionary` is a collection of many values. However, a list has a permanent set of indexes that start from 0 and are incremented by 1. If you have a list with three elements, the first element will always have the index `0`, the second `1`, the third `2`. However, unlike the indexes for lists, the indexes for a dictionary can be many different data types (not just integers like the lists).

The indexes for a dictionary are called `keys`, and a values associated with the keys are called the `values`. If there is a single key and a value that is associated with the key in a dictionary, then we say that the dictionary *has a* key-value pair. We can also synonymously say that the dictionary has a single entry, where we imply that the "entry" is a key-value pair. Another way to say this is: "The dictionary has a key-value entry."

### Creating and Using a Dictionary
#### Example #1 (Creating)
In code, a dictionary is typed with braces, `{}`. The following example shows two key-value entries for a dictionary called `my_cat`. `my_cat` dictionary represents the attributes of a cat such as its size and color. This assigns a dictionary to the `my_cat` variable. This dictionary keys are `size` and `color`. The values for these keys are `fat` and `gray`.

```python
>>> my_cat = {"size": "fat", "color": "gray"}
```
#### Example #2 (Using)
You can **access** the values in the above `my_cat` dictionary through their keys.
```python
>>> my_cat["size"]
'fat'
>>> "My cat has " + my_cat["color"] + " fur."
'My cat has gray fur.'
```
#### Example #3 (Creating & Using)
A dictionary can still use integer values as keys, just like lists use integers for indexes, but they do not have to start at 0 and can be any number.
```python
>>> variable = {12345: "Luggage Combination", 42: "The Answer"}
>>> variable[12345]
'Luggage Combination'
>>> variable[42]
'The Answer'
```
Notice that in the three examples above, the dictionaries `my_cat` and `variable` have keys that are of different data types. `my_cat` has keys that are of the string data type and the dictionary `variable` has the keys that are of the integer data type. The important bit that you have to remember regarding the data types for the keys in a dictionary is that *it does not matter what data type you are using* for the keys; a key can be a string, integer, float, boolean, and more.
### Dictionary versus List
Unlinke lists, the items/entries are unordered. Given a list `L = ["foo", "bar", "hello"]`, the **first item** of `L` is "foo", which is access by using the code `L[0]`. However, there is no concept of "**first**" item in a dictionary.
### The keys(), values(), and items() Functions
There are three functions that you can use with a dictionary:`keys()`, `values()`, and `items()`.  All three functions return a list. If you call `keys()` on a dictionary, you will get back a list of the dictionary's keys. If you call `values()` on a dictionary, you will get back a list of the dictionary's values. If you call `items()` on a dictionary, you will get back a list of tuples, where every tuple has two elements; the first element is the key and the second element is the value associated with the key.
#### Example #1 (keys, values, items)
```python
>>> my_cat = {"size": "fat", "color": "gray"}
>>> my_cat.keys()
["size", "color"]
>>> my_cat.values()
["fat", "gray"]
>>> my_cat.items()
[("size", "fat"), ("color", "gray")]
```
#### Example #2 (Using Loops)
```python
# values function
>>> spam = {'color': 'red', 'age': 42}
>>> for v in spam.values():
		print v
red
42
```
```python
# keys function
>>> spam = {'color': 'red', 'age': 42}
>>> for k in spam.keys():
		print k
color
age
```
```python
# items function
>>> spam = {'color': 'red', 'age': 42}
>>> for k, v in spam.items():
		print k, v
color red
age 42
```
### Checking if a Key or Value Exists in a Dictionary
Recall that from previous lessons and exercizes that the `in` and the `not in` operators can check whether or not a value exists in a `list`. You can also use these operators to see whether a certain key or value exists in a dictionary.
```python
>>> spam = {"name": "Zophie", "age": 7}
>>> "name" in spam.keys()
True
>>> "Zophie" in spam.values()
True
>>> "color" in spam.keys()
False
>>> "color" not in spam.keys()
True
>>> "color" in spam
False
```
In the example above, notice that the code: `"color" in spam`, is essentially a shorter version of writing the code: `"color" in spam.keys()`. If you ever want to check whether something is a key in the dictionary, you can simply use the `in` or `not in` operator with the dictionary itself (without calling the `keys()` function).
### The `get()` Function
It is tedious to check whether a key exists in a dictionary before accessing that key’s value. Fortunately, dictionaries have a `get()` function that takes two arguments: the key of the value to retrieve and a fallback value to return if that key does not exist.

The `get()` function takes two arguments:

1. The key of the value to retrieve
2. And a fallback value to return if that key does not exist.

```python
>>> picnic_items = {"apples": 5, "cups": 2}
>>> 'I am bringing ' + str(picnic_items.get("cups", 0)) + ' cups.'
'I am bringing 2 cups.'
>>> 'I am bringing ' + str(picnic_items.get("eggs", 0)) + ' eggs.'
'I am bringing 0 eggs.'
```

Because there is no "eggs" key in the `picnic_items` dictionary, the default value 0 is returned by the `get()` function. Without using `get()`, the code would have caused an error message, such as in the following example:

```python
>>> picnic_items = {"apples": 5, "cups": 2}
>>> "I am bringing " + str(picnic_items['eggs']) + " eggs."
Traceback (most recent call last):
	File "<pyshell#34>", line 1, in <module>
		'I am bringing ' + str(picnic_items['eggs']) + ' eggs.'
KeyError: 'eggs'
```

### The `setdefault()` Function

You’ll often have to set a value in a dictionary for a certain key only if that key does not already have a value. The code looks something like this:

```python
spam = {"name": "Pooka", "age": 5}
if "color" not in spam:
	spam["color"] = "black"
```

`setdefault()` offers a way to do this in one line of code. The first argument passed to the function is the key to check for, and the second argument is the value to set at that key if the key does not exist. If the key exists, the `setdefault()` returns the value associated with the existing key. Here is an example of `setdefault()` usage:

```python
>>> spam = {"name": "Pooka", "age": 5}
>>> spam.setdefault("color", "black")
'black'
>>> spam
{'color': 'black', 'age': 5, 'name': 'Pooka'}
>>> spam.setdefault("color", "white")
'black'
>>> spam
{'color': 'black', 'age': 5, 'name': 'Pooka'}
```