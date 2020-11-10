---
layout: default
title: Advance Numbers
parent: Advance Object and Data
nav_order: 1
---

# Advanced Numbers
In this lecture we will learn about a few more representations of numbers in Python.

## Hexadecimal

Using the function <code>hex()</code> you can convert numbers into a [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal) format:


```python
hex(246)
```




    '0xf6'




```python
hex(512)
```




    '0x200'



## Binary 
Using the function <code>bin()</code> you can convert numbers into their [binary](https://en.wikipedia.org/wiki/Binary_number) format.


```python
bin(1234)
```




    '0b10011010010'




```python
bin(128)
```




    '0b10000000'




```python
bin(512)
```




    '0b1000000000'



## Exponentials
The function <code>pow()</code> takes two arguments, equivalent to ```x^y```.  With three arguments it is equivalent to ```(x^y)%z```, but may be more efficient for long integers.


```python
pow(3,4)
```




    81




```python
pow(3,4,5)
```




    1



## Absolute Value
The function <code>abs()</code> returns the absolute value of a number. The argument may be an integer or a floating point number. If the argument is a complex number, its magnitude is returned.



```python
abs(-3.14)
```




    3.14




```python
abs(3)
```




    3



## Round
The function <code>round()</code> will round a number to a given precision in decimal digits (default 0 digits). It does not convert integers to floats.


```python
round(3,2)
```




    3




```python
round(395,-2)
```




    400




```python
round(3.1415926535,2)
```




    3.14



Python has a built-in math library that is also useful to play around with in case you are ever in need of some mathematical operations. Explore the documentation [here](https://docs.python.org/3/library/math.html)!
