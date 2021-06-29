Setting up the environment
==========================

WAVEWATCH III permite que los resultados obtenidos sean exportados en formato NetCDF-4. Para esto se deben verificar las versiones de la librería NETCDF instalada, así:

VERIFICACION

Cuando se ha verificado lo anterior, se crean las siguientes variables de entorno:

Si tiene NetCDF-3:

* ``WWATCH3_NETCDF= NC3``

Si tiene NetCDF-4:

* ``WWATCH3_NETCDF= NC4``
* ``NETCDF_CONFIG``: es la ruta a NetCDF-4 nf-config utility program, regularmente es la carpeta ``bin``  en el que está construído la librería NETCDF


Estas variables de entorno se puedene definir de dos formas:

#. Escribir en la terminal:


.. code-block:: bash

    export WWATCH3_NETCDF=NC4
    export NETCDF_CONFIG=ruta/a/la/carpeta/bin/de/netcdf


Esto crea de forma temporal las variables mencionadas anteriormente 

#. Se debe buscar en el directorio ``HOME`` un archivo llamado ``.bashrc``. Este archivo *Qué es?*. En él se deben escribir las siguientes líneas

.. code-block:: bash

    export WWATCH3_NETCDF=NC4
    export NETCDF_CONFIG=ruta/a/la/carpeta/bin/de/netcdf

y luego compilarlo así:

.. code-block:: bash

    source ~/.bashrc


.. note:: 
	Si usa otra tipo de terminal, más ergonómica o tuneable que *bash*, debe buscar su archivo homónimo, por ejemplo: si tiene oh-my-zsh el archivo es `.zshrc`


