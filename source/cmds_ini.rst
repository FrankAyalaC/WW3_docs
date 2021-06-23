Comandos iniciales
==================


*******************
Ejecutando el setup
*******************

Estando en la carpeta WW3, se debe scribir la siguiente línea en la terminal.

.. code-block:: bash

	cd ruta/a/WW3
	./model/bin/w3_setup model

Este comando ejecutará las siguientes acciones:

Preguntará por los programas previos que se necesitan para WAVEWATHCIII, como sigue:

* Compilador de Fortran 
* Compilador de C++
* Printer
* Ruta scratch
* Ruta temporal

Después de las preguntas correrá la instalación de programas auxiliares, ejecutando los codigos en FORTRAN usando el compilador elegido. Después de la compilación de estos programas auxiliares se crean algunos archivos en el carpeta .model/aux o .model/bin

* ``w3adc.f``: WAVEWATCH III FORTRAN preprocessor.
* ``w3prnt.f``: Print files (source codes) including page and line numbers.
* ``w3list.f``: Generate a generic source code listing.
* ``w3split.f``: Creará el archivo de configuración del entorno ``wwatch_env`` a partir del setup. Este script crea/edita el archivo de configuración del entorno de WAVEWATCH III
  

``wwatch3.env`` será creado en la carpeta ``bin`` y alojará las configuraciones que tendrá el modelo para cuando se compile. Este archivo puede ser re-editado volviendo a ejecutar el programa ``w3_setup`` o editandolo manualmente.

Adicionalmente en el directorio ``model`` deben aparecer los siguientes directorios:

* ``exe``: WAVEWATCH III executables.
* ``mod``: Module files.
* ``obj``: Object files.

.. note:: 
	Esta confguración no reemplaza las configuraciones que cada usuario debe realizar para ejecutar sus casos específicos. Solo representa una configuración inicial


************************
Obteniendo los regtests
************************

Estando en la carpeta WW3, se debe escribir la siguiente línea en la terminal.

.. code-block:: bash

    ./model/bin/ww3 from ftp.sh

Este comando se utiliza para obtener archivos de gran tamaño que no están almacenados en el repositorio de Git.

Al ejecutarla aparecen dos carpetas en el directorio superior:

* ``data_regtests``: contiene toda la información de los regtests
* ``cases``:

Un regtest en WAVEWATCH es un caso base creado para que los usarios del modelo se familiaricen

***************
Errores comunes
***************

* Escribir mal las rutas
* No tener algunas librerías necesarias instaladas


Todos siguen la misma línea:

.. code-block:: bash

    w3_setup /home/user/WW3/model -c <comp> -s <switch>
