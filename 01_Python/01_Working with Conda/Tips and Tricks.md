# Tips and Tricks

For collaborating, managing conda environments is crucial. Suppose you are writing code in a Jupyter Notebook and sending that notebook to your colleague. Now, she has to look which packages you used, then she needs to create an environment containing all these packages and only then can she execute your notebook.

There is something you can do to help her, which is what we are going to explore now.

## Quickstarting an environment

First, let us create a new environment. We take the opportunity and show you some more advanced features that you can use to make working with conda easier. Just execute the following command, and then we will explore what exactly it does and its implications.

```
conda create --prefix ./envs python=3.9 jupyter notebook numpy=1.26
conda config --set env_prompt '({name}) '
conda activate ./envs
```

The first command creates a new environment at the 