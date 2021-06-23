Obtener el modelo
=================


*******************
Descargar WAVEWATCH
*******************

WAVEWATCHIII v6.07 es un modelo de oleaje de tercerga generación, su documentación, así como todas sus demás características están alojas en la plataforma Github. Github es un portal para alojar (hostear) proyectos que utilizan el sistema de control de versiones, Git. Es importante saber que al ser de carácter público, la comunidad Github puede no sólo clonar información de los proyectos (repositorios) alojados, sino también aportar al desarrollo desde la creación de nuevas características como el manejo de errores (bugs)
 
Se recomienda revisar la información del repositorio en el `repositorio de WW3 <https://github.com/NOAA-EMC/WW3>`_ (hablar de los releases).


Para más información leer Github (enlace a otro .rst interesante)

Clonar el repositorio de WAVEWATCHIII implica hacer una copia del proyecto desde Gthub. Para clonar se escribe el siguiente comando en la terminal desde el directorio dónde se esea descargar WW3, debe estar git instalado (en linux/ubuntu viene por defecto):

.. code-block:: bash

	git clone https://github.com/NOAA-EMC/WW3	


Lo anterior descargará una carpeta llamada WW3 en el directorio donde se clonó. Esta carpeta contiene la siguiente estructura:

* ``manual``:
* ``model``:
	* ``bin``: Esta carpeta contiene los programas necesarios para la compilación de WAVEWATCH (reccordar que los programas en bash son ejecutados con un ``.`` antes de la ruta)  
	* ``aux``:
* ``regtests``:
* ``guide``
* ``smc_docs``:

En este directorio queda una carpeta oculta que llamada .git, esta carpeta es creada por defecto cuando se tiene una carpeta como repositorio de Github. un archivo de licencia, un archivo .gitignore y otro README.md


*******
Gridgen
*******

Gridgen es un programa escrito en MATLAB para la creación de los archivos relacionadas a la batimetría, obstrucciones y máscaras empleados en WAVEWATCH, también está alojado en la plataforma Gtihub y puede ser obtenido así:

.. code-block:: bash

	git clone https://github.com/NOAA-EMC/gridgen
	

