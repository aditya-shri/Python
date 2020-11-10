---
layout: default
title: Advance Lists
parent: Advance Object and Data
nav_order: 5
---

# Advanced Lists

In this series of lectures we will be diving a little deeper into all the methods available in a list object. These aren't officially "advanced" features, just methods that you wouldn't typically encounter without some additional exploring. It's pretty likely that you've already encountered some of these yourself!

Let's begin!


```python
list1 = [1,2,3]
```

## append
You will definitely have used this method by now, which merely appends an element to the end of a list:


```python
list1.append(4)

list1
```




    [1, 2, 3, 4]



## count
We discussed this during the methods lectures, but here it is again. <code>count()</code> takes in an element and returns the number of times it occurs in your list:


```python
list1.count(10)
```




    0




```python
list1.count(2)
```




    1



## extend
Many times people find the difference between extend and append to be unclear. So note:

**append: appends whole object at end:**


```python
x = [1, 2, 3]
x.append([4, 5])
print(x)
```

    [1, 2, 3, [4, 5]]
    

**extend: extends list by appending elements from the iterable:**


```python
x = [1, 2, 3]
x.extend([4, 5])
print(x)
```

    [1, 2, 3, 4, 5]
    

Note how <code>extend()</code> appends each element from the passed-in list. That is the key difference.

## index
<code>index()</code> will return the index of whatever element is placed as an argument. Note: If the the element is not in the list an error is raised.


```python
list1.index(2)
```




    1




```python
list1.index(12)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-8-56b94ada72bf> in <module>()
    ----> 1 list1.index(12)
    

    ValueError: 12 is not in list


## insert 
<code>insert()</code> takes in two arguments: <code>insert(index,object)</code> This method places the object at the index supplied. For example:


```python
list1
```




    [1, 2, 3, 4]




```python
# Place a letter at the index 2
list1.insert(2,'inserted')
```


```python
list1
```




    [1, 2, 'inserted', 3, 4]



## pop
You most likely have already seen <code>pop()</code>, which allows us to "pop" off the last element of a list. However, by passing an index position you can remove and return a specific element.


```python
ele = list1.pop(1)  # pop the second element
```


```python
list1
```




    [1, 'inserted', 3, 4]




```python
ele
```




    2



## remove
The <code>remove()</code> method removes the first occurrence of a value. For example:


```python
list1
```




    [1, 'inserted', 3, 4]




```python
list1.remove('inserted')
```


```python
list1
```




    [1, 3, 4]




```python
list2 = [1,2,3,4,3]
```


```python
list2.remove(3)
```


```python
list2
```




    [1, 2, 4, 3]



## reverse
As you might have guessed, <code>reverse()</code> reverses a list. Note this occurs in place! Meaning it affects your list permanently.


```python
list2.reverse()
```


```python
list2
```




    [3, 4, 2, 1]



## sort
The <code>sort()</code> method will sort your list in place:


```python
list2
```




    [3, 4, 2, 1]




```python
list2.sort()
```


```python
list2
```




    [1, 2, 3, 4]



The <code>sort()</code> method takes an optional argument for reverse sorting. Note this is different than simply reversing the order of items.


```python
list2.sort(reverse=True)
```


```python
list2
```




    [4, 3, 2, 1]



## Be Careful With Assignment!
A common programming mistake is to assume you can assign a modified list to a new variable. While this typically works with immutable objects like strings and tuples:


```python
x = 'hello world'
```


```python
y = x.upper()
```


```python
print(y)
```

    HELLO WORLD
    

This will NOT work the same way with lists:


```python
x = [1,2,3]
```


```python
y = x.append(4)
```


```python
print(y)
```

    None
    

What happened? In this case, since list methods like <code>append()</code> affect the list *in-place*, the operation returns a None value. This is what was passed to **y**. In order to retain **x** you would have to assign a *copy* of **x** to **y**, and then modify **y**:


```python
x = [1,2,3]
y = x.copy()
y.append(4)
```


```python
print(x)
```

    [1, 2, 3]
    


```python
print(y)
```

    [1, 2, 3, 4]
    

Great! You should now have an understanding of all the methods available for a list in Python!
