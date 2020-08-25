Reading in Data and cleaning it is an important first step in data science. In this project, I read in data from several subjects and coded loops to create dictionaries of the data. 

## Read in data

Data are saved in files for each subject, continaing a set of four MNE `Evoked` instances. Each evoked object in the file for a subject represents the data for a particular condition, averaged over trials.

```python
data_path = 'evoked/'
```

Read in the data to a dictionary called `evoked`, with the dictionary keys being the ID codes for each subject.

```python
subjects= ['MSA_01', 'MSA_02', 'MSA_03', 'MSA_04', 'MSA_05', 'MSA_07', 'MSA_08', 'MSA_09', 'MSA_10', 'MSA_11', 'MSA_12', 'MSA_13', 'MSA_14', 'MSA_15', 'MSA_16', 'MSA_17', 'MSA_18', 'MSA_19']
evoked = {}
counter=0
for file in subjects:
    in_file= data_path + file + '-ave.fif'
    ev= {subjects[counter] : mne.read_evokeds(in_file, baseline=(None,0))}
    evoked.update(ev)
    counter += 1
```

Show the values for the first subject in the `evoked` dictionary:

```python
print(list(evoked.values())[0])
#To find the keys (subject) just change .values with .keys
```

    [<Evoked  |  'Ctrl' (average, N=30), [-0.19922, 1] sec, 64 ch, ~477 kB>, <Evoked  |  'RnotS' (average, N=33), [-0.19922, 1] sec, 64 ch, ~477 kB>, <Evoked  |  'RplusS' (average, N=37), [-0.19922, 1] sec, 64 ch, ~477 kB>, <Evoked  |  'WPtn' (average, N=33), [-0.19922, 1] sec, 64 ch, ~477 kB>]


What is the `type` of each entry in the `evoked` dictionary?


```python
for x in subjects:
    print(type(evoked[x]))
```

    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>
    <class 'list'>



Show how you would select the first item in the first dictionary entry:


```python
print(list(evoked.values())[0][0])
#can also use the key like: print(evoked["MSA_01"][0])
```

    <Evoked  |  'Ctrl' (average, N=30), [-0.19922, 1] sec, 64 ch, ~477 kB>


What is the `type` of the first item in the first dictionary entry? (Which will also be the type of every other entry)


```python
print(type(evoked["MSA_01"][0]))
#Or print(type(list(evoked.values())[0][0]))
```

    <class 'mne.evoked.Evoked'>


## Experimental conditions and contrasts


Create a list called `conditions`, using list comprehension, that contains the condition labels.


```python
conditions = [ ]
for comment in range(len(evoked["MSA_01"])):
    conditions.append(evoked["MSA_01"][comment].comment)
print(conditions)
```

    ['Ctrl', 'RnotS', 'RplusS', 'WPtn']


## Grand Averages

```python
# Initialize the dictionary, a list to hold values, and a counter to indicate condition. 
gavg = {}

# Loop over conditions and use them as keys in the gavg dictionary
for i, cond in enumerate(conditions):
    condValues = []
    # Loop over every subject and add the value to the condValues list. 
    for subject in range(len(subjects)):
        condValues.append(list(evoked.values())[subject][i])
    # After we loop through every subject for a given condition and save the values in a list, send that list to the mne.combine_evoked method.
    newAvg = {cond : mne.combine_evoked(condValues, weights = 'equal')}
    # Add it to the dictionary, reset the list, and update the condition counter. 
    gavg.update(newAvg)
gavg
```




    dict


Create an alternate version of `evoked`. Whereas `evoked` is keyed by subject, create `evoked_by_cond` such that is keyed by *condition*, with the dictionary values for each condition being a list of the data from that condition, for each subject.

```python
evoked_by_cond = {}
condValues2 = []
condCounter2 = 0

#Loop over conditions and use them as keys in the gavg dictionary
for cond2 in conditions:
    #Loop over every subject and add the value to the condValues list. 
    for subject2 in range(len(subjects)):
        condValues2.append(list(evoked.values())[subject2][condCounter2])
    #After we loop through every subject for a given condition and save the values in a list, send that list to the mne.combine_evoked method.
    newAvg2 = {cond2 : condValues2}
    #Add it to the dictionary, reset the list, and update the condition counter. 
    evoked_by_cond.update(newAvg2)
    condValues2 = []
    condCounter2 += 1
    
evoked_by_cond
```
