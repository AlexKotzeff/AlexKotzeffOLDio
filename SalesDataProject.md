[Back](DataScienceProjects.md)

**Visualizing (fake) Sales Data from 2011 to 2015**


```python
#Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
#Read in the .csv File
df = pd.read_csv("5000 Sales Records.csv", index_col = "Order Date", parse_dates = True)
```


```python
#Slice the data so we are looking at the correct years.
df1 = df.loc["2011-01-01":"2015-01-01"]
df1 = df1.reset_index()
```


```python
#Make a plot to show the number of orders for every region
sns.countplot(x="Region", data=df1)
plt.xticks(rotation=-90)
plt.title("Number of Orders Per Region")
plt.ylabel("Number of Orders")
```




    Text(0, 0.5, 'Number of Orders')



<img width="724" alt="countplot1" src="https://user-images.githubusercontent.com/67394270/89363876-3543c780-d69f-11ea-80d9-2b0b28595a5c.png">





```python
#Take a closer look at the region with the most orders in this time frame. Start by making a dataframe with only it's data.  
dfEurope = df1[df1["Region"] == "Europe"]
```


```python
#Lets see what the most popular products are by looking at the number of orders there were for a specific item. 
sns.countplot(x="Item Type", data=dfEurope)
plt.xticks(rotation=-90)
plt.title("Number of Orders Per Item in Europe")
plt.ylabel("Number of Orders")
```




    Text(0, 0.5, 'Number of Orders')






<img width="717" alt="countplot2" src="https://user-images.githubusercontent.com/67394270/89363954-6e7c3780-d69f-11ea-9c81-2e8406bc17eb.png">





```python
#It looks like personal care was the most purchased product in Europe at this time, so let's compare it's popularity to other regions.
dfPC = df1[df1["Item Type"] == "Personal Care"]
numberOfPCOrders = dfPC["Region"].value_counts()
totalOrders = df1["Region"].value_counts()
percentPCOrders = numberOfPCOrders/totalOrders*100

plt.figure(figsize=(10,5))
sns.barplot(percentPCOrders.index, percentPCOrders.values, alpha=0.8)
plt.title('Popularity of Personal Care Orders Per Region')
plt.ylabel('Percentage of PC Orders', fontsize=12)
plt.xlabel('Region', fontsize=12)
plt.xticks(rotation=-90)
plt.show()
```





<img width="608" alt="percentplot" src="https://user-images.githubusercontent.com/67394270/89363970-74721880-d69f-11ea-9210-c2f905ae5360.png">




```python

```
