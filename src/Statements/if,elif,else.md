---
layout: default
title: if, elif and else
parent: Statements
nav_order: 2
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# if, elif, else Statements

<code>if</code> Statements in Python allows us to tell the computer to perform alternative actions based on a certain set of results.

Verbally, we can imagine we are telling the computer:

"Hey if this case happens, perform some action"

We can then expand the idea further with <code>elif</code> and <code>else</code> statements, which allow us to tell the computer:

"Hey if this case happens, perform some action. Else, if another case happens, perform some other action. Else, if *none* of the above cases happened, perform this action."

Let's go ahead and look at the syntax format for <code>if</code> statements to get a better idea of this:

    if case1:
        perform action1
    elif case2:
        perform action2
    else: 
        perform action3

## First Example

Let's see a quick example of this:


```python
if True:
    print('It was true!')
```

    It was true!
    

Let's add in some else logic:


```python
x = False

if x:
    print('x was True!')
else:
    print('I will be printed in any case where x is not true')
```

    I will be printed in any case where x is not true
    

### Multiple Branches

Let's get a fuller picture of how far <code>if</code>, <code>elif</code>, and <code>else</code> can take us!

We write this out in a nested structure. Take note of how the <code>if</code>, <code>elif</code>, and <code>else</code> line up in the code. This can help you see what <code>if</code> is related to what <code>elif</code> or <code>else</code> statements.

We'll reintroduce a comparison syntax for Python.


```python
loc = 'Bank'

if loc == 'Auto Shop':
    print('Welcome to the Auto Shop!')
elif loc == 'Bank':
    print('Welcome to the bank!')
else:
    print('Where are you?')
```

    Welcome to the bank!
    

Note how the nested <code>if</code> statements are each checked until a True boolean causes the nested code below it to run. You should also note that you can put in as many <code>elif</code> statements as you want before you close off with an <code>else</code>.

Let's create two more simple examples for the <code>if</code>, <code>elif</code>, and <code>else</code> statements:


```python
person = 'Sammy'

if person == 'Sammy':
    print('Welcome Sammy!')
else:
    print("Welcome, what's your name?")
```

    Welcome Sammy!
    


```python
person = 'George'

if person == 'Sammy':
    print('Welcome Sammy!')
elif person =='George':
    print('Welcome George!')
else:
    print("Welcome, what's your name?")
```

    Welcome George!
    

## Indentation

It is important to keep a good understanding of how indentation works in Python to maintain the structure and order of your code. We will touch on this topic again when we start building out functions!
