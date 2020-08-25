[back](DataScienceProjects.md)

### Data Cleaning

```python
df = df.dropna(how="any")
```

Confirm that this was successful by re-running the command from above that counted the total number of missing values:

```python
df.isna().sum()
```


    id                    0
    year                  0
    month                 0
    day                   0
    hour                  0
    minute                0
    mapping               0
    messageViewingTime    0
    block                 0
    trialNum              0
    targetLocation        0
    target                0
    flankers              0
    rt                    0
    response              0
    error                 0
    anticipation          0
    feedbackResponse      0
    targetOnError         0
    dtype: int64



### Remove repeated rows


```python
# Use this cell to figure it out before assigning the result to df
df.iloc[::3, :]
```


```python
# use this cell to assign the result to df once you have the right output
df = df.iloc[::3, :]
```

Run the cell below to confirm there is only one row per trial (so the `trialNum` column should read 1, 2, 3, 4, etc.)


```python
df["trialNum"]
```




    0       1
    6       3
    9       4
    12      5
    15      6
           ..
    849    44
    852    45
    855    46
    858    47
    861    48
    Name: trialNum, Length: 287, dtype: int64



### Remove practice trials


```python
blue = blue + [1.]
```


```python
df["block"].unique()
```




    array(['practice', '1', '2', '3', '4', '5'], dtype=object)



The  point of practice is to give participants a chance to figure out the experiment (which is a bit complicated in this case), and make some errors, ask questions, etc., *before* running the experiment where we hope their data will be a valid reflection of their performance. So we should discard all the practice trials prior to doing EDA. 

The simplest way to remove all the rows from the practice block is actually to simply keep all the values that *don't* have the value of 'practice' in the `block` column. Fill in the Python "not equals" operator in the command below to do this. 


```python
df = df[df.block != 'practice']
```

Run a command that confirms that there are no practice trials left in `df`


```python
df[df.block == "practice"].sum()
```




    id                    0.0
    year                  0.0
    month                 0.0
    day                   0.0
    hour                  0.0
    minute                0.0
    mapping               0.0
    messageViewingTime    0.0
    block                 0.0
    trialNum              0.0
    targetLocation        0.0
    target                0.0
    flankers              0.0
    rt                    0.0
    response              0.0
    error                 0.0
    anticipation          0.0
    feedbackResponse      0.0
    targetOnError         0.0
    dtype: float64
