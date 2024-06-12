---
title: "Python3.12 Upgrade: Setting Up Virtualenvwrapper"
seoTitle: "Setting Up Virtualenvwrapper in Python 3.12"
seoDescription: "Guide to setting up `virtualenvwrapper` with Python 3.12 on Ubuntu 24.04 after upgrade issues. Avoid conflicts and maintain system stability"
datePublished: Wed Jun 12 2024 16:44:58 GMT+0000 (Coordinated Universal Time)
cuid: clxc2ac7l000208mnfq9i80qr
slug: python312-upgrade-setting-up-virtualenvwrapper
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1718210252646/649234f1-c0b5-464e-94ff-521bfac3b299.webp
tags: ubuntu, python, developer, python3, developer-tools, virtualenvwrapper, ubuntu-2404

---

### The Surprise Challenge

Recently, I decided to upgrade my system to Ubuntu 24.04. I enjoy keeping my setup current, and I wanted to take advantage of the latest features and improvements. Everything seemed to be going well until I hit a snag. I use `virtualenvwrapper` to manage my Python environments, but after the upgrade, it stopped working. I kept getting this error:

```bash
/usr/bin/python3: Error while finding module specification for 'virtualenvwrapper.hook_loader' (ModuleNotFoundError: No module named 'virtualenvwrapper')
virtualenvwrapper.sh: There was a problem running the initialization hooks.

If Python could not import the module virtualenvwrapper.hook_loader,
check that virtualenvwrapper has been installed for VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3 and that PATH is set properly.
```

### Digging into the Problem

This was a new problem for me. I discovered that Python 3.12, which comes with Ubuntu 24.04, has stricter rules about installing packages globally. This change is designed to prevent conflicts and maintain system stability by keeping the system's Python environment clean. However, it also means you can't just use `pip` to install things globally like before. Instead, you have to use virtual environments for package management.

I initially tried using `pipx` to install `virtualenvwrapper`, but I ran into another issue. The `virtualenvwrapper` installed via `pipx` wasn’t accessible in my `.zshrc` configuration. It seems `pipx` is great for some standalone applications, but it doesn't play well with tools like `virtualenvwrapper` that need to be sourced in a shell configuration file.

### Finding the Solution

To fix this, I decided to install `virtualenvwrapper` in its own virtual environment. Here’s how I did it:

#### Step 1: Create a Virtual Environment

First, I created a new virtual environment to keep things isolated.

```bash
python3 -m venv ~/.virtualenvs/venv
```

This command made a new virtual environment in the `~/.virtualenvs/venv` directory.

#### Step 2: Activate the Virtual Environment

Next, I activated the virtual environment.

```bash
source ~/.virtualenvs/venv/bin/activate
```

The shell prompt changed, showing I was now working inside the `venv` environment.

#### Step 3: Install `virtualenvwrapper`

With the virtual environment activated, I installed `virtualenvwrapper`.

```bash
pip install virtualenvwrapper
```

**Why Do This in a Virtual Environment?**

1. **Avoid Conflicts**: Python 3.12 doesn’t let you install packages globally to avoid messing up the system’s packages. Using a virtual environment keeps everything separate.
    
2. **Isolation**: By installing in a virtual environment, `virtualenvwrapper` gets its own set of dependencies, with no interference from other projects.
    
3. **Easy Management**: If something breaks, you can just delete the virtual environment and start over, without affecting the system Python or other projects.
    

#### Step 4: Set Up My Shell

Next, I needed to tell my shell to use this new setup. I edited my `.zshrc` file (it could be `.bashrc` if you use bash).

##### Edit `.zshrc`

I opened my shell configuration file in a text editor:

```bash
nano ~/.zshrc
```

I added these lines:

```bash
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=$HOME/.virtualenvs/venv/bin/python
export VIRTUALENVWRAPPER_VIRTUALENV=$HOME/.virtualenvs/venv/bin/virtualenv
source $HOME/.virtualenvs/venv/bin/virtualenvwrapper.sh
```

**What Do These Lines Do?**

* `export WORKON_HOME=$HOME/.virtualenvs`: This sets the directory where `virtualenvwrapper` will keep all my virtual environments.
    
* `export VIRTUALENVWRAPPER_PYTHON=$HOME/.virtualenvs/venv/bin/python`: This tells `virtualenvwrapper` to use the Python from my virtual environment.
    
* `export VIRTUALENVWRAPPER_VIRTUALENV=$HOME/.virtualenvs/venv/bin/virtualenv`: This points to the `virtualenv` executable in my virtual environment.
    
* `source $HOME/.virtualenvs/venv/bin/`[`virtualenvwrapper.sh`](http://virtualenvwrapper.sh): This initializes `virtualenvwrapper` so I can use its commands.
    

##### Save and Exit

In `nano`, I saved the file by pressing `Ctrl+O` and then `Enter`, and exited with `Ctrl+X`.

#### Step 5: Reload My Shell Configuration

To apply the changes, I reloaded my shell configuration:

```bash
source ~/.zshrc
```

#### Step 6: Check the Installation

Finally, I checked to see if everything was set up correctly:

```bash
which mkvirtualenv
```

This command showed the path to the `mkvirtualenv` script in my virtual environment, confirming that everything was working.

### Wrapping It Up

Upgrading to Ubuntu 24.04 brought a little challenge with `virtualenvwrapper`, but I learned a lot by solving it. By using a dedicated virtual environment, I kept my system clean and my projects organized. If you run into the same issue, I hope this guide helps you out. Happy coding!