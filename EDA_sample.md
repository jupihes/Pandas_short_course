
## vector (array) action importance

- performance comparison 


## data manipulation

- make delta `Age` per family

## string methods


## time methods

df['Brith_year'] = 1402 - df['Age']

df['Brithday'] = 1402 - df['Age']  # 1402-06-31 - df['Age'] * 365.25
# df['Brithday'] = df['Year'] + '/' + df['Month'] + '/' + df['Day']  # 2022/05/17

## Investigate number of childern, order birth, gender type and age
How to do?

    Any recommendation
    Use rank and partition to label child rank
    Any other method?

Data issue identification
```python
df = df.assign(child_rank = df.groupby('ParentID').cumcount() + 1)
#df['row_num'] = df.groupby('city').cumcount() + 1
```
    What is `cumcount`?
        check pandas website
        Let's check
            trick on investigate of investigate to see what exist ;-)





```python
df = (df.assign(family_rank = df.sort_values(['BirthDate'], ascending=True)
.groupby(['ParentID'])
.cumcount()+1)
#.query('r < 3')
.sort_values(['ParentID', 'family_rank']))
```






```python
dfff = df.pivot_table(index='ParentID', values = ['ID', 'GenderId','BirthDate'],
                     aggfunc= {'ID': [np.count_nonzero, lambda x:','.join(x)],
                               'GenderId': lambda x:' '.join(x),
                               'BirthDate':['first','last']
                              }
                     )#np.max() - np.min())

dfff.head()

df_parent_child = df.pivot_table(index='ParentID', values = ['ID', 'GenderId','BirthDate'],
                     aggfunc= {'ID': [np.count_nonzero, lambda x:','.join(x)],
                               'GenderId': lambda x:' '.join(x),
                               'BirthDate': lambda x: set(x)
                              }
                     )#np.max() - np.min())

df_parent_child.head()
df_parent_child.reset_index(inplace=True)
df_parent_child.columns = ['ParentID', 'Distinct BirthDate', 'List Gender', 'List_N_ID', 'count_nonzero_N_ID']
```

## Which gender is more as first child?
- How to identify childerns of `ParentID`?

   -first child of person?
