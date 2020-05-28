# Modelo Predictivo para estimar Precios de Hogares

En esta demo, vamos a determinar el mejor modelo de estimación del precios de hogares. Utilizaremos como referencia, un notebook desarrollado por el gran Raj Mehrotra [1]. Además, vamos a utilizar algunos otros notebook que extrajimos de Kaggle. Específicamente los desarrollados por X, Y y Z.

A modo de resumen, vamos a utilizar las siguientes herramientas.
- JupyterLab
- Librerías de ML de Python
- Git

## Fork del Proyecto en Github

El primer paso es desarrollar un fork (copiado) de la librería a mi repo de Github. La manera más sencilla es hacerlo directamente desde Github

A continuación, debemos enlazar desde JupyterLab nuestra cuenta de Git, para poder tener acceso remoto al repositorio y guardar todos los cambios que vayamos implementando.

Luego, traemos el repositorio desde Github

git clone https://github.com/lcajachahua/Housing-Prices-EDA-and-Regression-Models.git


## Instalación de Librerías

Utilizamos la siguiente sintaxis para instalar las librerías de Python que necesitamos

    conda install -c conda-forge missingno xgboost


