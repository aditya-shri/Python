---
layout: default
title: Comparison Operators
nav_order: 3
has_children: true
---

# Comparison Operators 

In this lecture we will be learning about Comparison Operators in Python. These operators will allow us to compare variables and output a Boolean value (True or False). 

If you have any sort of background in Math, these operators should be very straight forward.

First we'll present a table of the comparison operators and then work through some examples:

<h2> Table of Comparison Operators </h2><p>  In the table below, a=3 and b=4.</p>

<table class="table table-bordered">
<tr>
<th style="width:10%">Operator</th><th style="width:45%">Description</th><th>Example</th>
</tr>
<tr>
<td>==</td>
<td>If the values of two operands are equal, then the condition becomes true.</td>
<td> (a == b) is not true.</td>
</tr>
<tr>
<td>!=</td>
<td>If values of two operands are not equal, then condition becomes true.</td>
<td>(a != b) is true</td>
</tr>
<tr>
<td>&gt;</td>
<td>If the value of left operand is greater than the value of right operand, then condition becomes true.</td>
<td> (a &gt; b) is not true.</td>
</tr>
<tr>
<td>&lt;</td>
<td>If the value of left operand is less than the value of right operand, then condition becomes true.</td>
<td> (a &lt; b) is true.</td>
</tr>
<tr>
<td>&gt;=</td>
<td>If the value of left operand is greater than or equal to the value of right operand, then condition becomes true.</td>
<td> (a &gt;= b) is not true. </td>
</tr>
<tr>
<td>&lt;=</td>
<td>If the value of left operand is less than or equal to the value of right operand, then condition becomes true.</td>
<td> (a &lt;= b) is true. </td>
</tr>
</table>

Let's now work through quick examples of each of these.

#### Equal


```python
2 == 2
```




    True




```python
1 == 0
```




    False



Note that <code>==</code> is a <em>comparison</em> operator, while <code>=</code> is an <em>assignment</em> operator.

#### Not Equal


```python
2 != 1
```




    True




```python
2 != 2
```




    False



#### Greater Than


```python
2 > 1
```




    True




```python
2 > 4
```




    False



#### Less Than


```python
2 < 4
```




    True




```python
2 < 1
```




    False



#### Greater Than or Equal to


```python
2 >= 2
```




    True




```python
2 >= 1
```




    True



#### Less than or Equal to


```python
2 <= 2
```




    True




```python
2 <= 4
```




    True



**Great! Go over each comparison operator to make sure you understand what each one is saying. But hopefully this was straightforward for you.**

Next we will cover chained comparison operators
