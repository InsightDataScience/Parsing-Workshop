# Chapter 2: Python Fundamentals

This chapter will review basic data structures in Python as well as some standard commands/modules useful for log parsing. The reader is expected to have a basic familiarity with Python.
This introduction is by no means comprehensive - refer to our [additional resources](#additional-resources) for more information.

## Data structures
A very brief overview over essential data structures in Python.  
### Variables
As Python is an untyped scripting language, variable assignments are as simple as can be.

```Python
a = "hello"
print(a)
a = [1, 2, 3]
print(a)
```


### Comments
Comments are an essential part of good software engineering practices. especially for complex code.
In Python, comments are started with `#`:

```Python
# I am a comment
#Please do not this, there should always be a whitespace after #
```
### Lists
A list is Python's version of an array. It is important to be familiar with lists and the methods the standard library provides. Here is a quick rundown:
```Python
a = [2, 1, 3]
print(a.sort()) # [1, 2, 3]
a.append(3)
print(a) # [1, 2, 3, 3]
a.extend([-9, 8])
print(a) # [1, 2, 3, 3, -9, 8]
a.remove(1)
print(a) # [2, 3, 3, -9, 8]
print(a[-1]) # [8]
print(a[2:4]) # [3, -9]
print(max(a)) # 8
print(a.count(3)) # 2
```
### Strings
Similar to lists, strings come with a bunch of handy built in functions. Let us again review them by example:
```Python
a = 'i am a string with a couple of words'
print(a.count('str')) # 1 because it counts occurences of 'str'
print(a.capitalize()) # I am a string with a couple of words
print(a.endswith('words')) # True
print(a.isalpha()) # True
print(a.isdigit()) # False, as a contains non-digit characters.
print(a.upper()) # 'I AM A STRING WITH A COUPLE OF WORDS'
print(a.split(' ')) # ['i', 'am', 'a', 'string', 'with', 'a', 'couple', 'of', 'words']

```
A couple of other useful functions to review:
- `.format()`: Allows you to reformat strings nicely.
- `sorted()`: Sorts strings alphanumerically.
### Dictionaries
### Regular Expressions


## Working with Files
## Argument Parsing
## Important Modules
## Additional Resources

## Next Chapter
Let us move on to [chapter 3](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/chapter3).
