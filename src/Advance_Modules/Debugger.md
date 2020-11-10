---
layout: default
title: Debugger
parent: Advance Modules
nav_order: 5
---

# Python Debugger

You've probably used a variety of print statements to try to find errors in your code. A better way of doing this is by using Python's built-in debugger module (pdb). The pdb module implements an interactive debugging environment for Python programs. It includes features to let you pause your program, look at the values of variables, and watch program execution step-by-step, so you can understand what your program actually does and find bugs in the logic.

This is a bit difficult to show since it requires creating an error on purpose, but hopefully this simple example illustrates the power of the pdb module. <br>*Note: Keep in mind it would be pretty unusual to use pdb in an Jupyter Notebook setting.*

___
Here we will create an error on purpose, trying to add a list to an integer


```python
x = [1,3,4]
y = 2
z = 3

result = y + z
print(result)
result2 = y+x
print(result2)
```

    5
    


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-1-905e8cfe6928> in <module>()
          5 result = y + z
          6 print(result)
    ----> 7 result2 = y+x
          8 print(result2)
    

    TypeError: unsupported operand type(s) for +: 'int' and 'list'


Hmmm, looks like we get an error! Let's implement a set_trace() using the pdb module. This will allow us to basically pause the code at the point of the trace and check if anything is wrong.


```python
import pdb

x = [1,3,4]
y = 2
z = 3

result = y + z
print(result)

# Set a trace using Python Debugger
pdb.set_trace()

result2 = y+x
print(result2)
```

    5
    --Return--
    > <ipython-input-2-1084246755fa>(11)<module>()->None
    -> pdb.set_trace()
    (Pdb) x
    [1, 3, 4]
    (Pdb) y
    2
    (Pdb) result2
    *** NameError: name 'result2' is not defined
    (Pdb) q
    


    ---------------------------------------------------------------------------

    BdbQuit                                   Traceback (most recent call last)

    <ipython-input-2-1084246755fa> in <module>()
          9 
         10 # Set a trace using Python Debugger
    ---> 11 pdb.set_trace()
         12 
         13 result2 = y+x
    

    C:\Users\Marcial\Anaconda3\lib\bdb.py in trace_dispatch(self, frame, event, arg)
         53             return self.dispatch_call(frame, arg)
         54         if event == 'return':
    ---> 55             return self.dispatch_return(frame, arg)
         56         if event == 'exception':
         57             return self.dispatch_exception(frame, arg)
    

    C:\Users\Marcial\Anaconda3\lib\bdb.py in dispatch_return(self, frame, arg)
         97             finally:
         98                 self.frame_returning = None
    ---> 99             if self.quitting: raise BdbQuit
        100             # The user issued a 'next' or 'until' command.
        101             if self.stopframe is frame and self.stoplineno != -1:
    

    BdbQuit: 


Great! Now we could check what the various variables were and check for errors. You can use 'q' to quit the debugger. For more information on general debugging techniques and more methods, check out the official documentation:
https://docs.python.org/3/library/pdb.html
