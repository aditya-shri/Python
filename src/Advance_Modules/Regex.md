---
layout: default
title: Regex
parent: Advance Modules
nav_order: 6
---

# Overview of Regular Expressions

Regular Expressions (sometimes called regex for short) allows a user to search for strings using almost any sort of rule they can come up. For example, finding all capital letters in a string, or finding a phone number in a document. 

Regular expressions are notorious for their seemingly strange syntax. This strange syntax is a byproduct of their flexibility. Regular expressions have to be able to filter out any string pattern you can imagine, which is why they have a complex string pattern format.

Let's begin by explaining how to search for basic patterns in a string!

## Searching for Basic Patterns

Let's imagine that we have the following string:


```python
text = "The person's phone number is 408-555-1234. Call soon!"
```

We'll start off by trying to find out if the string "phone" is inside the text string. Now we could quickly do this with:


```python
'phone' in text
```




    True



But let's show the format for regular expressions, because later on we will be searching for patterns that won't have such a simple solution.


```python
import re
```


```python
pattern = 'phone'
```


```python
re.search(pattern,text)
```




    <_sre.SRE_Match object; span=(13, 18), match='phone'>




```python
pattern = "NOT IN TEXT"
```


```python
re.search(pattern,text)
```

Now we've seen that re.search() will take the pattern, scan the text, and then returns a Match object. If no pattern is found, a None is returned (in Jupyter Notebook this just means that nothing is output below the cell).

Let's take a closer look at this Match object.


```python
pattern = 'phone'
```


```python
match = re.search(pattern,text)
```


```python
match
```




    <_sre.SRE_Match object; span=(13, 18), match='phone'>



Notice the span, there is also a start and end index information.


```python
match.span()
```




    (13, 18)




```python
match.start()
```




    13




```python
match.end()
```




    18



But what if the pattern occurs more than once?


```python
text = "my phone is a new phone"
```


```python
match = re.search("phone",text)
```


```python
match.span()
```




    (3, 8)



Notice it only matches the first instance. If we wanted a list of all matches, we can use .findall() method:


```python
matches = re.findall("phone",text)
```


```python
matches
```




    ['phone', 'phone']




```python
len(matches)
```




    2



To get actual match objects, use the iterator:


```python
for match in re.finditer("phone",text):
    print(match.span())
```

    (3, 8)
    (18, 23)
    

If you wanted the actual text that matched, you can use the .group() method.


```python
match.group()
```




    'phone'



# Patterns

So far we've learned how to search for a basic string. What about more complex examples? Such as trying to find a telephone number in a large string of text? Or an email address?

We could just use search method if we know the exact phone or email, but what if we don't know it? We may know the general format, and we can use that along with regular expressions to search the document for strings that match a particular pattern.

This is where the syntax may appear strange at first, but take your time with this, often its just a matter of looking up the pattern code.

Let' begin!

## Identifiers for Characters in Patterns

Characters such as a digit or a single string have different codes that represent them. You can use these to build up a pattern string. Notice how these make heavy use of the backwards slash \ . Because of this when defining a pattern string for regular expression we use the format:

    r'mypattern'
    
placing the r in front of the string allows python to understand that the \ in the pattern string are not meant to be escape slashes.

Below you can find a table of all the possible identifiers:

<table ><tr><th>Character</th><th>Description</th><th>Example Pattern Code</th><th >Exammple Match</th></tr>

<tr ><td><span >\d</span></td><td>A digit</td><td>file_\d\d</td><td>file_25</td></tr>

<tr ><td><span >\w</span></td><td>Alphanumeric</td><td>\w-\w\w\w</td><td>A-b_1</td></tr>



<tr ><td><span >\s</span></td><td>White space</td><td>a\sb\sc</td><td>a b c</td></tr>



<tr ><td><span >\D</span></td><td>A non digit</td><td>\D\D\D</td><td>ABC</td></tr>

<tr ><td><span >\W</span></td><td>Non-alphanumeric</td><td>\W\W\W\W\W</td><td>*-+=)</td></tr>

<tr ><td><span >\S</span></td><td>Non-whitespace</td><td>\S\S\S\S</td><td>Yoyo</td></tr></table>

For example:


```python
text = "My telephone number is 408-555-1234"
```


```python
phone = re.search(r'\d\d\d-\d\d\d-\d\d\d\d',text)
```


```python
phone.group()
```




    '408-555-1234'



Notice the repetition of \d. That is a bit of an annoyance, especially if we are looking for very long strings of numbers. Let's explore the possible quantifiers.

## Quantifiers

Now that we know the special character designations, we can use them along with quantifiers to define how many we expect.

<table ><tr><th>Character</th><th>Description</th><th>Example Pattern Code</th><th >Exammple Match</th></tr>

<tr ><td><span >+</span></td><td>Occurs one or more times</td><td>	Version \w-\w+</td><td>Version A-b1_1</td></tr>

<tr ><td><span >{3}</span></td><td>Occurs exactly 3 times</td><td>\D{3}</td><td>abc</td></tr>



<tr ><td><span >{2,4}</span></td><td>Occurs 2 to 4 times</td><td>\d{2,4}</td><td>123</td></tr>



<tr ><td><span >{3,}</span></td><td>Occurs 3 or more</td><td>\w{3,}</td><td>anycharacters</td></tr>

<tr ><td><span >\*</span></td><td>Occurs zero or more times</td><td>A\*B\*C*</td><td>AAACC</td></tr>

