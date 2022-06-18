# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Import the necessary packages.
2. Read the given csv file and display the few contents of the data.
3. Import K Means and use for loop to calculate the within cluster sum of squares the data.
4. Plot the wcss for each iteration, also known as the elbow method plot.
5. Predict the clusters and plot them. 

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Subanu. K
RegisterNumber:  212219040152
*/
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("Mall_Customers.csv")
df.head()

df.info()
df.isnull().sum()

from sklearn.cluster import KMeans
wcss = []  
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
plt.show()
km = KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
y_pred = km.predict(df.iloc[:,3:])
df["cluster"] = y_pred
df0 = df[df["cluster"]==0]
df1 = df[df["cluster"]==1]
df2 = df[df["cluster"]==2]
df3 = df[df["cluster"]==3]
df4 = df[df["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="yellow",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="cyan",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="skyblue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="violet",label="cluster4")
plt.legend()
plt.title("Customer Segments")
plt.show()
```

## Output:
### Initial Dataset:
![Screenshot (130)](https://user-images.githubusercontent.com/87663343/174424462-689a88f8-501a-4778-9542-ce2566810b66.png)
### Data Information:
![image](https://user-images.githubusercontent.com/87663343/174425074-35e030d6-304a-4fac-b0ae-b6adbddb7eb2.png)
### Elbow graph:
![image](https://user-images.githubusercontent.com/87663343/174425085-02cc575c-a045-493c-ae74-20dded05d8e1.png)
### Cluster Graph:
![Screenshot (132)](https://user-images.githubusercontent.com/87663343/174425166-acc86d40-e63f-4282-86cf-1773628cdbb8.png)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
