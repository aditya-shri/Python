---
layout: default
title: while Loop
parent: Statements
nav_order: 4
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# while Loops

The <code>while</code> statement in Python is one of most general ways to perform iteration. A <code>while</code> statement will repeatedly execute a single statement or group of statements as long as the condition is true. The reason it is called a 'loop' is because the code statements are looped through over and over again until the condition is no longer met.

The general format of a while loop is:

    while test:
        code statements
    else:
        final code statements

Let’s look at a few simple <code>while</code> loops in action. 


```python
x = 0

while x < 10:
    print('x is currently: ',x)
    print(' x is still less than 10, adding 1 to x')
    x+=1
```

    x is currently:  0
     x is still less than 10, adding 1 to x
    x is currently:  1
     x is still less than 10, adding 1 to x
    x is currently:  2
     x is still less than 10, adding 1 to x
    x is currently:  3
     x is still less than 10, adding 1 to x
    x is currently:  4
     x is still less than 10, adding 1 to x
    x is currently:  5
     x is still less than 10, adding 1 to x
    x is currently:  6
     x is still less than 10, adding 1 to x
    x is currently:  7
     x is still less than 10, adding 1 to x
    x is currently:  8
     x is still less than 10, adding 1 to x
    x is currently:  9
     x is still less than 10, adding 1 to x
    

Notice how many times the print statements occurred and how the <code>while</code> loop kept going until the True condition was met, which occurred once x==10. It's important to note that once this occurred the code stopped. Let's see how we could add an <code>else</code> statement:


```python
x = 0

while x < 10:
    print('x is currently: ',x)
    print(' x is still less than 10, adding 1 to x')
    x+=1
    
else:
    print('All Done!')
```

    x is currently:  0
     x is still less than 10, adding 1 to x
    x is currently:  1
     x is still less than 10, adding 1 to x
    x is currently:  2
     x is still less than 10, adding 1 to x
    x is currently:  3
     x is still less than 10, adding 1 to x
    x is currently:  4
     x is still less than 10, adding 1 to x
    x is currently:  5
     x is still less than 10, adding 1 to x
    x is currently:  6
     x is still less than 10, adding 1 to x
    x is currently:  7
     x is still less than 10, adding 1 to x
    x is currently:  8
     x is still less than 10, adding 1 to x
    x is currently:  9
     x is still less than 10, adding 1 to x
    All Done!
    

# break, continue, pass

We can use <code>break</code>, <code>continue</code>, and <code>pass</code> statements in our loops to add additional functionality for various cases. The three statements are defined by:

    break: Breaks out of the current closest enclosing loop.
    continue: Goes to the top of the closest enclosing loop.
    pass: Does nothing at all.
    
    
Thinking about <code>break</code> and <code>continue</code> statements, the general format of the <code>while</code> loop looks like this:

    while test: 
        code statement
        if test: 
            break
        if test: 
            continue 
    else:

<code>break</code> and <code>continue</code> statements can appear anywhere inside the loop’s body, but we will usually put them further nested in conjunction with an <code>if</code> statement to perform an action based on some condition.

Let's go ahead and look at some examples!


```python
x = 0

while x < 10:
    print('x is currently: ',x)
    print(' x is still less than 10, adding 1 to x')
    x+=1
    if x==3:
        print('x==3')
    else:
        print('continuing...')
        continue
```

    x is currently:  0
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  1
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  2
     x is still less than 10, adding 1 to x
    x==3
    x is currently:  3
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  4
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  5
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  6
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  7
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  8
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  9
     x is still less than 10, adding 1 to x
    continuing...
    

Note how we have a printed statement when x==3, and a continue being printed out as we continue through the outer while loop. Let's put in a break once x ==3 and see if the result makes sense:


```python
x = 0

while x < 10:
    print('x is currently: ',x)
    print(' x is still less than 10, adding 1 to x')
    x+=1
    if x==3:
        print('Breaking because x==3')
        break
    else:
        print('continuing...')
        continue
```

    x is currently:  0
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  1
     x is still less than 10, adding 1 to x
    continuing...
    x is currently:  2
     x is still less than 10, adding 1 to x
    Breaking because x==3
    

Note how the other <code>else</code> statement wasn't reached and continuing was never printed!

After these brief but simple examples, you should feel comfortable using <code>while</code> statements in your code.

**A word of caution however! It is possible to create an infinitely running loop with <code>while</code> statements. For example:**


```python
# DO NOT RUN THIS CODE!!!! 
while True:
    print("I'm stuck in an infinite loop!")
```

A quick note: If you *did* run the above cell, click on the Kernel menu above to restart the kernel!