<tr ><td><span >?</span></td><td>Once or none</td><td>plurals?</td><td>plural</td></tr></table>

Let's rewrite our pattern using these quantifiers:


```python
re.search(r'\d{3}-\d{3}-\d{4}',text)
```




    <_sre.SRE_Match object; span=(23, 35), match='408-555-1234'>



## Groups

What if we wanted to do two tasks, find phone numbers, but also be able to quickly extract their area code (the first three digits). We can use groups for any general task that involves grouping together regular expressions (so that we can later break them down). 

Using the phone number example, we can separate groups of regular expressions using parenthesis:


```python
phone_pattern = re.compile(r'(\d{3})-(\d{3})-(\d{4})')
```


```python
results = re.search(phone_pattern,text)
```


```python
# The entire result
results.group()
```




    '408-555-1234'




```python
# Can then also call by group position.
# remember groups were separated by parenthesis ()
# Something to note is that group ordering starts at 1. Passing in 0 returns everything
results.group(1)
```




    '408'




```python
results.group(2)
```




    '555'




```python
results.group(3)
```




    '1234'




```python
# We only had three groups of parenthesis
results.group(4)
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-32-866de7a94a57> in <module>()
          1 # We only had three groups of parenthesis
    ----> 2 results.group(4)
    

    IndexError: no such group


## Additional Regex Syntax

### Or operator |

Use the pipe operator to have an **or** statment. For example


```python
re.search(r"man|woman","This man was here.")
```




    <_sre.SRE_Match object; span=(5, 8), match='man'>




```python
re.search(r"man|woman","This woman was here.")
```




    <_sre.SRE_Match object; span=(5, 10), match='woman'>



### The Wildcard Character

Use a "wildcard" as a placement that will match any character placed there. You can use a simple period **.** for this. For example:


```python
re.findall(r".at","The cat in the hat sat here.")
```




    ['cat', 'hat', 'sat']




```python
re.findall(r".at","The bat went splat")
```




    ['bat', 'lat']



Notice how we only matched the first 3 letters, that is because we need a **.** for each wildcard letter. Or use the quantifiers described above to set its own rules.


```python
re.findall(r"...at","The bat went splat")
```




    ['e bat', 'splat']



However this still leads the problem to grabbing more beforehand. Really we only want words that end with "at".


```python
# One or more non-whitespace that ends with 'at'
re.findall(r'\S+at',"The bat went splat")
```




    ['bat', 'splat']



### Starts with and Ends With

We can use the **^** to signal starts with, and the **$** to signal ends with:


```python
# Ends with a number
re.findall(r'\d$','This ends with a number 2')
```




    ['2']




```python
# Starts with a number
re.findall(r'^\d','1 is the loneliest number.')
```




    ['1']



Note that this is for the entire string, not individual words!

### Exclusion

To exclude characters, we can use the **^** symbol in conjunction with a set of brackets **[]**. Anything inside the brackets is excluded. For example:


```python
phrase = "there are 3 numbers 34 inside 5 this sentence."
```


```python
re.findall(r'[^\d]',phrase)
```




    ['t',
     'h',
     'e',
     'r',
     'e',
     ' ',
     'a',
     'r',
     'e',
     ' ',
     ' ',
     'n',
     'u',
     'm',
     'b',
     'e',
     'r',
     's',
     ' ',
     ' ',
     'i',
     'n',
     's',
     'i',
     'd',
     'e',
     ' ',
     ' ',
     't',
     'h',
     'i',
     's',
     ' ',
     's',
     'e',
     'n',
     't',
     'e',
     'n',
     'c',
     'e',
     '.']



To get the words back together, use a + sign 


```python
re.findall(r'[^\d]+',phrase)
```




    ['there are ', ' numbers ', ' inside ', ' this sentence.']



We can use this to remove punctuation from a sentence.


```python
test_phrase = 'This is a string! But it has punctuation. How can we remove it?'
```


```python
re.findall('[^!.? ]+',test_phrase)
```




    ['This',
     'is',
     'a',
     'string',
     'But',
     'it',
     'has',
     'punctuation',
     'How',
     'can',
     'we',
     'remove',
     'it']




```python
clean = ' '.join(re.findall('[^!.? ]+',test_phrase))
```


```python
clean
```




    'This is a string But it has punctuation How can we remove it'



## Brackets for Grouping

As we showed above we can use brackets to group together options, for example if we wanted to find hyphenated words:


```python
text = 'Only find the hypen-words in this sentence. But you do not know how long-ish they are'
```


```python
re.findall(r'[\w]+-[\w]+',text)
```




    ['hypen-words', 'long-ish']



## Parenthesis for Multiple Options

If we have multiple options for matching, we can use parenthesis to list out these options. For Example:


```python
# Find words that start with cat and end with one of these options: 'fish','nap', or 'claw'
text = 'Hello, would you like some catfish?'
texttwo = "Hello, would you like to take a catnap?"
textthree = "Hello, have you seen this caterpillar?"
```


```python
re.search(r'cat(fish|nap|claw)',text)
```




    <_sre.SRE_Match object; span=(27, 34), match='catfish'>




```python
re.search(r'cat(fish|nap|claw)',texttwo)
```




    <_sre.SRE_Match object; span=(32, 38), match='catnap'>




```python
# None returned
re.search(r'cat(fish|nap|claw)',textthree)
```

### Conclusion

Excellent work! For full information on all possible patterns, check out: https://docs.python.org/3/howto/regex.html

____
