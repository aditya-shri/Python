---
layout: default
title: Methods
parent: Methods and Functions
nav_order: 1
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# Methods

We've already seen a few example of methods when learning about Object and Data Structure Types in Python. Methods are essentially functions built into objects. Later on in the course we will learn about how to create our own objects and methods using Object Oriented Programming (OOP) and classes.

Methods perform specific actions on an object and can also take arguments, just like a function. This lecture will serve as just a brief introduction to methods and get you thinking about overall design methods that we will touch back upon when we reach OOP in the course.

Methods are in the form:

    object.method(arg1,arg2,etc...)
    
You'll later see that we can think of methods as having an argument 'self' referring to the object itself. You can't see this argument but we will be using it later on in the course during the OOP lectures.

Let's take a quick look at what an example of the various methods a list has:


```python
# Create a simple list
lst = [1,2,3,4,5]
```

Fortunately, with iPython and the Jupyter Notebook we can quickly see all the possible methods using the tab key. The methods for a list are:

* append
* count
* extend
* insert
* pop
* remove
* reverse
* sort

Let's try out a few of them:

append() allows us to add elements to the end of a list:


```python
lst.append(6)
```


```python
lst
```




    [1, 2, 3, 4, 5, 6]



Great! Now how about count()? The count() method will count the number of occurrences of an element in a list.


```python
# Check how many times 2 shows up in the list
lst.count(2)
```




    1



You can always use Shift+Tab in the Jupyter Notebook to get more help about the method. In general Python you can use the help() function: 


```python
help(lst.count)
```

    Help on built-in function count:
    
    count(...) method of builtins.list instance
        L.count(value) -> integer -- return number of occurrences of value
    
    

Feel free to play around with the rest of the methods for a list. Later on in this section your quiz will involve using help and Google searching for methods of different types of objects!

Great! By this lecture you should feel comfortable calling methods of objects in Python!
