---
layout: default
title: Tuples
parent: Object and Data Structure
nav_order: 7
---

# Tuples

In Python tuples are very similar to lists, however, unlike lists they are *immutable* meaning they can not be changed. You would use tuples to present things that shouldn't be changed, such as days of the week, or dates on a calendar. 

In this section, we will get a brief overview of the following:

    1.) Constructing Tuples
    2.) Basic Tuple Methods
    3.) Immutability
    4.) When to Use Tuples

You'll have an intuition of how to use tuples based on what you've learned about lists. We can treat them very similarly with the major distinction being that tuples are immutable.

## Constructing Tuples

The construction of a tuples use () with elements separated by commas. For example:


```python
# Create a tuple
t = (1,2,3)
```


```python
# Check len just like a list
len(t)
```




    3




```python
# Can also mix object types
t = ('one',2)

# Show
t
```




    ('one', 2)




```python
# Use indexing just like we did in lists
t[0]
```




    'one'




```python
# Slicing just like a list
t[-1]
```




    2



## Basic Tuple Methods

Tuples have built-in methods, but not as many as lists do. Let's look at two of them:


```python
# Use .index to enter a value and return the index
t.index('one')
```




    0




```python
# Use .count to count the number of times a value appears
t.count('one')
```




    1



## Immutability

It can't be stressed enough that tuples are immutable. To drive that point home:


```python
t[0]= 'change'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-8-1257c0aa9edd> in <module>()
    ----> 1 t[0]= 'change'
    

    TypeError: 'tuple' object does not support item assignment


Because of this immutability, tuples can't grow. Once a tuple is made we can not add to it.


```python
t.append('nope')
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-9-b75f5b09ac19> in <module>()
    ----> 1 t.append('nope')
    

    AttributeError: 'tuple' object has no attribute 'append'


## When to use Tuples

You may be wondering, "Why bother using tuples when they have fewer available methods?" To be honest, tuples are not used as often as lists in programming, but are used when immutability is necessary. If in your program you are passing around an object and need to make sure it does not get changed, then a tuple becomes your solution. It provides a convenient source of data integrity.

You should now be able to create and use tuples in your programming as well as have an understanding of their immutability.

Up next Files!
