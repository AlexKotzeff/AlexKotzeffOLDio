[Back](DataScienceProjects.md)

**2019 Happiness Data**


```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns 
```


```
df = pd.read_csv("2019HappinessData.csv")
```


```
dfCategories = df.drop(["Overall rank", "Score"], axis=1)
sns.boxplot(data=dfCategories)
plt.xticks(rotation=-90)
plt.ylabel("Rating")
plt.xlabel("Categories")
plt.title("Distribution of Scoring For Each Category")
```




    Text(0.5, 1.0, 'Distribution of Scoring For Each Category')






<img width="727" alt="boxplot1" src="https://user-images.githubusercontent.com/67394270/89364104-c1ee8580-d69f-11ea-8326-e940b48e1f40.png">




**Determine which of the two least varried plots has the smaller correlation with final score**


```
sns.lmplot(x="Score", y="Perceptions of corruption", data=df)
plt.title("Perception of Curruption vs. Happiness Score")
plt.ylabel("Perceptions of Curruption (Higher Scores are Favourable)")
```




    Text(6.799999999999997, 0.5, 'Perceptions of Curruption (Higher Scores are Favourable)')






<img width="352" alt="scatter1" src="https://user-images.githubusercontent.com/67394270/89364106-c3b84900-d69f-11ea-9faf-43f07b5a9a2c.png">





```
#I was very interested by the generosity category and wondered if it really impacted the final results as much as some other variables. 
sns.lmplot(x="Score", y="Generosity", data=df)
plt.title("Generosity vs. Happiness Score")
```




    Text(0.5, 1.0, 'Generosity vs. Happiness Score')






<img width="352" alt="scatter2" src="https://user-images.githubusercontent.com/67394270/89364111-c61aa300-d69f-11ea-8d63-523a65d1e666.png">



**Understanding From EDA**

The two categories with the least variability were Generosity and Perception of Corruption. I believed it would be important to take a closer look at these categories to see if they are a good indicator for the final score, or if a different category should be added that whould be more accurate. The line of best fit for the Generosity category was only slightly positive compared to the Perception of Corruption plot. Because the Generosity scores showed to have a very small indication of the final Happiness score, this category would likely be the best factor to replace. 
