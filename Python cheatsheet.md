# Python Essential
----
## Variables

### 1. String
String can be added
Example:
>a = "ada"
b = "gwfwe"
c = a + b

1. Substring

``s[i:j+1]``: Extracts a substring from index i to j (inclusive) from the string s.
``s[i:j+1][::-1]``: Reverses the extracted substring.
``s[i:j+1] == s[i:j+1][::-1]``: Checks if the substring is identical to its reversed version, thereby determining if it's a palindrome.

---
### 2. List
A **list** is a mutable, ordered collection of items in Python. Lists can contain elements of different data types, including other lists.

#### **Empty List**

```python
empty_list = []
# or
empty_list = list()
#
fruits = ['apple', 'banana', 'cherry']
numbers = [1, 2, 3, 4, 5]
mixed = [1, 'apple', 3.14, True]
#
letters = list('hello')  # ['h', 'e', 'l', 'l', 'o']
```
**Cautious**
x = [a,b,c,d]
if you use x = y
then when x changes, y will also change.
To avoid this, use:
```python
y = list(x)
y=x[:]
```

#### Accessing List Elements
**Indexing**
```python
fruits = ['apple', 'banana', 'cherry']
print(fruits[0])  # Output: apple
print(fruits[2])  # Output: cherry
```
**Slicing**
==Does not contain the last number==
```python
print(fruits[0:2])  # Output: ['apple', 'banana']
print(fruits[:3])   # Output: ['apple', 'banana', 'cherry']
print(fruits[1:])   # Output: ['banana', 'cherry']
#Negative Indexing: Access elements from the end of the list.
print(fruits[-1])  # Output: cherry
print(fruits[-2])  # Output: banana
#fruit = [['apple',2],['banana',2],['cherry',3]]
print(fruits[1][1]) #output: 2
```
#### Modifying Lists
**Adding**
```python
fruits.append('date')
# ['apple', 'banana', 'cherry', 'date']
fruits.extend(['elderberry', 'fig'])
# ['apple', 'banana', 'cherry', 'date', 'elderberry', 'fig']
fruits.insert(1, 'blueberry')
# ['apple', 'blueberry', 'banana', 'cherry', 'date', 'elderberry', 'fig']
x = ["a", "b", "c", "d"]
y = x + ["e", "f"]
```
Use ``append()`` when:

You need to add a single element to the end of the list.
The element to add is not an iterable or you want to add it as a single object.
Use ``extend()`` when:

You want to concatenate another iterable's elements to the list.
You need to add multiple elements at once without creating nested structures.

```python
# Incorrect: This adds the entire list as a single element
fruits = ['apple', 'banana']
fruits.append(['cherry', 'date'])
print(fruits)
# Output: ['apple', 'banana', ['cherry', 'date']]

# Correct: This adds each element individually
fruits = ['apple', 'banana']
fruits.extend(['cherry', 'date'])
print(fruits)
# Output: ['apple', 'banana', 'cherry', 'date']
```

**Removing**
```python
fruits.remove('banana')
# ['apple', 'blueberry', 'cherry', 'date', 'elderberry', 'fig']
del fruits[2]
# ['apple', 'blueberry', 'cherry', 'date', 'elderberry', 'fig']
last_fruit = fruits.pop()
# last_fruit = 'fig'
# ['apple', 'blueberry', 'cherry', 'date', 'elderberry']
fruits.clear()
# []
```
**Updating**
```python
fruits = ['apple', 'banana', 'cherry']
fruits[1] = 'blueberry'
# ['apple', 'blueberry', 'cherry']
```
 ### 3. Dictionary

list1 = ['spain', 'france', 'germany', 'norway']
list2 = ['madrid', 'paris', 'berlin', 'oslo']

``list.index()`` Get the index of a value in the Dictionary
``list[index]`` Return the value of a index
```python
# Get index of 'germany': ind_ger
ind_ger = countries.index('germany')
# Use ind_ger to print out capital of Germany
capitals[ind_ger]
# Return keys of the dic
dict.keys()
#Return value of a key
dic[key1]
#Return if the key in dict
print(key in dict) #Output is True or False
#Delete value in dic
del(dict[key])
#update value in dic
dict[key] = value
# If the value of a key is a dictionary:
europe = { 'spain': { 'capital':'madrid', 'population':46.77 },
           'france': { 'capital':'paris', 'population':66.03 },
           'germany': { 'capital':'berlin', 'population':80.62 },
           'norway': { 'capital':'oslo', 'population':5.084 } }


# Print out the capital of France
print(europe['france']['capital'])
```
## If ,elif, else
### if
```python
if condition:
    result1
else ：
    result2
```
### elif

