---
layout: default
title: for Loop
parent: Statements
nav_order: 3
---
___

<a href='https://www.udemy.com/user/joseportilla/'><img src='../Pierian_Data_Logo.png'/></a>
___
<center><em>Content Copyright by Pierian Data</em></center>

# for Loops

A <code>for</code> loop acts as an iterator in Python; it goes through items that are in a *sequence* or any other iterable item. Objects that we've learned about that we can iterate over include strings, lists, tuples, and even built-in iterables for dictionaries, such as keys or values.

We've already seen the <code>for</code> statement a little bit in past lectures but now let's formalize our understanding.

Here's the general format for a <code>for</code> loop in Python:

    for item in object:
        statements to do stuff
    

The variable name used for the item is completely up to the coder, so use your best judgment for choosing a name that makes sense and you will be able to understand when revisiting your code. This item name can then be referenced inside your loop, for example if you wanted to use <code>if</code> statements to perform checks.

Let's go ahead and work through several example of <code>for</code> loops using a variety of data object types. We'll start simple and build more complexity later on.

## Example 1
Iterating through a list


```python
# We'll learn how to automate this sort of list in the next lecture
list1 = [1,2,3,4,5,6,7,8,9,10]
```


```python
for num in list1:
    print(num)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    

Great! Hopefully this makes sense. Now let's add an <code>if</code> statement to check for even numbers. We'll first introduce a new concept here--the modulo.
### Modulo
The modulo allows us to get the remainder in a division and uses the % symbol. For example:


```python
17 % 5
```




    2



This makes sense since 17 divided by 5 is 3 remainder 2. Let's see a few more quick examples:


```python
# 3 Remainder 1
10 % 3
```




    1




```python
# 2 Remainder 4
18 % 7
```




    4




```python
# 2 no remainder
4 % 2
```




    0



Notice that if a number is fully divisible with no remainder, the result of the modulo call is 0. We can use this to test for even numbers, since if a number modulo 2 is equal to 0, that means it is an even number!

Back to the <code>for</code> loops!

## Example 2
Let's print only the even numbers from that list!


```python
for num in list1:
    if num % 2 == 0:
        print(num)
```

    2
    4
    6
    8
    10
    

We could have also put an <code>else</code> statement in there:


```python
for num in list1:
    if num % 2 == 0:
        print(num)
    else:
        print('Odd number')
```

    Odd number
    2
    Odd number
    4
    Odd number
    6
    Odd number
    8
    Odd number
    10
    

## Example 3
Another common idea during a <code>for</code> loop is keeping some sort of running tally during multiple loops. For example, let's create a <code>for</code> loop that sums up the list:


```python
# Start sum at zero
list_sum = 0 

for num in list1:
    list_sum = list_sum + num

print(list_sum)
```

    55
    

Great! Read over the above cell and make sure you understand fully what is going on. Also we could have implemented a <code>+=</code> to perform the addition towards the sum. For example:


```python
# Start sum at zero
list_sum = 0 

for num in list1:
    list_sum += num

print(list_sum)
```

    55
    

## Example 4
We've used <code>for</code> loops with lists, how about with strings? Remember strings are a sequence so when we iterate through them we will be accessing each item in that string.


```python
for letter in 'This is a string.':
    print(letter)
```

    T
    h
    i
    s
     
    i
    s
     
    a
     
    s
    t
    r
    i
    n
    g
    .
    

## Example 5
Let's now look at how a <code>for</code> loop can be used with a tuple:


```python
tup = (1,2,3,4,5)

for t in tup:
    print(t)
```

    1
    2
    3
    4
    5
    

## Example 6
Tuples have a special quality when it comes to <code>for</code> loops. If you are iterating through a sequence that contains tuples, the item can actually be the tuple itself, this is an example of *tuple unpacking*. During the <code>for</code> loop we will be unpacking the tuple inside of a sequence and we can access the individual items inside that tuple!


```python
list2 = [(2,4),(6,8),(10,12)]
```


```python
for tup in list2:
    print(tup)
```

    (2, 4)
    (6, 8)
    (10, 12)
    


```python
# Now with unpacking!
for (t1,t2) in list2:
    print(t1)
```

    2
    6
    10
    

Cool! With tuples in a sequence we can access the items inside of them through unpacking! The reason this is important is because many objects will deliver their iterables through tuples. Let's start exploring iterating through Dictionaries to explore this further!

## Example 7


```python
d = {'k1':1,'k2':2,'k3':3}
```


```python
for item in d:
    print(item)
```

    k1
    k2
    k3
    

Notice how this produces only the keys. So how can we get the values? Or both the keys and the values? 

We're going to introduce three new Dictionary methods: **.keys()**, **.values()** and **.items()**

In Python each of these methods return a *dictionary view object*. It supports operations like membership test and iteration, but its contents are not independent of the original dictionary – it is only a view. Let's see it in action:


```python
# Create a dictionary view object
d.items()
```




    dict_items([('k1', 1), ('k2', 2), ('k3', 3)])



Since the .items() method supports iteration, we can perform *dictionary unpacking* to separate keys and values just as we did in the previous examples.


```python
# Dictionary unpacking
for k,v in d.items():
    print(k)
    print(v) 
```

    k1
    1
    k2
    2
    k3
    3
    

If you want to obtain a true list of keys, values, or key/value tuples, you can *cast* the view as a list:


```python
list(d.keys())
```




    ['k1', 'k2', 'k3']



Remember that dictionaries are unordered, and that keys and values come back in arbitrary order. You can obtain a sorted list using sorted():


```python
sorted(d.values())
```




    [1, 2, 3]



## Conclusion

We've learned how to use for loops to iterate through tuples, lists, strings, and dictionaries. It will be an important tool for us, so make sure you know it well and understood the above examples.

[More resources](http://www.tutorialspoint.com/python/python_for_loop.htm)
