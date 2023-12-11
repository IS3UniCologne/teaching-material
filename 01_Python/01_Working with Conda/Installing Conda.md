# Simplified Guide to Installing Conda

To work on Python projects, you need to add extra sets of code called **packages**. These are like toolkits made by other Python developers. By adding these toolkits, you can use their functions in your own code.

But, here's the catch: when you add these toolkits, they often depend on each other. Sometimes, they don't get along, and you might need to remove one toolkit to add another. Also, if you're working on a project with others, you all need to use the same toolkits.

To make this easier, there's something called a "virtual environment." Think of it as a special workspace just for your project. **Conda** is a tool that helps manage these workspaces. There are two versions: one with buttons (called [anaconda](http://)) and one with commands (called [miniconda](http://)).

## How to Install Conda

You can find step-by-step guides online:
- For Windows: [Tutorial](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html)
- For miniconda: [Tutorial](https://docs.conda.io/projects/miniconda/en/latest/)
- For anaconda on Mac: [Tutorial](https://docs.continuum.io/free/anaconda/install/mac-os/)

We also suggest adding a tool called `libmamba` to speed things up. It helps conda figure out which versions of toolkits work well together.

### Installing `libmamba`

Follow these steps from the command line (like Terminal or PowerShell):
```console
conda update -n base conda
conda install -n base conda-libmamba-solver
conda config --set solver libmamba
```

Here's what these commands do:
1. First, update conda itself. Don't put anything important in the "base" workspace; it's for basic stuff only.
2. Then, add the faster toolkit solver (`libmamba`) and set it as the default.

## Checking if Conda is Installed

After this, you should be able to use the `conda` command in your command line. If you're using buttons (GUI), you might need to start a "conda shell," which is a special command line. If you type `conda --version`, you should see the newest version of conda on your system. That means it's installed and ready to go!