```python
if condition :
    expression
elif condition:
    expression
else:
    expression
```
### Loop
#### While loop
While loop = repeated if condition
>while condition :
>--    expression

#### For loop 

Loop in ``List``
>for var in seq:
--    expression
Example:
```python
for index, area in enumerate(areas) : # using index can return the index in the list
    print('room '+ str(index) +':'+str(area))
```
Loop in ``Dictionary``
``for key, value in dict.items() :``


Loop in ``2D Array``
```python
np_height = np.array([1.73, 1.68, 1.71, 1.89, 1.79])
np_weight = np.array([65.4, 59.2, 63.6, 88.4, 68.7])
meas = np.array([np_height, np_weight])

for val in np.nditer(meas):
    expression
```
Loop in ``DataFrame``
```python
# Iterate over rows of cars
for row in cars: # simply return the row name itself
    print(row)
#Using dict.iterrows()
for lab , row in cars.iterrows():# return the row as series, making it easy to access columns by name 
#i.e:
for lab,row in cars.iterrows():
    cars.loc[lab, "COUNTRY"] = row["country"].upper() # Add column to capitalize country name
```


## Python Package: Numpy
### Array
First of all, numpy arrays cannot contain elements with different types. Second, the typical arithmetic operators, such as +, -, * and / have a different meaning for regular Python lists and numpy arrays.

``True`` is converted to 1, ``False`` is converted to 0.
1. Convert a list to array
```python
import numpy as np
np_height = np.array(height)
# With numpy array, you can conduct calculation between list and int
np_height = np.array(height)
np_weight = np.array(weight)
np_weight / np_height ** 2
```
2. Calculation between Numpy Array
```python
python_list = [1, 2, 3]
numpy_array = np.array([1, 2, 3])
python_list + python_list # output [1,2,3,1,2,3]
numpy_array + numpy_array # output: [2,4,6]

np.mean(array > = 60) #calculate all the num in array >=60 and divided by count of num
```


3. Slicing in Numpy Array
```python
# Print out the 50th row of np_baseball
print(np_baseball[49,:])

# Select the entire second column of np_baseball: np_weight_lb
np_weight_lb = np_baseball[:,1]

# Print out height of 124th player
print(np_baseball[123][0])
```

### Boolean operators with NumPy
Numpy array can do comparison of an array:
```python
bmi = [ 21.852, 20.975, 21.75 , 24.747, 21.441]
bmi > 23 # Output array([False, False, False, True, False], dtype=bool)
bmi[bmi > 23] # Output array([ 24.747])
```
Numpy array can not take multiple comparison
```python
bmi > 21 and bmi < 22 # Error
```

The way to do multi comparison is through logical
``logical_and()``
``logical_or()``
``logical_not()``

```python
np.logical_and(bmi > 21, bmi < 22) # Output array([True, False, True, False, True], dtype=bool)
```
### Comparison of Dictionary, Array and List
|Feature|List|Dictionary|Array|
|---|---|---|---|
|Definition|An ordered, mutable collection of elements.	|An unordered collection of key-value pairs.|A sequence of elements of the same type.|
||my_list = [1, 2, 3]|my_dict = {'a': 1, 'b': 2}	|my_array = array('i', [1, 2, 3])|
|Element Access	By index:| my_list[0]|By key: my_dict['a']|By index: my_array[0]
|Homogeneity|No (can contain elements of different data types).	|No (keys must be unique and immutable types; values can be any type).	|Yes (all elements must be of the same type).

### Random in Numpy
Use random seed
``np.random.seed()``
Generate random number
``np.random.rand()``
``np.random.rand(start_num,end_num)``
Generate integer
``print(np.random.randint(1,7))``

### Data explore in Numpy array

