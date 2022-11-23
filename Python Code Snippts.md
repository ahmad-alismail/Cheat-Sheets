### Loop through `josn` file and extract values with a specific key
```python
list_of_values = [data_item['key_level_2'] for data_item in data['key_level_1']]
```

### Filtering by categorical variables
````python

categ_df = df[list(df.dtypes[df.dtypes == 'object'].index)]
# or
categ_cols = train.dtypes[train.dtypes == np.object]  # filtering by categorical variables
categ_cols = categ_cols.index.tolist()     # list of categorical fields
train = pd.get_dummies(train, columns=categ_cols, drop_first=True)   # One hot encoding
````

### Selecting rows where a column value starts/ends with a value [Source](https://practicaldatascience.co.uk/data-science/how-to-select-filter-and-subset-data-in-pandas-dataframes)
```python
# starts with a value
df_technician = df[df['job'].str.startswith('data')]

# ends with a value
df_ar = df[df['job'].str.endswith('scientist')]

# conatins a value
df_education = df[df['education'].str.contains('university')]

# does NOT contain a value
df_education = df[~df['education'].str.contains('university')]
```

### The difference between ``apply()``, ``applymap()``, and ``map()`` 

![[Pasted image 20220609100518.png]]
**For DataFrame:**
-   `apply()`: It is used when you want to apply a function along the row or column. `axis = 0` for column and `axis = 1` for row.
```python 
df['D'] = df.apply(**lambda x:x.sum()**, axis=1)
```
![[Pasted image 20220609100556.png]]
-   `applymap()`: It is used for element-wise operation across the whole DataFrame. For the following dataframe:
![[Pasted image 20220609100844.png]]
implementing the following code:
```python 
df.applymap(np.square)
```
Will result:
![[Pasted image 20220609101101.png]]

**For Series:**
-   `apply()`: It is used when you want to apply a function on the values of Series. For example: 
```python 
df['D'] = df['C'].apply(**lambda x:x*2**)
```
![[Pasted image 20220609103203.png]]
-   `map()`: It is used to substitute each value with another value. For example:

![[Pasted image 20220609102627.png]]
```python 
df["Employee"] = df["Employee"].map({"Ahmad":"Abu Jad", "Majd":"Abu Alba"})
```
![[Pasted image 20220609102950.png]]
`map()` accepts also a function:
```python 
df["salary_usd"] = df["Salary"].map(lambda x: x* 1.07)
```
![[Pasted image 20220609103658.png]]

**See also:** 
- [Full intuitive article](https://towardsdatascience.com/introduction-to-pandas-apply-applymap-and-map-5d3e044e93ff#:~:text=apply()%20is%20used%20to,a%20Series%20with%20another%20value.)
- Python for Data Analysis ``p.151-153, p.198``

### Replace whole string if it contains substring in pandas
````python 
new = pd.DataFrame(
				   {'name': ['Bob', 'Jane', 'Alice','Ahmad'], 
                   'train':['tennis','football','basketball','BALL']}
                   )

# You can use str.contains to mask the rows that contain 'ball' and then overwrite with the new value:
df.loc[df['train'].str.contains('ball', case=False), 'train'] = 'ball sport'

````

### Pandas Plotting Backend in Python [See more](https://plotly.com/python/pandas-backend/)

````python
import pandas as pd
pd.options.plotting.backend = "plotly"

df = pd.DataFrame(dict(a=[1,3,2], b=[3,2,1]))
fig = df.plot()
fig.show()
````

### Lowercase all column names and replace spaces with _
````python
# Let's lowercase all the column names and replace spaces with _
df.columns = df.columns.str.lower().str.replace(' ', '_')
````

### Lowercase the string values in all columns of the dataframe
````python
for col in df.columns:
    df[col] = df[col].str.lower().str.replace(' ', '_')
````