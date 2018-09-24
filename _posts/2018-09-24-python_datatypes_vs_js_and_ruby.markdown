---
layout: post
title:      "Python Datatypes vs. JS & Ruby"
date:       2018-09-24 22:14:00 +0000
permalink:  python_datatypes_vs_js_and_ruby
---


Learning a second or third programming language is easy ... kind of. As I explained in my last post, you have a major advantage this time around than when you learned your first or even your second coding language. But just because it's easier doesn't mean it's a no-brainer. There is a reason that these languages are *different* in the first place. Despite the many similiarites that span across all/most languages, each has its specific features/quirks that make it unique and more suitable for certain jobs.

In this post, I'll be taking a brief look at the basic Python data types, some of their unique features and how they compare to my first two languages: Javascript and Ruby. 

#### Strings

This one should be no suprise. Strings are an essential part of all major programming languages. They are simply a collection of characters placed in between quotations (either double quotes " or single quotes ').

``` 
a = "This is a string." 

print(type(a)) # output: <class 'str'>
```

An imporant feature of a string is its ability to be sliced similiar to a list (we'll talk about those later). When you insert an index number in between brackets *after* the string/string's variable, the corresponding character will appear. For example in this string: ``` example = "All strings start at 0" ```, if after this expression is run, you input ``` example[4] ```, the console will return the fifth character in the string; in this case "s". Additionally, these strings are immutable, so if you tried to say ``` example[4] = "q" ```, it would return an error. You cannot alter a string this way.

#### Numbers 

In Python there are multiple ways to store a number. The most common are ```int``` and ```float```. We won't get into ```complex``` numbers right now. Both integers and floats function relatively the same. The biggest difference being that floats have decimal points and integers don't. If you're coming straight to Python from Javascript, this will be a new concept because in JS numbers are just ... numbers. 

```
num1 = 62

num2 = 3.14

print(type(num1)) # output: <class 'int'>

print(type(num2)) # output: <class 'float'>
```

#### Booleans

This one is pretty straightforward. Booleans are a statement of either "true" or "false". The main thing to remember in Python is that these are always capitalized. ```True``` will result in a truthy value, while ```true``` will result in an error, unlike in Ruby and Javascript. The same goes for ```False``` vs. ```false```.

#### Dictionaries

Dictionaries in Python are very similiar to objects in Javascript and hashes in Ruby, especially in terms of syntax. The major difference between a Python dictionary and a Javascript object is that Python evaluates the keys, while JS doesn't. 

```
# Python dictionary

me = { "name": "Sean", "height": 70, "developer": True }
```

```
// Javascript object

const me  = {name: "Sean", height: 70, developer: true }
```

As you can see in the examples, keys in Python must be placed in quotes if they are a string. This also means that there is no "dot-notation" in Python (I know ... I shed a single tear). Also, keys and values can be of any type. So if you created this dictionary: ``` dict = { True: "true", False: "false }``` then ```dict[True]``` would evaluate to ```"true"```.


#### Lists, Tuples and Sets

For me this is the trickiest one. Basically, Python has three different types of *array-like* data structures. The most similiar to a JS array is the ```list```. For the sake of brevity, a ```list``` syntactically is almost identical to a JS array. The new concepts here are the tuples and sets.

Tuples are just like lists *except* for one major feature. Tuples are immutable, meaning the actual data inside of it cannot be altered. To clarify, it cannot be directly lengthened or shortened, or cannot have an index removed or changed. Syntactically the difference is that tuples use parentheses instead of brackets ```("this", "is", "a", "tuple")```.

Sets are yet another type of data structure in Python. Sets stray a little bit further away from the arrays of JS and Ruby. A set is a list of values that are written in between curly brackets, but unlike a dictionary, there are no keys. 

```{ 0, 5, 2, 7, "set" }``` is an example of a set.

The two main things to know about a set is: 1) that the values appear in no specific order and have the capability of being in a different order every time the set is called: and 2) there are no duplicates within a set. Below is a demonstration of both of these behaviors.

```
set1 = { "example", 10, True, 7.2 }

print(set1) # output: { True, 7.2, "example", 10 }

set1.add("john doe")

print(set1) # output: { 7.2, "example", "john doe", 10, True }

set1.add(True)
set1.add("example")

print(set1) # output: { 7.2, "example", "john doe", 10, True }

```

So there is a quick summary of the basic Python data types and structures. There is way more depth to all of these concepts but I am hoping to dive in a little deeper as my Python knowledge grows.



