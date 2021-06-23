Prerequisites
=============

* Fortran compiler on linux
* C++ compiler on Linux
* netCDF library
* MPICH library

*************************
Fortran and C++ compilers
*************************

First and foremost, it is very important to have a Fortran and C++ compiler (gcc, cpp, etc.). We recommend gfortran and gcc. To test whether these exist on the system, type the following:


.. code-block:: bash

	which gfortran
	which cpp
	which gcc

If you have these installed, you should be given a path for the location of each. If you dont have you can install them from your terminal:

.. code-block:: bash

    sudo apt install build-essential
    sudo apt-get install gfortran

or

.. code-block:: bash
	
	sudo apt-get install gcc gfortran

These commands should install the latest versions of gfortran and gcc available for your system. To determine the versions of your libraries you have, type:

.. code-block:: bash

	gcc --version
	gfortran --version
	cpp --version

*****************
Installing netCDF
*****************


It's possible to install netCDF directly from snap on the ubuntu terminal with :literal:`sudo apt-get install libnetcdf-dev libnetcdff-dev` (this would download the lastest version netCDF), however this opction could bring problems at the moment to coupling WW3 with WRF troughout OASIS. The main reason is the 3 models must be compiled with the same netCDF version,  and the lastest version netCDF seems to be conflicting with older WRF versions (v3.7.1) used in this documentation.

It is recommended to install netCDF-Fortran and netCDF-C manually, to do this first it woul be installed 2 dependeces: zlib and hdf5. These libraries together with libpng and jasper libraries will be used for the WRF compiling.

Installing dependences
----------------------

Before getting started, you must move into to the folder that contain WRF model directory and to type. 

mkdir -p Build_WRF/Libraries

The command -p will create parent directory first if it doesn't exist, i.e ``Build_WRF`` and then will create the folder ``Libraries`` where will be installed the libraries.

Add the following enviroment variables to your bash profile. In our case, the bash profile is ``.zshrc``, this file is normally in ``home`` folder and you can easily edit it. 

.. code-block:: bash

	export DIR=/home/franklin/Documentos/WRF/Build_WRF/Libraries
	export CC=gcc
	export CXX=g++
	export FC=gfortran
	export FCFLAGS=-m64
	export F77=gfortran
	export FFLAGS=-m64

and type the following command to upload the change sin bash profile:

.. code-block:: bash

    sourde ~/.zshrc

The firt library to be installed is zlib. zlib is a library used to SOMETHING. Go to the `zlib oficial page <https://zlib.net/>`_  and download the suorce files to the installation (file .tar) in ``Libraries`` directory . In our case, we choose the version 1.2.8. In your terminal type the following:

.. code-block:: bash

	cd $DIR
	tar xvf zlib-1.2.8.tar.gz
	./configure --prefix=$DIR/grib2; make clean; make all install 
	cd ..

The folder in ``$DIR/grib2`` is the folder where will be installed and we explain it.

The other library, hdf5 is used in SOMETHING. HDF5 is available from the `HDF5 downloads site <https://www.hdfgroup.org/downloads/hdf5/>`_ . Our version installed is 1.8.13 and the installing process is similar to the zlib

.. code-block:: bash

	tar xvf hdf5-1.8.13.tar.gz
	cd hdf5-1.8.13
	./configure --prefix=$DIR/grib2 --with-zlib=$DIR/grib2; make clean; make all install
	cd ..

the command --with-zlib link the hdf5 with zlib library.

If you go to the grib2 directory, and you type ``ls`` in your terminal, you could get something like this:

.. code-block:: bash

	libhdf5.a     libhdf5_hl.la  libhdf5_hl.so.8      libhdf5.la        libhdf5.so    libhdf5.so.8.0.2  libz.so    libz.so.1.2.8
	libhdf5_hl.a  libhdf5_hl.so  libhdf5_hl.so.8.0.2  libhdf5.settings  libhdf5.so.8  libz.a            libz.so.1  pkgconfig


Building netCDF
---------------

netCDF library is used widely for the meteorological and oceanic data. In versions before 4.2, the Fortran netCDF library source (netCDF-Fortran) was bundled with the C library source (netCDF-C) in one distribution. With more recent versions, the Fortran netCDF library has been split off into an independent source distribution, intended to be built as a separate library, after the C library is built and installed. 

We decide to install 4.1.3 version, but you can install a newer version if you want it.

.. hint:: We recommend a library where NetCDF-4/HDF-5 is enabled. 

To install the version above mentioned, visit the `netCDF downloads site <https://www.unidata.ucar.edu/downloads/netcdf/>`_ and get your .tar file. Then, type:

.. code-block:: bash

    tar xvf netcdf-4.1.3.tar.gz
    cd netcdf-4.1.3
    LDFLAGS=-L$DIR/grib2/lib CPPFLAGS=-I$DIR/grib2/include ./configure --prefix=$DIR/netcdf; make clean; make all install
    cd ..

You can test if your netCDF library were well built typing these command lines in your terminal:

.. code-block:: bash

	wget https://www.unidata.ucar.edu/software/netcdf/examples/programs/simple_xy_wr.f90
	gfortran simple_xy_wr.f90 -o test_nc.exe -I$NETCDF/include -L$NETCDF/lib -lnetcdff
	./test_nc.exe

This should print: 

.. code-block:: none

        0          12          24          36
 	SUCCESS writing example file simple_xy.nc!

There is a lot of available tools to check, pre-visualizate and manipulate data content in .nc files. ``ncdump`` is one of them and can be installed with the commands:

.. code-block:: bash

	sudo apt install netcdf-bin

if you type: 

.. code-block:: bash

    ncdump -h simple_xy.nc

This print information about the .nc file: 

.. code-block:: none

	netcdf simple_xy {
	dimensions:
      	x = 6 ;
      	y = 12 ;
	variables:
      	int data(x, y) ;
	}

Finally, its important to verify that the installed version has netCDF4, to do it, move into ``bin`` directory in ``$NETCDF`` and type:

.. code-block:: bash

    ./nc-config --has-nc4

If the terminal print: **yes**, then all is working perfectly!

Installing MPICH
----------------
MPICH library is necessary if you are planning to build WW3 in parallel and to couple WW3 with WRF. If your machine does not have more than 1 processor, or if you have no need to run WW3 with multiple processors, you can skip this section.

To install this library: 

.. code-block:: bash

    sudo apt install mpich

if was correctly installed, the you can type: 

.. code-block:: bash

    which mpirun

you should be given a path for the location of each.

./ungrib.exe: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory

 When the coupling 

.. code-block:: bash

	cd /your_software/../lib/ (the directory containing libz.so.1)
	mv libz.so.1 libz.so.1.old
	ln -s /lib/x86_64-linux-gnu/libz.so.1

The solution were found in this `stackoverflow questions <https://stackoverflow.com/questions/48306849/lib-x86-64-linux-gnu-libz-so-1-version-zlib-1-2-9-not-found>`_