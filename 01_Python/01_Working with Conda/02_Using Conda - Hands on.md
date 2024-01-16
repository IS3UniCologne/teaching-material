# Using Conda - Hands On

If you haven't installed conda yet, check out [how to install Conda](/01_Python/01_Working%20with%20Conda/01_Installing%20Conda.md). Once it's on your system, open a command line with conda active and type the following command:
```console
conda --version
```
You should see the version number of conda as the response.

## Creating a Workspace

Now that conda is installed, you can use it to make special workspaces for your Python projects. Let's create a new workspace called 'learning-conda.' The command to create these workspaces is `conda create -n <workspace-name>`. For 'learning-conda,' use this command:
```console
conda create -n learning-conda
```
After running this command, you'll see a prompt like this:
```
Retrieving notices: ...working... done
Channels:
 - conda-forge
 - defaults
Platform: osx-arm64
Collecting package metadata (repodata.json): done
Solving environment: done


## Package Plan ##

  environment location: <path-to-your-conda>/miniconda/base/envs/learning-conda



Proceed ([y]/n)?
```
Just press enter (or type 'y' and then enter) to make it happen. Conda shows you what it's about to do and asks if you're okay with it. After pressing enter, you'll see this output:
```
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate learning-conda
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

Now, activate the new workspace using the command `conda activate learning-conda`. Your command line should change to something like this:
```
(learning-conda) <user>@<your-computer> ~ %
```
Now you have the `(learning-conda)` prefix, showing that you're in your special workspace. Keep this active for all following parts.


## Installing Packages

Now that you have a new workspace, it's time to bring in some tools. Right now, your workspace is like an empty toolbox. Check it by typing `conda list` in the command line. If it's empty, you'll see something like this:

```
# packages in environment at <wherever>/miniconda/base/envs/learning-conda:
#
# Name                    Version                   Build  Channel
```

Let's start by adding Python to your toolbox. Type `conda install python` and hit enter. It shows you what tools it needs to add to install Python. You can press enter or 'y' and then enter to continue.

```
Channels:
 - conda-forge
 - defaults
Platform: osx-arm64
Collecting package metadata (repodata.json): done
Solving environment: done


## Package Plan ##

  environment location: <wherever>/miniconda/base/envs/learning-conda

  added / updated specs:
    - python


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    pip-23.3.1                 |     pyhd8ed1ab_0         1.3 MB  conda-forge
    python-3.12.0              |h47c9636_0_cpython        12.7 MB  conda-forge
    wheel-0.42.0               |     pyhd8ed1ab_0          56 KB  conda-forge
    ------------------------------------------------------------
                                           Total:        14.1 MB

The following NEW packages will be INSTALLED:

  bzip2              conda-forge/osx-arm64::bzip2-1.0.8-h93a5062_5 
  ca-certificates    conda-forge/osx-arm64::ca-certificates-2023.11.17-hf0a4a13_0 
  libexpat           conda-forge/osx-arm64::libexpat-2.5.0-hb7217d7_1 
  libffi             conda-forge/osx-arm64::libffi-3.4.2-h3422bc3_5 
  libsqlite          conda-forge/osx-arm64::libsqlite-3.44.2-h091b4b1_0 
  libzlib            conda-forge/osx-arm64::libzlib-1.2.13-h53f4e23_5 
  ncurses            conda-forge/osx-arm64::ncurses-6.4-h463b476_2 
  openssl            conda-forge/osx-arm64::openssl-3.2.0-h0d3ecfb_1 
  pip                conda-forge/noarch::pip-23.3.1-pyhd8ed1ab_0 
  python             conda-forge/osx-arm64::python-3.12.0-h47c9636_0_cpython 
  readline           conda-forge/osx-arm64::readline-8.2-h92ec313_1 
  setuptools         conda-forge/noarch::setuptools-68.2.2-pyhd8ed1ab_0 
  tk                 conda-forge/osx-arm64::tk-8.6.13-h5083fa2_1 
  tzdata             conda-forge/noarch::tzdata-2023c-h71feb2d_0 
  wheel              conda-forge/noarch::wheel-0.42.0-pyhd8ed1ab_0 
  xz                 conda-forge/osx-arm64::xz-5.2.6-h57fd34a_0 


