PyNEMO
======

To be updated soon. This work springboards from the `PyNEMO Project <http://pynemo.readthedocs.io/en/latest/index.html/>`_.

What is this repository for?
----------------------------

How do I get set up?
--------------------

Steps to take to install PyNEMO, creating a specific conda virtual environment is highly recommended. 
`click here for more about virtual enviroments <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html/>`_

- Install Git (outside scope of this readme)
- Clone PyNEMO repository::
    
    $ git clone https://github.com/NOC-MSM/PyNEMO.git 
    
- Install Conda, either Anaconda or Miniconda (outside scope of this readme)
- Create conda environment for PyNEMO::

    $ cd to/PyNEMO/directory
    $ conda env create -f environment_pynemo.yml

- Activate the new virtual environment::

   $ source activate pynemo_env

- Install Jave JRE (outside scope of this readme) and link libjvm.dylib to LD_LIBRARY_PATH variable::

    $ export LD_LIBRARY_PATH=/path/to/java/library/folder/containing/libjvm.dylib:$LD_LIBARY_PATH # see notes below

- Install PyNEMO::
  
    $ cd /location/of/pynemo/repo 
    $ python setup.py build
    $ python setup.py install

This should result in PyNEMO being installed in the virtual environment, and can be checked by entering::  

    $ pynemo -v

Resulting in a help usage prompt::
 
    $ usage: pynemo -g -s <namelist.bdy> 

The virtual environment can be deactivated to return you to the normal prompt by typing::  
    
$ conda deactivate
To reactivate, the following needs to be typed::

    $ source activate pynemo_env


To use PyNEMO, the following command is entered: (the example will run an benchmarking test)::

    $ pynemo -s /path/to/namelist/file (e.g. PyNEMO/inputs/namelist_remote.bdy)

**Additional NOTES** 

For Macbook Pro 2015, macOS Mojave and Java SDK 13 and JRE 8 the following path for the libjvm library should be correct:: 

    /Library/Java/JavaVirtualMachines/jdk-13.0.1.jdk/Contents/Home/lib/server

Resulting in the following command: (this will be different for different java versions and operating systems)::

    $ export LD_LIBRARY_PATH=/Library/Java/JavaVirtualMachines/jdk-13.0.1.jdk/Contents/Home/lib/server:$LD_LIBRARY_PATH

For an iMac 2013, macOS Catalina and JRE 8 only the followinng path was found to be correct::
    
   /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/lib/server
   
With the following command being required to set the environment variable::

    $ export LD_LIBRARY_PATH=/Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/lib/server:$LD_LIBRARY_PATH

The conda environment creation command has not yet been tested. The yml document (can be opened using text editor) gives a list of all the modules and their versions that are required for PyNEMO so a environment can be constructed using this document as reference (or if you use pip!)

**Update** conda environment yaml file has been tested (and works!) on a Macbook Pro 2015 and iMac 2013 running Anaconda 3.7 and Miniconda 3.7 respectively. May need to set::

    export JAVA_HOME="$(/usr/libexec/java_home -v 1.8)"

Contribution guidelines
-----------------------

Bench Marking Tests
-------------------

The PyNEMO module can be tested using the bench marking namelist bdy file in the inputs folder. To check the outputs of the benchmark test, these can be visualised using the plotting script within the test_scripts folder. The following steps are required,

- Run PyNEMO using the namelist file in the inputs folder (namelist_remote.bdy) e.g.::

    $ pynemo -s /path/to/namelist/file

- This will create two output files coordinates.bdy.nc and NNA_R12_bdyT_y1979)m11.nc in an outputs folder

- To check the coordinates.bdy.nc has the correct boundary points, the script bdy_coords_plot.py will plot the domain boundaries and shown the different locations of the rim width (increasing number should go inwards) This script is located in the test_scripts folder.

- The result should look like this (if using the current benchmark data)

.. image:: /screenshots/example_bdy_coords.png
  :width: 800
  :alt: Example BDY coords output

Who do I talk to?
-----------------

* Repo owner or admin

  jdha

* Other community or team contact


For more information regarding the use and development of PyNEMO see: [PyNEMO Wiki](https://github.com/jdha/PyNEMO/wiki)
