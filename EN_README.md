# Demos with Jupyterlab R, Python, Teradata, Docker and Git

In these tutorials, we are going to learn to use JupyterLab for developing data analysis. Then, we would build our own JupyterLab environment,
using the Docker image provided by Teradata

## Why JupyterLab?

Jupyter Notebook is one of the most popular interfaces available in the analytical world. Considering that, Anaconda launched JupyterLab more than two years ago. This is a workbench that allows us
to work with Jupyter Notebooks, storage environments, command terminal, file explorers, kernels for a wide variety of programming languages and many other functionalities and tools to deal with analytical development.

In addition, to effectively organize and manage Jupyter Notebooks, JupyterLab has other functionalities that we can take advantage of:

- Integration with Git, to implement model versioning, collaborative development and organized documentation.
- The possibility to work with Jupyter Notebooks in different languages (Python, R, SQL Teradata, Julia, C ++, JavaScript, etc). There is even a kernel for SAS.
- The possibility of accessing a Linux terminal, which extends the capabilities of notebooks and enables the installation and updating of the environment in an agile way.
- Markdown standard for documents
- Simple and neat user interface

## Testing JupyterLab

You can test-drive JupyterLab, without having to install anything on your computer. Simply enter the following website:

https://jupyter.org/try

And choose the "Try JupyterLab" option. You can see a demo in the following video:

[Video]

## JupterLab on Docker (Powered by Teradata)

Teradata has developed a JupyterLab image that includes R, Python, Teradata, Julia kernels. Also Git and ZeroMQ. This version is available to be installed directly on Windows, Linux or Mac.

Additionally, there is an image for Docker. We are going to work with Docker, because it offers many enablers for the transition from developed models to production.

Essentially, Docker is used to:
- Deal with the hard work installing free software in production environments, maintenance, updating libraries, installing packages, etc. With Docker the environment is build with modules, including the necessary tools and libraries.
- Improve reproducibility and traceability of processes
- Work in a modular way with other types of solutions such as Jenkins (process automation tool), Airflow / Luigi (Pipelines). But it is not necessary to have a single monolithic system. Each one can run on a different container.
- Reuse of components
- Standard practices such as DataOps and MLOps

## How to install

In order to install JupyterLab on Docker, you can follow each of the instructions listed below. Each step has video tutorials (YouTube).

1. [Install Docker](https://github.com/lcajachahua/jupyterlab-demos/blob/master/EN_01_Install_Docker.md)

2. [Download JupyterLab](https://github.com/lcajachahua/jupyterlab-demos/blob/master/EN_02_Download_Jupyterlab.md)

3. Starting JupyterLab
[Windows](https://github.com/lcajachahua/jupyterlab-demos/blob/master/EN_03_Open_JupyterLab_Windows.md)
[Linux](https://github.com/lcajachahua/jupyterlab-demos/blob/master/EN_03_Open_JupyterLab_Linux.md)

4. [Implementing Image Changes](https://github.com/lcajachahua/jupyterlab-demos/blob/master/EN_04_Modifying_Image.md)

