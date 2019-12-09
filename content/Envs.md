# Scientific Development environments

## Why using environments ?
- reproductibility
- ...

- different version of Python
- separate site-packages


> all programs share the same global installation 
https://www.youtube.com/watch?v=i7_US0Jff30 


![python env xkcd drawing](https://imgs.xkcd.com/comics/python_environment.png)

## Anaconda

## Conda
- popular in the scientific community
- combination of package manager (like pip) & env manager (like virtualenv + virtualenvwrapper)
- easier to use ? (considered)
- does not support all the packages that pip does (e.g  beautifulsoup)
(can use pip inside conda)

## Pyvenv / pyenv / virtualenv / venv

### venv

### virtualenv / + wrapper

> [virtualenv](https://pypi.org/project/virtualenv/ "virtualenv project page") is a tool to create isolated Python environments. virtualenv creates a folder which contains all the necessary executables to use the packages that a Python project would need.
https://docs.python-guide.org/dev/virtualenvs/



### pyenv : managing the versions of Python

As a standard, only one version of Python can be installed on an operating system at a time. However, it can occur that we want to execute a script with a different version of Python than the default one installed locally on our system / computer. Especially, when you are running tests or because a library used in the project needs a specific version of Python to work.

### pipenv

> Pipenv is a project that aims to bring the best of all packaging worlds to the Python world. It harnesses Pipfile, pip, and virtualenv into one single toolchain. It features very pretty terminal colors.
https://packaging.python.org/key_projects/#pip

[Docs](https://pipenv.readthedocs.io/en/latest/ "Documentation of pipenv") | [Source](https://github.com/pypa/pipenv "Source code to pipenv") | [PyPI](https://pypi.org/project/pipenv/ "pipenv Project Page")

relies on two seperate files :
- pipfile
    - similar to requirements.in  -> requirements.txt
    - human readable
- pipfile.lock
    - real requirements.txt

pipfile + lock pipfile : use to regenerate env

- don't need to manipulate you pipfile > pipenv does it for you
- combination of virtualenv + pip
- recommanded by PyPA (Python Packaging Authority)
- use it ot generate and both create env, install dependencies into env, update pipfile / lock file.
Env  : directory associated to a project.

pipenv install package > install package + update pipfile & lock file

pipenv unstall --dev package >> seperate packages dev / production / etc

pipenv shell : activating the virtual env, spaws a sub-shell inside your shell, run in the virtual env

pipenv run python script.py : run the command using the virtual env but only the command. Back to original prompt /shell

pipenv graph : generate graph of packages installed and their dependencies, shows it 

IDE supporting pipenv : PyCharm, VS Code. NOT Atom


Drawbacks : 
- not recommanded if you are creating a package/library. Only for programs
- locking can be slow
- by default, update all the dependencies evry time a new package is installed 
    - can be changed with --selective-upgrade

Pros:
- installs packages and updates lock file in one command
- intalls packages concurrently
- prevents dependency conflit
- check for security

## pip : installation of packages / libraries
- relaesed in 2011
pip install -r requirements.txt
pip freeze (all that is installed, + the dependencies of what is installed)

lack of synchronisation > e.g. if a new package is installed but the requirements.txt is not updated.