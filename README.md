# How to get access to a bash shell, as a Windows user

These notes are meant for students of the course Python for Linguists 2 of Leiden University.


## Option A: Dual boot.

You can install a user-friendly Linux distribution (e.g., Ubuntu) _alongside_ your windows distribution. This is called _dual boot_. That way, when starting up your computer, you get to choose which operating system to use. For this course, you would then mostly work inside Linux.

Changing things at the operating system level carries with it some risk; make sure you have recent backups, and make sure you know how to (and have the means to) reinstall Windows, if necessary, if everything goes wrong.
  
This option has potentially the greatest cost up front, but will likely make everything easier down the road.


## Option B: the Windows Subsystem for Linux (WSL)
         
### 1. Install the Windows Subsystem for Linux
  
Follow the official [instructions](https://learn.microsoft.com/en-us/windows/wsl/install).

Then see if you can run the Windows Subsystem for Linux (wsl.exe), to get a command-line kind of interface. Also, see if you can find your new Linux 'virtual drive' in the Windows explorer.

### 2. Installing Python
                                   
Within the WSL, check whether Python is installed, and which version, by entering `python --version`. 
Version 3.11 might currently be ideal.
                                             
If Python 3.11 is not installed, you can install it, and its distutils (distribution utilities), from the 'deadsnakes' repository (because a Python is a kind of snake...), by entering the following commands in WLS:

                                   
```bash

sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.11
sudo apt install python3.11-distutils

```
                                             
### 3. Installing pip, pipx and venv

It might be necessary, and probably won't hurt, to install pip for Python 3.11 in the following way:

```bash
curl -sS https://bootstrap.pypa.io/get-pip.py | python3.11
```
                             
Next, to handle virtual environments, install `venv`, and to easily install Python tools as self-contained 'executables', install `pipx`:

```bash
sudo apt install python3.11-venv
python3.11 -m pip install pipx
```

These tools will be explained later in the course.

### 4. PyCharm setup: Choosing `wsl.exe` as the PyCharm shell

This and the following step are only for convenience, and not strictly necessary.

In PyCharm, you can select which shell to use, somewhere around settings>tools>terminal. If WSL doesn't show up (but it has been properly installed), you can enter `wsl.exe` manually. 

Presumably, restart the Terminal tab in PyCharm for it to take effect.

### 5. PyCharm setup: Choosing WSL's Python interpreter in PyCharm

You may recall that PyCharm needs to know which Python interpreter to use for your project -- somewhere around Settings>Project>Interpreter.

For consistency inside and outside PyCharm, you can select (or create a virtual environment based on) a Python interpreter in WSL.

Unfortunately, this is currently only supported if you have the PyCharm Professional edition. Fortunately, this editoin is free for students, so you might as well.

Caveat: The WSL shell in PyCharm does _not_ automatically activate the project's virtual environment.

Full instructions here: https://www.jetbrains.com/help/pycharm/using-wsl-as-a-remote-interpreter.html 

## Option C: cygwin

[Cygwin](https://www.cygwin.com/) is a bash terminal for Windows. 
The instructor of the course has only limited experience with setting this up, so you're somewhat 'on your own'.

Ideally, steps 2. and 3. of option B (WSL) should also apply to Cygwin. Perhaps something like step 4. can be worked out as well. A quick web search suggests PyCharm does not support cygwin.


## Finding your bearings
         
If you are lost in between all the different shells and different versions of Python, useful commands on the (bash) shell are `python --version`, `pip --version`, `which python` and `which pip`.
