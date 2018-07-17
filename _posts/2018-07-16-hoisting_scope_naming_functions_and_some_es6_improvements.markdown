---
layout: post
title:      "Hoisting, Scope, Naming Functions and Some ES6 Improvements"
date:       2018-07-16 19:10:25 -0400
permalink:  hoisting_scope_naming_functions_and_some_es6_improvements
---


Javascript can be your best friend and your worst enemy. Because of its humble beginnings, this programming language that is so near and dear to the heart of web developers can be a little quirky for those who are new to the language, and even those who have used it for years. Today I am going to talk about just a couple of these “quirks” relating to scope and how some of ES6’s features have helped to work around them. 

**Understanding Scope**

First off understanding how important functions are in Javascript is paramount in understanding the idea of scoping, closures, and hoisting. In addition, you must have a basic knowledge of functional programming to understand the significance of the ES6 features I will be touching on i.e. ```let```, ```const``` and arrow functions.

So now, lets briefly talk about scope. In Javascript, certain data can only be accessed within a particular scope. More specifically, Javascript has always utilized functional scoping, where variables cannot be accessed outside of the functions that they were originally defined in. So in the following example outerFunction is the parent function of innerFunction, because innerFunction is defined within outerFunction. 

```
function outerFunction(){
    var x = 1
    
    function innerFunction(){
        var y = 99

        console.log(x) // 1
        console.log(y) // 99
    }

    function otherFunction(){
        console.log(x) // 1
        console.log(y) // error: y is not defined        
    }

    innerFunction()
    otherFunction()

    console.log(y)  // error: y is not defined
}

```


Variables that are defined within outerFunction (but not inside of innerFunction) will be accessible anywhere inside of outerFunction’s scope, including inside of innerFunction and other functions defined within innerFunction. However, if a variable is defined within innerFunction, that data will not be available anywhere else in the program that is outside of innerFunction’s scope i.e. inside of otherFunction. This is called lexical scoping. I like to call it as “trickle-down” scoping, because the data from the parent functions always trickles down to the inner functions, but not vice-versa. 


**VAR, LET & CONST**

Now that we got all of that out of the way, lets talk about the different variable declarations now available in ES6 and their differences. The classic Javascript keyword to declare a variable within the current scope is ```var```. Despite being the go-to for developers over the years, ```var``` has its disadvantages, especially to those coming from other programming languages. Firstly, variables defined using ```var``` can be redefined. If you say ```var number = 1``` and then on the next line say ```number = 99``` then the current value of ```number``` is 99. Another thing to know about the ```var``` keyword is that it gives its variable function scope, instead of block scope. So if you create an if statement or some type of loop within your function define variable with ```var``` inside of its curly brackets, that variable will be accessible throughout that function’s entire scope. Finally, there is hoisting, which is kind of tricky. When defining a new variable with ```var```, the function is declared (but not defined) as soon as the parent function is called. Think of it as the variable’s declaration being lifted or *hoisted* to the top of the function’s code. In the example below, the code in ```actuallyHappening``` is what, is well … actually happening in the ```yourCode``` function, behind the scenes.

```
function yourCode(){

     console.log(“Blah blah”)
     var x = 1

}

function actuallyHappening(){
     var x

     console.log(“Blah blah”)
     x = 1
}

```

Now that we have an understanding of the quirks that come along with using ```var```, lets see how ```let``` and ```var``` have helped changed these aspects of variable declaration. 

LET
* Uses block scope, meaning if a variable is declared inside of a for loop or if statement, it cannot be accessed from outside of its curly brackets.
* Is not hoisted to the top of a function. The variable is declared on the same line that it is declared. If you try to access the variable before it is defined/declared, there will be an error rather than a value of ```undefined```.
* A variable can only be declared once using the ```let``` keyword, although it can be redefined once it has been declared, without using ```let``` (similar to ```var```).

CONST
* The big plus of using the ```const``` keyword to declare and define variables is that it has all of the same features as ```let``` EXCEPT for one big difference, you CANNOT redeclare **or** change the value of the variable using reassignment
* In addition to the feature above, you cannot declare a variable with ```const``` without defining it at the same time.

**Functions**

While we are talking about hoisting, Functions are also affected by hoisting, depending on how the function is defined. These are three common ways to define a function:

* Anonymous functions - can be defined and returned from within other functions, passed into functions as an argument, or created and then called immediately. They are not stored to their own variable and are defined simply by typing ```function(){  …  }```
* Function declaration - created with a name which is stored and hoisted, in its entirety (not just the name like a ```var```), to the top of the scope. These functions can be called before they are defined because of hoisting. Typed ```function nameHere(){ … }```, this seems to be the most common way to create a function because of how hoisting is used here, unlike…
* Function expressions - similar to function declarations, these functions are stored in a variable name. However, the big difference here is that these functions are NOT hoisted to the top of the scope because they are part of a var/let/const definition and can only be used after the function has been defined. For example ```const thisFunction = function(){ … }```&#x2028;

**Arrow Functions**

As with variable declarations, ES6 sought to improve upon the previous way that functions were both defined and implemented. This led to the creation of “arrow functions”. In terms of readability, the arrow function is a definite improvement over the traditional function declaration, but don’t make the mistake I made and think that arrow functions are simply easier on the eyes. They have two very useful characteristics. First, when typed without curly brackets ex:
``` () => 5 * 5 ``` they use implicit return, meaning the result of the function’s code will be returned automatically. In addition to this optional implicit return (remember, only without curly brackets), these arrow functions eliminate the need for ```.bind()``` when using the “this” keyword. Normally in a callback function, we must bind with an object in order to properly use the ```this``` keyword because when using ```this``` in a traditional function, ```this``` will just point to the function that is being called in. However, arrow functions will, more-or-less, inherit thier ```this``` from the scope that the parent function is called in.

Hopefully this post is able to help clear up just some tricky aspects of understanding Javascript. Sometimes it is easy to overlook certain elements of a language and be a little too hasty on continuing down the path or curriculum you may be on, but it always pays off to take some time to really look into some of these concepts, allowing for a deeper understanding of the the language.
