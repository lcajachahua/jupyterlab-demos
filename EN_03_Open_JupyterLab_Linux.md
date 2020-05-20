# Open the JupyterLab Image in Docker (Linux)

[Video in Youtube](https://www.youtube.com/watch?v=6X2JaXfxKoU)  
[![](http://img.youtube.com/vi/6X2JaXfxKoU/0.jpg)](http://www.youtube.com/watch?v=6X2JaXfxKoU "Open JupyterLab in Ubuntu")

Change the path to the folder where the downloaded file is located. In my case, it's on the USB key.

    $ cd /media/pc/USB

Load Imagen in Docker

    $ docker load -i teradatajupyterlabext_2.0.0-ec03262020.tar.gz

Let's discuss two possible ways of working with Docker:

1. Load the image by removing the container when it stops: Useful for working from scratch without changing the content and keeping the disk without unnecessary space occupied.

    $ docker run -it --rm -p 127.0.0.1:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

If you choose this option, you will have to enter a new token every time you load the image. A new nickname will also be created, which will be removed next to the container at the end of the session.

2. Load the image keeping the changes in the container when stopped: Useful to keep the created notebooks and changes. It also retains the nickname of the container, making it easier to load from now on.

    $ docker run -it -p 127.0.0.1:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

Look in the code for the token that allows you to open JupyterLab from the browser (it appears as http://localhost:8888?Token=3237de1ded3314de0eb4de19dd97121d8090d63cdc64345a for example, the token will be different in each case)

Copy the full address and paste into a browser (preferably Firefox or Chrome).

In the following opportunities that you want to enter, just lift the container and put the following address in the browser: http://localhost:8888/lab

If you chose the --rm option, which removes the container at the end of the session, you must re-enter the new token that is generated.

In order to use the R, Python and Teradata Kernels, go to the corresponding instructions in the same folder where you found this file.


## To exit JupyterLab and stop the container

Close all notebooks you have been working with. Then, you can download the JupyterLab Server with the 'Shutdown' option from the 'File' Menu. Confirm your choice by pressing the button shown. Then you can close the tab or the browser.

In the Docker Toolbox window, you can use the command 'docker ps' to see the name of the container.

    $ docker ps -a

If the JupyterLab container is still active (up) you can use the command 'docker stop'

    $ docker stop <container_nickname>

Unlike Docker in Windows, in Linux it is enough to stop the containers to end the active processes. No additional steps are required.


## To continue working on the container

Launch Docker Toolbox and use docker ps option to view JupyterLab container name

    $ docker ps -a

If the JupyterLab container is inactive (up), just use the command 'docker start <container_nickname>'

    $ docker start <container_nickname>

And in the browser, just enter the short address: http://localhost:8888/lab This opens JupyterLab

If for any reason, the Token is requested to enter, you can find it in the container log with the command docker logs <container_nickname>

    $ docker logs <container_nickname>
    
