---
layout: post
title: "Data Visualization"
date: 2020-11-22 21:30:00 +0200
description: "CNN, RNN, DEEP LEARNING ?"
tags: [Machine Learning,Python,Model,swift,SwiftUI,Combine,design,pattern,redux,unidirectional,data,flow,model,state,management]
comments: true
sharing: true
published: true
img: business-5475660_1280.jpg
---
 In every project, the first step is to load data.  
To read the CSV files we are the pandas function `read_csv()` :


**Model**: Read a CSV file with pandas

```python
import pandas

df = pandas.read_csv('data.csv') 
```

**View**: Dropping unnecessary columns in a DataFrame

```python
drop_columns = ['col1','col2']

df.drop(drop_columns, inplace=True, axis=1)

df = df.set_index('Identifier')

df.set_index('Identifier', inplace=True)
```

**View**: Changing the index of a DataFrame

```python
df.get_dtype_counts()

regex = r'^(\d{4})'

extr = df['Date of Publication'].str.extract(r'^(\d{4})', expand=False)

df['Date of Publication'] = pd.to_numeric(extr)
```

**View**: Using `.str()` methods to clean columns

```python
np.where(condition,
then, else)

pub = df['Place of Publication']

london = pub.str.contains('London')

london[:5]
```

**View**: Using the DataFrame.applymap() function to clean the entire dataset, element-wise

```python
university_towns = []

with open('Datasets/university_towns.txt') as file:
    for line in file:
        if '[edit]' in line:
            # Remember this `state` until the next is found
            state = line
        else:
            # Otherwise, we have a city; keep `state` as last-seen
            university_towns.append((state, line))

university_towns[:5]

towns_df = pd.DataFrame(university_towns, columns=['State', 'RegionName'])

towns_df.head()
 
def get_citystate(item):
    if '(' in item:
        return item[:item.find('(')]
    elif '[' in item:
        return item[:item.find('[')]
    else:
        return item

towns_df = towns_df.applymap(get_citystate)

towns_df.head()
```

**View**: Renaming columns to a more recognizable set of labels & Skipping unnecessary rows in a CSV file

```python
olympics_df = pd.read_csv('Datasets/olympics.csv', header=1)

new_names =  {'Unnamed: 0': 'Country',
              '? Summer': 'Summer Olympics',
              '01 !': 'Gold',
              '02 !': 'Silver',
              '03 !': 'Bronze',
              '? Winter': 'Winter Olympics',
              '01 !.1': 'Gold.1',
              '02 !.1': 'Silver.1',
              '03 !.1': 'Bronze.1',
              '? Games': '# Games',
              '01 !.2': 'Gold.2',
              '02 !.2': 'Silver.2',
              '03 !.2': 'Bronze.2'}

olympics_df.rename(columns=new_names,
inplace=True)
```

# Final thoughts

[The demo project](https://github.com/nalexn/clean-architecture-swiftui) now has **97% test coverage**, all thanks to the Clean Architecture's "dependency rule" and segregation of the app on multiple layers.