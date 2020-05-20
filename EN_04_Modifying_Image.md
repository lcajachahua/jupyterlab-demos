# Modify the JupyterLab Image

[Video in Youtube](https://www.youtube.com/watch?v=mSp9EBr9Xr0)  
[![](http://img.youtube.com/vi/mSp9EBr9Xr0/0.jpg)](http://www.youtube.com/watch?v=mSp9EBr9Xr0 "Modifying a Docker Image")

In this Guide, we give an example of how to make modifications and maintain changes. Specifically we are going to update the R version, install some additional libraries and export the entire updated environment to a new image, which can then be shared with other developers or sent to the production environment for use.

## Update components and install new libraries

To be able to update the version of R (or any other component), just raise the image that we created in the previous step, removing the -rm option

On Linux:

    $ docker run -it -p 127.0.0.1:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

On Windows:

    $ docker run -it -p 192.168.99.100:8888:8888 -v $pwd:/home/jovyan/JupyterLabroot teradatajupyterlabext_2.0.0-ec03262020

We enter JupyterLab and open a terminal. Inside, we check R's version.

    $ R --version

In order to update only the R version, we use the following commands:

    $ conda update conda r-base

It is customary to run the command 'conda update conda' before any update or installation.

To know all the libraries that are currently included in the distribution, you can run the following command:

    $ conda list

Optionally, you can install or update other libraries from the 'conda-forge' channel or others that you consider. Use the install command.

    $ conda install -c conda-forge missingno xgboost pytorch-cpu igraph plotly scrapy r-xgboost

Once done, just finish docker for the changes to be saved in the container. However, you need to move the changes from the container to an image to be able to export the container later. First, we list the containers we currently have:

    $ docker ps -a

This allows us to know the nickname of the container. Then, we save the changes with the docker commit command:

    $ docker commit <container_nickname> jupyter363

where jupyter363 will be the tag of the new, updated image.

## Export the new Image

Finally, in order to share the image, you can export it to a file with the following command:

    $ docker save jupyter363 | gzip > jupyter363.tar.gz

And the resulting file (jupyter363.tar.gz) can be shared with other users or taken to the production cluster for use.

Another way to share images is using DockerHub or a container service (on premise or cloud).
  
## Start the Container again

In order to view the created containers (active and inactive), just run the command:

    $ docker ps -a

Identify the container you want to activate. You can use the nickname to start it:

    $ docker start <container_nickname> 

