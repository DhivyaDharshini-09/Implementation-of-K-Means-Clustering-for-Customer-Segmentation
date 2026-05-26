# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the necessary packages using import statement

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head()

3.Import KMeans and use for loop to cluster the data

4.Predict the cluster and plot data graphs

5.Print the outputs and end the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DHIVYA DHARSHINI P
RegisterNumber:  212225220028
*/


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

df = pd.read_csv(r"C:\Users\acer\Downloads\Mall_Customers.csv")
print("First 5 rows of data:")
print(df.head())
print("\n" + "="*50)

df['Gender'] = df['Gender'].map({'Male': 0, 'Female': 1})

X = df[['Annual Income (k$)', 'Spending Score (1-100)']]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

kmeans = KMeans(
    n_clusters=5,
    random_state=42,
    n_init=10
)

df['Cluster'] = kmeans.fit_predict(X_scaled)


plt.figure(figsize=(10, 6))

colors = ['red', 'blue', 'green', 'orange', 'purple']

for i in range(5):
    cluster_data = df[df['Cluster'] == i]

    plt.scatter(
        cluster_data['Annual Income (k$)'],
        cluster_data['Spending Score (1-100)'],
        color=colors[i],
        label=f'Cluster {i}',
        alpha=0.6
    )

plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.title('Customer Segments using K-Means')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

print("\nCLUSTER ANALYSIS:")
print("-" * 50)

for i in range(5):

    cluster_data = df[df['Cluster'] == i]

    print(f"\nCluster {i}:")
    print(f"  Number of customers: {len(cluster_data)}")
    print(f"  Average Income: ${cluster_data['Annual Income (k$)'].mean():.1f}k")
    print(f"  Average Spending Score: {cluster_data['Spending Score (1-100)'].mean():.1f}")
    print(f"  Average Age: {cluster_data['Age'].mean():.1f} years")

    males = len(cluster_data[cluster_data['Gender'] == 0])
    females = len(cluster_data[cluster_data['Gender'] == 1])

    print(f"  Gender: {males} Male, {females} Female")


df.to_csv('customer_segments.csv', index=False)

print("\n" + "="*50)
print("Results saved to 'customer_segments.csv'")
```

## Output:
<img width="846" height="180" alt="image" src="https://github.com/user-attachments/assets/d1ab9e5d-f6fb-4979-8f2f-436166dc39c1" />
<img width="1322" height="696" alt="image" src="https://github.com/user-attachments/assets/a8fd5cc1-0ec3-4a7f-b6a0-97b11cacf29e" />
<img width="947" height="656" alt="image" src="https://github.com/user-attachments/assets/79e1f27f-5f10-4702-b47e-945784e8bea6" />
<img width="1162" height="215" alt="image" src="https://github.com/user-attachments/assets/89cdf44a-3090-4e47-b0b2-59a3cb80fc11" />




## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
