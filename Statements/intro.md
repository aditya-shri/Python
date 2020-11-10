---
layout: default
title: Statements
parent: Statements
nav_order: 1
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# Introduction to Python Statements

In this lecture we will be doing a quick overview of Python Statements. This lecture will emphasize differences between Python and other languages such as C++. 

There are two reasons we take this approach for learning the context of Python Statements:

    1.) If you are coming from a different language this will rapidly accelerate your understanding of Python.
    2.) Learning about statements will allow you to be able to read other languages more easily in the future.

## Python vs Other Languages

Let's create a simple statement that says:
"If a is greater than b, assign 2 to a and 4 to b"

Take a look at these two if statements (we will learn about building out if statements soon).

**Version 1 (Other Languages)**

    if (a>b){
        a = 2;
        b = 4;
    }
                        
**Version 2 (Python)**   

    if a>b:
        a = 2
        b = 4

You'll notice that Python is less cluttered and much more readable than the first version. How does Python manage this?

Let's walk through the main differences:

Python gets rid of () and {} by incorporating two main factors: a *colon* and *whitespace*. The statement is ended with a colon, and whitespace is used (indentation) to describe what takes place in case of the statement.

Another major difference is the lack of semicolons in Python. Semicolons are used to denote statement endings in many other languages, but in Python, the end of a line is the same as the end of a statement.

Lastly, to end this brief overview of differences, let's take a closer look at indentation syntax in Python vs other languages:

## Indentation

Here is some pseudo-code to indicate the use of whitespace and indentation in Python:

**Other Languages**

    if (x)
        if(y)
            code-statement;
    else
        another-code-statement;
        
**Python**
    
    if x:
        if y:
            code-statement
    else:
        another-code-statement

Note how Python is so heavily driven by code indentation and whitespace. This means that code readability is a core part of the design of the Python language.

Now let's start diving deeper by coding these sort of statements in Python!

## Time to code!
