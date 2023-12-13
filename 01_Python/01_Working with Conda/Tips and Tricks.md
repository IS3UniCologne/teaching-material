# Tips and Tricks

For collaborating, managing conda environments is crucial. Suppose you are writing code in a Jupyter Notebook and sending that notebook to your colleague. Now, she has to look which packages you used, then she needs to create an environment containing all these packages and only then can she execute your notebook.

There is something you can do to help her, which is what we are going to explore now.

## Quickstarting an environment

First, let us create a new environment. We take the opportunity and show you some more advanced features that you can use to make working with conda easier. Just execute the following command, and then we will explore what exactly it does and its implications.

```
conda create -n quickstart python=3.9 jupyter notebook numpy=1.26
conda activate quickstart
```

The first command creates a new environment with a new part `python=3.9 jupyter notebook numpy=1.26`. It is simply telling conda to add the packages to the newly created environment. Then we activate it.

## Porting an environment

Remember our scenario: we want to make our environment available to another user. Conda contains commands to export all information necessary. Here, we will use it with the `--from-history` option, which only exports the package names we used explicitly.

```
conda env export --from-history

name: quickstart
channels:
  - conda-forge
  - defaults
dependencies:
  - jupyter
  - notebook
  - numpy=1.26
  - python=3.9
prefix: <wherever>/miniconda/base/envs/quickstart
```
You can see that it documents all steps necessary to reproduce the environment, listing the name, the channels used and the dependencies. The last line is unnecessary and should not be sent to your colleague.

To create a new file containing this information, simply modify the command above like this:
```
conda env export --from-history > environment.yml
```
Now you can delete the prefix line from the file and voila you have a file that you can use to recreate the environment.

Lets try it out ourselves. First, deactivate the environment and delete it.
```
conda deactivate
conda env remove -n quickstart
```
Now, we can use the file to recreate the environment like this:
```
conda env create -f environment.yml
```
Afterwards, you can activate the environment quickstart again and it has the packages installed that you specified.

### New way of managing packages

If you are using git in your project, the file we just created is perfectly suitable for version control. Just commit the initial version of it, and all other collaborators can use it to create an environment as specified above.

But that also changes the way we should update dependencies, like adding or removing them. For a start, we add another dependency to pandas 2.0. For that, we add the line 
```
- pandas=2.0
```
at the end of the file. Now, we can update our environment with the following command:
```
conda env update -f environment.yml
```
If we discovery later in the project that we actually don't need either pandas or jupyter, we can remove both and reexecute the command, with the option --prune added at the end. This way, conda checks whether there are any unnecessary packages installed and removes these:
```
conda env update -f environment.yml --prune
```
For this to work conda needs to be version 23.9 or younger.

