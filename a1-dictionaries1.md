# Dictionary
## Introduction
A dictionary is written as a series of key-value pairs within curly braces.

> The keys and the values can be of any data type (i.e. str, int, float)
```python
phone_numbers = {
	'John Doe': '123',
	'John Adams': '456'
}
```
## Printing the Entire Dictionary

You can print the entire dictionary in the following way.
```python
print phone_numbers
# Output: {'John Doe': '123','John Adams': '456'}
```
## Empty Dictionary
An empty dictionary is just an empty pair of curly braces. You can create an empty dictionary in the following way:
```python
phone_numbers = {}
```
## Setting Values to Dictionary
You can set values to a dictionary in the following way. You first have to write the code ```phone_numbers = {}``` to create an empty dictionary. Afterward, you have to set all the keys-value pairs to the dictionary in the following way:
```python
phone_numbers['John Doe'] = '123'
phone_numbers['John Adams'] = '456'
```
You can also create and set the key-value pairs for a dictionary in the following way:
```python
phone_numbers = {
	'John Doe': '123',
	'John Adams': '456'
}
```
## Indexing or Looking up a Value in Dictionary
Indexing into a dictionary or looking up a dictionary uses square brackets.
```python
print phone_numbers['John Doe']
# Output: 123
```
## Iterating Over a Dictionary
A for-loop on a dictionary iterates over its keys by default.
```python
for key in phone_numbers:
	print phone_numbers[key]
```
The above code prints out all the values that are associated with all the keys in the dictionary.
## Dictionary Functions
```keys()``` function returns a **list** of all the keys in a dictionary.
```values()``` function returns a **list** of all the values in a dictionary.
The following code prints out the lists of keys and values within the ```phone_numbers``` dictionary.
```python
print phone_numbers.keys()
print phone_numbers.values()
# Output:
# ['John Doe', 'John Adamas']
# ['123', '456']
```
## Deleting a Key-value Entry in a Dictionary
The ```del``` operator deletes a key-value entry of a dictionary.
The following code removes the entire key-value pair in ```phone_numbers``` dictionary.
```python
del phone_numbers['John Doe']
```
The above code deleted the key-value pair of ```'John Doe': '123'```.
Now, if you print out the entire dictionary like so:
```python
print phone_numbers
# Output: {'John Adams': '456'}
```
You no longer see ```'John Doe': '123'``` entry.
# Exercise
Create a dictionary with 5 key-value pairs. The keys should have the following types of values:

1. ```string```
2. ```integer```
3. ```float```
4. ```boolean```
5. ```variable (string)```

You may set the values of the dictionary to anything; ```string```, ```float```, ```integer```, ```boolean```.
Use a **while-loop** to print out each of the values in the dictionary. **Do not** use the ```values()``` function. **Use** the ```keys()``` function.

For example, if we had a dictionary like the following: ```var = {'2': 1, 'hi': 'bye'}```, ```print var.keys()``` will print out the keys of the dictionary as a list. Also, you can use the ```len()``` function to get the total length of a list.
