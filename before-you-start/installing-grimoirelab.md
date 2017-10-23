## Installing GrimoireLab Python modules

Most of GrimoireLab are Python modules. The easiest way of installing them is using pip, which will retrieve the corresponding packages from the [Python Package Index](https://pypi.python.org/), and will automatically install them, including their dependecies (other Python packages that they need).

Although it is not needed, we recomend using [Python virtual environments](https://docs.python.org/3/tutorial/venv.html) for installing packages. Below, you can find a section on how to prepare vitual packages in Python3, and then how to install GrimoireLab modules in them. If you are not interested in virtual environments, and know what you are doing, you can skip that part. Only remember, in that case, that it is very likely that you will need to prefix with `sudo` any installation command, to install, as root, in the default location in your system, instead of in a virtual environment.

## Preparing a virtualenv

I'm assuming you already have Python3 installed, as detailed in the [Supporting systems](/before-you-start/supporting-systems.md) section. Let's use it to create a Python virtual environment, so that we have a cozy place to work. For that we will use [Python3 venv module](https://docs.python.org/3/library/venv.html).

> _Note:_ Instead of driving the `venv` module directly, you can also use [the pipenv module](http://docs.python-guide.org/en/latest/dev/virtualenvs/#installing-pipenv).

First, let's create our new environment. I like my Python virtual environments under the `venvs` subdirectory in my home directory, and in this case I will call it `grimoirelab` \(see how original I am!\):

```bash
$ python3 -m venv ~/venvs/grimoirelab
```

Once the virtual environment is created, you can  activate it:

```bash
$ source ~/venvs/grimoirelab/bin/activate
(grimoirelab) $
```

Now, any Python module you install in that shell will be installed under ~/venvs/grimoirelab, and it will be used by Python only in shells with the virtual environment activated. Since the virtual environment is under your home directory, you won't need to sudo to install: everything will be installed in your name, with your permissions.

When you are done with a virtual environment, you can deactivate it until you need to activate it again. Deactivating is easy:

```bash
(grimoirelab) $ deactivate
$
```

Remember that the virtual environment will stay activated only in the shell where you activated it. If you are using several shells \(for example, in several windows\), you can activate the virtual environment as in as many of them as you may want. But all of them will share the Python installation, which means that any module installed in the virtual environment will be available in all the shells where that virtual environment is installed.

You can also have several different virtual environments, each with different sets of Python modules installed. You can use them for different projects, with different dependencies, for example. You just need to activate the one you need when you have to work in the corresponding project.

## Installing Perceval

In an activated virtual environment we will use `pip` to install the module from the [Pypi archive](https://pypi.python.org/pypi).

```bash
(grimoirelab) $ pip3 install perceval
```

This will install Perceval and its dependencies \(other Python modules that are needed by Perceval to work\). So, we're ready to see what it can do.

Once Perceval is installed, we can check that the installation went well. For a starter, you can use the `perceval` script, which should have been installed, since it comes with the Perceval package. It is a simple front-end to the Perceval module, which gets data from a data source, and writes what it finds as JSON documents in stdout. To learn about its command line arguments, just use the `--help` flag:

```bash
(grimoirelab) $ perceval --help
```

This should produce a banner with information about command line arguments, and a listing of Perceval backends. If that banner doesn't show up, it is likely that something wrong happened during the installation.

Assuming everything was fine, next thing is getting information about an specific backend. Let's start with the git backend, which will be a good starter for testing:

```
(grimoirelab) $ perceval git --help
```

If this shows a banner with information about how to use the Perceval git backend, we can assume that Perceval and all its dependencies were installed appropriately.