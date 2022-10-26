``` python
from __future__ import annotations
```
```__future__``` A built-in module in Python that is used to inherit new features that will be available in the new Python versions. annotations is something which helps ous to have forward notation for ```class``` because sometime we want our class to be used inside itself but at the moment, it is being defined . It cannot be used but, if we have to use it we just have to write these line which will tell python at that moment I even don't know about these class but we will check it out once we have defined these class and once the class get defined it no longer stays undefined.
***********************************
```python
from copy import deepcopy
```
In python when ever a variable is created like a list of number for example ```number = [ 1, 2, 3, 4, 5]``` and on the next line we create a new variable name ```number1 = number``` and tryed to change the value of the ```number1``` it will change value asigned to ```number1``` and ```number``` also.
example code 
```python
number = [1, 2, 3, 4, 5]
number1 = number
number1[0] = 9
print(number)
print(id(number))
print(number1)
print(id(number1))
```

output 

```
[9, 2, 3, 4, 5]
1657313579528
[9, 2, 3, 4, 5]
1657313579528
```
As we can see, these objects are not copies of each other. They are two variables pointing at the same address (references). Hence, it is not a copy. If we want them to act like a separate variable, but being the copy (pointing to one memory address or referenec) of each other won't affect both of them. We can use the copy library. The below code will demonstrate it correctly.
```python
import copy
number = [1, 2, 3, 4, 5]
number1 = copy.copy(number) # it creates a copy of whole list [1, 2, 3, 4, 5] which is point at new reference or memory address but the elements of these list still points to same address or refreances
number1[0] = 9
print(number)
print(number[1])
print(id(number))
print(id(number[1]))
print(number1)
print(number1[1])
print(id(number1))
print(id(number1[1]))
print(number)
```
output
```
[1, 2, 3, 4, 5]
2
1800675767752
140735370460256
[9, 2, 3, 4, 5]
2
1800677745928
140735370460256
[1, 2, 3, 4, 5]
```
here it creates a copy of whole list or list object but not the copy of elements inside in it which might bother ous if we have nested list.
Even if we tryed to edit any variable it will no longer will point to same memory address or reference example.
```python
import copy
number = [1, 2, 3, 4, 5]
number1 = copy.copy(number) # it creates a copy of whole list [1, 2, 3, 4, 5] which is point at new reference or memory address but the elements of these list still points to same address or refreances
number1[0] = 9
print(number)
print(number[0])
print(id(number))
print(id(number[0]))
print(number1)
print(number1[0])
print(id(number1))
print(id(number1[0]))
```
output
```
[1, 2, 3, 4, 5]
1
2384744068552
140735678086208
[9, 2, 3, 4, 5]
9
2384746046728
140735678086464
```
In case of nested list we have to use deepcopy which make a copy of object and the also the elements inside the object
example 
```python
copy.deepcopy(variable)
```
********************************************************
```python
from typing import TYPE_CHECKING
```
Python is a dynamically typed language, which means it is not necessary to define what type of data we want to store. We want the variable to be stored in memory, which sometimes leads to major problems, and even though Python during compiling does not raise any errors because it sees Python as a dynamically typed language, not like static languages like C or Java. But this time we want Python to raise an error when we do so, which is done by these libraries.

-> in def block in python is
In the following code:
```python
    def f(x) -> int:
        return int(x)
```
the `-> int` just tells that `f()` returns an integer (but it doesn't force the function to return an integer). It is called a *return annotation*, and can be accessed as `f.__annotations__['return']`.

Python also supports parameter annotations:
```python
    def f(x: float) -> int:
        return int(x)
```
`: float` tells people who read the program (and some third-party libraries/programs, e. g. pylint) that `x` should be a `float`. It is accessed as `f.__annotations__['x']`, and doesn't have any meaning by itself.
