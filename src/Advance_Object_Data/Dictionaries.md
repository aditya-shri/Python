---
layout: default
title: Advance Dictionaries
parent: Advance Object and Data
nav_order: 4
---
# Advanced Dictionaries
Unlike some of the other Data Structures we've worked with, most of the really useful methods available to us in Dictionaries have already been explored throughout this course. Here we will touch on just a few more for good measure:

## Dictionary Comprehensions

Just like List Comprehensions, Dictionary Data Types also support their own version of comprehension for quick creation. It is not as commonly used as List Comprehensions, but the syntax is:


```python
{x:x**2 for x in range(10)}
```




    {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}



One of the reasons it is not as common is the difficulty in structuring key names that are not based off the values.

## Iteration over keys, values, and items
Dictionaries can be iterated over using the keys(), values() and items() methods. For example:


```python
d = {'k1':1,'k2':2}
```


```python
for k in d.keys():
    print(k)
```

    k1
    k2
    


```python
for v in d.values():
    print(v)
```

    1
    2
    


```python
for item in d.items():
    print(item)
```

    ('k1', 1)
    ('k2', 2)
    

# Viewing keys, values and items
By themselves the keys(), values() and items() methods return a dictionary *view object*. This is not a separate list of items. Instead, the view is always tied to the original dictionary.


```python
key_view = d.keys()

key_view
```




    dict_keys(['k1', 'k2'])




```python
d['k3'] = 3

d
```




    {'k1': 1, 'k2': 2, 'k3': 3}




```python
key_view
```




    dict_keys(['k1', 'k2', 'k3'])



Great! You should now feel very comfortable using the variety of methods available to you in Dictionaries!
