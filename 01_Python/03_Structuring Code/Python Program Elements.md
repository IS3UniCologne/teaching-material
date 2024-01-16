# Python Program Elements

After seeing a lot of code, another very interesting question arises. How do you deal with growing amounts of code, and how can you do it for example in your own group project? To start, we need to know what exists in python to structure code and how this relates to the organization of code.

## Python Structure Elements

You already learned about variables, which can hold arbitrary things. In python, this ranges from values, to instances of objects, to functions, class definitions and all bigger code elements. So here is a short collection of structuring that is inherent in python (not necessarily complete):

- variables
- functions
- classes

Each of these has a use case, so lets cover how you would use them in your code.

### Variables
For any python code you run, you will need variables. However, there is different ways you could use them in your code to structure your program. This is where conventions to formatting come in. Global, unchanging variables are usually definned in all upper case:
```
PI = 3.141
MY_CONSTANT_VARIABLE = 50
```
To make it easier to follow your code, it is nice to also put these constants early in your code, so that they are easy to find if somebody wants to look up their value. Some variables might be quasi constant, or constant for a single run. Then you would not put them in uppercase, but it is still very helpful to use a variable above some block of code, in order for you and others to have an easier time to work with it. Consider the following example:

```
result = complex_function_call(1, 2, 3)
result2 = another_complex_function(result, 1, 5)
print(result2, 5)
```

Can you know whether the argument (1) for both functions has anything to do with each other? No, so extracting the arguments to variables has a lot of value in that regard as well.

```
amount = 1
price = 2
iterations = 3
verbose = 1
print_format = 5

result = complex_function_call(amount, price, iterations)
result2 = another_complex_function(result, verbose, print_format)
print(result2, print_format)
```

See? Now, the code is more readable as you can understand more of it. There are limits to this, which are that simply this might be too much information. For instance, verbose is an argument that is only locally relevant in that code snippet. If you never want to change it, and it is only necessary for one function, you can also just set it for that specific function. Long story short: in most cases, defining and using variables helps to understand unseen code and structures the code to help you work with it.

### Functions

While variables are helpful, they don't really change the way your code looks. Functions provide a different level of structuring that you can leverage to shorten everything you have to write dramatically. Furthermore, it avoids repetition and reduces local complexity.

- repeatable code
- code used in multiple contexts
- bundle variables for local execution context
- only modify some variables -> arguments
- readability (don't need to understand how it does it)
- levels of abstraction -> abstract flow, functions contain concrete logic

### Classes
- bundle both functions and variables
- behavior -> functions that work on the object
- abstraction of creation of object, dependencies between variables
- captures state, so repeated invokation of same function can yield different results


