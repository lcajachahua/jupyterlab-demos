# Demos con Jupyterlab R, Python, Teradata, Docker y Git

En esta serie de instructivos, vamos a ver cómo podemos utilizar JupyterLab para desarrollar algunos análisis de datos. Luego, veremos como construir nuestro propio entorno JupyterLab, 
utilizando la imagen Docker que Teradata ha liberado 

## ¿Por qué JupyterLab?

Jupyter Notebook es uno de los más populares interfaces disponibles en el mundo analítico. Consciente de eso, Anaconda lanzó hace más de dos años JupyterLab, que es un workbench que nos permite
trabajar con Jupyter Notebooks, un árbol de carpetas, terminal de comandos, exploradores de archivos, kernels que sirven para utilizar una gran variedad de lenguajes de programación y muchas otras 
funcionalidades y herramientas para lidiar con el desarrollo analítico.

Además, de organizar y administrar efectivamente los Jupyter Notebooks, JupyterLab tiene muchas otras funcionalidades que podemos aprovechar:

- Integración con Git, para implementar el versionado de modelos, desarrollo colaborativo y documentación ágilmente organizada.
- La posibilidad de trabajar con con Jupyter Notebooks en lenguajes diferentes (Python, R, SQL Teradata, Julia, C++, JavaScript, etc). Incluso hay un kernel para SAS.
- La posibilidad de acceder a una terminal Linux, lo que amplía las capacidades de los notebooks y posibilita la instalación y actualización del entorno de manera ágil.
- Estándar Markdown para documentos
- Interfaz de usuario sencilla y ordenada


## Probando JupyterLab

Puede hacer un test-drive de JupyterLab, sin necesidad de instalar nada en su computadora. Simplemente ingrese a la siguiente web:

https://jupyter.org/try

Y elija la opción "Try JupyterLab". Puede ver una demo en el siguiente video:

[Video]



## JupterLab sobre Docker (Powered by Teradata)

Teradata ha desarrollado una imagen de JupyterLab que viene con kernels R, Python, Teradata, Julia. También incluye Git. Esta versión está disponible para ser instalada directamente en Windows, Linux o Mac.

Adicionalmente, existe una versión para Docker. Nosotros vamos a trabajar sobre Docker, debido a que ofrece una serie de beneficios que facilitan el pase de los modelos desarrollados a producción.

Esencialmente, Docker se utiliza para:
- Lidiar con la dificultad para instalar software libre en los entornos de producción, además de lidiar con el manteniniento de los mismos, actualización de librerías, instalación de paquetes, etc. Con Docker el ambiente va empaquetado, incluyendo las herramientas y librerías necesarias.
- Mejorar la reproducibilidad y la trazabilidad de los procesos
- Trabajar en forma modular con otro tipo de soluciones como Jenkins (herramienta de automatización de procesos), Airflow/Luigi (Pipelines). Pero no es necesario tener un solo sistema monolítico. Cada uno puede ir sobre un contenedor distinto.   
- Reutilización de componentes
- Estándar en DevOps y MLOps
