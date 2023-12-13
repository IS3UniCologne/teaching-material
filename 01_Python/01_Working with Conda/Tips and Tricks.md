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

The first command creates a new environment with two new features, the part `--prefix ./envs` and the part `python=3.9 jupyter notebook numpy=1.26`. We start off explaining the second part; it is simply telling conda to add the packages to the newly created environment. The first part is a little more tricky. It changes the location the environment is saved at. Before, we always installed the environment at the default location. The prefix now tells conda to put the environment in a folder called envs at the location the command line is currently active at. 

That might be difficult, so lets look at some properties of the command line first. When you have your terminal, power shell of conda shell open, there is always some bits of information visible. 

```
user@pc ~/Repo/teaching-material %
```

In this example, the user "user" is logged into the computer "pc" and the terminal used is currently in the directory Repo/teaching-material. The ~ symbol tells you that this is under the home directory of the user.

When we now execute the conda command above, it does two things:
- create a folder called envs in the location ~/Repo/teaching-material/envs
- copy all files necessary to this folder

Having understood the first part, we quickly go over the two other commands. The second one is only visual. Without it, the command line would always show the full path, which can be quite long. The second activates the newly created environment. Note that this only works if your command line is at the same location as the folder envs.

## Porting an environment

Remember our scenario: we want to make our environment available to another user. Conda contains commands to export all information necessary. Here, we will use it with the `--from-history` option, which only exports the package names we used explicitly.

```
conda env export --from-history
```
