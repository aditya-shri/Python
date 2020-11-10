---
layout: default
title: Variable Assignment
parent: Object and Data Structure
nav_order: 2
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# Variable Assignment

## Rules for variable names
* names can not start with a number
* names can not contain spaces, use _ intead
* names can not contain any of these symbols:

      :'",<>/?|\!@#%^&*~-+
       
* it's considered best practice ([PEP8](https://www.python.org/dev/peps/pep-0008/#function-and-variable-names)) that names are lowercase with underscores
* avoid using Python built-in keywords like `list` and `str`
* avoid using the single characters `l` (lowercase letter el), `O` (uppercase letter oh) and `I` (uppercase letter eye) as they can be confused with `1` and `0`

## Dynamic Typing

Python uses *dynamic typing*, meaning you can reassign variables to different data types. This makes Python very flexible in assigning data types; it differs from other languages that are *statically typed*.


```python
my_dogs = 2
```


```python
my_dogs
```




    2




```python
my_dogs = ['Sammy', 'Frankie']
```


```python
my_dogs
```




    ['Sammy', 'Frankie']



### Pros and Cons of Dynamic Typing
#### Pros of Dynamic Typing
* very easy to work with
* faster development time

#### Cons of Dynamic Typing
* may result in unexpected bugs!
* you need to be aware of `type()`

## Assigning Variables
Variable assignment follows `name = object`, where a single equals sign `=` is an *assignment operator*


```python
a = 5
```


```python
a
```




    5



Here we assigned the integer object `5` to the variable name `a`.<br>Let's assign `a` to something else:


```python
a = 10
```


```python
a
```




    10



You can now use `a` in place of the number `10`:


```python
a + a
```




    20



## Reassigning Variables
Python lets you reassign variables with a reference to the same object.


```python
a = a + 10
```


```python
a
```




    20



There's actually a shortcut for this. Python lets you add, subtract, multiply and divide numbers with reassignment using `+=`, `-=`, `*=`, and `/=`.


```python
a += 10
```


```python
a
```




    30




```python
a *= 2
```


```python
a
```




    60



## Determining variable type with `type()`
You can check what type of object is assigned to a variable using Python's built-in `type()` function. Common data types include:
* **int** (for integer)
* **float**
* **str** (for string)
* **list**
* **tuple**
* **dict** (for dictionary)
* **set**
* **bool** (for Boolean True/False)


```python
type(a)
```




    int




```python
a = (1,2)
```


```python
type(a)
```




    tuple



## Simple Exercise
This shows how variables make calculations more readable and easier to follow.


```python
my_income = 100
tax_rate = 0.1
my_taxes = my_income * tax_rate
```


```python
my_taxes
```




    10.0



Great! You should now understand the basics of variable assignment and reassignment in Python.<br>Up next, we'll learn about strings!
