OWA simulations in BOCHICA
==========================

Initial folders
***************

Initially, a folder havo to be created where the coupled simulation will be executed (WORKDIR). This folder have to be in the ``runs`` directory:

.. code-block:: bash
	mkdir owa_HURRICANE_NAME
	cd owa_HURRICANE_NAME

3 subfolders must be created/copied in this directory:

	1. ``input_files``: is a folder where the initial croco and wrf files must be putted.

.. code-block:: bash
	mkdir input_files
	cp path/to/wrf/files/* input_files/.
	cp path/to/croco/files/* input_files/.

	2. ``exec_files``: is a folder where all executable files to prepare the coupled simulation are hosted. This folder is in the root directory of the user

.. code-block:: bash
	cp -r ~/exec_files/ .

.. note:: 
	In this directory there is a subfolder with the executable files for the coupled run from a local machine (``exec_from_local``). This folder must be copied to the local machine in order to execute them there.

	3. An empty folder where will be the final files before to launch the simulation

.. code-block:: bash
	mkdir cpl_files

Running executables
*******************

It must be edited ``init.sh`` file according to the folder initially created. This file is executed after all necessary modifications:

.. code-block:: bash
	./exec_files/init.sh

In the local machine must be created a similar folder to ``owa_HURRICANE_NAME`` like this:

.. code-block:: bash
	mkdir owa_HURRICANE_NAME
	cd owa_HURRICANE_NAME

A folder with the initial batimethric files must be created in ``owa_HURRICANE_NAME``, these files are copied for the original directory.

.. code-block:: bash
        mkdir input_files_ww3
        cp path/to/bath/files/* input_files_ww3/.

Inside this directory it is also copied the folder with the executable files aforementioned. The first file to edit is ``convert_wrf_and_croco_input.sh`` according the required settings. After this, ``convert_wrf_and_croco_input.sh`` must be runned in order to preprare the input files to the noncoupled simulation of ww3:

.. code-block:: bash
	sshpass -f ~/pass_file scp -r ffayalac@168.176.123.121:exec_files/exec_from_local/ .
	mv exec_from_local/* .
	rm -rf exec_from_local
	./convert_wrf_and_croco_input.sh

The non coupled simulation is generated in the cluster and it is used to obtain the ww3 initial file via ``frc_ww3.sh`` bash script. This initial file is later employed to generate the initial OASIS files. Please edit the script according to the requirements:

.. code-block:: bash
	./exec_files/frc_ww3.sh

Subsequently, another file in the local machine is executed. With ``./prep_oasis_files.sh`` script are created the initial files for OASIS (``wav.nc`` and ``atm.nc``). Edit it and run it like this:

.. code-block:: bash
	./prep_oasis_files.sh

In order to set-up the required files to launch the coupled run, it must be edited the ``owa_files.sh``script and later it is executed:

.. code-block:: bash
	./exec_files/owa_files.sh

Finally, the coupled simulations is launched after to edit the ``submit.pbs``

.. code-block:: bash
	qsub exec_files/submit_owa.pbs
