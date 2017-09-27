# EnvironmentSetup

You will need to prepare your system to run python and Flask. If you have previously used Flask, skip to the [testing](#testing) section to verify that your installation works. As you go through the tutorial, feel free to skip certain steps in the tutorial if you have already completed the instructions earlier.

### Table of Contents

1. [Mac OS Installation](#mac-osx)
	1. [Package Manager](#1.-package-manager)
	2. [pip](#pip)
	3. [virtualenv](#virtualenv)
	4. [Testing](#testing)

## Mac OSX
For the majority of the installation, we will be using the terminal. Don't worry if you're unfamiliar with it - we will walk you step by step through the installation.
Open terminal by simply typing it into the spotlight search.

### 1. Package Manager
Your system has a preinstalled version of python that we have limited control over. You can type `python --version` into your terminal window to see your current python version. If you don't see `Python 2.7.13`, follow the rest of this step.

We want to maintain our own version of python which we are going to do via the Homebrew package manager for mac-osx.

1. Install homebrew by running the following command:
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
2. Update your brew references:
```shell
brew update
```
3.

### 4. Testing
If you followed all of the previous steps without error, you should be able to run Flask now!
1. Make sure that your virtualenv is activated (remember: `source bin/activate`)
2. Copy and paste the following code into a file (don't worry if you don't understand what's going on - we'll be going into granular detail in the coming weeks!):
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return "Hello World!"

if __name__ == "__main__":
	app.run()
```
3. Save the file as app.py and run `python app.py`. You should see:
```shell
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```
4. Open a web browser and go to `127.0.0.1:5000` and you should see something like this!
