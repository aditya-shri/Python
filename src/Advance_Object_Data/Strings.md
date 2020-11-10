---
layout: default
title: Advance Strings
parent: Advance Object Data
nav_order: 2
---

# Advanced Strings
String objects have a variety of methods we can use to save time and add functionality. Let's explore some of them in this lecture:


```python
s = 'hello world'
```

## Changing case
We can use methods to capitalize the first word of a string, or change the case of the entire string.


```python
# Capitalize first word in string
s.capitalize()
```




    'Hello world'




```python
s.upper()
```




    'HELLO WORLD'




```python
s.lower()
```




    'hello world'



Remember, strings are immutable. None of the above methods change the string in place, they only return modified copies of the original string.


```python
s
```




    'hello world'



To change a string requires reassignment:


```python
s = s.upper()
s
```




    'HELLO WORLD'




```python
s = s.lower()
s
```




    'hello world'



## Location and Counting


```python
s.count('o') # returns the number of occurrences, without overlap
```




    2




```python
s.find('o') # returns the starting index position of the first occurence
```




    4



## Formatting
The <code>center()</code> method allows you to place your string 'centered' between a provided string with a certain length. Personally, I've never actually used this in code as it seems pretty esoteric...


```python
s.center(20,'z')
```




    'zzzzhello worldzzzzz'



The <code>expandtabs()</code> method will expand tab notations <code>\t</code> into spaces:


```python
'hello\thi'.expandtabs()
```




    'hello   hi'



## is check methods
These various methods below check if the string is some case. Let's explore them:


```python
s = 'hello'
```

<code>isalnum()</code> will return True if all characters in **s** are alphanumeric


```python
s.isalnum()
```




    True



<code>isalpha()</code> will return True if all characters in **s** are alphabetic


```python
s.isalpha()
```




    True



<code>islower()</code> will return True if all cased characters in **s** are lowercase and there is
at least one cased character in **s**, False otherwise.


```python
s.islower()
```




    True



<code>isspace()</code> will return True if all characters in **s** are whitespace.


```python
s.isspace()
```




    False



<code>istitle()</code> will return True if **s** is a title cased string and there is at least one character in **s**, i.e. uppercase characters may only follow uncased characters and lowercase characters only cased ones. It returns False otherwise.


```python
s.istitle()
```




    False



<code>isupper()</code> will return True if all cased characters in **s** are uppercase and there is
at least one cased character in **s**, False otherwise.


```python
s.isupper()
```




    False



Another method is <code>endswith()</code> which is essentially the same as a boolean check on <code>s[-1]</code>


```python
s.endswith('o')
```




    True



## Built-in Reg. Expressions
Strings have some built-in methods that can resemble regular expression operations.
We can use <code>split()</code> to split the string at a certain element and return a list of the results.
We can use <code>partition()</code> to return a tuple that includes the first occurrence of the separator sandwiched between the first half and the end half.


```python
s.split('e')
```




    ['h', 'llo']




```python
s.partition('l')
```




    ('he', 'l', 'lo')



Great! You should now feel comfortable using the variety of methods that are built-in string objects!
