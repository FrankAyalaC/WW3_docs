Preprocessing
=============

# Archivos de entrada

## ww3_grid

### inputs
- ww3_grid.inp 
- archivo de batimetría (.bottom)
- archivo de mallado de obstruccione (.obstr)
- archivo mallada de máscara (.mask)

Los últimos 3 archivos son generados por la herramienta gridgen, por lo que es importante 

### output
- Standard out (Salida formateada del programa)
- mod_def.ww3 (Archivo de definición de modelo en formato WAVEWATCH III.)
- mask.ww3 (Archivo de máscara de tierra-mar (interruptor o2a).)

### Parámetros que se definen
- Frecuencia inicial y factor de incremento de la frecuencia
- número de frecuencias (Información espectral)
- Información de paso de tiempo
- Resolución

## ww3_prep

### inputs
- ww3_strt.inp
- mod_def.ww3

### output
- Standard out
- restart.ww3

### Parámetros que se definen
Define el tipo de archivo inicial con el cual se ejecuta el modelo, elige el **tipo de espectro que se empleara en las condiciones iniciales**

- ww3_prep.inp
- mod_def.ww3

- Standard out
- level.ww3, current.ww3, wind.ww3, ice.ww3
- data0.ww3, data1.ww3,data2.ww3

- Forzadores del modelo
- Magnitudes de la malla
- Se define donde arranca y donde termina (LAT - LON)

- ww3_shel.inp
- mod_def.ww3, level.ww3,
 current.ww3, wind.ww3, ice.ww3,
 restar.ww3
- nest.ww3, data0.ww3, data1.ww3,
 data2.ww3
- track_i.ww3

-Standard out
-log.ww3, test.ww3

restarn.ww3, nestn.ww3
-out_grd.ww3
-out_pnt.ww3

- Ejecución del modelo
- Tiempo de cálculo, cuando
empieza y cuando termina
- Definir el tipo de archivo de salida
del modelo

output del modelo

*se recomienda el uso de ncview y ncdump para la manipulaicón de archivos en formato netCDF*


Gridgen