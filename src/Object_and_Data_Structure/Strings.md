---
layout: default
title: Strings
parent: Object and Data Structure
nav_order: 3
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# Strings

Strings are used in Python to record text information, such as names. Strings in Python are actually a *sequence*, which basically means Python keeps track of every element in the string as a sequence. For example, Python understands the string "hello' to be a sequence of letters in a specific order. This means we will be able to use indexing to grab particular letters (like the first letter, or the last letter).

This idea of a sequence is an important one in Python and we will touch upon it later on in the future.

In this lecture we'll learn about the following:

    1.) Creating Strings
    2.) Printing Strings
    3.) String Indexing and Slicing
    4.) String Properties
    5.) String Methods
    6.) Print Formatting

## Creating a String
To create a string in Python you need to use either single quotes or double quotes. For example:


```python
# Single word
'hello'
```




    'hello'




```python
# Entire phrase 
'This is also a string'
```




    'This is also a string'




```python
# We can also use double quote
"String built with double quotes"
```




    'String built with double quotes'




```python
# Be careful with quotes!
' I'm using single quotes, but this will create an error'
```


      File "<ipython-input-4-da9a34b3dc31>", line 2
        ' I'm using single quotes, but this will create an error'
            ^
    SyntaxError: invalid syntax
    


The reason for the error above is because the single quote in <code>I'm</code> stopped the string. You can use combinations of double and single quotes to get the complete statement.


```python
"Now I'm ready to use the single quotes inside a string!"
```




    "Now I'm ready to use the single quotes inside a string!"



Now let's learn about printing strings!

## Printing a String

Using Jupyter notebook with just a string in a cell will automatically output strings, but the correct way to display strings in your output is by using a print function.


```python
# We can simply declare a string
'Hello World'
```




    'Hello World'




```python
# Note that we can't output multiple strings this way
'Hello World 1'
'Hello World 2'
```




    'Hello World 2'



We can use a print statement to print a string.


```python
print('Hello World 1')
print('Hello World 2')
print('Use \n to print a new line')
print('\n')
print('See what I mean?')
```

    Hello World 1
    Hello World 2
    Use 
     to print a new line
    
    
    See what I mean?
    

## String Basics

We can also use a function called len() to check the length of a string!


```python
len('Hello World')
```




    11



Python's built-in len() function counts all of the characters in the string, including spaces and punctuation.

## String Indexing
We know strings are a sequence, which means Python can use indexes to call parts of the sequence. Let's learn how this works.

In Python, we use brackets <code>[]</code> after an object to call its index. We should also note that indexing starts at 0 for Python. Let's create a new object called <code>s</code> and then walk through a few examples of indexing.


```python
# Assign s as a string
s = 'Hello World'
```


```python
#Check
s
```




    'Hello World'




```python
# Print the object
print(s) 
```

    Hello World
    

Let's start indexing!


```python
# Show first element (in this case a letter)
s[0]
```




    'H'




```python
s[1]
```




    'e'




```python
s[2]
```




    'l'



We can use a <code>:</code> to perform *slicing* which grabs everything up to a designated point. For example:


```python
# Grab everything past the first term all the way to the length of s which is len(s)
s[1:]
```




    'ello World'




```python
# Note that there is no change to the original s
s
```




    'Hello World'




```python
# Grab everything UP TO the 3rd index
s[:3]
```




    'Hel'



Note the above slicing. Here we're telling Python to grab everything from 0 up to 3. It doesn't include the 3rd index. You'll notice this a lot in Python, where statements and are usually in the context of "up to, but not including".


```python
#Everything
s[:]
```




    'Hello World'



We can also use negative indexing to go backwards.


```python
# Last letter (one index behind 0 so it loops back around)
s[-1]
```




    'd'




```python
# Grab everything but the last letter
s[:-1]
```




    'Hello Worl'



We can also use index and slice notation to grab elements of a sequence by a specified step size (the default is 1). For instance we can use two colons in a row and then a number specifying the frequency to grab elements. For example:


```python
# Grab everything, but go in steps size of 1
s[::1]
```




    'Hello World'




```python
# Grab everything, but go in step sizes of 2
s[::2]
```




    'HloWrd'




```python
# We can use this to print a string backwards
s[::-1]
```




    'dlroW olleH'



## String Properties
It's important to note that strings have an important property known as *immutability*. This means that once a string is created, the elements within it can not be changed or replaced. For example:


```python
s
```




    'Hello World'




```python
# Let's try to change the first letter to 'x'
s[0] = 'x'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-26-976942677f11> in <module>()
          1 # Let's try to change the first letter to 'x'
    ----> 2 s[0] = 'x'
    

    TypeError: 'str' object does not support item assignment


Notice how the error tells us directly what we can't do, change the item assignment!

Something we *can* do is concatenate strings!


```python
s
```




    'Hello World'




```python
# Concatenate strings!
s + ' concatenate me!'
```




    'Hello World concatenate me!'




```python
# We can reassign s completely though!
s = s + ' concatenate me!'
```


```python
print(s)
```

    Hello World concatenate me!
    


```python
s
```




    'Hello World concatenate me!'



We can use the multiplication symbol to create repetition!


```python
letter = 'z'
```


```python
letter*10
```




    'zzzzzzzzzz'



## Basic Built-in String methods

Objects in Python usually have built-in methods. These methods are functions inside the object (we will learn about these in much more depth later) that can perform actions or commands on the object itself.

We call methods with a period and then the method name. Methods are in the form:

object.method(parameters)

Where parameters are extra arguments we can pass into the method. Don't worry if the details don't make 100% sense right now. Later on we will be creating our own objects and functions!

Here are some examples of built-in methods in strings:


```python
s
```




    'Hello World concatenate me!'




```python
# Upper Case a string
s.upper()
```




    'HELLO WORLD CONCATENATE ME!'




```python
# Lower case
s.lower()
```




    'hello world concatenate me!'




```python
# Split a string by blank space (this is the default)
s.split()
```




    ['Hello', 'World', 'concatenate', 'me!']




```python
# Split by a specific element (doesn't include the element that was split on)
s.split('W')
```




    ['Hello ', 'orld concatenate me!']



There are many more methods than the ones covered here. Visit the Advanced String section to find out more!

## Print Formatting

We can use the .format() method to add formatted objects to printed string statements. 

The easiest way to show this is through an example:


```python
'Insert another string with curly brackets: {}'.format('The inserted string')
```




    'Insert another string with curly brackets: The inserted string'



We will revisit this string formatting topic in later sections when we are building our projects!

## Next up: Lists!
