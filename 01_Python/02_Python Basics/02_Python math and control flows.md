# Python math and control flows

In the [previous part](/01_Python/02_Python%20Basics/01_Introduction%20to%20Python), we explored what python is exactly, how you can interact with it and looked at the basic elements of variables and functions. Now, we are looking into working with the variables. One simple thing that helps explore is doing basic calculations in python code. So lets start. To follow along, open your favourite command line with the learning-python conda environment open and open a python session (by typing python and pressing enter).

## Calculations with Integers

Just execute the code here, and then we will do stuff with it:

```
>>> int_1 = 2
>>> int_2 = 5
>>> int_3 = 357
```

Now lets use these to perform calculations. The calculations in python are mapped to the symbols you would use to write the calculations down. The basic ones you will all know:

```
>>> int_1 + int_2
7
>>> int_3 - int_2
352
>>> int_1 * int_2
10
>>> int_2 / int_1
2.5
```

But wait - why is the result of the last calculation 2.5? Those of you who did not do any programming before will now ask why this is a surprise, it is because *the type of the result is different than the variables*. Let me show you:

```
>>> type(int_1)
<class 'int'>
>>> type(int_2)
<class 'int'>
>>> type(int_2 / int_1)
<class 'float'>
```


This is something python likes to do, it changes the type associated with the type when it thinks it is helpful for you. In the case of division, python assumes that it is better for you to receive a float as a result so it returns one. You can force python to divide full numbers using the double slash, then, as programmers expect, it results in an integer, cutting off the digits behind the floating point:

```
>>> >>> int_2 // int_1
2
```

Other calculations are:

```
>>> int_2 ** 2
25
>>> 2 ** int_2
32
>>> int_2 % 4
1
>>> int_1 % 4
2
```

The first is the power function, raising the first by the second. So, the top one is the same as `int_2 * int_2` and the second example is the same as `2 * 2 * ... * 2` int_2 times, so exactly 5 times (the value of int_2). The second operator you see there is the modulo operator, which calculates the reminder of the division by the number. These are all special operators that exist for calculation. In the next section, we will explore what happens when we include floats into the calculations.

## Calculations with Floats

to be continued.