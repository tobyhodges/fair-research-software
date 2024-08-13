---
title: Reproducible development environment
teaching: 60
exercises: 30
---

:::::::::::::::::::::::::::::::::::::: questions

- What are virtual environments in software development and why you should use them?
- How can we manage Python virtual environments and external (third-party) libraries?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

After completing this episode, participants should be able to:

- Set up a Python virtual environment for our software project using `venv` and `pip`.

::::::::::::::::::::::::::::::::::::::::::::::::

So far we have created a local Git repository to track changes in our software project and pushed it to GitHub 
to enable others to see and contribute to it.

We now want to start developing the code further. 
If we have a look at our script, we may notice a few `import` lines like the following:

```python
import json
```

```python
import csv
```

```python
import datetime as dt
```

```python
import matplotlib.pyplot as plt
```
This means that our code requires several **external libraries**
(also called third-party packages or dependencies) -
`json`, `csv`, `datetime` and `matplotlib`.
Python applications often use external libraries that do not come as part of the standard Python distribution.
This means that you will have to use a **package manager** tool to install them on your system.
Applications will also sometimes need a
specific version of an external library
(e.g. because they were written to work with feature, class,
or function that may have been updated in more recent versions),
or a specific version of Python interpreter.
This means that each Python application you work with may require a different setup
and a set of dependencies so it is useful to be able to keep these configurations
separate to avoid confusion between projects.
The solution for this problem is to create a self-contained
**virtual environment** per project,
which contains a particular version of Python installation
plus a number of additional external libraries.

## Virtual environments
So what exactly are virtual environments, and why use them?

A Python virtual environment helps us create an **isolated working copy** of a software project
that uses a specific version of Python interpreter
together with specific versions of a number of external libraries
installed into that virtual environment.
Python virtual environments are implemented as
directories with a particular structure within software projects,
containing links to specified dependencies
allowing isolation from other software projects on your machine that may require
different versions of Python or external libraries.

It is recommended to create a separate virtual environment for each project.
Then you do not have to worry about changes to the environment of the current project you are working on 
affecting other projects - you can use different Python versions and different versions of the same third party
dependency by different projects on your machine independently from one another.

Another big motivator for using virtual environments is that they make sharing your code with others much easier - 
as we will see shortly you can record your virtual environment in a special file and share it with your collaborators
who can then recreate the same development environment on their machines.

You do not have to worry too much about specific versions of external libraries
that your project depends on most of the time.
Virtual environments also enable you to always use
the latest available version without specifying it explicitly.
They also enable you to use a specific older version of a package for your project, should you need to.

## Managing Python virtual environments

There are several command line tools used for managing Python virtual environments - we will use `venv`, 
available by default from the standard `Python` distribution since `Python 3.3`.