Proceed ([y]/n)? 
```

The part labeled **Package Plan** tells you where your workspace is and what it's about to add. In this case, it's adding Python and some other packages it needs. Conda chooses the latest version of Python (3.12 in this case) because we didn't specify a version.

If you press enter, it starts downloading and installing the packages:

```
Downloading and Extracting Packages
                                                                                
Preparing transaction: done                                                     
Verifying transaction: done                                                     
Executing transaction: done
```

And just like that, you've added your first package to your workspace!


### Installing a specific version of a package

Usually, you want a particular version of a tool, not just any. Let's install a specific version of numpy, like 1.26.2. The command is pretty much the same:

```console
conda install numpy=1.26.2
...
## Package Plan ##

  environment location: <wherever>/miniconda/base/envs/learning-conda

  added / updated specs:
    - numpy=1.26.2
...
```

You can see that now we specify the version number for the package. Press enter to install it.

Now, there could be a situation where the version you want doesn't play well with the other tools you have. Let's try installing pandas version 2.0.3:

```console
conda install pandas=2.0.3

Could not solve for environment specs
The following packages are incompatible
├─ pandas 2.0.3**  is installable with the potential options
│  ├─ pandas 2.0.3 would require
│  │  └─ python >=3.10,<3.11.0a0 , which can be installed;
│  ├─ pandas 2.0.3 would require
│  │  └─ python >=3.11,<3.12.0a0 , which can be installed;
│  ├─ pandas 2.0.3 would require
│  │  └─ python >=3.8,<3.9.0a0 , which can be installed;
│  └─ pandas 2.0.3 would require
│     └─ python >=3.9,<3.10.0a0 , which can be installed;
└─ python 3.12**  is not installable because there are no viable options
   ├─ python 3.12.0 would require
   │  └─ python_abi 3.12.* *_cp312, which conflicts with any installable versions previously reported;
   ├─ python 3.12.0rc3 would require
   │  └─ _python_rc, which does not exist (perhaps a missing channel);
   └─ python 3.12.0 conflicts with any installable versions previously reported
```

This tells us that pandas 2.0.3 is not compatible with Python 3.12. The solution? Install pandas 2.0.3 with a compatible Python version, like 3.11. Where do we see that 3.11 is a compatible version? It is in the tree like structure below pandas 2.0.3, with all other possible choices for python version being also listed.

```console
conda install python=3.11 pandas=2.0.3
...
## Package Plan ##
...
  added / updated specs:
    - pandas=2.0.3
    - python=3.11
...
The following packages will be DOWNGRADED:

  numpy                              1.26.2-py312h5d55045_0 --> 1.26.2-py311h6d074dd_0 
  python                          3.12.0-h47c9636_0_cpython --> 3.11.6-h47c9636_0_cpython 
  python_abi                                   3.12-4_cp312 --> 3.11-4_cp311 
...
```

Here, conda suggests downgrading some packages to make everything compatible. It keeps track of dependencies, saving you from the headache of figuring it out yourself.

And that's it! Now you know how to install packages using conda.

## Removing packages

Exactly as we can add packages, we can remove packages from an environment. The command is `conda remove <package>`. So let's remove pandas again:

```
conda remove pandas
...
## Package Plan ##
...
  removed specs:
    - pandas

The following packages will be REMOVED:

  pandas-2.0.3-py311h9e438b8_1
  python-dateutil-2.8.2-pyhd8ed1ab_0
  python-tzdata-2023.3-pyhd8ed1ab_0
  pytz-2023.3.post1-pyhd8ed1ab_0
  six-1.16.0-pyh6c4a22f_0
```

As you can see, it automatically detects all packages that are only installed because pandas is installed and also selects them for removal. After pressing enter, the packages are removed.

## Looking at your workspaces

Now, after a while it might be that you have many local workspaces, or you forgot the name of a workspace. In that case, you can see the list using the command `conda env list`:

```
# conda environments:
#
base                     <wherever>/miniconda/base
learning-conda        *  <wherever>/miniconda/base/envs/learning-conda
```

## Removing workspaces

Finally, you can remove a workspace you don't need any longer:

```
conda env remove --name learning-conda
```

If you try to execute it now, conda throws an error. This is because you still have the environment active. So before deleting the environment, you have to deactivate it. This can be simply done by executing `conda deactivate` first.

That was it for this tutorial. For collaborating with conda see [Tips and Tricks](/01_Python/01_Working%20with%20Conda/03_Collaborating%20with%20Environments.md).

## References
https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html