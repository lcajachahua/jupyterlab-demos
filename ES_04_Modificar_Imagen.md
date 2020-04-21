
# DEMO: ACTUALIZAR LA VERSIÓN DE R, INSTALAR LIBRERÍAS DE R Y PYTHON Y FINALMENTE EXPORTAR LA IMAGEN PARA COMPARTIR


## ACTUALIZAR EL CONTENIDO DE LA IMAGEN

Para poder actualizar la versión de R (o de cualquier otro componente) basta con levantar la imagen que creamos en el paso anterior, quitando la opción -rm

En Linux:
    $ docker run -it -p 127.0.0.1:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

En Windows
    $ docker run -it -p 192.168.99.100:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

Ingresamos a JupyterLab y abrimos un terminal. Dentro, comprobamos la versión de R.

    $ R --version

Para poder actualizar sólo la versión de R, utilizamos los siguientes comandos:

    $ conda update conda r-base

Se acostumbra ejecutar el comando 'conda update conda' antes de cualquier actualización o instalación.

Para conocer todas las librerías que están actualmente incluidas en la distribución, puede ejecutar el siguiente comando:

    $ conda list

Opcionalmente, puede instalar o actualizar otras librerías del canal 'conda-forge' u otros que usted considere. Utilice el comando install.

    $ conda install -c conda-forge missingno xgboost pytorch-cpu igraph plotly scrapy r-xgboost

Una vez que haya terminado, basta con finalizar docker para que los cambios se guarden en el contenedor. Sin embargo, es necesario trasladar los cambios del contenedor a una imagen para poder exportar luego el contenedor. Primero, listamos los contenedores que tenemos actualmente:

    $ docker ps -a

Esto nos permite conocer el sobrenombre del contenedor. Luego, salvamos los cambios con el comando docker commit:

    $ docker commit <sobrenombre_contenedor> jupyter363

donde jupyter363 será la etiqueta (tag) de la imagen nueva, actualizada.


## EXPORTAR LA IMAGEN PARA COMPARTIR

Finalmente, para poder compartir la imagen, puede exportarla a un archivo con el siguiente comando:

    $ docker save jupyter363 | gzip > jupyter363.tar.gz

Y el archivo resultante (jupyter363.tar.gz) puede ser compartido con otros usuarios o llevado al cluster de producción para su uso.

Otra forma de compartir imagenes es utilizando DockerHub o un servicio de contenedores (on premise o nube).




## INICIAR NUEVAMENTE EL CONTENEDOR


Para poder visualizar los contenedores creados (activos e inactivos), basta con ejecutar el comando:

    $ docker ps -a

Identifique el contenedor que desea activar. Puede utilizar el sobrenombre para iniciarlo:

    $ docker start <sobrenombre_contenedor> 




