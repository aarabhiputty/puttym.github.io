---
layout: post
title: Random pandas notes
date: 2020-04-25
category: machine learning
---

*A dump of pandas commands which I have found useful.*

* **Change datatype of selected columns while creating a dataframe**
  - Use the `converters` parameter
```python
df = pd.read_excel("datafile.xlxs", converters={'Year':np.int32, 'Month':np.int32})
```
  In the above example, the datatype of columns 'Year' and 'Month' are
  changed to `numpy.int32`.

* **Changing indices in a dataframe**
```python
df.index=df['Year'] # Indices changed to Year column
df.reset_index(drop=True) # Indices changed to default values
```
  In the above example, the indices are first changed to 'Year' values.
  `reset_index` with parameter `drop` switches the indices back to
  default values

* **Print all the entire dataframe/series/column**
```python
print(df.to_string()) # Print entire dataframe
print(df['Year'].to_string()) # Print all values of the column Year
```

* **Sorting a data frame by column/s**
```python
df = df.sort_values(['Year', 'Month'])
df.sort_values(['Year', 'Month'], inplace=True) # Same as above
```
  Year values are sorted first, and then Month values are sorted without
  without affecteing the order of Year values.

  Suppose there are 5 year values which are not sorted. Each each year
  has 12 month values which again are not sorted. The above command
  first sorts the year values, and then sorts the month values.

  `sort_values` has the following parameters. (Refer to documentation
  for a complete list)
    - `ascending`: boolean. Default is `True` 
    - `inplace`: boolean. Default is `False`. Returns a sorted object
	if `False`, and returns nothing if `True`.
    - `axis`: 0 or `index` to sort rows. 1 or `columns` to sort columns
    - `na_position`: `first` or `last`. Sets the position of `Nan` values.
	Default: `last`
    - `kind`: Algorithm used for sorting. 
       Accepted values: 
       1. `quicksort` 
       2. `mergesort` 
       3. `heapsort`.

        	Default is `quicksort`.

<br>
* **Dealing with NaN values**
```python
df.dropna() # Drop rows with NaN values
df.isnull().sum() # Find number of NaN values
```

* **Selection by row number**
```python
df.iloc[2:60] #selects rows from 2 to 59
```

