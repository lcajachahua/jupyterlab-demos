# Testing Jupyterlab: Clustering Methods

In this demo, we are going to take a look at JupyterLab. We are using the online version, so you don't need to install anything beforehand to be able to replicate this demo.

We are going to explore different clustering techniques, using as a reference a notebook made by Abdul Meral [1], made to test ten clustering methods included in scikit-learn [2].


## Starting JupyterLab

Go to https://jupyter.org/try and choose "Try JupyterLab"

![IMAGEN](images/TryJupyterLab.png)

## Download Kaggle Notebooks and Datasets

You can manually download Kaggle notebooks and datasets. However, you can also use a library to import and export information using scripts.

First, install the required library using Terminal:

    $ conda install -c conda-forge kaggle


Upon completion, a key needs to be generated from Kaggle to connect. There is a guide [3] in the References section at the end of this document.

Drag the downloaded key to the JupyterLab home. To copy it to the apropriate folder, you can use the following commands:

    $ mkdir ~/.kaggle
    $ cp kaggle.json ~/.kaggle/kaggle.json
    $ chmod 600 ~/.kaggle/kaggle.json


We are ready to copy elements from any Kaggle page, using the appropriate syntax. In our case, we need to copy an example notebook, which describes some ways to use clustering algorithms.

    $ kaggle kernels pull abdulmeral/10-models-for-clustering
    $ kaggle datasets download -d shwetabh123/mall-customers
    $ unzip mall_customers.zip

Finally, we can replicate the procedure indicated in the Notebook to understand certain clustering algorithms. It is only necessary to modify the code that is used to import the file.

## Complementing the Analysis with R's NbClust

Once we have reviewed the Clustering algorithms in Python, we turned to the NbClust library [4] to see how to test different Clustering algorithms and metrics in R.

The first step is to install the NbClust library, using Terminal

    $ conda install -c conda-forge r-nbclust

Then, we open an R notebook and start invoking the libraries that we are going to use:

    library(NbClust)
    library(ggplot2)

Load the dataset:

    data<-read.csv("Mall_Customers.csv")

Review the first rows

    head(data)

Replace the names:

    names(data)[4:5]<-c('AnnualIncome','SpendingScore')

And we run a series of tests, running different segmentations, to determine the optimal number of clusters.

    NbClust(data[,c(4,5)], diss=NULL, distance="euclidean", min.nc=4, max.nc=12, method="kmeans", index="all")

After reviewing the results, we can store them to plot the clusters

    nbclu<-NbClust(data[,c(4,5)], diss=NULL, distance="euclidean", min.nc=4, max.nc=12, method="kmeans", index="all")

We combine the dataset information with the cluster tag that comes from NbClust

    data<-cbind(data,'cluster'=nbclu$Best.partition)

And we convert 'cluster' into a factor to be able to use it as an argument to color the clusters with ggplot

    data$cluster<-as.factor(data$cluster)

Y build the plot:

    ggplot(data, aes(x=AnnualIncome, y=SpendingScore, shape=cluster, color=cluster)) + geom_point()

Podemos seguir cambiando y eligiendo otras distiancias, métodos y métricas para encontrar la que mejor se adecúe a nuestros datos. Del mismo modo, podemos aprender más sobre las catacterísticas de JupyterLab, a través de un VideoTutorial [5] o de la documentación correspondiente.
We can continue changing and choosing other distances, methods and metrics to find the one that best suits our data. Also, we can learn more about the characteristics of JupyterLab, through a Tutorial [5] or the corresponding documentation.


## References

[1] [Kaggle: 10 Models for Clustering](https://www.kaggle.com/abdulmeral/10-models-for-clustering/)

[2] [Overview of clustering methods](https://scikit-learn.org/stable/modules/clustering.html#overview-of-clustering-methods)

[3] [ConfusedCoders: How to copy Kaggle data to Amazon S3](https://confusedcoders.com/data-engineering/how-to-copy-kaggle-data-to-amazon-s3)

[4] [NbClust Package For Determining The Best Number Of Clusters](https://www.rdocumentation.org/packages/NbClust/versions/3.0/topics/NbClust)

[5] [Tutorial: How to use JupyterLab](https://www.youtube.com/watch?v=A5YyoCKxEOU)

[6] [Library optCluster](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5450252/)

[7] [Library PyCluster](https://www.theoj.org/joss-papers/joss.01230/10.21105.joss.01230.pdf)
