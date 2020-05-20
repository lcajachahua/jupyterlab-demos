# Open the JupyterLab Image in Docker (Windows)

[Video in Youtube](https://www.youtube.com/watch?v=6UGWn11RllM)  
[![](http://img.youtube.com/vi/6UGWn11RllM/0.jpg)](http://www.youtube.com/watch?v=6UGWn11RllM "Open Jupyterlab in Windows")

Create a folder named 'Lab' in C:/ 

Move the file from the Downloads folder to C:/Lab

Open Docker Toolbox. Look at the IP that appears at the beginning of the header, next to the drawing of the whale (usually it is 192.168.99.100)

Find the path you are on

    $ pwd

Move to C:/Lab

    $ cd /c/Lab

Load the Docker Image

    $ docker load -i teradatajupyterlabext_2.0.0-ec03262020.tar.gz

Let's discuss two possible ways of working with Docker:

Load the image by removing the container when it stops: Useful for working from scratch without changing the content and keeping the disk without unnecessary space occupied.

    $ docker run -it --rm -p 192.168.99.100:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

If you choose this option, you will have to enter a new token every time you load the image. A new nickname will also be created, which will be removed next to the container at the end of the session.

Load the image keeping the changes in the container when stopped: Useful to keep the created notebooks and changes. It also retains the nickname of the container, making it easier to load from now on.

    $ docker run -it -p 192.168.99.100:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext

Look in the code for the token that allows you to open JupyterLab from the browser (it appears as http://192.168.99.100:8888?token=3237de1ded3314de0eb4de19dd97121d8090d63cdc64345a for example, the token will be different in each case)

Copy the full address and paste into a browser (preferably Firefox or Chrome). Replace the word 'localhost' with the IP that appeared when starting docker (the address should be as http://192.168.99.100:8888?token=3237de1ded3314de0eb4de19dd97121d8090d63cdc64345a) and press ENTER

In the following opportunities that you want to enter, just lift the container and put the following address in the browser: http://192.168.99.100:8888/lab (The IP corresponds to the one that Docker is using). If you chose the --rm option, which removes the container at the end of the session, you must re-enter the new token that is generated.

In order to use the R, Python and Teradata Kernels, go to the corresponding instructions in the same folder where you found this file.

## To exit JupyterLab and stop the container

Close all notebooks you have been working on. Then you can download the JupyterLab Server with the Shutdown option from the Menu File. Confirm your choice by pressing the button shown. Then you can close the tab or the browser.

In the Docker Toolbox window, you can use the command 'docker ps' to see the container nickname.

    $ docker ps -a

If the JupyterLab container is still active (up) just use the command 'docker stop'

    $ docker stop <container_nickname>

After verifying that the container is already down, you can stop VirtualBox with the following command:

    $ docker-machine stop

Once the 'default' machine has stopped, you can close the Docker Toolbox. Another way to exit is to type the command 'exit', which closes the application window.

    $ exit

## To continue working on the container

Start Docker Toolbox and use docker ps option to see the name of JupyterLab containers (active and inactive)

    $ docker ps -a

If the JupyterLab container is inactive (up), just use the command 'docker start <container_nickname>'

    $ docker start <container_nickname>

And in the browser, just enter the short address: http://192.168.99.100:8888/lab This opens JupyterLab

If for some reason the Token is requested to enter, you can find it in the container log with the command 'docker logs <container_nickname>'

    $ docker logs <container_nickname>

Never forget to stop the virtual machine before exiting Docker. Failure to stop the VM could cause serious errors on the containers and also problems when shutting down the PC.

    $ docker-machine stop
