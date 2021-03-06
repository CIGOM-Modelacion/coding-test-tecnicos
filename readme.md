# Coding Test técnico modelación numérica CIGOM

## Tarea: 

El objetivo de esta tarea es ofrecer de una estrategia para la descarga de los datos mas recientes
del modelo numérico operacional [NCOM](https://www.ncei.noaa.gov/products/weather-climate-models/fnmoc-regional-navy-coastal-ocean) región *American Seas*, que produce diariamente un pronostico de 5 días de 
condiciones físicas del océano.

Estos datos se utilizaran para alimentar al modelo numérico de simulación de derrames de petróleo.
De este modelo NCOM solo se requieren descargar los datos en formato [netCDF](https://www.unidata.ucar.edu/software/netcdf/) de las variables 3D que contienen los componentes del vector de velocidad de corrientes. En el conjunto de datos las encuentran por los nombres:

- water_u  (El componente u de los vectores de velocidad)
- water_v  (El componente v de los vectores de velocidad)

Los datos que se descarguen se deben de complementar agregando algunos [atributos asociados a sus variables](https://www.unidata.ucar.edu/software/netcdf/documentation/NUG/netcdf_data_set_components.html#variables), con el 
objetivo de que cumplan con la convención de metadatos [Climate & Forecast v1.8](https://cfconventions.org/Data/cf-conventions/cf-conventions-1.8/cf-conventions.html) (CF), esto es importante para que futuras herramientas
que utilizemos "reconozcan" y sepan a que se refieren estos datos.
En especifico hay que agregar lo siguiente:

Para la variable *lon*
 - axis = 'X'
 - standard_name = 'longitude'

Para la variable *lat*
 - axis = 'Y'
 - standard_name = 'latitude' 

Para la variable *depth*
 - axis = 'Z'
 - standard_name = 'depth' 

Para la variable *time*
 - axis = 'T'

Para la variable *water_u*
 - standard_name = 'x_sea_water_velocity'

Para la variable *water_v*
 - standard_name = 'y_sea_water_velocity'



Al candidato se le solicita, defina una estrategia para descargar el ultimo pronostico del modelo NCOM 
la región American Seas, estos datos están disponibles en un servidor de datos tipo [Thredds](https://www.unidata.ucar.edu/software/tds/current/) en la siguiente ruta:

https://www.ncei.noaa.gov/thredds-coastal/catalog/amseas/amseas_20201218_to_current/catalog.html

La solución ideal es descargar solo las variables de interés, y de esta forma reducir el tamaño de los
datos que se descargaran. Para lo anterior, se recomiendan utilizar alguna de las siguientes
herramientas que utilizan el protocolo [OPENDAP](https://earthdata.nasa.gov/collaborate/open-data-services-and-software/api/opendap) para la descarga de subconjuntos:

- Comandos [NCO](http://nco.sourceforge.net/), el comando [ncks](http://nco.sourceforge.net/nco.html#ncks) para extracciones y [ncatted](http://nco.sourceforge.net/nco.html#ncatted) para editar atributos.
- Operadores [CDO](https://code.mpimet.mpg.de/projects/cdo/wiki/Cdo#Documentation)
- Librería de python [xarray](http://xarray.pydata.org/en/stable/)
- Librería de python [netCDF4](https://unidata.github.io/netcdf4-python/)
- Otra que decida el candidato.

De igual forma para agregar a los datos descargados los atributos necesarios para cumplir con la 
convención de metadatos *CF*, el candidato puede utilizar alguna de las herramientas arriba mencionadas.

Se valorará que la solución se presente a manera de un script que pueda ser reutilizado para la 
descarga de pronósticos diarios, y que se documente la forma de utilizarlo.  El candidato es libre de
utilizar el lenguaje de scripting que el prefiera Ej. bash, batch, python, perl, etc. 

Enviar su solución al correo hmedrano @ cicese.mx


Links de apoyo:


- https://www.ncei.noaa.gov/products/weather-climate-models/fnmoc-regional-navy-coastal-ocean
- https://www.unidata.ucar.edu/software/netcdf/
- https://earthdata.nasa.gov/collaborate/open-data-services-and-software/api/opendap
- https://cfconventions.org/
- http://nco.sourceforge.net/nco.html#ncks
- http://nco.sourceforge.net/nco.html#ncatted
- https://code.mpimet.mpg.de/projects/cdo/wiki/Cdo#Documentation
- http://xarray.pydata.org/en/stable/user-guide/io.html
- https://unidata.github.io/netcdf4-python/
- https://www.opendap.org/support/OPeNDAP-clients
- https://ferret.pmel.noaa.gov/Ferret/


