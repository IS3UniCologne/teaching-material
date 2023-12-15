# Simplified Guide to Installing Conda

To work on Python projects, you need to add extra sets of code called **packages**. These are like toolkits made by other Python developers. By adding these toolkits, you can use their functions in your own code.

But, here's the catch: when you add these toolkits, they often depend on each other. Sometimes, they don't get along, and you might need to remove one toolkit to add another. Also, if you're working on a project with others, you all need to use the same toolkits.

To make this easier, there's something called a "virtual environment." Think of it as a special workspace just for your project. **Conda** is a tool that helps manage these workspaces. There are two versions: one with buttons (called [anaconda](http://)) and one with commands (called [miniconda](http://)).

## How to Install Conda

You can find step-by-step guides online:
- For Windows: [Tutorial](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html)
- For miniconda: [Tutorial](https://docs.conda.io/projects/miniconda/en/latest/)
- For anaconda on Mac: [Tutorial](https://docs.continuum.io/free/anaconda/install/mac-os/)

After this, you should be able to use the `conda` command in your command line. If you're using buttons (GUI), you might need to start a "conda shell," which is a special command line. If you type `conda --version`, you should see the newest version of conda on your system. That means it's installed and ready to go!

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

## Adding More Sources

Another important thing to set up in your conda is where it looks for extra tools. Usually, there's just one place, but you might want to add more. Check what you currently have by using this command: `conda config --show channels`. 

Now, why does it matter? Well, lots of Python tools are neatly organized in a special place called `conda-forge`. Adding this popular spot to your default sources lets you grab even more tools.

Use the command `conda config --add channels conda-forge` to make it happen. After this, your sources should look like this:

```
channels:
  - conda-forge
  - defaults
```

Now you're all set to find and install a wider variety of tools for your projects!

Next [Using Conda - Hands on](/01_Python/01_Working%20with%20Conda/02_Using%20Conda%20-%20Hands%20on.md)