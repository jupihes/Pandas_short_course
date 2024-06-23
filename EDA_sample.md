
## vector (array) action importance

- performance comparison 


```python
# DataFrame iteration methods
df.iteritems() # (col-index, Series) pairs
df.iterrows() # (row-index, Series) pairs
# example ... iterating over columns ...
for (name, series) in df.iteritems():
    print('\nCol name: ' + str(name))
    print('1st value: ' + str(series.iat[0]))
```

## Why not using `iter...` when possible?

### What is %timeit?

```python
my_arr = np. arange(1_000_000)
my_list = list(range(1_000_000))
```
Now let’s multiply each sequence by 2:
```python
%timeit my_arr2 = my_arr * 2 # 1.99 ms ± 72.4 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```

```python
%timeit my_list2 = [x * 2 for x in my_list] # 96.9 ms ± 954 µs per loop (mean ± std. dev. of 7 runs, 10 loops each)
```

Look at page 85 of Book:

>    NumPy-based algorithms are generally 10 to 100 times faster (or more) than their pure Python counterparts and use
>     significantly less memory.




## data manipulation

- make delta `Age` per family

## String methods String techniuques

- Review string functions
    `.str.`
    [Pandas_documentation](https://pandas.pydata.org/docs/reference/series.html#string-handling)



## time methods
```python
df['Brith_year'] = 1402 - df['Age']

df['Brithday'] = 1402 - df['Age']  # 1402-06-31 - df['Age'] * 365.25
# df['Brithday'] = df['Year'] + '/' + df['Month'] + '/' + df['Day']  # 2022/05/17
```
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



```python
## pandas boxplot sort  
# https://stackoverflow.com/questions/21912634/how-can-i-sort-a-boxplot-in-pandas-by-the-median-values
# draw a boxplot of column Z in dataframe df by the categories X and Y. How can I sort the boxplot by the median, in descending order?

def boxplot_sorted(df, by, column):
    df2 = pd.DataFrame({col:vals[column] for col, vals in df.groupby(by)})
    meds = df2.median().sort_values(ascending=False)
    print(meds)
    df2[meds.index[:40]].boxplot(rot=45)

boxplot_sorted(df_99[df_99.Dar_100MT>0], by=['Ostan'], column='Dar_100MT')
plt.yscale('log')

```



```python
import seaborn as sns

# https://jakevdp.github.io/PythonDataScienceHandbook/04.05-histograms-and-binnings.html
# box and distribution plot 
# Cut the window in 2 parts
f, (ax_box, ax_hist) = plt.subplots(2, sharex=True, gridspec_kw={"height_ratios": (.15, .85)})

# Add a graph in each part
sns.boxplot(df_99.loc[df_99.Dar_100MT>0, 'Dar_100MT'], ax=ax_box)
sns.distplot(df_99.loc[df_99.Dar_100MT>0, 'Dar_100MT'], ax=ax_hist)

# Remove x axis name for the boxplot
ax_box.set(xlabel='')
```


```python
count_, bins_ = np.histogram(df_99.Dar_100MT)
```


```python
df['Dar_100MT'] = df['Daramad_Total_Rials']/ 10**9

del df['Daramad_Total_Rials']

df.groupby(by= 'frstPrd_99' ).agg({
 'frstPrd_99': np.count_nonzero,
 'lstPrd_99': [np.sum, np.mean, np.std, np.median],
 'lstPrd_1400': [np.min, np.max],
 'Dar_100MT': [np.count_nonzero, np.sum, np.mean, np.std]  
})
```
## Grouping data - Group by and Pivot_table

[data-aggregation :: groupby_fundamentals](https://wesmckinney.com/book/data-aggregation.html#groupby_fundamentals)

Hadley Wickham, an author of many popular packages for the R programming language, coined the term split-apply-combine for describing group operations. In the first stage of the process, data contained in a pandas object, whether a Series, DataFrame, or otherwise, is split into groups based on one or more keys that you provide. The splitting is performed on a particular axis of an object. For example, a DataFrame can be grouped on its rows (`axis="index"`) or its columns (`axis="columns"`). Once this is done, a function is applied to each group, producing a new value. Finally, the results of all those function applications are combined into a result object. The form of the resulting object will usually depend on what’s being done to the data. See Figure 10.1 for a mockup of a simple group aggregation.

Each grouping key can take many forms, and the keys do not have to be all of the same type:

    - A list or array of values that is the same length as the axis being grouped
    
    - A value indicating a column name in a DataFrame
    
    - A dictionary or Series giving a correspondence between the values on the axis being grouped and the group names
    
    - A function to be invoked on the axis index or the individual labels in the index


 <img src=https://wesmckinney.com/book/images/pda3_1001.png alt=\"Grouping implemnetation\" width=\"42%\" >



 The Python command is as follows:
```python
(df
 .groupby(['col_1', ..., 'col_n'])
 .agg({'col': builtin_agg})
```
where builtin_agg is among the following:

<table class="table">
<caption>Table&nbsp;10.1: Optimized <code>groupby</code> methods</caption>
<thead>
<tr class="header">
<th style="text-align: left;">Function name</th>
<th style="text-align: left;">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><code>any, all</code></td>
<td style="text-align: left;">Return <code>True</code> if any (one or more values) or all non-NA values are "truthy"</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>count</code></td>
<td style="text-align: left;">Number of non-NA values</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>cummin, cummax</code></td>
<td style="text-align: left;">Cumulative minimum and maximum of non-NA values</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>cumsum</code></td>
<td style="text-align: left;">Cumulative sum of non-NA values</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>cumprod</code></td>
<td style="text-align: left;">Cumulative product of non-NA values</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>first, last</code></td>
<td style="text-align: left;">First and last non-NA values</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>mean</code></td>
<td style="text-align: left;">Mean of non-NA values</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>median</code></td>
<td style="text-align: left;">Arithmetic median of non-NA values</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>min, max</code></td>
<td style="text-align: left;">Minimum and maximum of non-NA values</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>nth</code></td>
<td style="text-align: left;">Retrieve value that would appear at position <code>n</code> with the data in sorted order</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>ohlc</code></td>
<td style="text-align: left;">Compute four "open-high-low-close" statistics for time series-like data</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>prod</code></td>
<td style="text-align: left;">Product of non-NA values</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>quantile</code></td>
<td style="text-align: left;">Compute sample quantile</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>rank</code></td>
<td style="text-align: left;">Ordinal ranks of non-NA values, like calling <code>Series.rank</code></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>size</code></td>
<td style="text-align: left;">Compute group sizes, returning result as a Series</td>
</tr>
<tr class="even">
<td style="text-align: left;"><code>sum</code></td>
<td style="text-align: left;">Sum of non-NA values</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><code>std, var</code></td>
<td style="text-align: left;">Sample standard deviation and variance</td>
</tr>
</tbody>
</table>
