# Python

Python is an interpreted general purpose programming language. Its key features include dynamic-typing, support for multiple programming paradigms and emphasis on code readability.

## Distributions

Before getting started programming in Python, you may want to consider which distribution of Python to use. Generally different distributions offer different ways to;

1. Change which version of the Python interpreter to use
2. Discover and download Python packages
3. Manage Python virtual environments

The official distribution is CPython which can be downloaded from <https://www.python.org>. This guide will only cover the official distribution.

## Interpreters

Python code is read and executed by an interpreter which can be provided interactively or pass in as a file. For example to run a Python program written in the file `HelloWorld.py`, run the command;

    python HelloWorld.py

When working with different Python projects, you may encounter a need to switch between different version of the Python interpreter. How you do this will depend on the distribution of Python you are using. [`pyenv`](https://github.com/pyenv/pyenv) is an example of a tool you could use to do this. There is also [`pyenv-win`](https://github.com/pyenv-win/pyenv-win) if you are using Windows.

## Package Management

`pip` is the default package manager in Python that installs packages from the [Python Package Index (PyPi)](https://pypi.org). To install a package, you can run one of the following;

    python -m pip install SomePackage               # Latest Version
    python -m pip install SomePackage==1.0.4        # Specific Version
    python -m pip install "SomePackage>=1.0.4"      # Minimum Version

To upgrade a package a different command must be used;

    python -m pip install --upgrade SomePackage

Likewise to uninstall a package, use this command;

    python -m pip uninstall SomePackage

By default, `pip` installs packages for all users on a system. To install packages only for the current user, add the option `--user` to your command. To list what packages are installed you can use one of the following commands;

    python -m pip list                              # All Users
    python -m pip list --user                       # Current User

When working on a Python project, developers will often list all the required packages for that project in a file called `requirements.txt`. To install all the packages in this file, you can run;

    python -m pip install -r requirements.txt

There is also a command to generate a `requirements.txt` file from your current active Python environment as well;

    python -m pip freeze > requirements.txt

To learn more about `pip`, please checkout the [Python Packaging User Guide](https://packaging.python.org).

## Virtual Environment Management

Virtual environments is Python's solution to installing and managing packages on a per project basis. This is very important when working on different Python projects that require different versions of the same package. `venv` is the default virtual environment manager in Python.

To create a virtual environment, use the command;

    python -m venv .venv

`.venv` is actually the name and location of the directory to create the virtual environment in. You can use any name and location you want but `.venv` is common. Once created, you will need to activate your virtual environment before you can start using it.

To activate a virtual environment on macOS or Unix like operating systems, run;

    source .venv/bin/activate

To activate a virtual environment on Windows, run;

    .venv\Scripts\activate.bat

Once activate, `pip` will install Python packages into the virtual environment.

To deactivate a virtual environment, simply run;

    deactivate
