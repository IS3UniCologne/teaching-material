# Reproducible Setup with uv

When working on Python projects, you'll often need to add extra sets of code called **packages** (like toolkits made by other developers). Just like we learned with Conda, adding these toolkits can get messy. They might depend on each other, or you might need a specific version of a toolkit that conflicts with another one.

To make this easier, we use "virtual environments"—special workspaces just for your project. While Conda is a popular tool for this, **`uv`** is an incredibly fast, modern alternative that handles everything from installing Python to managing your packages and workspaces.

This tutorial will show you how to set up `uv`, use it to manage your project's workspace, and make sure your colleagues can easily recreate the exact same workspace on their computers.

## 1. Installing uv

`uv` is known for being extremely fast and simple to install. You don't need a heavy installer.

You can find step-by-step guides for your specific system online:
- [uv Installation Guide](https://docs.astral.sh/uv/getting-started/installation/)

For example, on macOS or Linux, you can typically install it by opening your terminal and running a command provided on their website. On Windows, you can use PowerShell.

After installation, restart your command line or terminal. Type the following command to check if it worked:
```console
uv --version
```
If you see a version number, `uv` is installed and ready to go!

## 2. Using uv - Hands On

Unlike Conda, where you might create an environment and then "activate" it before installing packages, `uv` encourages a project-based approach.

### Creating a Workspace

Let's create a new project called `learning-uv`. Open your command line and create a folder, then move into it:
```console
mkdir learning-uv
cd learning-uv
```

Now, initialize a new `uv` project:
```console
uv init
```
This tells `uv` that this folder is a special workspace. `uv` will create a few files for you, including one called `pyproject.toml`. This file is like a blueprint for your project—it keeps track of your Python version and the toolkits you need.

### Installing Python and Packages

With Conda, you have to manually install Python into your workspace. `uv` is smarter: it can automatically download and manage Python versions for you!

Let's start adding tools to our empty toolbox. First, we will add a popular toolkit for math, `numpy`. Instead of installing it into a global space, we add it to our project:

```console
uv add numpy
```

When you run this, `uv` does a few things automatically:
1. It creates a virtual environment (a special `.venv` folder) just for this project if one doesn't exist.
2. It figures out what Python version you need and uses it.
3. It downloads `numpy` incredibly fast.
4. It updates your `pyproject.toml` blueprint to say "this project needs numpy."
5. It creates a file called `uv.lock`.

If you want a specific version of a tool, you can ask for it, just like in Conda:
```console
uv add pandas==2.0.3
```

### Removing Packages

If you decide you don't need a toolkit anymore, `uv` makes it easy to remove it and update your project blueprint:
```console
uv remove pandas
```
`uv` will take pandas out of your workspace and remove it from your `pyproject.toml`.

### Running Code

With Conda, you usually run `conda activate my-env` and then run your code. With `uv`, you don't even need to activate the environment! You can just tell `uv` to run your script, and it knows to use the special workspace it created:

```console
uv run python -c "import numpy; print(numpy.__version__)"
```
This runs a quick piece of Python code to print the `numpy` version, using the exact setup in your workspace.

## 3. Collaborating with Environments

For collaborating, managing your environment is crucial. Suppose you send your `learning-uv` code to a colleague. How do they get the exact same toolkits and versions?

This is where `uv` shines. Remember those two files `uv init` and `uv add` created?
- `pyproject.toml`: Your project blueprint.
- `uv.lock`: A highly detailed list of the *exact* versions of every toolkit (and the toolkits they depend on) that you used.

### Sharing Your Workspace

If you are using Git (version control), you should commit both `pyproject.toml` and `uv.lock` to your repository.

When your colleague downloads your project, all they have to do is navigate to the folder in their command line and run:
```console
uv sync
```

That's it! `uv` will read the `uv.lock` file, automatically download the correct version of Python if they don't have it, and install the exact same versions of all the toolkits you were using. This guarantees their workspace is a perfect clone of yours. No messy export commands or "works on my machine" problems!

If you add a new package later with `uv add matplotlib`, your `uv.lock` updates. You send the updated `uv.lock` to your colleague, they run `uv sync` again, and their workspace is instantly updated to match.

## References
- [uv Official Documentation](https://docs.astral.sh/uv/)
- [Getting Started with uv](https://docs.astral.sh/uv/getting-started/)