## Python Package: Matplotlib
### Line Plot
 ```python
# Import matplotlib.pyplot as plt
import matplotlib.pyplot as plt
# Make a line plot: year on the x-axis, pop on the y-axis
plt.plot(year,pop)
# Display the plot with plt.show()
plt.show()
```
### Scatter plot & Hist Gram
```python
# Scatter Plot (x,y,size)
plt.scatter(gdp_cap, life_exp,s = size, c=color)
#Put the x-axis on a logarithmic scale
plt.xscale('log')
#Hist gram
plt.hist(life_exp) #the default bin is 10
plt.hist(life_exp,20) # set bins to 20
```
### Customize the chart

```python
#Edit Label
plt.xlabel('Year')
plt.ylabel('Population')
#Add title
plt.title('World Population Projections')
#Edit Y ticks 
plt.yticks([0, 2, 4, 6, 8, 10])
# Add text to certain point
plt.text(1550, 71, 'India')
plt.text(5700, 80, 'China')
# Display grid in plot
plt.grid(True)
```
## Python Package Pandas
### import Pandas as pd
```python
# Turn dict into dataframe
cars = pd.DataFrame(cars_dict)
# Set index of df to a list
df.index = list1
#Read CSV file
df1 = pd.read_csv("path/to/brics.csv")
cars = pd.read_csv('cars.csv',index_col = 0)#set index to 0
```
### Read data from dataframe
```python
# return column as Pandas Series
pd['column']
# return column as Pandas DataFrame
pd[['column']]
# Print out first 3 observations
print(cars[0:3])
```
### ``loc`` and ``iloc``
With ``loc`` and ``iloc`` you can do practically any data selection operation on DataFrames you can think of. 
``loc`` is label-based
``iloc`` is integer index based

```python
#Return rows in dataframe
print(cars.loc[['AUS','EG']])
# Print sub-DataFrame
print(cars.loc[['RU','MOR'],['country','drives_right']])

```
### Calculating in Pandas
1. Simple calculation on a column/row
```python
# Sum of each column
column_sum = df.sum()
# Sum of each row
row_sum = df.sum(axis=1)
# Mean of each column
column_mean = df.mean()
# Median of each column
column_median = df.median()
# Minimum of each column
column_min = df.min()
# Descriptive statistics
desc_stats = df.describe()
```
2. Count in DataFrame: ``Null``? ``Non-null``?``Unique``?
```python
# Count in column (unique & not Null)
desc_stats = df.value_counts()
store_props = store_types['type'].value_counts(normalize=True) #transfer count to proportion
# Count in column (duplicate & not Null)
desc_stats = df.count()
#Unique & Null
df['col'].value_counts(dropna=False)
#duplicate & Null rows
len(df['col'])
# Shape
df['col'].shape # returns (3, 3), indicating 3 rows and 3 columns.
df['col'].shape[0] #this is a method , return number of rows
df['col'].shape[1] #return number of columns
```
3. ``Group By`` a Single Column
```python
# Group by 'Department' and calculate mean salary
grouped_mean = df.groupby('Department')['Salary'].mean()
# Group by 'Department' and calculate sum and mean salary
grouped_stats = df.groupby('Department')['Salary'].agg(['sum', 'mean'])
```
4. Create ``pivot`` table

```python
# Creating a pivot table
pivot = pd.pivot_table(
    df, 
    values='Revenue', 
    index='Date', 
    columns='Department', 
    aggfunc='sum')
```


### Data filtering in Pandas
Since ``df['column']`` return the result as ``Series``
One way of filtering the data is using a boolean series:

```python
df['column'] = condition # Output a series of ['true','false',...]
con = (df['column']= condition)
result = df[con] # return the data with this condition
#i.e:
np.logical_and(brics["area"] > 8, brics["area"] < 10)
brics[np.logical_and(brics["area"] > 8, brics["area"] < 10)]
```
Apply multiple condition to a DataFrame:

```python
movie_short = netflix_df
[
    (netflix_df['type'] == 'Movie')
    &(netflix_df['genre'] == 'Action')
    & (netflix_df['release_year'] >= 1990) 
    & (netflix_df['release_year'] < 2000)
    &(netflix_df['duration'] <=90)
]
```


## Data Explore
```python
np.mean(np_city[:, 0])
np.median(np_city[:, 0])
stddev = np.std(np_baseball[:,0])
corr = np.corrcoef(np_baseball[:,0],np_baseball[:,1])
```

