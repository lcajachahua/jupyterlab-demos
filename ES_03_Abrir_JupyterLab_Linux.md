# Cargar el Contenedor de JupyterLab sobre Docker (Linux)

[Video Instructivo](https://www.youtube.com)

Cambie el path a la carpeta en la que se encuentra el archivo descargado. En mi caso, está en el USB

    $ cd /media/pc/USB

Cargar la Imagen en Docker

    $ docker load -i teradatajupyterlabext_2.0.0-ec03262020.tar.gz


Analicemos dos posibles formas de trabajar con Docker:

1. Cargar la imagen eliminando el contenedor cuando se detenga: Útil para trabajar desde cero sin cambiar el contenido y mantener el disco sin espacio ocupado innecesariamente.

    $ docker run -it --rm -p 127.0.0.1:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

Si elige esta opción, tendrá que ingresar un token nuevo cada vez que cargue la imagen. También se creará un sobrenombre nuevo, el que será eliminado junto al contenedor al finalizar la sesión.

2. Cargar la imagen conservando los cambio en el contenedor cuando se detiene: Útil para conservar los notebooks creados y cambios. También conserva el sobrenombre del contenedor, lo que facilita la carga en lo sucesivo.

    $ docker run -it -p 127.0.0.1:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020




Busque en el código el token que le permita abrir JupyterLab desde el navegador (aparece como http://localhost:8888?token=3237de1ded3314de0eb4de19dd97121d8090d63cdc64345a por ejemplo, el token será diferente en cada caso)


Copie la dirección completa y pegue en un navegador (de preferencia Firefox o Chrome). 

En las siguientes oportunidades que quiera ingresar, basta con levantar el contenedor y colocar en el navegador la siguiente dirección http://localhost:8888/lab 

Si eligió la opción --rm, que elimina el contenedor al finalizar la sesión, debe volver a ingresar el token nuevo que se genera.

Para poder utilizar los Kernels de R, Python y Teradata, vaya a los instructivos correspondientes en la misma carpeta donde encontró este archivo. 



## Para salir de JupyterLab y detener el contenedor


Cierre todos los notebooks en los que haya estado trabajando. Luego puede bajar el Servidor JupyterLab con la opción 'Shutdown' del Menu 'File'. Confirme su elección, presionando el botón que se muestra. Luego, puede cerrar la pestaña o el navegador.


En la ventana de Docker Toolbox, puede utilizar el comando 'docker ps' para ver el nombre del contenedor.

    $ docker ps -a


Si el contenedor de JupyterLab siguiera activo (up) basta con utilizar el comando 'docker stop'

    $ docker stop <sobrenombre_contenedor>


A diferencia de Docker en Windows, en Linux basta con detener los contenedores para finalizar los procesos activos. No hacen falta pasos adicionales.



## Para continuar trabajando en el contenedor

Inicie Docker Toolbox y utilice la opción docker ps para ver el nombre del contenedor de JupyterLab

    $ docker ps -a


Si el contenedor de JupyterLab estuviera inactivo (up) basta con utilizar el comando docker start <nombre_repo>

    $ docker start <sobrenombre_contenedor>


Y en el navegador, sólo debe ingresar la dirección corta: http://localhost:8888/lab Esto abre JupyterLab


Si por algún motivo, se le solicita el Token para poder ingresar, lo puede encontrar en el log del contenedor con el comando docker logs <sobrenombre_contenedor>

    $ docker logs <sobrenombre_contenedor>
    