Part of managing your (virtual) working environment involves
installing, updating and removing external packages on your system.
The Python package manager tool `pip` is most commonly used for this -
it interacts and obtains the packages from the central repository called
[Python Package Index (PyPI)](https://pypi.org/).

So, we will use `venv` and `pip` in combination to help us create and share our virtual development environments.

## Creating virtual environments

Creating a virtual environment with `venv` is done by executing the following command:

```python
$ python -m venv /path/to/new/virtual/environment
```

where `/path/to/new/virtual/environment` is a path to a directory where you want to place it -
conventionally within your software project so they are co-located.
This will create the target directory for the virtual environment.

For our project let's create a virtual environment called "venv_spacewalks".
First, ensure you are within the project root directory, then:

```python
$ python -m venv venv_spacewalks
```

If you list the contents of the newly created directory "venv", on a Mac or Linux system
(slightly different on Windows as explained below) you should see something like:

```bash
$ ls -l venv_spacewalks
```

```bash
total 8
drwxr-xr-x  12 alex  staff  384  5 Oct 11:47 bin
drwxr-xr-x   2 alex  staff   64  5 Oct 11:47 include
drwxr-xr-x   3 alex  staff   96  5 Oct 11:47 lib
-rw-r--r--   1 alex  staff   90  5 Oct 11:47 pyvenv.cfg
```
So, running the `python -m venv venv_spacewalks` command created the target directory called "venv_spacewalks"
containing:

- `pyvenv.cfg` configuration file
  with a home key pointing to the Python installation from which the command was run,
- `bin` subdirectory (called `Scripts` on Windows)
  containing a symlink of the Python interpreter binary used to create the environment
  and the standard Python library,
- `lib/pythonX.Y/site-packages` subdirectory (called `Lib\site-packages` on Windows)
  to contain its own independent set of installed Python packages isolated from other projects, and
- various other configuration and supporting files and subdirectories.

Once you’ve created a virtual environment, you will need to activate it.

On Mac or Linux, it is done as:

```bash
$ source venv_spacewalks/bin/activate
(venv_spacewalks) $
```

On Windows, recall that we have `Scripts` directory instead of `bin`
and activating a virtual environment is done as:

```bash
$ source venv_spacewalks/Scripts/activate
(venv_spacewalks) $
```

Activating the virtual environment will change your command line’s prompt
to show what virtual environment you are currently using
(indicated by its name in round brackets at the start of the prompt),
and modify the environment so that running Python will get you
the particular version of Python configured in your virtual environment.

You can verify you are using your virtual environment's version of Python
by checking the path using the command `which`:

```bash
(venv_spacewalks) $ which python
```

When you’re done working on your project, you can exit the environment with:

```bash
(venv_spacewalks) $ deactivate
```

If you've just done the `deactivate`,
ensure you reactivate the environment ready for the next part:

```bash
$ source venv_spacewalks/bin/activate
(venv_spacewalks) $
```

Note that, since our software project is being tracked by Git,
the newly created virtual environment will show up in version control -
we will see how to handle it using Git in one of the subsequent episodes.

## Installing external packages

We noticed earlier that our code depends on four *external packages/libraries* -
`json`, `csv`, `datetime` and `matplotlib`. 
As of Python 3.5, Python comes with in-built JSON and CSV libraries - this means there is no need to install these  
additional packages (if you are using a fairly recent version of Python), but you still need to import them in any 
script that uses them. 
However, we still need to install packages `datetime` and `matplotlib` as they do not come as standard with 
Python distribution.

To install the latest version of packages `datetime` and `matplotlib` with `pip`
you use pip's `install` command and specify the package’s name, e.g.:

```bash
(venv_spacewalks) $ python -m pip install datetime
(venv_spacewalks) $ python -m pip install matplotlib
```

or like this to install multiple packages at once for short:

```bash
(venv_spacewalks) $ python -m pip install datetime matplotlib
```

The above commands have installed packages `datetime` and `matplotlib` in our currently active `venv_spacewalks` 
environment and will not affect any other Python projects we may have on our machines.

If you run the `python -m pip install` command on a package that is already installed,
`pip` will notice this and do nothing.

To install a specific version of a Python package
give the package name followed by `==` and the version number,
e.g. `python -m pip install matplotlib==3.5.3`.

To specify a minimum version of a Python package,
you can do `python -m pip install matplotlib>=3.5.1`.

To upgrade a package to the latest version, e.g. `python -m pip install --upgrade matplotlib`.

To display information about a particular installed package do:

```bash
(venv_spacewalks) $ python -m pip show matplotlib
Name: matplotlib
Version: 3.9.0
Summary: Python plotting package
Home-page: 
Author: John D. Hunter, Michael Droettboom
Author-email: Unknown <matplotlib-users@python.org>
License: License agreement for matplotlib versions 1.3.0 and later
=========================================================
...
Location: /opt/homebrew/lib/python3.11/site-packages
Requires: contourpy, cycler, fonttools, kiwisolver, numpy, packaging, pillow, pyparsing, python-dateutil
Required-by: 
```

To list all packages installed with `pip` (in your current virtual environment):

```bash
(venv_spacewalks) $ python -m pip list
Package         Version
--------------- -----------
contourpy       1.2.1
cycler          0.12.1
DateTime        5.5
fonttools       4.53.1
kiwisolver      1.4.5
matplotlib      3.9.2
numpy           2.0.1
packaging       24.1
pillow          10.4.0
pip             23.3.1
pyparsing       3.1.2
python-dateutil 2.9.0.post0
pytz            2024.1
setuptools      69.0.2
six             1.16.0
zope.interface  7.0.1
```

To uninstall a package installed in the virtual environment do: `python -m pip uninstall <package-name>`.
You can also supply a list of packages to uninstall at the same time.

## Exporting/Importing virtual environments

You are collaborating on a project with a team so, naturally,
you will want to share your environment with your collaborators
so they can easily 'clone' your software project with all of its dependencies
and everyone can replicate equivalent virtual environments on their machines.
`pip` has a handy way of exporting, saving and sharing virtual environments.

To export your active environment -
use `python -m pip freeze` command to produce a list of packages installed in the virtual environment.
A common convention is to put this list in a `requirements.txt` file:

```bash
(venv_spacewalks) $ python -m pip freeze > requirements.txt
(venv_spacewalks) $ cat requirements.txt
contourpy==1.2.1
cycler==0.12.1
DateTime==5.5
fonttools==4.53.1
kiwisolver==1.4.5
matplotlib==3.9.2
numpy==2.0.1
packaging==24.1
pillow==10.4.0
pyparsing==3.1.2
python-dateutil==2.9.0.post0
pytz==2024.1
six==1.16.0
zope.interface==7.0.1
```

The first of the above commands will create a `requirements.txt` file in your current directory.
Yours may look a little different,
depending on the version of the packages you have installed,
as well as any differences in the packages that they themselves use.

The `requirements.txt` file can then be committed to a version control system
(we will see how to do this using Git in one of the following episodes)
and get shipped as part of your software and shared with collaborators and/or users.
They can then replicate your environment
and install all the necessary packages from the project root as follows:

~~~
(venv_spacewalks) $ python -m pip install -r requirements.txt
~~~
{: .language-bash}

As your project grows - you may need to update your environment for a variety of reasons.
For example, one of your project's dependencies has just released a new version
(dependency version number update),
you need an additional package for data analysis (adding a new dependency)
or you have found a better package and no longer need the older package
(adding a new and removing an old dependency).
What you need to do in this case
(apart from installing the new and removing the packages that are no longer needed
from your virtual environment)
is update the contents of the `requirements.txt` file accordingly
by re-issuing `pip freeze` command
and propagate the updated `requirements.txt` file to your collaborators
via your code sharing platform (e.g. GitHub).

Let's do that now.

```bash
(venv_spacewalks) $ git add requirements.txt
(venv_spacewalks) $ git commit -m "Initial commit of requirements.txt."
(venv_spacewalks) $ git push origin main
```
