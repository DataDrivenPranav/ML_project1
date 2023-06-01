# Sparktask2 :  Predicting the Optimal Number of Clusters in the Iris Dataset
Project Description: Predicting the Optimal Number of Clusters in the Iris Dataset using the Elbow Method

The project focuses on using the Elbow Method to determine the optimal number of clusters in the well-known Iris dataset. The Iris dataset is a multivariate dataset that includes measurements of sepal length, sepal width, petal length, and petal width for three different species of Iris flowers.

The goal of this project is to apply clustering techniques to the Iris dataset and determine the appropriate number of clusters that best represent the underlying structure of the data. The Elbow Method is a widely used technique for this purpose.

To begin, the Iris dataset is loaded into the project environment. The dataset is carefully examined to ensure its quality and consistency. Exploratory data analysis techniques may be applied to gain insights into the characteristics of the data, such as the distributions of the different features and potential outliers.

Next, the Elbow Method is applied to determine the optimal number of clusters. The Elbow Method involves running clustering algorithms, such as K-means, with varying numbers of clusters. For each iteration, the sum of squared distances between data points and their assigned cluster centers is calculated. These values are then plotted on a graph, with the number of clusters on the x-axis and the corresponding sum of squared distances on the y-axis.

The graph obtained from the Elbow Method typically exhibits a distinct "elbow" shape. The optimal number of clusters can be identified at the point where the decrease in the sum of squared distances significantly slows down, forming the elbow on the graph. This point indicates the number of clusters that effectively captures the main structure of the data without overfitting or underfitting.

Once the optimal number of clusters is determined using the Elbow Method, the clustering algorithm is applied with that specific number of clusters. The algorithm assigns each data point to its corresponding cluster based on its feature values. The resulting clusters can be visualized to understand the separation and grouping patterns of the Iris flowers in the dataset.

The project also provides an opportunity to assess the quality of the clustering results. Evaluation metrics such as silhouette score or within-cluster sum of squares can be calculated to quantify the compactness and separation of the clusters. These metrics provide a quantitative measure of the clustering performance and can further validate the chosen number of clusters.

In summary, this project employs the Elbow Method to predict the optimal number of clusters in the Iris dataset. By leveraging this technique, it helps to reveal the inherent structure and patterns in the data, allowing for a better understanding of the relationships among different Iris flower species.


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

     

df=pd.read_csv('/content/Iris (1).csv')

     
CHEAKING NULL VALUES


df.isna().sum()
     
Id               0
SepalLengthCm    0
SepalWidthCm     0
PetalLengthCm    0
PetalWidthCm     0
Species          0
dtype: int64
SPLITING DATA INTO TRAINING SET


X=df.iloc[:,[1,2,3,4]]
     
FINDING THE OPTIMAL NUMBER OF CLUSTERS IN IRIS DATASET BY THE The Elbow Method


from sklearn.cluster import KMeans
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters = i, init = 'k-means++', random_state = 42)
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.title('The Elbow Method')
plt.xlabel('Number of clusters')
plt.ylabel('WCSS')
plt.show()
     
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(
/usr/local/lib/python3.10/dist-packages/sklearn/cluster/_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
  warnings.warn(

AS WE CAN CLEARLY SEE THAT ELBOW LIKE STRUCTURE IS GETTING FORMED AT 2 AND 3 SO THERE WILL BE 2 OR 3 CLUSTERS IN THE IRIS DATA

