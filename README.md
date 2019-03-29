# :snake: Managing Packages in Conda Virtual Environments
A straightforward how-to guide for managing Python packages in conda virtual environments for use in [Jupyter Notebook](http://jupyter.org/).

*NOTE: Execute the code snippets below in your terminal of choice, making sure to replace anything between `< ... >` with the relevant info for your set-up.*

## Basic Workflow
This workflow assumes you have a functioning installation of [Anaconda](https://www.anaconda.com/download/) and have [created a conda virtual environment](https://conda.io/docs/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands) within which you would like to install additional packages.

This workflow also assumes that you have installed `pip` to the virtual environment you are working with. If this is not the case, follow the instructions below to first install `pip` (using the `conda install` option in step 2).

1. Activate the virtual environment you are working in:

   For Mac terminal or Git Bash:\
   `source activate <virtual_environment_name>`

   For Anaconda Prompt:\
   `activate <virtual_environment_name>`

2. Install the package using conda if possible:\
   `conda install <package_name>`

   If the package is not available via conda, install it using pip:\
   `pip install <package_name>`

   *NOTE: either method installs the package only in your activated virtual environment.*

3. [Optional] Launch jupyter notebook with your virtual environment still activated:\
`jupyter notebook`

   *NOTE: if you only see 1 kernel in your notebook, this is the kernel for the virtual environment that is activated and will include all packages installed to that environment. If you see multiple kernels, make sure to select the one associated with the virtual environment that you want to use.*

## Advanced Workflow
Certain libraries require more complicated installation procedures. It is always a good idea to refer to the package's own installation documentation and follow their recommended steps.

*NOTE: typically, you would replace Step 2 of the Basic Workflow above with the package's recommended installation steps to ensure that you are installing to the desired virtual environment.*

As an example, consider the [gmaps](https://jupyter-gmaps.readthedocs.io/en/stable/index.html) package. By referring to the [gmaps installation documentation](https://jupyter-gmaps.readthedocs.io/en/stable/install.html), we can modify the Basic Workflow as follows:

1. Activate the virtual environment you are working in:\
   `source activate <virtual_environment_name>`

2. Follow the gmaps-specific installation instructions.

   Make sure that you have enabled ipywidgets widgets extensions:\
   `jupyter nbextension enable --py --sys-prefix widgetsnbextension`

   You can then install gmaps with:\
   `pip install gmaps`

   Then tell Jupyter to load the extension with:\
   `jupyter nbextension enable --py --sys-prefix gmaps`

3. [Optional] Launch jupyter notebook with your virtual environment still activated:\
`jupyter notebook`

## Troubleshooting
Here are some useful commands for troubleshooting when things go squirrely.

Q: What virtual environments do I have and which one am I in?\
A: List all virtual environments and their directories (the activated environment is indicated with a * in the print out):\
`conda info --envs`

Q: How do I know what packages I have installed?\
A: List all the packages and their versions for a specific environment:\
`conda list -n <virtual_environment_name>`

Q: How do I know if I have a specific package installed?\
A: Look in a specific environment for a specific package:\
`conda list -n <virtual_environment_name> <package_name>`
