# Cargar el Contenedor de JupyterLab sobre Docker (Windows)

[Video Instructivo](https://www.youtube.com)

Crear una Carpeta llamada 'Lab' en la raíz de C:/ 


Mover el archivo  de la carpeta de Descargas a C:/Lab


Abrir Docker Toolbox. Fijese en la IP que aparece al inicio de la cabecera, junto al dibujo de la ballena (normalmente es 192.168.99.100)


Buscar la ruta en la que se encuentra

    $ pwd


Moverte a la carpeta C:/Lab

    $ cd /c/Lab


Cargar la Imagen en Docker

    $ docker load -i teradatajupyterlabext_2.0.0-ec03262020.tar.gz


Analicemos dos posibles formas de trabajar con Docker:

1. Cargar la imagen eliminando el contenedor cuando se detenga: Útil para trabajar desde cero sin cambiar el contenido y mantener el disco sin espacio ocupado innecesariamente.

    $ docker run -it --rm -p 192.168.99.100:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

Si elige esta opción, tendrá que ingresar un token nuevo cada vez que cargue la imagen. También se creará un sobrenombre nuevo, el que será eliminado junto al contenedor al finalizar la sesión.

2. Cargar la imagen conservando los cambio en el contenedor cuando se detiene: Útil para conservar los notebooks creados y cambios. También conserva el sobrenombre del contenedor, lo que facilita la carga en lo sucesivo.

    $ docker run -it -p 192.168.99.100:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext




Busque en el código el token que le permita abrir JupyterLab desde el navegador (aparece como http://localhost:8888?token=3237de1ded3314de0eb4de19dd97121d8090d63cdc64345a por ejemplo, el token será diferente en cada caso)


Copie la dirección completa y pegue en un navegador (de preferencia Firefox o Chrome). Remplace la palabra 'localhost' por la IP que le haya aparecido al iniciar docker (la dirección debería quedar como http://192.168.99.100:8888?token=3237de1ded3314de0eb4de19dd97121d8090d63cdc64345a) y presione ENTER


En las siguientes oportunidades que quiera ingresar, basta con levantar el contenedor y colocar en el navegador la siguiente dirección http://192.168.99.100:8888/lab (La IP corresponde a la que esté usando Docker). Si eligió la opción --rm, que elimina el contenedor al finalizar la sesión, debe volver a ingresar el token nuevo que se genera.


Para poder utilizar los Kernels de R, Python y Teradata, vaya a los instructivos correspondientes en la misma carpeta donde encontró este archivo. 



## Para salir de JupyterLab y detener el contenedor


Cierre todos los notebooks en los que haya estado trabajando. Luego puede bajar el Servidor JupyterLab con la opción Shutdown del Menu File. Confirme su elección, presionando el botón que se muestra. Luego, puede cerrar la pestaña o el navegador.


En la ventana de Docker Toolbox, puede utilizar el comando 'docker ps' para ver el nombre del contenedor.

    $ docker ps -a


Si el contenedor de JupyterLab siguiera activo (up) basta con utilizar el comando 'docker stop'

    $ docker stop <sobrenombre_contenedor>


Luego de verificar que el contenedor ya está abajo, puede detener VirtualBox con el siguiente comando:

    $ docker-machine stop


Una vez que se haya detenido la máquina 'default', usted puede cerrar Docker Toolbox. Otra forma de salir, es digitar el comando 'exit', que cierra la ventana de la aplicación.

    $ exit



## Para continuar trabajando en el contenedor

Inicie Docker Toolbox y utilice la opción docker ps para ver el nombre de los contenedores de JupyterLab (activos e inactivos)

    $ docker ps -a


Si el contenedor de JupyterLab estuviera inactivo (up) basta con utilizar el comando docker start <sobrenombre_contenedor>

    $ docker start <sobrenombre_contenedor>


Y en el navegador, sólo debe ingresar la dirección corta: http://192.168.99.100:8888/lab Esto abre JupyterLab


Si por algún motivo, se le solicita el Token para poder ingresar, lo puede encontrar en el log del contenedor con el comando docker logs <nombre_repo>

    $ docker logs <sobrenombre_contenedor>

Nunca olvide detener la máquina virtual antes de salir de Docker. El no detener la VM podría generar errores graves sobre los contenedores y también inconvenientes al momento de apagar la PC.

    $ docker-machine stop

