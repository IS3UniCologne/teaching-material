# Introduction to Python

In our courses we choose to teach python. Why did we choose this language? The main reason is that python is the most used programming language for machine learning. This comes from the ecosystem of packages. You already know how to install packages (if not see [conda](/01_Python/01_Working%20with%20Conda/Installing%20Conda.md)), but how can we use them? And why are there so many packages written in python?

The main reason is: python is very simple to write and read, with a low entry hurdle to master and enough features that this does not hamper more advanced coding (too much). What do we mean by simple? If you know any programming language, then will probably be used to writing ; at the end of every line, to type {} brackets everywhere and overall be pretty confused about why exactly you need to do this. Most of these things are not needed in python, which also means every symbol you see actually has a direct meaning.

But enough of intro text, you are probably here to see code and explore what python can do. 

## Running python
In our workshops we usually start with Jupyter Notebooks (for a tutorial starting there, see [missing]). But here, we actually start at the very bottom: the python interpreter. For this, open your conda terminal (or whatever you use for that) and create a new environment of the name `learning-python` and install python=3.10 in there. Then activate this new environment. Now, you can execute `python` and something new will open:

```
> python
Python 3.10.13 | packaged by conda-forge | (main, Oct 26 2023, 18:09:17) [Clang 16.0.6 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

That command you just used is what is called the python interpreter. It is a program that understands python, so you can now simply execute python commands. Let's try it out:

```
>>> print('Hello World')
Hello World
```

After this obligatory command (and you will see how useful printing is in every context), we can start with actual programming. What is the first ingredient that you will ALWAYS see and use? It is using variables. So lets define a variable in python:

```
>>> a = "Hello World"
>>> a
'Hello World'
>>> print(a)
Hello World
```

And as easy as that, you can define variables. However, we already showed you a huge mistake: naming your variables without any logic. If, in two month, you would see the variable `a` and would need to describe it for your team project, would you know what it means? So from now on, we will use longer variable names, which tell you a little more about what is going on.

```
>>> an_integer = 5
>>> type(an_integer)
<class 'int'>
>>> an_integer
5
```

What are we doing in the above snippet? We are setting a variable called `an_integer`, then we are writing something `type()` and last we are looking at the value of our variable `an_integer`. What exactly does the `type()` thing do? This is our first *function* we are using. A function is a piece of code which takes arguments, these are the things you write in the () brackets, and produces an output. In this case, the function is looking at the variable we put in there and returns the type (as the name suggests).

## 