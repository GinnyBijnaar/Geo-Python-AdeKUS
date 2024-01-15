Installing Python
=================

In order to do programming with Python on your own computer, you need to install Python.

The purpose of this page is to help you to install Python and different Python packages into your own computer.
Even though it is possible to install Python from the `Python homepage <https://www.python.org/>`_, **we highly recommend using** `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`_ to install Python.
Miniconda comes with Python and a small number of essential packages.
Additional packages can be installed using the package management system `conda <https://docs.conda.io/en/latest/>`__.


Miniconda is a light-weight version of `Anaconda <https://www.anaconda.com/>`_ which is an open source distribution of the Python and R programming languages for large-scale data processing, predictive analytics, and scientific computing, that aims to simplify package management and deployment.
In short, it makes life much easier when installing new tools for use in Python.
The full anaconda installation comes with all packages needed in the Geo-Python course (and much more!),
but Miniconda allows us to save some disk space and avoid package conflicts (important for those installing GIS packages!).

In case you already have Anaconda installed on your computer, you can continue using that during the Geo-Python course without a problem. **However, if you are new to Python and have not yet installed anything,** we recommend you start by installing `Miniconda  <https://docs.conda.io/en/latest/miniconda.html>`_ on your computer.


Install Miniconda
-----------------

You can find several versions of Miniconda for different operating systems on the `Miniconda dowload page <https://docs.conda.io/en/latest/miniconda.html>`__.
Details on the installation for Windows, macOS and Linux users below.

.. note::

    Although some of the screenshots below highlight download links for older versions of Python, we recommend using **Miniconda based on Python 3.10 for this course**.

Windows
~~~~~~~

To install Miniconda, visit the `Miniconda download page <https://docs.conda.io/en/latest/miniconda.html#windows-installers>`__ and download the **Miniconda3 Windows 64-bit** installer for Windows.

.. figure:: img/miniconda-windows.png
    :width: 600px
    :align: center
    :alt: Downloading Miniconda for Windows

Install Miniconda to your computer by double clicking the installer and install it into a directory you want (needs admin rights).
Install it for **all users** and use default settings.

After the installation is completed, test that the package manager ``conda`` works by
`opening a command prompt as an admin user <http://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/>`_
and running command ``conda --version``. If the command returns a version number of conda (e.g. ``conda 4.10.3``) everything is working correctly.


Installing the Geo-Python packages
----------------------------------

As noted above, we will be using the conda package installer to manage the installation of Python packages in Miniconda.
To do this, we must download some Python environment files that contain the list of packages used in the Geo-Python course.
This will ensure the Python environment on your computer is the same for everyone in the course.
The steps for installing the Geo-Python packages are below.



Downloading the Python environment files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The files needed for creating the Geo-Python environment can be `found on GitHub <https://github.com/geo-python/python-environments/>`__.

**If you are already familiar with using git**, you can clone the repository containing the files by typing

.. code-block:: bash

    # Clone Geo-Python environment files
    git clone https://github.com/geo-python/python-environments/

**If you are not familiar with git**, you can visit the `GitHub repository with the environment files <https://github.com/geo-python/python-environments/>`__, click on the green **Code** button, and select **Download ZIP** to download a copy of the files.

.. figure:: img/python-environment.png
    :width: 600px
    :align: center
    :alt: Downloading the python-environments files

After downloading the files, extract the zip file to your computer.

Installing the packages (student)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once you have obtained the code (either by cloning with git or downloading otherwise) can return to your terminal window, change to the directory where you have downloaded the files and create the environment as shown below.
For example, on macOS or Linux you would do the following.

.. code-block:: bash

    # Change to directory containing environment files
    cd python-environments
    
    # Create the environment using mamba
    conda env create -f inl_inf_student.yml

    # Activate the new environment and update Jupyter
    # NOTE: conda is used to activate an environment!
    conda activate inl_inf_student
    sh postBuild

This creates a new Python virtual environment called ``inl_inf_student``, which contains the packages listed in the file ``inl_inf_student.yml``. The new environment is helpful because it will be isolated from other Python packages you might install on your computer and ensure you have all of the packages needed for this course. Finally, the last steps will ensure that the Jupyter environment in the new Python installation has all of its extensions enabled (such as ``jupyterlab-git``).

To use the environment (since it will not be the default environment on your computer) you should type something like the following whenever you open a terminal window to use Python.

.. code-block:: bash

    # Activate the your Python environment
    conda activate inl_inf_student
    

Running JupyterLab
------------------

We use `JupyerLab <https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html>`__ as the main developing environment during this course.

you can start a JupyterLab instance by running this command (notice the space between the words!):

.. code-block:: bash

    jupyter lab

After running the command, JupyterLab should open up automatically in a browser window.

Getting the lesson notebooks
----------------------------

In order to be able to follow the course lessons it may also be helpful to have a copy of the course notebooks.
You can download a copy of the course notebooks from `<https://github.com/geo-python/notebooks.git>`_ by clicking on the **Code** button and then selecting **Download ZIP**.
Alternatively, once you are familiar with git, you can clone the course notebook repository by typing

.. code-block:: bash

    git clone https://github.com/geo-python/notebooks.git

The command above will clone the notebook files into a directory titled ``notebooks``.

Additional notes
----------------

You can install new packages using the `mamba install <https://mamba.readthedocs.io/en/latest/user_guide/mamba.html>`__ command.
The basic syntax for installing packages is ``mamba install package-name``.
In addition, we also want to specify the **channel** from where the package is downloaded using the parameter ``-c``.

**Installing the pandas package from the conda-forge channel:**

.. code-block:: bash

    mamba install -c conda-forge pandas

Once you run this command, you will see also other packages getting installed and/or updated as mamba checks for dependencies of the installed package.
Read more about package installations in the `mamba documentation <https://mamba.readthedocs.io/en/latest/advanced_usage/detailed_operations.html>`__
It's a good idea to search for installation instructions for each package online.

.. admonition:: Conda channels

    `Conda channels <https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html>`__ used by mamba and are remote locations where packages are stored.
    During this course (and in general when installing packages for scientific computing and GIS analysis) we download most packages from the `conda-forge <https://conda-forge.org/#about>`__ channel.

.. admonition:: Conflicting packages

    A good rule of thumb is to **always install packages from the same channel** (for this course, we prefer the ``conda-forge`` channel).
    In case you encounter an error message when installing new packages, you might want to first check the versions and channels of existing
    packages using the `mamba list` command before trying again.
