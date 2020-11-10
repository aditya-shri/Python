---
layout: default
title: timeit
parent: Advance Modules
nav_order: 7
---

# Timing your code
Sometimes it's important to know how long your code is taking to run, or at least know if a particular line of code is slowing down your entire project. Python has a built-in timing module to do this. 

## Example Function or Script

Here we have two functions that do the same thing, but in different ways.
How can we tell which one is more efficient? Let's time it!


```python
def func_one(n):
    '''
    Given a number n, returns a list of string integers
    ['0','1','2',...'n]
    '''
    return [str(num) for num in range(n)]
```


```python
func_one(10)
```




    ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']




```python
def func_two(n):
    '''
    Given a number n, returns a list of string integers
    ['0','1','2',...'n]
    '''
    return list(map(str,range(n)))
```


```python
func_two(10)
```




    ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']



### Timing Start and Stop

We can try using the time module to simply calculate the elapsed time for the code. Keep in mind, due to the time module's precision, the code needs to take **at least** 0.1 seconds to complete.


```python
import time
```


```python
# STEP 1: Get start time
start_time = time.time()
# Step 2: Run your code you want to time
result = func_one(1000000)
# Step 3: Calculate total time elapsed
end_time = time.time() - start_time
```


```python
end_time
```




    0.18550348281860352




```python
# STEP 1: Get start time
start_time = time.time()
# Step 2: Run your code you want to time
result = func_two(1000000)
# Step 3: Calculate total time elapsed
end_time = time.time() - start_time
```


```python
end_time
```




    0.1496279239654541



### Timeit Module

What if we have two blocks of code that are quite fast, the difference from the time.time() method may not be enough to tell which is fater. In this case, we can use the timeit module.

The timeit module takes in two strings, a statement (stmt) and a setup. It then runs the setup code and runs the stmt code some n number of times and reports back average length of time it took.


```python
import timeit
```

The setup (anything that needs to be defined beforehand, such as def functions.)


```python
setup = '''
def func_one(n):
    return [str(num) for num in range(n)]
'''
```


```python
stmt = 'func_one(100)'
```


```python
timeit.timeit(stmt,setup,number=100000)
```




    1.3161248000000114



Now let try running func_two 10,000 times and compare the length of time it took.


```python
setup2 = '''
def func_two(n):
    return list(map(str,range(n)))
'''
```


```python
stmt2 = 'func_two(100)'
```


```python
timeit.timeit(stmt2,setup2,number=100000)
```




    1.0892171000000417



It looks like func_two is more efficient. You can specify more number of runs if you want to clarify the different for fast performing functions.


```python
timeit.timeit(stmt,setup,number=1000000)
```




    13.129837899999984




```python
timeit.timeit(stmt2,setup2,number=1000000)
```




    10.894090699999992



## Timing you code with Jupyter "magic" method

**NOTE: This method is ONLY available in Jupyter and the magic command needs to be at the top of the cell with nothing above it (not even commented code)**


```python
%%timeit
func_one(100)
```

    100000 loops, best of 3: 13.4 µs per loop
    


```python
%%timeit
func_two(100)
```

    100000 loops, best of 3: 10.9 µs per loop
    

Great! Check out the documentation for more information:
https://docs.python.org/3/library/timeit.html
