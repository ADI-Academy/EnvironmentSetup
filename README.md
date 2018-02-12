# EnvironmentSetup

You will need to prepare your system to run python and Flask. If you have previously used Flask, skip to the [testing](#testing) section to verify that your installation works. As you go through the tutorial, feel free to skip certain steps if you have already completed the instructions prior.

### Table of Contents

1. [Mac OS Installation](#mac-osx)
	1. [Package Manager](#1-package-manager)
	2. [pip](#2-pip)
	3. [virtualenv and flask](#3-virtualenv-and-flask)
	4. [Testing](#4-testing)
2. [Windows Installation](#windows)
	1. [Python](#1-python-for-windows)
	2. [pip](#2-pip-for-windows)
	3. [virtualenv and flask](#3-virtualenv-and-flask-for-windows)
	4. [Testing](#4-testing-for-windows)
3. [Anaonda Setup](#anaconda)
4. [Editors](#editors)

-----
**IMPORTANT: Please check if you have Anaconda installed on your computer.** If you have taken 1006, you most likely have it installed and should first proceed to the [anaconda section](#conda) before completing this tutorial.


## Mac OSX
For the majority of the installation, we will be using the Command Line (known as "terminal" on mac) which allows us to access a text-based interface to the computer. You can open the program by simply searching for "terminal" into your spotlight bar.

**Note:** In this tutorial, whenever you see terminal inputs such as `$ echo "Hello World"` the `$` at the beginning of the line is just a convention to indicate the terminal - please do not add it to your actual command.

### 1. Package Manager
Your system has a preinstalled version of python that we have limited control over. You can type `python --version` into your terminal window to see your current python version. However, we want to be using python 3 since python 2 is quickly reaching the end of its lifetime.

In order to download and maintain our own version of python, we are going to use the Homebrew package manager for Mac-OSX.

1. Install homebrew by running the following command and following the printed instructions. This step should takea  few minutes to complete.
```shell
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Update your brew references:
```shell
$ brew update
```

3. Install python 3
```shell
$ brew install python3
```

4. Test to see if your output matches the below lines!
```shell
$ python3 --version
Python 3.6.4
$ which python3
/usr/local/bin/python3
```
If you got to this step then your python has been installed correctly!

### 2. The Virtual Environment
**READ THIS: ITS IMPORTANT**
Proper python development should be done in a **Virtual Environment**, or `virtualenv` for short. `virtualenv` is a tool to create an isolated **python environment**, the collection of software and files that give developers tools to use the language (including `python` and `pip`).

Why do we need this isolated environment? Suppose you're using Software X, and it depends on version 1.0 of SomeLibrary. Everything's fine until you start working on Project Y, which depends on version 2.0 of SomeLibrary. How can you work with both applications when they depend on conflicting pieces of software? As your project expands, how do you prevent your dependencies from becoming a mess.

The main use of an isolated environment is to give you a clean set of python libraries so that your projects do not interfere and pollute each other's requirements. Beginners to python often find the process of setting up and using a `virtualenv` rather tedious but the benefits of isolating your environment cannot be overstated.

*Advanced (optional):* More specifically, the `virtualenv` simply contains a copy of the python binaries and a separate, initially empty, folder for the python libraries. When you activate your virtual environment (see below), a script prepends the `virtualenv` python to your path and changes some system python variables to allow you to use the isolated python libraries.

#### Setting up your virtualenv  
**NOTE:** If you are not familiar with the Command Line, there are just a few commands that you need to be familiar with:

a. `cd`: `cd` stands for "change directory". It allows you to navigate to a different folder (or directory) in your computer.
```shell
Academys-Macbook-Pro:~ academy$ cd Desktop
Academys-Macbook-Pro:~/Desktop academy$
```
b. `ls`: `ls` lists the contents of the current directory. This allows you to see which directories you can navigate to.
```shell
Academys-Macbook-Pro:~ academy$ ls
Desktop        Downloads      Movies        Pictures
Documents      Library        Music         Public
```
c. `mkdir`: `mkdir` is short for "make directory" and makes a directory with the name you supply.
```shell
Academys-Macbook-Pro:~ academy$ mkdir Academy
Academys-Macbook-Pro:~ academy$ ls
Academy        Documents      Library       Music          Public
Desktop        Downloads      Music         Pictures
```

All of these commands are just simpler (and often quicker) ways of interacting with your computer if you were using the Finder and clicking through folders.

**Setup**
1. Navigate (using `ls` and `cd`) to a directory where you want to store your web application. For convenience, we recommend creating a folder (using `mkdir`) on your Desktop.

2. Use the following command to create a virtualenv
```shell
$ python3 -m venv my_venv
```
This will create a folder called `my_venv` which contains all that you need to run your isolated python environment.

3. **SUPER IMPORTANT: ACTIVATING YOUR VIRTUALENV** You need to activate your virtualenv **each** time that you want to use it. Navigate to the directory that contains `my_venv`:

	```shell
	$ ls
	my_venv
	$ source my_venv/bin/activate
	```
	You should commit the `source my_venv/bin/activate` command to memory. We'll be using it *every* time we do any coding.
If all goes well, you should see that the name of your virtualenv (in this case `my_venv`) has been prepended to your terminal output. It should look something like below:

	```shell
	(my_venv) $
	```

4. Remember again to check if your virtualenv is activated by seeing if the name is in parentheses at the beginning of your terminal prompt!

5. If you ever need to exit out of a virtualenv, either to go to a different virtualenv or to use your system python version, simply use the `deactivate` command.
```shell
(my_venv) $ deactivate
```


### 3. pip
Libraries are so crucial to the python language that there is a specific software, known as a **package manager** that helps developers install, organize, and maintain their libraries. We call this  tool `pip`. We will start by downloading and installing our most important library, the `flask` web development package.

1. Installing with pip is extremely easy - simply use `pip install <name_of_package>`. Make sure that you are in your virtualenv!
```shell
(my_venv) $ pip install flask
```
You should see a bunch of text notifying you what `pip` is up to. Notice that in addition to installing `flask`, the program also installs a bunch of other libraries (`click`, `Werkzeug`, etc.). These libraries are called **dependencies** since our target library `flask` needs these other packages in order to run.

2. You can see which programs you have installed by using the `list` subcommand.
```shell
$ pip list
click (6.7)
Flask (0.12.2)
itsdangerous (0.24)
Jinja2 (2.10)
MarkupSafe (1.0)
pip (9.0.1)
setuptools (28.8.0)
Werkzeug (0.14.1)
```


### 4. Testing
If you followed all of the previous steps without error, you should be able to run Flask now!
1. Make sure that your virtualenv is activated (remember: `$ source bin/activate`)

2. Copy and paste the following code into a file and save it . If you don't know how to do this, download [an editor](#editors), copy the code into a file and save it in the same folder as your virutalenv. (don't worry if you don't understand what's going on in the code - we'll be going into granular detail in the coming weeks!):

	```python
	from flask import Flask
	app = Flask(__name__)

	@app.route('/')
	def index():
	    return "Hello World!"

	if __name__ == "__main__":
		app.run()
	```

3. Save the file as `app.py` in `$ACACDEMY` and run `python app.py`. You should see:
```shell
(my_venv) $ python app.py
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 ```
4. Open a web browser and go to `localhost:5000` and you should see something like this!

![Hello World Flask](images/flask-hello-world.png)

-------
## Windows
For the majority of the installation, we will be using command prompt (or Git Bash if you choose to). To access command prompt, press the start key and type in 'cmd' into the search bar and press enter.

**Note:** Whenever you see cmd inputs such as `$ echo "Hello World"` the `$` at the beginning of the line is just a convention to indicate the terminal - please do not add it to your actual command.

### 1. Python for Windows
If you have Python 3.6.4 already installed, you can skip this step. If you don't know if you do, you can type `python --version` into your terminal window to see your current python version. If you don't have Python 3.6.4 installed, follow these steps.

Install the python package from [here](https://www.python.org/downloads/windows/). We will be using python 3.6.x in this course where x is just the latest version of python.
_At the time of this writing, [Python 3.6.4](https://www.python.org/downloads/release/python-364/) is the latest._  

Download the executable installer and click on ENABLE PATH VARIABLE. Make sure this is checked!

* Verify a successful installation by opening a command prompt window typing the following commands.
    ```
    Microsoft Windows [Version 6.2.9200]
    (c) 2012 Microsoft Corporation. All rights reserved.

    C:\Users\Username>python --version
    Python 3.6.4
    ```

### 2. pip for Windows
pip is the official package manager for python and allows you to install and manage third-party extensions to python. As we use python more and more, this tool becomes invaluable and you should spend some time playing around with it to see how it works. Pip is automatically installed with Python3.

### 3. virtualenv and flask for Windows
**READ THIS: ITS IMPORTANT**
Most of professional python coding is done in a **Virtual Environment**, or virtualenv for short, a tool to create an isolated **python environment**. When programmer's refer to the "python environment", they are talking about the collection of software and files that give developers tools to use the language. The software component includes the python binary (what the system calls when you type `python3`) and some other useful tools that we will cover later including `pip` and `wheel`. The second main component is the collection of **libraries** that a developer has downloaded. It is often said that python has a library for everything and it is indeed this feature of python that gives the language so much power and versatility.

The main use of the virtualenv is to simulate an **isolated python environment** complete with its own set of binaries (`python`, `pip`, etc.) and a clean set of libraries. This allows you to separate different projects with different requirements and prevent your application from being polluted by differences in library versions, cross-platform differences, etc. Beginners to python often find the process of setting up and using a virtualenv rather tedious but the benefits of good practice with python cannot be overstated.

*Advanced (optional):* More specifically, the virtualenv simply contains a copy of the python binaries and a separate, initially empty, folder for the python libraries. When you activate your environment (see below), a script prepends the virtualenv python to your path and changes some system python variables to allow you to use the isolated python libraries.

#### Setting up your virtualenv  
**NOTE:** If you are not familiar with the Command Line, there are just a few commands that you need to be familiar with:

a. `cd`: `cd` stands for "change directory". It allows you to navigate to a different folder (or directory) in your computer.
```shell
C:\Users\User> cd Desktop
C:\Users\User\Desktop>
```
b. `dir`: `dir` lists the contents of the current directory. This allows you to see which directories you can navigate to.
```shell
C:\Users\User> dir
Desktop        Downloads      Movies        Pictures
Documents      Library        Music         Public
```
c. `mkdir`: `mkdir` is short for "make directory" and makes a directory with the name you supply.
```shell
C:\Users\User> mkdir Academy
C:\Users\User> ls
Academy        Documents      Library       Music          Public
Desktop        Downloads      Music         Pictures
```

All of these commands are just simpler (and often quicker) ways of interacting with your computer if you were using the Finder and clicking through folders.

**Setup**
1. Navigate (using `dir` and `cd`) to a directory where you want to store your web application. For convenience, we recommend creating a folder (using `mkdir`) on your Desktop.

2. Use the following command to create a virtualenv
```shell
> python -m venv my_venv
```
This will create a folder called `my_venv` which contains all that you need to run your isolated python environment.

3. **SUPER IMPORTANT: ACTIVATING YOUR VIRTUALENV** You need to activate your virtualenv **each** time that you want to use it. Navigate to the directory that contains `my_venv`:
```shell
> dir
my_venv
> .\Scripts\activate
```
You should commit the `.\Scripts\activate` command to memory. We'll be using it *every* time we do any coding.
If all goes well, you should see that the name of your virtualenv (in this case `my_venv`) has been prepended to your terminal output. It should look something like below:

```shell
(my_venv) $
```

4. Remember again to check if your virtualenv is activated by seeing if the name is in parentheses at the beginning of your terminal prompt!

5. If you ever need to exit out of a virtualenv, either to go to a different virtualenv or to use your system python version, simply use the `deactivate` command.
```shell
(my_venv) > deactivate
```

### 4. Installing Flask
5. We will install our first package in our new virutalenv.
```shell
(my_venv) C:\Users\User\Desktop\my_venv> pip install flask
```
The [flask library](http://flask.pocoo.org/docs/0.12/) contains the majority of the important functionality that we will use this semester.

## Conda
Having Anaconda installed on your computer presents a few difficulties. Throughout the tutorials, we will be using the `pip` package manager which interferes with Anaconda's built in package manager, `conda`. You have two options:
### 1. Remove Anaconda (Recommended)
If you are no longer taking 1006 or do not need the Anaconda environment any longer, the easiest solution is just to delete Anaconda entirely. This can be done by using your system uninstaller or by moving the entire Anaconda folder to the trash.
#### Conda Uninstall - Mac OSX
If you are familiar with using the terminal, just input the following command and you should be able to remove Anaconda:

`rm -rf ~/anaconda`

In addition, Mac users need to remove Anaconda's path variable from their `.bash_profile`. If you do not know what this means, simply type the following into your terminal:

`rm ~/.bash_profile && touch ~/.bash_profile`

Otherwise, remove the line that adds the Anaconda python path from your `.bash_profile`. It should look something like:

`export PATH=/usr/bin/anaconda`

Just delete this line and restart your terminal! To make sure that you successfully reached this step, you should see the following after running `python`:

```shell
$ python
Python 2.7.10 (default, Jul 15 2017, 17:16:57)
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.31)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
Note that we are now using the system default python distribution. Press `ctrl-c` to exit out of this environment! You're now set to proceed with the [rest of the Mac installation](#mac-osx)

#### Conda Uninstall - Windows
On windows, simply delete the Anaconda folder from your computer or use the system uninstaller to remove Anaconda. Contact a TA if you are not sure how to do this. Once you are done, make sure that you successfully uninstalled Anaconda by running the `python` command. You should see an error! No worries, proceed with the [rest of the Windows python installation](#windows).

### 2. Keep Anaconda
If you need to use the scientific resources provided by Anaconda in the future, and want to keep the software on your computer, you can still use flask! Follow the installation steps below.

1. Python should be already be installed on your computer from the Anaconda environment. If you type the `python3` command in your command line (terminal for mac or command prompt for windows), you should see something like the following:

	```shell
	$ python3
	Python 3.6.3 |Anaconda, Inc.| (default, Oct 6 2017, 12:04:38)
	[GCC 4.2.1 Compatible Clang 4.0.1 (tags/RELEASE_401/final)] on darwin
	Type "help", "copyright", "credits" or "license" for more information.
	>>>
	```
	Note that the distributor for your python is `Anaconda, Inc.` instead of the default mac distribution. Enter `ctrl-c` to exit out of your python shell.

2. Create your virtual environment. **IMPORTANT:** Please read the explanation of why we use virtual environments [here](#3-virtualenv-and-flask).

	```shell
	$ conda create -n my_venv
	```

Follow the on-screen prompts.

3. Every time that you want to code in flask, you must first activate your virtual environment. Commit the next line of instruction to memory - you'll be seeing it over and over again!

	```shell
	$ source activate my_venv
	```

	When you want to leave your conda virtual environment, you need to use the following command:
 	```shell
	$ source deactivate
	```

4. Once you are in your virtual environment, you should see that the front of your terminal prompt shows the name of the environment in parentheses (e.g. `(my_venv) MY_NAME $`). Make sure you look for this whenever you want to be in a virtual environment. We now install the flask packages. Type the following command to install flask into your virtual environment.

	```shell
	conda install flask
	```

Follow the on screen prompts and proceed to [testing](#testing) to make sure that you have a proper installation!


## Editors
Having a good text editor is essential to programming. However, the choice of editors between programmers can be a source of the most vehement passive-aggressiveness (which is what passes as conflict between coders). That being said, we have included a few options if you don't have a favorite yet.
##### [Sublime Text](https://www.sublimetext.com/)
**Used by:** Nick, Jonathan

An extremely popular, minimalistic editor that also has one of the biggest community of contributors who have created almost every possibly extension thought possible. Pick this one either if you don't want to choose or are just looking for a solid setup.

##### [Atom](https://atom.io/)
Another popular, minimalistic editor that was created by the guys at Github. Atom is very similar to Sublime Text with a comparable library of stable plugins and extensions to the language. Some people believe that Sublime Text is faster however while Atom boasts a cleaner interface. Choose this if you want to stir up fights with your basic teammates who all are using Sublime Text.

##### [Visual Code](https://code.visualstudio.com/)
An up and coming editor made by Microsoft and the people behind the madly popular Visual Studios suite (very different from Visual Code). There has been a sizable exodus from both the Sublime Text and Atom camp to this editor in the past few years. Check this one out if you want something a bit different or if Sublime Text and Atom are too dry for you. Also, if you choose this one, please let us know your thoughts.

##### [Pycharm](https://www.jetbrains.com/pycharm/)
**Used by:** Jonathan

This is hands-down the best editor for most things in python and especially flask. There is an overwhelming suite of different functionality that make your life as programmer worth living. As a student, you can even get the premium (read: expensive) version for free. However, this editor is not recommended for beginners as it is has a rather steep learning curve and will consume significantly more memory and resources on your computer than the others on this chart.
