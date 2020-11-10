---
layout: default
title: Chained Comparison Operators
parent: Comparison Operators
nav_order: 2
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# Chained Comparison Operators

An interesting feature of Python is the ability to *chain* multiple comparisons to perform a more complex test. You can use these chained comparisons as shorthand for larger Boolean Expressions.

In this lecture we will learn how to chain comparison operators and we will also introduce two other important statements in Python: **and** and **or**.

Let's look at a few examples of using chains:


```python
1 < 2 < 3
```




    True



The above statement checks if 1 was less than 2 **and** if 2 was less than 3. We could have written this using an **and** statement in Python:


```python
1<2 and 2<3
```




    True



The **and** is used to make sure two checks have to be true in order for the total check to be true. Let's see another example:


```python
1 < 3 > 2
```




    True



The above checks if 3 is larger than both of the other numbers, so you could use **and** to rewrite it as:


```python
1<3 and 3>2
```




    True



It's important to note that Python is checking both instances of the comparisons. We can also use **or** to write comparisons in Python. For example:


```python
1==2 or 2<3
```




    True



Note how it was true; this is because with the **or** operator, we only need one *or* the other to be true. Let's see one more example to drive this home:


```python
1==1 or 100==1
```




    True



Great! For an overview of this quick lesson: You should have a comfortable understanding of using **and** and **or** statements as well as reading chained comparison code.

Go ahead and go to the quiz for this section to check your understanding!
