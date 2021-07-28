## Pandas Tutorial – Pandas Examples

*pandas* library helps you to carry out your entire data analysis workflow in Python.

With Pandas, the environment for doing data analysis in Python excels in performance, productivity, and the ability to collaborate.



### Import pandas

pandas is built on numpy. So, while importing pandas, import numpy as well.

```python
import numpy as np
import pandas as pd
```

This is how the pandas community usually import and alias the libraries. We will also use the same alias names in our pandas examples going forward.

Following is a list of Python Pandas topics, we are going to learn in these series of tutorials.



### Pandas Series Basics

- [Pandas Series Example](https://pythonexamples.org/pandas-series-example/)

#### Create Pandas Series

To create Pandas Series in Python, pass a list of values to the Series() class. Pandas will create a default integer index.

In the following example, we will create a pandas Series with integers.

**Python Program**

```python
import numpy as np
import pandas as pd

s = pd.Series([1, 3, 5, 12, 6, 8])

print(s)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd s+%3D+pd.Series([1%2C+3%2C+5%2C+12%2C+6%2C+8]) print(s))

**Output**

```python
0     1
1     3
2     5
3    12
4     6
5     8
dtype: int64
```

The datatype of the elements in the Series is int64. Based on the values present in the series, the datatype of the series is decided.



#### Pandas Series with NaN values

You can also include numpy NaN values in pandas series.

In the following Pandas Series example, we will create a Series with one of the value as **numpy.NaN**.

**Python Program**

```python
import numpy as np
import pandas as pd

s = pd.Series([1, 3, np.nan, 12, 6, 8])

print(s)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd s+%3D+pd.Series([1%2C+3%2C+np.nan%2C+12%2C+6%2C+8]) print(s))

**Output**

```python
0     1.0
1     3.0
2     NaN
3    12.0
4     6.0
5     8.0
dtype: float64
```



#### Pandas Series with Strings

You can include strings as well for elements in the series.

In the following example, we will create a Pandas Series with one of the value as string.

**Python Program**

```python
import numpy as np
import pandas as pd

s = pd.Series(['python', 3, np.nan, 12, 6, 8])

print(s)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd s+%3D+pd.Series(['python'%2C+3%2C+np.nan%2C+12%2C+6%2C+8]) print(s))

**Output**

```python
0    python
1         3
2       NaN
3        12
4         6
5         8
dtype: object
```

As the elements belong to different datatypes, like integer and string, the datatype of all the elements in this pandas series is considered as **object**. But when you access the elements individually, the corresponding datatype is returned, like int64, str, float, etc.



#### Access Elements of Pandas Series

You can access elements of a Pandas Series using index.

In the following Pandas Series example, we create a series and access the elements using index.

**Python Program**

```python
import numpy as np
import pandas as pd

s = pd.Series(['python', 3, np.nan, 12, 6, 8])

print(s[0])
print(s[4])
```

[ Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd s+%3D+pd.Series(['python'%2C+3%2C+np.nan%2C+12%2C+6%2C+8]) print(s[0]) print(s[4]))

**Output**

```python
python
6
```



#### Summary

In this tutorial of [Python Examples](https://pythonexamples.org/), we learned how to create a Pandas Series with elements belonging to different datatypes, and access the elements of the Series using index, with the help of well detailed examples.




### Pandas DataFrame Basics

#### Pandas DataFrame – Create or Initialize

In Python Pandas module, DataFrame is a very basic and important type. To create a DataFrame from different sources of data or other Python datatypes, we can use DataFrame() constructor.

In this tutorial, we will learn different ways of how to create and initialize Pandas DataFrame.

![Python Pandas Create or Initialize DataFrame](https://pythonexamples.org/images/python-pandas-create-dataframe.svg)



Syntax of DataFrame() class

The syntax of DataFrame() class is

```python
DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
```

where all the arguments are optional and

- **data** can be ndarray, iterable, dictionary or another dataframe.
- **index** can be Index or an array. If no index is provided, it defaults to Range Index, i.e., **0** to **number of rows – 1**.
- **columns** are used to label the columns
- **dtype** is used to specify or force a datatype on the data. If you do not specify, **dtype** is inferred from the data itself.
- **copy** if True, copies data from inputs. Note that this affects only DataFrame or 2d ndarray input.



##### Example 1: Create an Empty DataFrame

To create an empty DataFrame, pass no arguments to pandas.DataFrame() class.

In this example, we create an empty DataFrame and print it to the console output.

**Python Program**

```python
import pandas as pd

df = pd.DataFrame()

print(df)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame() print(df))

**Output**

```python
Empty DataFrame
Columns: []
Index: []
```

As we have provided no arguments, the **columns** array is empty and **index** array is empty.



##### Example 2: Create DataFrame from List of Lists

To initialize a DataFrame from list of lists, you can pass this list of lists to pandas.DataFrame() constructor as `data` argument.

In this example, we will create a DataFrame for list of lists.

**Python Program**

```python
import pandas as pd

#list of lists
data = [['a1', 'b1', 'c1'],
        ['a2', 'b2', 'c2'],
        ['a3', 'b3', 'c3']]

df = pd.DataFrame(data)
print(df)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23list+of+lists data+%3D+[['a1'%2C+'b1'%2C+'c1']%2C ++++++++['a2'%2C+'b2'%2C+'c2']%2C ++++++++['a3'%2C+'b3'%2C+'c3']] df+%3D+pd.DataFrame(data) print(df))

**Output**

```python
   0  1  2
0  a  b  c
1  d  e  f
2  g  h  i
3  j  k  l
```



##### Example 3: Create DataFrame from Dictionary

To initialize a DataFrame from dictionary, pass this dictionary to pandas.DataFrame() constructor as `data` argument.

In this example, we will create a DataFrame for list of lists.

**Python Program**

```python
    0   1   2
0  a1  b1  c1
1  a2  b2  c2
2  a3  b3  c3
```

[ Run](https://pythonexamples.org/run.php?pgm=0+++1+++2 0++a1++b1++c1 1++a2++b2++c2 2++a3++b3++c3)

**Output**

```python
   aN  bN  cN
0  a1  b1  c1
1  a2  b2  c2
2  a3  b3  c3
```



##### Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we learned how to create an empty DataFrame, and then to create a DataFrame with data from different Python objects, with the help of well detailed examples.

#### [Pandas DataFrame – Create from Dictionary](https://pythonexamples.org/pandas-construct-dataframe-from-dictionary/)

You can create a DataFrame from Dictionary by passing a dictionary as the **data** argument to DataFrame() class.

In this tutorial, we shall learn how to create a Pandas DataFrame from Python Dictionary.



#####  Syntax – Create DataFrame

The syntax to create a DataFrame from dictionary object is shown below.

```python
mydataframe = DataFrame(dictionary)
```

Each element in the dictionary is translated to a column, with the key as column name and the array of values as column values.

![Python Pandas - Create DataFrame from Dictionary](https://pythonexamples.org/images/python-pandas-dataframe-create-from-dictionary.svg)



#####  Example 1: Create DataFrame from Dictionary

In the following example, we will create a dictionary, and pass this dictionary as data argument to the DataFrame() class.

**Python Program**

```python
import numpy as np
import pandas as pd

mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'],
	'physics': [68, 74, 77, 78],
	'chemistry': [84, 56, 73, 69],
	'algebra': [78, 88, 82, 87]}

#create dataframe using dictionary
df_marks = pd.DataFrame(mydictionary)

print(df_marks)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe+using+dictionary df_marks+%3D+pd.DataFrame(mydictionary) print(df_marks))

**Output**

```python
  names  physics  chemistry  algebra
0   Geo       68         84       78
1  Kiku       74         56       88
2  Amol       77         73       82
3  Lini       78         69       87
```

The key values (names, physics, chemistry, algebra) transformed to column names and the array of values to column values.



##### Example 2: Create DataFrame from Python Dictionary

In this example, we will create a DataFrame with two columns and four rows of data using a Dictionary.

**Python Program**

```python
import numpy as np
import pandas as pd

mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'],
	'roll_no': [1, 2, 3, 4]
	}

#create dataframe using dictionary
df_students = pd.DataFrame(mydictionary)

print(df_students)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'roll_no'%3A+[1%2C+2%2C+3%2C+4] } %23create+dataframe+using+dictionary df_students+%3D+pd.DataFrame(mydictionary) print(df_students))

**Output**

```python
  names  roll_no
0  Somu        1
1  Kiku        2
2  Amol        3
3  Lini        4
```



##### Video

<iframe title="Python Pandas - Create DataFrame using Dictionary" width="640" height="360" src="https://www.youtube.com/embed/vEq8qGrCrNo?feature=oembed" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" style="box-sizing: inherit;"></iframe>
Pandas Create DataFrame from Python Dictionary



##### Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we learned how to create a Pandas DataFrame from Python Dictionary with the help of well detailed examples.

#### [Pandas DataFrame – Create from List of Lists](https://pythonexamples.org/pandas-create-dataframe-from-list-of-lists/)

To create Pandas DataFrame from list of lists, you can pass this list of lists as `data` argument to pandas.DataFrame().

Each inner list inside the outer list is transformed to a row in resulting DataFrame.

The syntax of DataFrame() class is

```python
DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
```



##### Example 1: Create DataFrame from List of Lists

In this example, we will

1. Import pandas package.
2. Initialize a Python List of Lists.
3. Create DataFrame by passing this list of lists object as `data` argument to pandas.DataFrame().
4. pandas.DataFrame(list of lists) returns DataFrame.

**Python Program**

```python
import pandas as pd

#list of lists
data = [['a1', 'b1', 'c1'],
        ['a2', 'b2', 'c2'],
        ['a3', 'b3', 'c3']]

df = pd.DataFrame(data)
print(df)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23list+of+lists data+%3D+[['a1'%2C+'b1'%2C+'c1']%2C ++++++++['a2'%2C+'b2'%2C+'c2']%2C ++++++++['a3'%2C+'b3'%2C+'c3']] df+%3D+pd.DataFrame(data) print(df))

**Output**

```python
    0   1   2
0  a1  b1  c1
1  a2  b2  c2
2  a3  b3  c3
```



##### Example 2: Create DataFrame from List of Lists with Column Names & Index

In this example, we will

1. Import pandas package.
2. Initialize a Python List of Lists.
3. Initialize a List for column name of DataFrame.
4. Initialize a List for index of DataFrame.
5. Create DataFrame by passing this list of lists object as `data` argument to pandas.DataFrame().
6. pandas.DataFrame(list of lists) returns DataFrame.

**Python Program**

```python
import pandas as pd

#list of lists
data = [['a1', 'b1', 'c1'],
        ['a2', 'b2', 'c2'],
        ['a3', 'b3', 'c3']]

columns = ['aN', 'bN', 'cN']
index = [1, 2, 3]

df = pd.DataFrame(data, index, columns)
print(df)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23list+of+lists data+%3D+[['a1'%2C+'b1'%2C+'c1']%2C ++++++++['a2'%2C+'b2'%2C+'c2']%2C ++++++++['a3'%2C+'b3'%2C+'c3']] columns+%3D+['aN'%2C+'bN'%2C+'cN'] index+%3D+[1%2C+2%2C+3] df+%3D+pd.DataFrame(data%2C+index%2C+columns) print(df))

**Output**

```python
   aN  bN  cN
1  a1  b1  c1
2  a2  b2  c2
3  a3  b3  c3
```



##### Example 3: Create DataFrame from List of Lists with Different List Lengths

If the inner lists have different lengths, the lists with lesser values will be transformed to rows with appended values of `None` to match the length of longest row in the DataFrame.

In this example, we will

1. Import pandas package.
2. Initialize a Python List of Lists such that inner lists are of different lengths.
3. Create DataFrame by passing this list of lists object for `data` parameter to pandas.DataFrame() constructor.
4. pandas.DataFrame(list of lists) returns DataFrame.

**Python Program**

```python
import pandas as pd

#list of lists
data = [['a1', 'b1', 'c1', 'd1'],
        ['a2', 'b2', 'c2'],
        ['a3', 'b3', 'c3']]

df = pd.DataFrame(data)
print(df)
```

[ Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23list+of+lists data+%3D+[['a1'%2C+'b1'%2C+'c1'%2C+'d1']%2C ++++++++['a2'%2C+'b2'%2C+'c2']%2C ++++++++['a3'%2C+'b3'%2C+'c3']] df+%3D+pd.DataFrame(data) print(df))

**Output**

```python
    0   1   2     3
0  a1  b1  c1    d1
1  a2  b2  c2  None
2  a3  b3  c3  None
```



##### Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we learned how to create a Pandas DataFrame from Python List of Lists, with the help of well detailed examples.

#### [Pandas DataFrame – Create from Numpy Array](https://pythonexamples.org/pandas-create-dataframe-from-numpy-array/)

To create Pandas DataFrame from Numpy Array, you can pass this array as `data` argument to pandas.DataFrame().

Each row of numpy array will be transformed to a row in resulting DataFrame.

The syntax of DataFrame() class constructor is

```
DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
```

##### Example 1: Create DataFrame from Numpy Array

In this example, we will

1. Import pandas package and numpy package.
2. Initialize a 2D Numpy Array `array`.
3. Create DataFrame by passing this numpy array `array` as `data` parameter to pandas.DataFrame().
4. pandas.DataFrame(numpy array) returns DataFrame.

**Python Program**

```
import pandas as pd
import numpy as np

array = np.array([['a1', 'b1', 'c1'],
                  ['a2', 'b2', 'c2'],
                  ['a3', 'b3', 'c3']])
df = pd.DataFrame(array)
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np array+%3D+np.array([['a1'%2C+'b1'%2C+'c1']%2C ++++++++++++++++++['a2'%2C+'b2'%2C+'c2']%2C ++++++++++++++++++['a3'%2C+'b3'%2C+'c3']]) df+%3D+pd.DataFrame(array) print(df))

**Output**

```
    0   1   2
0  a1  b1  c1
1  a2  b2  c2
2  a3  b3  c3
```

##### Example 2: Create DataFrame from Numpy Array with Column Names & Index

In this example, we will

1. Import pandas package and numpy package.
2. Initialize a 2D Numpy Array.
3. Initialize a List for column name of DataFrame.
4. Initialize a List for index of DataFrame.
5. Create DataFrame by passing this numpy array object for `data` parameter to pandas.DataFrame() constructor.
6. pandas.DataFrame(ndarray) returns DataFrame.

**Python Program**

```
import pandas as pd
import numpy as np

array = np.array([['a1', 'b1', 'c1'],
                  ['a2', 'b2', 'c2'],
                  ['a3', 'b3', 'c3']])

columns = ['aN', 'bN', 'cN']
index = [1, 2, 3]

df = pd.DataFrame(array, index, columns)
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np array+%3D+np.array([['a1'%2C+'b1'%2C+'c1']%2C ++++++++++++++++++['a2'%2C+'b2'%2C+'c2']%2C ++++++++++++++++++['a3'%2C+'b3'%2C+'c3']]) columns+%3D+['aN'%2C+'bN'%2C+'cN'] index+%3D+[1%2C+2%2C+3] df+%3D+pd.DataFrame(array%2C+index%2C+columns) print(df))

**Output**

```
   aN  bN  cN
1  a1  b1  c1
2  a2  b2  c2
3  a3  b3  c3
```

##### Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we learned how to create a Pandas DataFrame from Numpy ndarray, with the help of well detailed examples.

#### [Pandas DataFrame – Load Data from CSV File](https://pythonexamples.org/pandas-dataframe-read-csv-load-data-csv/)

To load data into Pandas DataFrame from a CSV file, use pandas.read_csv() function.

In this tutorial, we will learn different scenarios that occur while loading data from CSV to Pandas DataFrame.

![Python Pandas - Create DataFrame from CSV](https://pythonexamples.org/images/python-pandas-dataframe-from-csv.svg)



##### Example 1: Load CSV Data into DataFrame

In this example, we take the following csv file and load it into a DataFrame using `pandas.read_csv()` method.

data.csv

```python
name,physics,chemistry,algebra
Somu,68,84,78
Kiku,74,56,88
Amol,77,73,82
Lini,78,69,87
```

**Python Program**

```python
import pandas as pd 
df = pd.read_csv("data.csv") 
print(df)
```

**Output**

```python
 name physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87
```

The first row in the csv file is taken as column names, and the rest as rows of the dataframe.



##### Example 2: Load DataFrame from CSV file data with specific delimiter

If you are using a different delimiter to differentiate the items in your data, you can specify that delimiter to read_csv() function using **delimiter** argument.

Consider the following csv file. In this csv file, the delimiter is a space.

**data.csv**

```python
name physics chemistry algebra
Somu 68 84 78
Kiku 74 56 88
Amol 77 73 82
Lini 78 69 87
```

Now we will provide the delimiter as space to read_csv() function.

**Python Program**

```python
import pandas as pd 
df = pd.read_csv('data.csv', delimiter=' ') 
print(df)
```

**Output**

```python
 name physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87
```



Load DataFrame from CSV with no header

If your CSV file does not have a header (column names), you can specify that to read_csv() in two ways.

1. Pass the argument **header=None** to pandas.read_csv() function.
2. Pass the argument **names** to pandas.read_csv() function, which implicitly makes **header=None**.

**Python Program**

```python
import pandas as pd df = pd.read_csv('data.csv', header=None) df1 = pd.read_csv('data.csv', names=list_of_column_names)
```

For more options available with read_csv() function, refer https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html



Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we learned how to load data from CSV file into Pandas DataFrame.



#### [Pandas DataFrame – Print DataFrame Information](https://pythonexamples.org/print-information-of-pandas-dataframe/)

To print information of Pandas DataFrame, call DataFrame.info() method. The DataFrame.info() method returns nothing but just prints information about this DataFrame.

The syntax to use info() method of a DataFrame is

```python
DataFrame.info(verbose=None, buf=None, max_cols=None, memory_usage=None, show_counts=None, null_counts=None)
```



##### Example 1: Print DataFrame Information

In the following program, we have created a DataFrame. We shall print this DataFrame’s information using DataFrame.info() method.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [['abc', 22], ['xyz', 25], ['pqr', 31]], columns=['name', 'age']) 
df.info()
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[['abc'%2C+22]%2C ++++['xyz'%2C+25]%2C ++++['pqr'%2C+31]]%2C ++++columns%3D['name'%2C+'age']) df.info())

**Output**

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3 entries, 0 to 2
Data columns (total 2 columns):
name 3 non-null object
age 3 non-null int64
dtypes: int64(1), object(1)
memory usage: 128.0+ bytes
```

If we observe, info() method printed the type of this object, range, columns, number of entries in each columns, if the columns are non-null, datatype of columns, and memory usage of this DataFrame.



##### Summary

In this tutorial of [Python Examples](https://pythonexamples.org/), we learned how to print the information of a DataFrame using DataFrame.info() method.



#### [Pandas DataFrame – Get Index](https://pythonexamples.org/get-index-of-pandas-dataframe/)

To get the index of a Pandas DataFrame, call DataFrame.index property. The DataFrame.index property returns an Index object representing the index of this DataFrame.

##### syntax

The syntax to use index property of a DataFrame is

```python
DataFrame.index
```

The index property returns an object of type Index. We could access individual index using any looping technique in Python.

In the following program, we have a DataFrame with no index specified. Since no index is specified, a range that starts at 0 and increments in steps of 1 would be assigned to the DataFrame. Let us get the index of this DataFrame using **DataFrame.index**.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[88, 72, 67], [23, 78, 62], [55, 54, 76]], columns=['a', 'b', 'c']) index = df.index
print(index)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( [[88%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [55%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) index+%3D+df.index print(index))

**Output**

```python
RangeIndex(start=0, stop=3, step=1)
```

We can print the elements of Index object using a [for loop](https://pythonexamples.org/python-for-loop-example/) as shown in the following.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[88, 72, 67], [23, 78, 62], [55, 54, 76]], columns=['a', 'b', 'c']) index = df.index 
for i in index: print(i)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( [[88%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [55%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) index+%3D+df.index for+i+in+index%3A ++++print(i))

**Output**

```python
0
1
2
```

Let us consider another example, where we have set a specific index for a DataFrame. And we are going to get the index of this DataFrame using DataFrame.index.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[88, 72, 67], [23, 78, 62], [55, 54, 76]], index=[2, 4, 9], columns=['a', 'b', 'c']) index = df.index
print(index)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[[88%2C+72%2C+67]%2C ++++[23%2C+78%2C+62]%2C ++++[55%2C+54%2C+76]]%2C ++++index%3D[2%2C+4%2C+9]%2C ++++columns%3D['a'%2C+'b'%2C+'c']) index+%3D+df.index print(index))

**Output**

```python
Int64Index([2, 4, 9], dtype='int64')
```



##### Summary

In this tutorial of [Python Examples](https://pythonexamples.org/), we learned how to get the index of a DataFrame using DataFrame.index property.

#### [Pandas DataFrame – Check if Empty](https://pythonexamples.org/pandas-check-if-dataframe-is-empty/)

You can check if a Pandas DataFrame is empty or not. To check if DataFrame is empty in Pandas, use `DataFrame.empty`.

`DataFrame.empty` returns a boolean indicator if the DataFrame is empty or not. If the DataFrame is empty, `True` is returned. If the DataFrame is not empty, `False` is returned.

![Python Pandas - Check if DataFrame is empty](https://pythonexamples.org/images/python-pandas-dataframe-check-if-empty.svg)



##### Example 1: Empty DataFrame

In this example, we will initialize an empty DataFrame and check if the DataFrame is empty using `DataFrame.empty` attribute.

**Python Program**

```python
import pandas as pd df = pd.DataFrame() isempty = df.empty
print('Is the DataFrame empty :', isempty)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame() isempty+%3D+df.empty print('Is+the+DataFrame+empty+%3A'%2C+isempty))

`df = pd.DataFrame()` initializes an empty dataframe. And then `df.empty` checks if the dataframe is empty. Since the dataframe is empty, we will get boolean value `True` to the variable `isempty`.

**Output**

```python
Is the DataFrame empty : True
```



##### Example 2: Non-empty DataFrame

In the following example, we have initialized a DataFrame with some rows and then check if `DataFrame.empty` returns `False`.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67.1], [23, 78, 69.5], [32, 74, 56.6], [52, 54, 76.2]], columns=['a', 'b', 'c']) isempty = df.empty
print('Is the DataFrame empty :', isempty)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67.1]%2C [23%2C+78%2C+69.5]%2C [32%2C+74%2C+56.6]%2C [52%2C+54%2C+76.2]]%2C columns%3D['a'%2C+'b'%2C+'c']) isempty+%3D+df.empty print('Is+the+DataFrame+empty+%3A'%2C+isempty))

**Output**

```python
Is the DataFrame empty : False
```



##### Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we learned how to check if a Pandas DataFrame is empty or not.

#### [Pandas DataFrame – Get Number of Axes](https://pythonexamples.org/pandas-dataframe-get-number-of-axes/)

To get number of axes or array dimensions in a Pandas DataFrame, call DataFrame.ndim property. The DataFrame.ndim returns an integer representing the number of axes in this DataFrame.

The syntax to call `ndim` property of a DataFrame is

```python
DataFrame.ndim
```



##### Example 1: Get Number of Axes in DataFrame

In this example, we have created a DataFrame and we shall get the number of axes in this DataFrame using DataFrame.ndim property.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [['abc', 22, 22.6], ['xyz', 25, 23.2], ['pqr', 31, 30.5]], columns=['name', 'age', 'bmi']) 
number_of_axes = df.ndim
print(f'Number of axes in this DataFrame = {number_of_axes}')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[['abc'%2C+22%2C+22.6]%2C ++++['xyz'%2C+25%2C+23.2]%2C ++++['pqr'%2C+31%2C+30.5]]%2C ++++columns%3D['name'%2C+'age'%2C+'bmi']) number_of_axes+%3D+df.ndim print(f'Number+of+axes+in+this+DataFrame+%3D+{number_of_axes}'))

**Output**

```python
Number of axes in this DataFrame = 2
```

Since there are only two axes in our DataFrame, ndim property returned a value of 2.

#### [Pandas DataFrame – Access a Single Cell Value](https://pythonexamples.org/pandas-dataframe-access-a-single-value/)

You can access a single value from a DataFrame in two ways.

**Method 1:** `DataFrame.at[index, column_name]` property returns a single value present in the row represented by the index and in the column represented by the column name.

**Method 2:** Or you can use `DataFrame.iat(row_position, column_position)` to access the value present in the location represented by the row position row_position and column position column_position, irrespective of the row and column labels.

In this tutorial, we will go through examples using DataFrame.at() and DataFrame.iat(), where we shall access a single value from DataFrame.



##### Example 1 – DataFrame.at

In this example, we will initialize a DataFrame and use DataFrame.at property to access a value.

**Python Program**

```python
import pandas as pd 
df1 = pd.DataFrame({'A': ['aa', 'bb'], 'M': ['cc', 'dd'], 'C': ['ee', 'ff']}, index=[2, 5]) 
value1 = df1.at[2, 'M']
print(value1) 
value2 = df1.at[5, 'A']
print(value2)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['aa'%2C+'bb']%2C ++++++++++++++++++++'M'%3A+['cc'%2C+'dd']%2C ++++++++++++++++++++'C'%3A+['ee'%2C+'ff']}%2C +++++++++++++++++++index%3D[2%2C+5]) %23value+at+index+2+and+column+name+'M' value1+%3D+df1.at[2%2C+'M'] print(value1) %23value+at+index+5+and+column+name+'A' value2+%3D+df1.at[5%2C+'A'] print(value2))

**Output**

```python
cc
bb
```



##### Example 2 – DataFrame.at

In this example, we take a DataFrame initialized with no index. If no index is provided, you can consider index to be starting at 0 and increment in steps of 1 with each successive row.

**Python Program**

```python
import pandas as pd 
df1 = pd.DataFrame({'A': ['aa', 'bb'], 'M': ['cc', 'dd'], 'C': ['ee', 'ff']}) 
value1 = df1.at[0, 'C']
print(value1) 

value2 = df1.at[1, 'A']
print(value2)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['aa'%2C+'bb']%2C ++++++++++++++++++++'M'%3A+['cc'%2C+'dd']%2C ++++++++++++++++++++'C'%3A+['ee'%2C+'ff']}) value1+%3D+df1.at[0%2C+'C'] print(value1) value2+%3D+df1.at[1%2C+'A'] print(value2))

**Output**

```python
ee
bb
```



##### Example 3 – DataFrame.iat

In this example, we take a DataFrame initialized with no index. If no index is provided, you can consider index to be starting at 0 and increment in steps of 1 with each successive row.

**Python Program**

```python
import pandas as pd 
df1 = pd.DataFrame({'A': ['aa', 'bb'], 'M': ['cc', 'dd'], 'C': ['ee', 'ff']}, index=[2, 5]) 
value1 = df1.iat[0, 1]
print(value1) 

value2 = df1.iat[1, 1]
print(value2)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['aa'%2C+'bb']%2C ++++++++++++++++++++'M'%3A+['cc'%2C+'dd']%2C ++++++++++++++++++++'C'%3A+['ee'%2C+'ff']}%2C +++++++++++++++++++index%3D[2%2C+5]) %23value+at+row+position+0%2C+column+position+1 value1+%3D+df1.iat[0%2C+1] print(value1) %23value+at+row+position+1%2C+column+position+1 value2+%3D+df1.iat[1%2C+1] print(value2))

**Output**

```python
cc
dd
```



#### [Pandas DataFrame – Get Number of Elements](https://pythonexamples.org/get-number-of-elements-in-pandas-dataframe/)

To get number of elements in a Pandas DataFrame, call DataFrame.size property. The DataFrame.size returns an integer representing the number of elements in this DataFrame. In other words, size property returns (number of rows * number of columns).

The syntax to call `size` property of a DataFrame is

```python
DataFrame.size
```



##### Example 1: Get Number of Elements in DataFrame

In this example, we have created a DataFrame and we shall get the number of elements in this DataFrame using DataFrame.size property.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [['abc', 22, 22.6], ['xyz', 25, 23.2], ['pqr', 31, 30.5]], columns=['name', 'age', 'bmi']) number_of_elements = df.size
print(f'Number of elements in this DataFrame = {number_of_elements}')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[['abc'%2C+22%2C+22.6]%2C ++++['xyz'%2C+25%2C+23.2]%2C ++++['pqr'%2C+31%2C+30.5]]%2C ++++columns%3D['name'%2C+'age'%2C+'bmi']) number_of_elements+%3D+df.size print(f'Number+of+elements+in+this+DataFrame+%3D+{number_of_elements}'))

**Output**

```python
Number of elements in this DataFrame = 9
```

Since there are three rows and three columns in this DataFrame, size property returns 3*3 = 9.

#### [Pandas DataFrame – Shape](https://pythonexamples.org/pandas-dataframe-shape/)

To get the shape of Pandas DataFrame, use DataFrame.shape. The `shape` property returns a tuple representing the dimensionality of the DataFrame. The format of shape would be (rows, columns).

In this tutorial, we will learn how to get the shape, in other words, number of rows and number of columns in the DataFrame, with the help of examples.

![Pandas DataFrame - Shape or Dimension](https://pythonexamples.org/images/python-pandas-dataframe-shape.svg)



##### Example: DataFrame Shape

In the following example, we will find the shape of DataFrame. Also, you can get the number of rows or number of columns using index on the shape.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[21, 72, 67.1], [23, 78, 69.5], [32, 74, 56.6], [52, 54, 76.2]], columns=['a', 'b', 'c']) print('The DataFrame is :\n', df) shape = df.shape
print('\nDataFrame Shape :', shape)
print('\nNumber of rows :', shape[0])
print('\nNumber of columns :', shape[1])
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67.1]%2C [23%2C+78%2C+69.5]%2C [32%2C+74%2C+56.6]%2C [52%2C+54%2C+76.2]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('The+DataFrame+is+%3A\n'%2C+df) %23get+dataframe+shape shape+%3D+df.shape print('\nDataFrame+Shape+%3A'%2C+shape) print('\nNumber+of+rows+%3A'%2C+shape[0]) print('\nNumber+of+columns+%3A'%2C+shape[1]))

Output

![pandas dataframe shape example](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-dataframe-shape.png)



##### Example 2: Shape of Empty DataFrame

In this example we will initialize an empty DataFrame and try to find the shape of it. Of course, the DataFrame.shape would return (0, 0).

**Python Program**

```python
import pandas as pd df = pd.DataFrame() print('The DataFrame is :\n', df) shape = df.shape
print('DataFrame Shape :', shape)
print('Number of rows :', shape[0])
print('Number of columns :', shape[1])
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame() print('The+DataFrame+is+%3A\n'%2C+df) %23get+dataframe+shape shape+%3D+df.shape print('DataFrame+Shape+%3A'%2C+shape) print('Number+of+rows+%3A'%2C+shape[0]) print('Number+of+columns+%3A'%2C+shape[1]))

**Output**

```python
The DataFrame is : Empty DataFrame
Columns: []
Index: []
DataFrame Shape : (0, 0)
Number of rows : 0
Number of columns : 0
```

The number of rows is zero and the number of columns is zero.

#### [Pandas DataFrame – Concatenate – pandas.concat()](https://pythonexamples.org/pandas-concatenate-dataframes/)

You can concatenate two or more Pandas DataFrames with similar columns. To concatenate Pandas DataFrames, usually with similar columns, use `pandas.concat()` function.

In this tutorial, we will learn how to concatenate DataFrames with similar and different columns.

![Python Pandas - Concatenate DataFrames](https://pythonexamples.org/images/python-pandas-dataframe-concatenate.svg)



##### Syntax of pandas.concat() method

The syntax of pandas.concat() is:

```python
pandas.concat(objs, axis=0, join='outer', join_axes=None, ignore_index=False, keys=None, levels=None, names=None, verify_integrity=False, sort=None, copy=True)
```



##### Example 1: Concatenate DataFrames with Similar Columns

In this example, we take two DataFrames with same column names and concatenate them using concat() function.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','algebra','calculus']) frames = [df_1, df_2] df = pd.concat(frames, sort=False) print("df_1\n------\n",df_1)
print("\ndf_2\n------\n",df_2)
print("\ndf\n--------\n",df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus'])	 frames+%3D+[df_1%2C+df_2] %23concatenate+dataframes df+%3D+pd.concat(frames%2C+sort%3DFalse) %23print+dataframe print("df_1\n------\n"%2Cdf_1) print("\ndf_2\n------\n"%2Cdf_2) print("\ndf\n--------\n"%2Cdf))

**Output**

![pandas.concat() function example](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-concat-example-1.png)

The two DataFrames are concatenated. But the index is not in order. You can reset the index by using `reset_index()` function.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','algebra','calculus']) frames = [df_1, df_2] df = pd.concat(frames) df.reset_index(drop=True, inplace=True) print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus'])	 frames+%3D+[df_1%2C+df_2] %23concatenate+dataframes df+%3D+pd.concat(frames) %23+reset+index df.reset_index(drop%3DTrue%2C+inplace%3DTrue) %23print+dataframe print(df))

**Output**

```python
 name physics chemistry algebra calculus
0 Somu 68 84 78 96
1 Kiku 74 56 88 85
2 Ajit 77 73 82 87
3 Amol 72 67 91 83
4 Lini 78 69 87 92
```



##### Example 2: Concatenate two DataFrames with different columns

In this following example, we take two DataFrames. The second dataframe has a new column, and does not contain one of the column that first dataframe has.

pandas.concat() function concatenates the two DataFrames and returns a new dataframe with the new columns as well. The dataframe row that has no value for the column will be filled with `NaN` short for Not a Number.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','geometry','calculus']) frames = [df_1, df_2] df = pd.concat(frames, sort=False) print("df_1\n------\n",df_1)
print("\ndf_2\n------\n",df_2)
print("\ndf\n--------\n",df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'geometry'%2C'calculus'])	 frames+%3D+[df_1%2C+df_2] %23concatenate+dataframes df+%3D+pd.concat(frames%2C+sort%3DFalse) %23print+dataframe print("df_1\n------\n"%2Cdf_1) print("\ndf_2\n------\n"%2Cdf_2) print("\ndf\n--------\n"%2Cdf))

**Output**

![pandas.concat() function example - when columns are different](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-concat-example-2.png)



#### [Pandas DataFrame – Append](https://pythonexamples.org/pandas-append-dataframe/)

pandas.DataFrame.append() function creates and returns a new DataFrame with rows of second DataFrame to the end of caller DataFrame.

##### Example 1: Append a Pandas DataFrame to Another

In this example, we take two dataframes, and append second dataframe to the first.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','algebra','calculus']) frames = [df_1, df_2] df = df_1.append(df_2, ignore_index=True) print("df_1\n------\n",df_1)
print("\ndf_2\n------\n",df_2)
print("\ndf\n--------\n",df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus'])	 frames+%3D+[df_1%2C+df_2] %23append+dataframes df+%3D+df_1.append(df_2%2C+ignore_index%3DTrue) %23print+dataframe print("df_1\n------\n"%2Cdf_1) print("\ndf_2\n------\n"%2Cdf_2) print("\ndf\n--------\n"%2Cdf))

**Output**

![Pandas Append DataFrame](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-append-dataframe-example.png)

In this pandas dataframe.append() example, we passed argument `ignore_index=Ture`. This helps to reorder the index of resulting dataframe. If `ignore_index=False`, the output dataframe’s index looks as shown below.

![Pandas Append DataFrame](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-append-dataframe-example-2.png)



##### Example 2: Append DataFrames with Different Columns

Now, let us take two DataFrames with different columns and append the DataFrames.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','science','calculus']) frames = [df_1, df_2] df = df_1.append(df_2, ignore_index=True, sort=False) print("df_1\n------\n",df_1)
print("\ndf_2\n------\n",df_2)
print("\ndf\n--------\n",df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'science'%2C'calculus'])	 frames+%3D+[df_1%2C+df_2] %23append+dataframes df+%3D+df_1.append(df_2%2C+ignore_index%3DTrue%2C+sort%3DFalse) %23print+dataframe print("df_1\n------\n"%2Cdf_1) print("\ndf_2\n------\n"%2Cdf_2) print("\ndf\n--------\n"%2Cdf))

**Output**

![img](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-append-dataframe-example-3.png)

For those rows, whose corresponding column is not present, the value is defaulted to **NaN**. And also, the other values in the column are hosting floating values.



#### [Pandas DataFrame – Query](https://pythonexamples.org/pandas-dataframe-query/)-重点

To query DataFrame rows based on a condition applied on columns, you can use **pandas.DataFrame.query()** method.

By default, query() function returns a DataFrame containing the filtered rows. You can also pass `inplace=True` argument to the function, to modify the original DataFrame.



##### Example 1: Query DataFrame with Condition on Single Column

In this example, we will query the DataFrame to return filtered DataFrame with rows that satisfy the passed boolean expression.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 56], [73, 88, 67], [32, 74, 56], [43, 78, 69], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) 
df1 = df.query('a>50') 
print(df1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+56]%2C [73%2C+88%2C+67]%2C [32%2C+74%2C+56]%2C [43%2C+78%2C+69]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23query+single+column df1+%3D+df.query('a%26gt%3B50') %23print+the+dataframe print(df1))

**Output**

```python
 a b c
3 73 88 67
7 52 54 76
```



##### Example 2: Query DataFrame with Condition on Multiple Columns using AND operator

In this example, we will try to apply the condition on multiple columns and use AND operator.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 56], [73, 88, 67], [32, 74, 56], [43, 78, 69], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) 
df1 = df.query('a>30 and c>60')
print(df1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+56]%2C [73%2C+88%2C+67]%2C [32%2C+74%2C+56]%2C [43%2C+78%2C+69]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23query+multiple+columns df1+%3D+df.query('a%26gt%3B30+and+c%26gt%3B60') %23print+the+dataframe print(df1))

**Output**

```python
 a b c
3 73 88 67
5 43 78 69
7 52 54 76
```



##### Example 3: Query DataFrame with Condition on Multiple Columns using OR operator

In this example, we will try to apply the condition on multiple columns and use OR operator.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 56], [73, 88, 67], [32, 74, 56], [43, 78, 69], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) 
df1 = df.query('a>50 or c>60') 
print(df1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+56]%2C [73%2C+88%2C+67]%2C [32%2C+74%2C+56]%2C [43%2C+78%2C+69]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23query+multiple+columns df1+%3D+df.query('a%26gt%3B50+or+c%26gt%3B60') %23print+the+dataframe print(df1))

**Output**

```python
 a b c
0 21 72 67
1 23 78 62
3 73 88 67
5 43 78 69
7 52 54 76
```



##### Example 4: DataFrame Query with inplace parameter

We can pass `inplace=True`, to modify the actual DataFrame we are working on.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 56], [73, 88, 67], [32, 74, 56], [43, 78, 69], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) 
df.query('a>50 and c>60', inplace=True) print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+56]%2C [73%2C+88%2C+67]%2C [32%2C+74%2C+56]%2C [43%2C+78%2C+69]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23query+dataframe+with+inplace+trues df.query('a%26gt%3B50+and+c%26gt%3B60'%2C+inplace%3DTrue) %23print+the+dataframe print(df))

**Output**

```python
 a b c
3 73 88 67
7 52 54 76
```



#### [Pandas DataFrame – Reset Index](https://pythonexamples.org/pandas-dataframe-reset-index/)

When you concatenate, sort, join or do some rearrangements with your DataFrame, the index gets shuffled or out of order.

To reset the index of a dataframe, you can use pandas.DataFrame.reset_index() method.



##### Syntax of reset_index()

The syntax of DataFrame.reset_index() function is given below.

```python
DataFrame.reset_index(level=None, drop=False, inplace=False, col_level=0, col_fill='')
```

[Run](https://pythonexamples.org/run.php?pgm=DataFrame.reset_index(level%3DNone%2C+drop%3DFalse%2C+inplace%3DFalse%2C+col_level%3D0%2C+col_fill%3D''))

To reset the index, pass the parameters **drop=True** and **inplace=True**.



##### Example 1: Pandas Reset Index of DataFrame using reset_index()

In this example, we will concatenate two dataframes and then use reset_index() to re-order the index of the dataframe.

**Python Program**

```python
import pandas as pd 
df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) 
df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','algebra','calculus']) 
df = pd.concat([df_1, df_2]) 
df.reset_index(drop=True, inplace=True) 
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus'])	 %23concatenate+dataframes df+%3D+pd.concat([df_1%2C+df_2]) %23now+the+index+is+not+in+order %23+reset+index df.reset_index(drop%3DTrue%2C+inplace%3DTrue) %23print+dataframe print(df))

**Output**

![Python Reset Index of DataFrame](https://pythonexamples.org/wp-content/uploads/2019/02/pandas-dataframe-reset-index.png)



##### Example 2: Pandas Reset Index of DataFrame using concat()

You can reset the index using concat() function as well. Pass in the argument `ignore_index=True` to the concat() function.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','algebra','calculus']) df = pd.concat([df_1, df_2], ignore_index=True) print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus'])	 %23reset+index+while+concatenating df+%3D+pd.concat([df_1%2C+df_2]%2C+ignore_index%3DTrue) %23print+dataframe print(df))

**Output**

```python
 name physics chemistry algebra calculus
0 Somu 68 84 78 96
1 Kiku 74 56 88 85
2 Ajit 77 73 82 87
3 Amol 72 67 91 83
4 Lini 78 69 87 92
```

If you have only one dataframe whose index has to be reset, then just pass that dataframe in the list to the concat() function.

**Python Program**

```python
import pandas as pd 
df_1 = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Ajit', 77, 73, 82, 87]], columns=['name', 'physics', 'chemistry','algebra','calculus']) 
df_2 = pd.DataFrame( [['Amol', 72, 67, 91, 83], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry','algebra','calculus']) 
df = pd.concat([df_1, df_2]) 
df = pd.concat([df], ignore_index=True) 
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd  df_1+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Ajit'%2C+77%2C+73%2C+82%2C+87]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus']) df_2+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91%2C+83]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C'algebra'%2C'calculus'])	 %23concatenate df+%3D+pd.concat([df_1%2C+df_2]) %23now+the+index+is+not+in+order %23reset+the+index df+%3D+pd.concat([df]%2C+ignore_index%3DTrue) %23print+dataframe print(df))

##### Video Tutorial – Reset Index of Pandas DataFrame

#### [Pandas DataFrame – Render as HTML](https://pythonexamples.org/pandas-render-dataframe-as-html-table/)

You can convert DataFrame to a table in HTML, to represent the DataFrame in web pages.

To render a Pandas DataFrame to HTML Table, use `pandas.DataFrame.to_html()` method.

The total DataFrame is converted to `` html element, while the column names are wrapped under table head html element. And, each row of DataFrame is converted to a row in HTML table.



##### Example 1: Render DataFrame as HTML Table

In this example, we will initialize a DataFrame and render it into HTML Table.

**Python Program**

```python
import pandas as pd df_marks = pd.DataFrame({'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]}) html = df_marks.to_html()
print(html)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23+create+dataframe df_marks+%3D+pd.DataFrame({'name'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C +++++'physics'%3A+[68%2C+74%2C+77%2C+78]%2C +++++'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C +++++'algebra'%3A+[78%2C+88%2C+82%2C+87]}) %23+render+dataframe+as+html html+%3D+df_marks.to_html() print(html))

**Output**

```python
<table border="1" class="dataframe"> <thead> <tr style="text-align: right;"> <th></th> <th>name</th> <th>physics</th> <th>chemistry</th> <th>algebra</th> </tr> </thead> <tbody> <tr> <th>0</th> <td>Somu</td> <td>68</td> <td>84</td> <td>78</td> </tr> <tr> <th>1</th> <td>Kiku</td> <td>74</td> <td>56</td> <td>88</td> </tr> <tr> <th>2</th> <td>Amol</td> <td>77</td> <td>73</td> <td>82</td> </tr> <tr> <th>3</th> <td>Lini</td> <td>78</td> <td>69</td> <td>87</td> </tr> </tbody>
</table>
```

Let us write the html data to a file using Python.

**Python Program**

```python
import pandas as pd df_marks = pd.DataFrame({'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]}) html = df_marks.to_html() text_file = open("index.html", "w")
text_file.write(html)
text_file.close()
```

The file will be created with html data in the current working directory.

Now, open the html file with browser. The output should look similar to the following screenshot.

![Pandas - Render DataFrame as HTML Table](https://pythonexamples.org/wp-content/uploads/2019/04/pandas-dataframe-to-html.png)



#### [Pandas DataFrame – Write as Excel](https://pythonexamples.org/pandas-write-dataframe-to-excel-sheet/)

You can save or write a DataFrame to an Excel File or a specific Sheet in the Excel file using `pandas.DataFrame.to_excel()` method of DataFrame class.

In this tutorial, we shall learn how to write a Pandas DataFrame to an Excel File, with the help of well detailed example Python programs.

**Prerequisite**

The prerequisite to work with Excel file functions in pandas is that, you have to install openpyxl module. To install openpyxl using pip, run the following pip command.

```python
pip install openpyxl
```



##### Example 1: Write DataFrame to Excel File

You can write the DataFrame to Excel File without mentioning any sheet name. The step by step process is given below:

1. Have your DataFrame ready. In this example we shall initialize a DataFrame with some rows and columns.
2. Create an Excel Writer with the name of the output excel file, to which you would like to write our DataFrame.
3. Call to_excel() function on the DataFrame with the Excel Writer passed as argument.
4. Save the Excel file using save() method of Excel Writer.

**Python Program**

```python
import pandas as pd df_marks = pd.DataFrame({'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]}) writer = pd.ExcelWriter('output.xlsx') df_marks.to_excel(writer) writer.save()
print('DataFrame is written successfully to Excel File.')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23+create+dataframe df_marks+%3D+pd.DataFrame({'name'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C +++++'physics'%3A+[68%2C+74%2C+77%2C+78]%2C +++++'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C +++++'algebra'%3A+[78%2C+88%2C+82%2C+87]}) %23+create+excel+writer+object writer+%3D+pd.ExcelWriter('output.xlsx') %23+write+dataframe+to+excel df_marks.to_excel(writer) %23+save+the+excel writer.save() print('DataFrame+is+written+successfully+to+Excel+File.'))

**Output**

Run the above program, and an excel file shall be created with the name specified while creating excel writer.

![Pandas - Write DataFrame to Excel Sheet](https://pythonexamples.org/wp-content/uploads/2019/04/write-dataframe-to-excel.png)

**Output Excel File**

Open the excel file, and you shall see the index, column labels and row data written to file.

![Pandas - Write DataFrame to Excel Sheet](https://pythonexamples.org/wp-content/uploads/2019/04/excel-output.png)



##### Example 2: Write DataFrame to a specific Excel Sheet

You can write the DataFrame to a specific Excel Sheet. The step by step process is:

1. Have your DataFrame ready.
2. Create an Excel Writer with the name of the desired output excel file.
3. Call to_excel() function on the DataFrame with the writer and the name of the Excel Sheet passed as arguments.
4. Save the Excel file using save() method of Excel Writer.

**Python Program**

```python
import pandas as pd df_marks = pd.DataFrame({'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]}) writer = pd.ExcelWriter('output.xlsx') df_marks.to_excel(writer, 'marks') writer.save()
print('DataFrame is written successfully to Excel Sheet.')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23+create+dataframe df_marks+%3D+pd.DataFrame({'name'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C +++++'physics'%3A+[68%2C+74%2C+77%2C+78]%2C +++++'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C +++++'algebra'%3A+[78%2C+88%2C+82%2C+87]}) %23+create+excel+writer writer+%3D+pd.ExcelWriter('output.xlsx') %23+write+dataframe+to+excel+sheet+named+'marks' df_marks.to_excel(writer%2C+'marks') %23+save+the+excel+file writer.save() print('DataFrame+is+written+successfully+to+Excel+Sheet.'))

**Run Program**

![img](https://pythonexamples.org/wp-content/uploads/2019/04/write-dataframe-to-excel-sheet.png)

**Output Excel File**

Open the excel file. Please note the name of the excel sheet. It is named to the string we specified as second argument to to_excel() function.

![img](https://pythonexamples.org/wp-content/uploads/2019/04/excel-output-1.png)





#### [Pandas DataFrame – Get Maximum Value](https://pythonexamples.org/pandas-dataframe-maximum-max/)

To find the maximum value of a Pandas DataFrame, you can use pandas.DataFrame.max() method. Using max(), you can find the maximum value along an axis: row wise or column wise, or maximum of the entire DataFrame.



##### Example 1: Find Maximum of DataFrame along Columns

In this example, we will calculate the maximum along the columns. We will come to know the highest marks obtained by students, subject wise.

**Python Program**

```python
import pandas as pd 
mydictionary = {'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(mydictionary)
print('DataFrame\n----------')
print(df_marks) 
mean = df_marks.max()
print('\nMaximum Value\n------')
print(mean)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'physics'%3A+[68%2C+74%2C+77%2C+78]%2C +++++'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C +++++'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23+create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('DataFrame\n----------') print(df_marks) %23+calculate+max+along+columns mean+%3D+df_marks.max() print('\nMaximum+Value\n------') print(mean))

**Output**

```python
DataFrame
---------- 
physics chemistry algebra
0 68 84 78
1 74 56 88
2 77 73 82
3 78 69 87 
Maximum Value
------
physics 78
chemistry 84
algebra 88
dtype: int64
```



##### Example 2: Find Maximum along Row

In this example, we will find the maximum along rows of the DataFrame. It results in finding the maximum marks obtained by the student for any subject.

**Python Program**

```python
import pandas as pd mydictionary = {'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} df_marks = pd.DataFrame(mydictionary)
print('DataFrame\n----------')
print(df_marks) 
mean = df_marks.max(axis=1)
print('\nMaximum Value\n------')
print(mean)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'physics'%3A+[68%2C+74%2C+77%2C+78]%2C +++++'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C +++++'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23+create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('DataFrame\n----------') print(df_marks) %23+calculate+max+along+columns mean+%3D+df_marks.max(axis%3D1) print('\nMaximum+Value\n------') print(mean))

**Output**

```python
DataFrame
---------- 
physics chemistry algebra
0 68 84 78
1 74 56 88
2 77 73 82
3 78 69 87 
Maximum Value
------
0 84
1 88
2 82
3 87
dtype: int64
```



##### Example 3: Maximum Value of complete DataFrame

In this example, we will find out the maximum value in a DataFrame irrespective of rows or columns.

In the previous examples, we have found maximum value along columns and rows respectively. Apply max() function to the result of the max() function in those cases. You will get the maximum of complete DataFrame.

**Python Program**

```python
import pandas as pd 
mydictionary = {'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(mydictionary)
print('DataFrame\n----------')
print(df_marks) 
mean = df_marks.max().max()
print('\nMaximum Value\n------')
print(mean)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'physics'%3A+[68%2C+74%2C+77%2C+78]%2C +++++'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C +++++'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23+create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('DataFrame\n----------') print(df_marks) %23+calculate+max+of+whole+DataFrame mean+%3D+df_marks.max().max() print('\nMaximum+Value\n------') print(mean))

**Output**

```python
DataFrame
---------- physics chemistry algebra
0 68 84 78
1 74 56 88
2 77 73 82
3 78 69 87 Maximum Value
------
88
```



#### [Pandas DataFrame – Calculate Mean](https://pythonexamples.org/pandas-dataframe-mean/)

To calculate mean of a Pandas DataFrame, you can use pandas.DataFrame.mean() method. Using mean() method, you can calculate mean along an axis, or the complete DataFrame.



##### Example 1: Mean along columns of DataFrame

In this example, we will calculate the mean along the columns. We will come to know the average marks obtained by students, subject wise.

**Python Program**

```python
import pandas as pd mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} df_marks = pd.DataFrame(mydictionary)
print('DataFrame\n----------')
print(df_marks) mean = df_marks.mean()
print('\nMean\n------')
print(mean)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23+create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('DataFrame\n----------') print(df_marks) %23+calculate+mean mean+%3D+df_marks.mean() print('\nMean\n------') print(mean))

**Output**

```python
DataFrame
---------- 
names physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87 
Mean
------
physics 74.25
chemistry 70.50
algebra 83.75
dtype: float64
```

The mean() function returns a Pandas Series. This is the default behavior of the mean() function. Hence, for this particular case, you need not pass any arguments to the mean() function. Or, if you want to explicitly mention to mean() function, to calculate along the columns, pass `axis=0` as shown below.

```python
df_marks.mean(axis=0)
```

[Run](https://pythonexamples.org/run.php?pgm=df_marks.mean(axis%3D0))

##### Example 2: Mean of DataFrame

In this example, we will create a DataFrame with numbers present in all columns, and calculate mean of complete DataFrame.

From the previous example, we have seen that mean() function by default returns mean calculated among columns and return a Pandas Series. Apply mean() on returned series and mean of the complete DataFrame is returned.

**Python Program**

```python
import pandas as pd 
mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(mydictionary)
print('DataFrame\n----------')
print(df_marks) 
mean = df_marks.mean().mean()
print('\nMean\n------')
print(mean)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23+create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('DataFrame\n----------') 

**Output**

```python
DataFrame
---------- 
names physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87 
Mean
------
76.16666666666667
```



##### Example 3: Mean of DataFrame along Rows

In this example, we will calculate the mean of all the columns along rows or `axis=1`. In this particular example, the mean along rows gives the average or percentage of marks obtained by each student.

**Python Program**

```python
import pandas as pd 
mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(mydictionary)
print('DataFrame\n----------')
print(df_marks) 
mean = df_marks.mean(axis=1)
print('\nMean\n------')
print(mean) 
print('\nAverage marks or percentage for each student')
print(pd.concat([df_marks['names'], mean], axis=1))
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23+create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('DataFrame\n----------') 

**Output**

```python
DataFrame
----------
names physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87 
Mean
------
0 76.666667
1 72.666667
2 77.333333
3 78.000000
dtype: float64 Average marks or percentage for each student names 0
0 Somu 76.666667
1 Kiku 72.666667
2 Amol 77.333333
3 Lini 78.000000
```



##### Summary

In this [Pandas Tutorial](https://pythonexamples.org/pandas-examples/), we have learned how to calculate mean of whole DataFrame, mean of DataFrame along column(s) and mean of DataFrame along rows.

#### [Pandas DataFrame – fillna()](https://pythonexamples.org/pandas-dataframe-fillna/)

DataFrame.fillna() method fills(replaces) NA or NaN values in the DataFrame with the specified values.

fillna() method can be used to fill NaN values in the whole DataFrame, or specific columns, or modify inplace, or limit on the number of fillings, or choose an axis along which filling has to take place etc.

In this tutorial, we will go through some of the above scenarios to fill NaN values in DataFrame with example programs.



##### Syntax of DataFrame.fillna

The syntax of DataFrame.fillna() method is

```python
DataFrame.fillna(self, value=None, method=None, axis=None, inplace=False, limit=None, downcast=None) → Union[ForwardRef(‘DataFrame’), NoneType][source]
```

where

- **value** can be scalar, dictionary, pandas Series or a DataFrame
- **method** can be one of these values {‘backfill’, ‘bfill’, ‘pad’, ‘ffill’, None}.
- **axis** can take 0 or ‘index’, 1 or ‘columns’.
- **inplace** is a boolean argument. If True, the DataFrame is modified inplace, and if False a new DataFrame with resulting contents is returned.
- **limit** takes integer or None. This is the maximum number of consecutive NaN values to forward/backward fill. This argument is used only if **method** is specified.
- **downcast** can be a dictionary or None.

The arguments are self explanatory. We have provided the possible values that can be passed for these arguments. And we shall dive into the examples to understand how fillna() can be used.



##### Example 1: DataFrame.fillna() to replace NaN values with 0

This is one of the basic usage of fillna() method, and a good place to start understanding the usage.

In the following program, we shall create a DataFrame with values containing NaN. And we will use fillna() method to replace these NaN values with 0. We pass value `0` for the argument `value` in fillna().

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, 78, 62], [32, 74, np.nan], [np.nan, 54, 76]], columns=['a', 'b', 'c']) df_result = df.fillna(0) print('Original DataFrame\n', df) print('\nResulting DataFrame\n', df_result) 
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) df_result+%3D+df.fillna(0) print('Original+DataFrame\n'%2C+df)+ print('\nResulting+DataFrame\n'%2C+df_result))

**Output**

```python
Original DataFrame a b c
0 NaN 72 67.0
1 23.0 78 62.0
2 32.0 74 NaN
3 NaN 54 76.0 Resulting DataFrame a b c
0 0.0 72 67.0
1 23.0 78 62.0
2 32.0 74 0.0
3 0.0 54 76.0
```



##### Example 2: DataFrame.fillna() to fill NaN values with Column Specific Values

The `value` argument can take a dictionary. This dictionary we pass are a set of column name and value pairs. NaN values in the column are replaced with value specific to the column.

In the following program, we shall create a DataFrame with values containing NaN. And we will use fillna() method to replace these NaN values with different values in different columns. We will pass the dictionary specifying these columns and values.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, np.nan, 62], [32, 74, np.nan], [np.nan, 54, 76]], columns=['a', 'b', 'c']) df_result = df.fillna(value={'a': 0, 'b': 1, 'c': 2}) print('Original DataFrame\n', df) print('\nResulting DataFrame\n', df_result) 
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+np.nan%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) df_result+%3D+df.fillna(value%3D{'a'%3A+0%2C+'b'%3A+1%2C+'c'%3A+2}) print('Original+DataFrame\n'%2C+df)+ print('\nResulting+DataFrame\n'%2C+df_result))

**Output**

```python
Original DataFrame a b c
0 NaN 72.0 67.0
1 23.0 NaN 62.0
2 32.0 74.0 NaN
3 NaN 54.0 76.0 Resulting DataFrame a b c
0 0.0 72.0 67.0
1 23.0 1.0 62.0
2 32.0 74.0 2.0
3 0.0 54.0 76.0
```



##### Example 3: DataFrame.fillna() with inplace=True

By default, fillna() method returns a DataFrame with resulting or modified data. But, if you would like to modify the original DataFrame inplace, pass True for inplace argument.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, np.nan, 62], [32, 74, np.nan], [np.nan, 54, 76]], columns=['a', 'b', 'c'])
print('Original DataFrame\n', df) df.fillna(value=0, inplace=True)
print('\nModified DataFrame\n', df) 
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+np.nan%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Original+DataFrame\n'%2C+df)+ df.fillna(value%3D0%2C+inplace%3DTrue) print('\nModified+DataFrame\n'%2C+df))

**Output**

```python
Original DataFrame a b c
0 NaN 72.0 67.0
1 23.0 NaN 62.0
2 32.0 74.0 NaN
3 NaN 54.0 76.0 Modified DataFrame a b c
0 0.0 72.0 67.0
1 23.0 0.0 62.0
2 32.0 74.0 0.0
3 0.0 54.0 76.0
```

#### [Pandas DataFrame – Replace NaN values with Zero](https://pythonexamples.org/pandas-dataframe-replace-nan-values-with-zero/)

You can replace NaN values with 0 in Pandas DataFrame using DataFrame.fillna() method. Pass zero as argument to fillna() method and call this method on the DataFrame in which you would like to replace NaN values with zero.

fillna() method returns new DataFrame with NaN values replaced by specified value.



##### Sample Code Snippet

Following is a sample code snippet to replace NaN values with 0.

```python
df = df.fillna(0)
```



##### Example 1: Replace NaN values with 0 in DataFrame

In the following Python program, we take a DataFrame with some of the values as NaN (numpy.nan). Then we will use fillna() method to replace these numpy.nan values with zero.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, 78, 62], [32, 74, np.nan], [np.nan, 54, 76]], columns=['a', 'b', 'c'])
print('Original DataFrame\n', df) df = df.fillna(0)
print('\nModified DataFrame\n', df) 
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Original+DataFrame\n'%2C+df)+ df+%3D+df.fillna(0) print('\nModified+DataFrame\n'%2C+df))

**Output**

![img](https://pythonexamples.org/wp-content/uploads/2020/07/pandas-dataframe-replace-nan-with-0.png)

All the NaN values across the DataFrame are replaced with 0.



##### Example 2: Replace NaN values with 0 in Specified Columns of DataFrame

You can also replace NaN values with 0, only in specific columns. Following example program demonstrates how to replace numpy.nan values with 0 for column ‘**a**‘.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, 78, 62], [32, 74, np.nan], [np.nan, 54, 76]], columns=['a', 'b', 'c'])
print('Original DataFrame\n', df) df['a'] = df['a'].fillna(0)
print('\nModified DataFrame\n', df) 
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Original+DataFrame\n'%2C+df)+ df['a']+%3D+df['a'].fillna(0) print('\nModified+DataFrame\n'%2C+df))

**Output**

![img](https://pythonexamples.org/wp-content/uploads/2020/07/pandas-dataframe-column-replace-nan-with-0.png)



#### [Pandas DataFrame – Get Axes Information](https://pythonexamples.org/pandas-dataframe-get-axes-information/)

To get the axes information like index, name of the columns, and datatypes of these, you can use DataFrame.axes property.

In this tutorial, we shall learn how to get the DataFrame axes information.

##### Example 1

In this example, we shall initialize a DataFrame with some rows. Then we shall call axes property on the DataFrame.

**Python Program**

```python
import pandas as pd

df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                    'B': ['B0', 'B1', 'B2', 'B3'],
                    'C': ['C0', 'C1', 'C2', 'C3'],
                    'D': ['D0', 'D1', 'D2', 'D3']},
                   index=[0, 1, 2, 3])

axesInfo = df1.axes

print(axesInfo)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['A0'%2C+'A1'%2C+'A2'%2C+'A3']%2C ++++++++++++++++++++'B'%3A+['B0'%2C+'B1'%2C+'B2'%2C+'B3']%2C ++++++++++++++++++++'C'%3A+['C0'%2C+'C1'%2C+'C2'%2C+'C3']%2C ++++++++++++++++++++'D'%3A+['D0'%2C+'D1'%2C+'D2'%2C+'D3']}%2C +++++++++++++++++++index%3D[0%2C+1%2C+2%2C+3]) axesInfo+%3D+df1.axes print(axesInfo))

**Output**

```
D:\>python example.py
[Int64Index([0, 1, 2, 3], dtype='int64'), Index(['A', 'B', 'C', 'D'], dtype='object')]
```

##### Example 2

In this example, we have initialized a DataFrame without index. We shall observe what DataFrame.axes property returns.

**Python Program**

```python
import pandas as pd

df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                    'B': ['B0', 'B1', 'B2', 'B3'],
                    'C': ['C0', 'C1', 'C2', 'C3'],
                    'D': ['D0', 'D1', 'D2', 'D3']})

axesInfo = df1.axes

print(axesInfo)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['A0'%2C+'A1'%2C+'A2'%2C+'A3']%2C ++++++++++++++++++++'B'%3A+['B0'%2C+'B1'%2C+'B2'%2C+'B3']%2C ++++++++++++++++++++'C'%3A+['C0'%2C+'C1'%2C+'C2'%2C+'C3']%2C ++++++++++++++++++++'D'%3A+['D0'%2C+'D1'%2C+'D2'%2C+'D3']}) axesInfo+%3D+df1.axes print(axesInfo))

**Output**

```python
D:\>python example.py
[RangeIndex(start=0, stop=4, step=1), Index(['A', 'B', 'C', 'D'], dtype='object')]
```

A default index shall be created when you do not provide during DataFrame initialization. The same is reflected when we accessed DataFrame.axes property.

#### [Pandas DataFrame – Inner Join](https://pythonexamples.org/pandas-dataframes-inner-join/)

You can inner join two DataFrames during concatenation which results in the intersection of the two DataFrames.

##### syntax 

The syntax of concat() function to inner join is given below.

```python
pd.concat([df1, df2], axis=1, join='inner')
```

[Run](https://pythonexamples.org/run.php?pgm=pd.concat([df1%2C+df2]%2C+axis%3D1%2C+join%3D'inner'))

Inner join results in a DataFrame that has intersection along the given axis to the concatenate function.



##### Example 1: Inner Join DataFrames

In this example, we shall take two DataFrames and find their inner join along axis=1.

**Python Program**

```python
import pandas as pd df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'], 'B': ['B0', 'B1', 'B2', 'B3'], 'C': ['C0', 'C1', 'C2', 'C3'], 'D': ['D0', 'D1', 'D2', 'D3']}, index=[0, 1, 2, 3]) df2 = pd.DataFrame({'B': ['B2', 'B3', 'B4', 'B5'], 'D': ['D2', 'D3', 'D4', 'D5'], 'F': ['F2', 'F3', 'F4', 'F5']}, index=[2, 3, 4, 5]) result = pd.concat([df1, df2], axis=1, join='inner') print(result)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['A0'%2C+'A1'%2C+'A2'%2C+'A3']%2C ++++++++++++++++++++'B'%3A+['B0'%2C+'B1'%2C+'B2'%2C+'B3']%2C ++++++++++++++++++++'C'%3A+['C0'%2C+'C1'%2C+'C2'%2C+'C3']%2C ++++++++++++++++++++'D'%3A+['D0'%2C+'D1'%2C+'D2'%2C+'D3']}%2C +++++++++++++++++++index%3D[0%2C+1%2C+2%2C+3]) df2+%3D+pd.DataFrame({'B'%3A+['B2'%2C+'B3'%2C+'B4'%2C+'B5']%2C ++++++++++++++++++++'D'%3A+['D2'%2C+'D3'%2C+'D4'%2C+'D5']%2C ++++++++++++++++++++'F'%3A+['F2'%2C+'F3'%2C+'F4'%2C+'F5']}%2C +++++++++++++++++++index%3D[2%2C+3%2C+4%2C+5]) result+%3D+pd.concat([df1%2C+df2]%2C+axis%3D1%2C+join%3D'inner') print(result))

**Output**

```python
D:\>python example.py A B C D B D F
2 A2 B2 C2 D2 B2 D2 F2
3  A3  B3  C3  D3  B3  D3  F3
```



##### Example 2: Inner Join DataFrames

In this example, we shall try the inner join of DataFrames along a different axis from that of the previous example.

**Python Program**

```python
import pandas as pd df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'], 'B': ['B0', 'B1', 'B2', 'B3'], 'C': ['C0', 'C1', 'C2', 'C3'], 'D': ['D0', 'D1', 'D2', 'D3']}, index=[0, 1, 2, 3]) df2 = pd.DataFrame({'B': ['B2', 'B3', 'B4', 'B5'], 'D': ['D2', 'D3', 'D4', 'D5'], 'F': ['F2', 'F3', 'F4', 'F5']}, index=[2, 3, 4, 5]) result = pd.concat([df1, df2], axis=0, join='inner') print(result)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['A0'%2C+'A1'%2C+'A2'%2C+'A3']%2C ++++++++++++++++++++'B'%3A+['B0'%2C+'B1'%2C+'B2'%2C+'B3']%2C ++++++++++++++++++++'C'%3A+['C0'%2C+'C1'%2C+'C2'%2C+'C3']%2C ++++++++++++++++++++'D'%3A+['D0'%2C+'D1'%2C+'D2'%2C+'D3']}%2C +++++++++++++++++++index%3D[0%2C+1%2C+2%2C+3]) df2+%3D+pd.DataFrame({'B'%3A+['B2'%2C+'B3'%2C+'B4'%2C+'B5']%2C ++++++++++++++++++++'D'%3A+['D2'%2C+'D3'%2C+'D4'%2C+'D5']%2C ++++++++++++++++++++'F'%3A+['F2'%2C+'F3'%2C+'F4'%2C+'F5']}%2C +++++++++++++++++++index%3D[2%2C+3%2C+4%2C+5]) result+%3D+pd.concat([df1%2C+df2]%2C+axis%3D0%2C+join%3D'inner') print(result))

**Output**

```python
D:\>python example.py B D
0 B0 D0
1 B1 D1
2 B2 D2
3 B3 D3
2 B2 D2
3 B3 D3
4 B4 D4
5  B5  D5
```



##### Example 3: Inner Join more than two DataFrames using concat()

In this example, we shall take more than two DataFrames, which is three, and find the inner join of these DataFrames along an axis.

**Python Program**

```python
import pandas as pd df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'], 'B': ['B0', 'B1', 'B2', 'B3'], 'C': ['C0', 'C1', 'C2', 'C3'], 'D': ['D0', 'D1', 'D2', 'D3']}, index=[0, 1, 2, 3]) df2 = pd.DataFrame({'B': ['B2', 'B3', 'B4', 'B5'], 'D': ['D2', 'D3', 'D4', 'D5'], 'F': ['F2', 'F3', 'F4', 'F5']}, index=[2, 3, 4, 5]) df3 = pd.DataFrame({'D': ['D3', 'D4', 'D5'], 'G': ['G3', 'G4', 'G5']}, index=[3, 4, 5]) result = pd.concat([df1, df2, df3], axis=1, join='inner') print(result)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df1+%3D+pd.DataFrame({'A'%3A+['A0'%2C+'A1'%2C+'A2'%2C+'A3']%2C ++++++++++++++++++++'B'%3A+['B0'%2C+'B1'%2C+'B2'%2C+'B3']%2C ++++++++++++++++++++'C'%3A+['C0'%2C+'C1'%2C+'C2'%2C+'C3']%2C ++++++++++++++++++++'D'%3A+['D0'%2C+'D1'%2C+'D2'%2C+'D3']}%2C +++++++++++++++++++index%3D[0%2C+1%2C+2%2C+3]) df2+%3D+pd.DataFrame({'B'%3A+['B2'%2C+'B3'%2C+'B4'%2C+'B5']%2C ++++++++++++++++++++'D'%3A+['D2'%2C+'D3'%2C+'D4'%2C+'D5']%2C ++++++++++++++++++++'F'%3A+['F2'%2C+'F3'%2C+'F4'%2C+'F5']}%2C +++++++++++++++++++index%3D[2%2C+3%2C+4%2C+5]) df3+%3D+pd.DataFrame({'D'%3A+['D3'%2C+'D4'%2C+'D5']%2C ++++++++++++++++++++'G'%3A+['G3'%2C+'G4'%2C+'G5']}%2C +++++++++++++++++++index%3D[3%2C+4%2C+5]) result+%3D+pd.concat([df1%2C+df2%2C+df3]%2C+axis%3D1%2C+join%3D'inner') print(result))

**Output**

```python
D:\>python example.py A B C D B D F D G
3  A3  B3  C3  D3  B3  D3  F3  D3  G3
```

### **Cell Operations**

#### [Pandas DataFrame – Check if Cell Value is NaN](https://pythonexamples.org/pandas-check-if-cell-value-is-nan/)

In this tutorial, we will learn how to check if a cell value is NaN (np.nan) in Pandas.

NaN means Not a Number. Pandas uses numpy.nan as NaN value.

To check if value at a specific location in Pandas is NaN or not, call numpy.isnan() function with the value passed as argument.

```python
numpy.isnan(value)
```

If value equals numpy.nan, the expression returns True, else it returns False.



##### Example 1: Check if Cell Value is NaN in Pandas DataFrame

In this example, we will take a DataFrame with NaN values at some locations. We will check if values at specific locations are NaN or not.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, 78, 62], [32, 74, np.nan], [np.nan, 54, 76]], columns=['a', 'b', 'c']) value = df.at[0, 'a'] isNaN = np.isnan(value)
print("Is value at df[0, 'a'] NaN :", isNaN) value = df.at[0, 'b'] isNaN = np.isnan(value)
print("Is value at df[0, 'b'] NaN :", isNaN)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) value+%3D+df.at[0%2C+'a']++%23nan isNaN+%3D+np.isnan(value) print("Is+value+at+df[0%2C+'a']+NaN+%3A"%2C+isNaN) value+%3D+df.at[0%2C+'b']++%2372 isNaN+%3D+np.isnan(value) print("Is+value+at+df[0%2C+'b']+NaN+%3A"%2C+isNaN))

**Output**

```python
Is value at df[0, 'a'] NaN : True
Is value at df[0, 'b'] NaN : False
```



##### Example 2: Check if Cell Value is NaN in Pandas DataFrame Iteratively

In this example, we will take a DataFrame with NaN values at some locations. We will iterate over each of the cell values in this DataFrame and check if the value at this location is NaN or not.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[np.nan, 72, 67], [23, 78, 62], [32, 74, np.nan], [np.nan, 54, 76]]) for i in range(df.shape[0]): for j in range(df.shape[1]): value = df.at[i, j] print(np.isnan(value), end="\t") print()
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[np.nan%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+np.nan]%2C [np.nan%2C+54%2C+76]]) for+i+in+range(df.shape[0])%3A+%23iterate+over+rows ++++for+j+in+range(df.shape[1])%3A+%23iterate+over+columns ++++++++value+%3D+df.at[i%2C+j]+%23get+cell+value ++++++++print(np.isnan(value)%2C+end%3D"\t") ++++print())

**Output**

```python
True False False
False False False
False False True
True False False
```

 #### [Pandas DataFrame – Iterate over Cells](https://pythonexamples.org/pandas-dataframe-iterate-over-cells/)

In this tutorial, we will learn how to iterate over cell values of a Pandas DataFrame.

**Method 1**: Use a nested for loop to traverse the cells with the help of DataFrame Dimensions.

**Method 2**: Iterate over rows of DataFrame using DataFrame.iterrows(), and for each row, iterate over the items using Series.items().



##### Example 1: Iterate over Cells in Pandas DataFrame using DataFrame.shape

In this example, we will use a nested for loop to iterate over the rows and columns of Pandas DataFrame. We will take the help of DataFrame.shape to get the number of rows and number of columns in the DataFrame. To access the cell value, we will use DataFrame.at().

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]) for i in range(df.shape[0]): for j in range(df.shape[1]): value = df.at[i, j] print(value, end="\t") print()
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[1%2C+2%2C+3]%2C [4%2C+5%2C+6]%2C [7%2C+8%2C+9]%2C [10%2C+11%2C+12]]) for+i+in+range(df.shape[0])%3A+%23iterate+over+rows ++++for+j+in+range(df.shape[1])%3A+%23iterate+over+columns ++++++++value+%3D+df.at[i%2C+j]+%23get+cell+value ++++++++print(value%2C+end%3D"\t") ++++print())

**Output**

```python
1 2 3
4 5 6
7 8 9
10 11 12
```



##### Example 2: Iterate over Cells in Pandas

In this example, we will use a nested for loop to iterate over the rows and columns of Pandas DataFrame.

To iterate over the rows, we will use DataFrame.iterrows(). And for each row, which we get as a Series, we will iterate over the items using Series.items().

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]) for rowIndex, row in df.iterrows(): for columnIndex, value in row.items(): print(value, end="\t") print()
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [[1%2C+2%2C+3]%2C [4%2C+5%2C+6]%2C [7%2C+8%2C+9]%2C [10%2C+11%2C+12]]) for+rowIndex%2C+row+in+df.iterrows()%3A+%23iterate+over+rows ++++for+columnIndex%2C+value+in+row.items()%3A ++++++++print(value%2C+end%3D"\t") ++++print())

**Output**

```python
1 2 3
4 5 6
7 8 9
10 11 12
```

We have access to row index and column index as well, while traversing through the cells in the DataFrame.

### Pandas DataFrame Column Operations
#### [Pandas – Get Column Names](https://pythonexamples.org/pandas-dataframe-get-column-names/)

You can access the column names of DataFrame using columns property.

```python
DataFrame.columns
```

It returns an object. You can access the column names using index.

补充：获取列标签并转为一个list

```python
column_headers_list  = df.columns.values.list()
```



##### Example 1: Print DataFrame Column Names

In this example, we get the dataframe column names and print them.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [['Amol', 72, 67, 91], ['Lini', 78, 69, 87], ['Kiku', 74, 56, 88], ['Ajit', 54, 76, 78]], columns=['name', 'physics', 'chemistry', 'algebra']) 
cols = df.columns 
print(cols)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91]%2C ['Lini'%2C+78%2C+69%2C+87]%2C ['Kiku'%2C+74%2C+56%2C+88]%2C ['Ajit'%2C+54%2C+76%2C+78]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C+'algebra'])	 %23get+the+dataframe+columns cols+%3D+df.columns+ %23print+the+columns print(cols))

**Output**

```python
Index(['name', 'physics', 'chemistry', 'algebra'], dtype='object')
```



##### Example 2: Access Individual Column Names using Index

You can access individual column names using the index.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [['Amol', 72, 67, 91], ['Lini', 78, 69, 87], ['Kiku', 74, 56, 88], ['Ajit', 54, 76, 78]], columns=['name', 'physics', 'chemistry', 'algebra']) 
cols = df.columns 
for i in range(len(cols)): 
    print(cols[i])
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91]%2C ['Lini'%2C+78%2C+69%2C+87]%2C ['Kiku'%2C+74%2C+56%2C+88]%2C ['Ajit'%2C+54%2C+76%2C+78]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C+'algebra'])	 %23get+the+dataframe+columns cols+%3D+df.columns+ %23print+the+columns for+i+in+range(len(cols))

**Output**

```python
name
physics
chemistry
algebra
```



##### Example 3: Print Columns using For Loop

You can use for loop to iterate over the columns of dataframe.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [['Amol', 72, 67, 91], ['Lini', 78, 69, 87], ['Kiku', 74, 56, 88], ['Ajit', 54, 76, 78]], columns=['name', 'physics', 'chemistry', 'algebra']) 
cols = df.columns 
for column in cols: print(column)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [['Amol'%2C+72%2C+67%2C+91]%2C ['Lini'%2C+78%2C+69%2C+87]%2C ['Kiku'%2C+74%2C+56%2C+88]%2C ['Ajit'%2C+54%2C+76%2C+78]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C+'algebra'])	 %23get+the+dataframe+columns cols+%3D+df.columns+ %23print+the+columns for+column+in+cols%3A print(column))

**Output**

```python
name
physics
chemistry
algebra
```



#### [Pandas – Change Column Labels](https://pythonexamples.org/pandas-dataframe-change-rename-column-labels/)

##### Syntax

The syntax to assign new column names is given below.

```python
dataframe.columns = new_columns
```

The `new_columns` should be an array of length same as that of number of columns in the dataframe.



##### Example 1: Rename Column Labels of DataFrame

In this example, we will create a dataframe with some initial column names and then change them by assigning columns attribute of the dataframe.

**Python Program**

```python
import numpy as np
import pandas as pd 
df_marks = pd.DataFrame( [['Somu', 68, 84, 78, 96], ['Kiku', 74, 56, 88, 85], ['Amol', 77, 73, 82, 87], ['Lini', 78, 69, 87, 92]], columns=['name', 'physics', 'chemistry', 'algebra', 'calculus']) 
print('Original DataFrame\n------------------------')
print(df_marks) 
df_marks.columns = ['name', 'physics', 'biology', 'geometry', 'calculus']
print('\n\nColumns Renamed\n------------------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+numpy+as+np import+pandas+as+pd df_marks+%3D+pd.DataFrame( [['Somu'%2C+68%2C+84%2C+78%2C+96]%2C ['Kiku'%2C+74%2C+56%2C+88%2C+85]%2C ['Amol'%2C+77%2C+73%2C+82%2C+87]%2C ['Lini'%2C+78%2C+69%2C+87%2C+92]]%2C columns%3D['name'%2C+'physics'%2C+'chemistry'%2C+'algebra'%2C+'calculus']) print('Original+DataFrame\n------------------------') print(df_marks) %23rename+columns df_marks.columns+%3D+['name'%2C+'physics'%2C+'biology'%2C+'geometry'%2C+'calculus'] print('\n\nColumns+Renamed\n------------------------') print(df_marks))

**Output**

```python
Original DataFrame
------------------------ 
name physics chemistry algebra calculus
0 Somu 68 84 78 96
1 Kiku 74 56 88 85
2 Amol 77 73 82 87
3 Lini 78 69 87 92 Columns Renamed
------------------------ 
name physics biology geometry calculus
0 Somu 68 84 78 96
1 Kiku 74 56 88 85
2 Amol 77 73 82 87
3 Lini 78 69 87 92
```

New column labels have been applied to the DataFrame.

##### **补充问题**：

有一个DataFrame，列名为：`['$a', '$b', '$c', '$d', '$e']`
现需要改为：`['a', 'b', 'c', 'd', 'e']`
有何办法？

```python
import pandas as pd
df = pd.DataFrame({'$a': [1], '$b': [1], '$c': [1], '$d': [1], '$e': [1]})
```

**解决**：

##### 方式一：columns属性

```python
# ①暴力
df.columns = ['a', 'b', 'c', 'd', 'e']

# ②修改
df.columns = df.columns.str.strip('$')

# ③修改
df.columns = df.columns.map(lambda x:x[1:])
```

##### 方式二：rename方法、columns参数

```python
# ④暴力（好处：也可只修改特定的列）
df.rename(columns=('$a': 'a', '$b': 'b', '$c': 'c', '$d': 'd', '$e': 'e'}, inplace=True) 

# ⑤修改
df.rename(columns=lambda x:x.replace('$',''), inplace=True)
```

标签: [python](https://www.cnblogs.com/hhh5460/tag/python/), [pandas](

#### [Pandas – Get Datatypes of Columns](https://pythonexamples.org/get-datatypes-of-columns-in-pandas-dataframe/)

To get the datatypes of columns in a Pandas DataFrame, call DataFrame.dtypes property. The DataFrame.dtypes property returns an object of type pandas.Series with the datatypes of each column in it.

##### syntax

The syntax to use dtypes property of a DataFrame is

```python
DataFrame.dtypes
```

In the following program, we have created a DataFrame with specific data and column names. Let us get the datatypes of columns in this DataFrame using **DataFrame.dtypes**.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [['abc', 22], ['xyz', 25], ['pqr', 31]], columns=['name', 'age']) datatypes = df.dtypes
print(datatypes)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[['abc'%2C+22]%2C ++++['xyz'%2C+25]%2C ++++['pqr'%2C+31]]%2C ++++columns%3D['name'%2C+'age']) datatypes+%3D+df.dtypes print(datatypes))

**Output**

```python
name object
age int64
dtype: object
```

We can print the elements of the returned value by DataFrame.dtypes using a [for loop](https://pythonexamples.org/python-for-loop-example/) as shown in the following.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [['abc', 22], ['xyz', 25], ['pqr', 31]], columns=['name', 'age']) datatypes = df.dtypes
for dtype in datatypes: print(dtype)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[['abc'%2C+22]%2C ++++['xyz'%2C+25]%2C ++++['pqr'%2C+31]]%2C ++++columns%3D['name'%2C+'age']) datatypes+%3D+df.dtypes for+dtype+in+datatypes%3A ++++print(dtype))

**Output**

```python
object
int64
```

#### [Pandas – Rename Column](https://pythonexamples.org/pandas-dataframe-rename-columns/)

You can rename a single column or multiple columns of a pandas DataFrame using pandas.DataFrame.rename() method.

In the following set of examples, we will learn how to rename a single column, and how to rename multiple columns of Pandas DataFrame.



##### Example 1: Rename Single Column

To rename a single column, you can use `DataFrame.rename()` function as shown below.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[41, 72, 67, 91], [21, 78, 69, 87], [95, 74, 56, 88], [54, 54, 76, 78]], columns=['a', 'b', 'c', 'd']) 
df.rename(columns={'b': 'k'}, inplace=True) print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[41%2C+72%2C+67%2C+91]%2C [21%2C+78%2C+69%2C+87]%2C [95%2C+74%2C+56%2C+88]%2C [54%2C+54%2C+76%2C+78]]%2C columns%3D['a'%2C+'b'%2C+'c'%2C+'d'])	 %23rename+single+column df.rename(columns%3D{'b'%3A+'k'}%2C+inplace%3DTrue) %23print+the+columns print(df))

**Output**

```python
 a k c d
0 41 72 67 91
1 21 78 69 87
2 95 74 56 88
3 54 54 76 78
```

The column name `b` has been renamed to `k` for the Pandas DataFrame.



##### Example 2: Rename Multiple Columns

To rename multiple columns, you can use `DataFrame.rename()` method with multiple old column names and new column names as key:value pairs as shown below.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame( [[41, 72, 67, 91], [21, 78, 69, 87], [95, 74, 56, 88], [54, 54, 76, 78]], columns=['a', 'b', 'c', 'd']) 
df.rename(columns={'b': 'k', 'c': 'm'}, inplace=True) print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[41%2C+72%2C+67%2C+91]%2C [21%2C+78%2C+69%2C+87]%2C [95%2C+74%2C+56%2C+88]%2C [54%2C+54%2C+76%2C+78]]%2C columns%3D['a'%2C+'b'%2C+'c'%2C+'d'])	 %23rename+single+column df.rename(columns%3D{'b'%3A+'k'%2C+'c'%3A+'m'}%2C+inplace%3DTrue) %23print+the+columns print(df))

**Output**

```python
 a k m d
0 41 72 67 91
1 21 78 69 87
2 95 74 56 88
3 54 54 76 78
```

The column named `b` has been renamed to `k` and column `c` has been renamed to `m`



#### [Pandas – Select Column](https://pythonexamples.org/pandas-dataframe-select-column/)

You can select a column from Pandas DataFrame using dot notation or either with brackets.



##### Syntax

```python
a = myDataframe.column_name 
a = myDataframe[coulumn_name]
```

[Run](https://pythonexamples.org/run.php?pgm=%23select+column+using+dot+operator a+%3D+myDataframe.column_name %23select+column+using+square+brackets a+%3D+myDataframe[coulumn_name])

Selecting a column return Pandas Series.



##### Example 1: Select a Column using Dot Operator

In this example, we will select a column, from pre-initialized dataframe, using dot operator `. `. And shall print the column contents and its datatype.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'a': [57, 43, 85], 'b': [92, 30, 66]}) 
a = df.a 
print('Selected Column\n---------------\n',a,sep='')
print('\n',type(a),sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[57%2C+43%2C+85]%2C+'b'%3A+[92%2C+30%2C+66]}) %23select+column a+%3D+df.a print('Selected+Column\n---------------\n'%2Ca%2Csep%3D'') print('\n'%2Ctype(a)%2Csep%3D''))

**Output**

```python
Selected Column
---------------
0 57
1 43
2 85
Name: a, dtype: int64 <class 'pandas.core.series.Series'>
```

The selected column is of class type `pandas.core.series.Series`.



##### Example 2: Select a column using Square Brackets

In this example, we will select a column from Pandas DataFrame using square brackets `[]`.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'a': [57, 43, 85], 'b': [92, 30, 66]}) 
a = df['a'] 
print('Selected Column\n---------------\n',a,sep='')
print('\n',type(a),sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[57%2C+43%2C+85]%2C+'b'%3A+[92%2C+30%2C+66]}) %23select+column a+%3D+df['a'] print('Selected+Column\n---------------\n'%2Ca%2Csep%3D'') print('\n'%2Ctype(a)%2Csep%3D''))

**Output**

```python
Selected Column
---------------
0 57
1 43
2 85
Name: a, dtype: int64 <class 'pandas.core.series.Series'>
```

Selecting a column using square brackets is preferred because in some special scenarios, which we will discuss in the following examples, using dot operator does not work.



##### Example 3: Select Column whose name has spaces

In this example, we will select column whose name coincides with a function name.

Using dot operator in this scenario returns the column as a method.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'sum': [57, 43, 85], 'b': [92, 30, 66]}) 
a = df.sum 
print('Selected Column\n---------------\n',a,sep='')
print('\n',type(a),sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'sum'%3A+[57%2C+43%2C+85]%2C+'b'%3A+[92%2C+30%2C+66]}) %23select+column a+%3D+df.sum print('Selected+Column\n---------------\n'%2Ca%2Csep%3D'') print('\n'%2Ctype(a)%2Csep%3D''))

**Output**

```python
Selected Column
---------------
<bound method DataFrame.sum of sum b
0 57 92
1 43 30
2 85 66> <class 'method'>
```

Using square brackets will select a column and return the Series.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'sum': [57, 43, 85], 'b': [92, 30, 66]}) 
a = df['sum'] 
print('Selected Column\n---------------\n',a,sep='')
print('\n',type(a),sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'sum'%3A+[57%2C+43%2C+85]%2C+'b'%3A+[92%2C+30%2C+66]}) %23select+column a+%3D+df['sum'] print('Selected+Column\n---------------\n'%2Ca%2Csep%3D'') print('\n'%2Ctype(a)%2Csep%3D''))

**Output**

```python
Selected Column
---------------
0 57
1 43
2 85
Name: sum, dtype: int64 <class 'pandas.core.series.Series'>
```



##### Example 4: Select Column Name with Spaces

In this example, we will select column whose name coincides with a function name.

Using dot operator in this scenario throws SyntaxError.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'a': [57, 43, 85], 'b': [92, 30, 66], 'sum a b': [149, 73, 151]}) 
a = df.sum a b 
print('Selected Column\n---------------\n',a,sep='')
print('\n',type(a),sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[57%2C+43%2C+85]%2C+'b'%3A+[92%2C+30%2C+66]%2C+'sum+a+b'%3A+[149%2C+73%2C+151]}) %23select+column a+%3D+df.sum+a+b print('Selected+Column\n---------------\n'%2Ca%2Csep%3D'') print('\n'%2Ctype(a)%2Csep%3D''))

**Output**

```python
 File "example1.py", line 7 a = df.sum a b ^
SyntaxError: invalid syntax
```

Using square brackets will select the column with spaces and returns Series.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'a': [57, 43, 85], 'b': [92, 30, 66], 'sum a b': [149, 73, 151]}) 
a = df['sum a b'] 
print('Selected Column\n---------------\n',a,sep='')
print('\n',type(a),sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[57%2C+43%2C+85]%2C+'b'%3A+[92%2C+30%2C+66]%2C+'sum+a+b'%3A+[149%2C+73%2C+151]}) %23select+column a+%3D+df['sum+a+b'] print('Selected+Column\n---------------\n'%2Ca%2Csep%3D'') print('\n'%2Ctype(a)%2Csep%3D''))

**Output**

```python
Selected Column
---------------
0 149
1 73
2 151
Name: sum a b, dtype: int64 <class 'pandas.core.series.Series'>
```



#### [Pandas – Select Columns of Numeric Datatype](https://pythonexamples.org/pandas-dataframe-select-columns-of-numeric-datatype/)

To select columns that are only of numeric datatype from a Pandas DataFrame, call DataFrame.select_dtypes() method and pass `np.number` or `'number'` as argument for include parameter. The DataFrame.select_dtypes() method for this given argument returns a subset of this DataFrame with only numeric columns.

The syntax to call select_datatypes() method of a DataFrame is

```python
DataFrame.select_dtypes(include=None, exclude=None)
```



##### Example 1: Select Numeric Columns from DataFrame

In this example, we have created a DataFrame and we shall get only those columns which are numeric using DataFrame.select_dtypes() method.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [['abc', 22, 22.6], ['xyz', 25, 23.2], ['pqr', 31, 30.5]], columns=['name', 'age', 'bmi']) result = df.select_dtypes(include='number')
print(result)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame( ++++[['abc'%2C+22%2C+22.6]%2C ++++['xyz'%2C+25%2C+23.2]%2C ++++['pqr'%2C+31%2C+30.5]]%2C ++++columns%3D['name'%2C+'age'%2C+'bmi']) result+%3D+df.select_dtypes(include%3D'number') print(result))

**Output**

```python
 age bmi
0 22 22.6
1 25 23.2
2 31 30.5
```

Only the columns with numeric datatype are selected from this DataFrame.



#### [Pandas – Sort by Column](https://pythonexamples.org/pandas-dataframe-sort-by-column/)

To sort the rows of a DataFrame by a column, use `pandas.DataFrame.sort_values()` method with the argument `by=column_name`. The sort_values() method does not modify the original DataFrame, but returns the sorted DataFrame.

You can sort the dataframe in ascending or descending order of the column values. In this tutorial, we shall go through some example programs, where we shall sort dataframe in ascending or descending order.



##### Example 1: Sort DataFrame by a Column in Ascending Order

The default sorting order of sort_values() function is ascending order. In this example, we will create a dataframe and sort the rows by a specific column in ascending order.

**Python Program**

```python
import pandas as pd 
data = {'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(data) 
sorted_df = df_marks.sort_values(by='algebra')
print(sorted_df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd data+%3D+{'name'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} 	 %23create+dataframe df_marks+%3D+pd.DataFrame(data) %23sort+dataframe sorted_df+%3D+df_marks.sort_values(by%3D'algebra') print(sorted_df))

**Output**

```python
 name physics chemistry algebra
0 Somu 68 84 78
2 Amol 77 73 82
3 Lini 78 69 87
1 Kiku 74 56 88
```

You can see that the rows are sorted based on the increasing order of the column **algebra**.



##### Example 2: Sort DataFrame by a Column in Descending Order

To sort the dataframe in descending order a column, pass `ascending=False` argument to the `sort_values()` method. . In this example, we will create a dataframe and sort the rows by a specific column in descending order.

**Python Program**

```python
import pandas as pd 
data = {'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(data) 
sorted_df = df_marks.sort_values(by='algebra', ascending=False)
print(sorted_df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd data+%3D+{'name'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} 	 %23create+dataframe df_marks+%3D+pd.DataFrame(data) %23sort+dataframe sorted_df+%3D+df_marks.sort_values(by%3D'algebra'%2C+ascending%3DFalse) print(sorted_df))

**Output**

```python
 name physics chemistry algebra
1 Kiku 74 56 88
3 Lini 78 69 87
2 Amol 77 73 82
0 Somu 68 84 78
```

You can see that the rows are sorted based on the decreasing order of the column **algebra**.

#### [Pandas – Add Column](https://pythonexamples.org/pandas-dataframe-add-column/)

To add a new column to the existing Pandas DataFrame, assign the new column values to the DataFrame, indexed using the new column name.

In this tutorial, we shall learn how to add a column to DataFrame, with the help of example programs, that are going to be very detailed and illustrative.



##### Syntax – Add Column

The syntax to add a column to DataFrame is:

```python
mydataframe['new_column_name'] = column_values
```

where **mydataframe** is the dataframe to which you would like to add the new column with the label **new_column_name**. You can either provide all the column values as a list or a single value that is taken as default value for all of the rows.



##### Example 1: Add Column to Pandas DataFrame

In this example, we will create a dataframe `df_marks` and add a new column with name `geometry`.

**Python Program**

```python
import pandas as pd mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} df_marks = pd.DataFrame(mydictionary)
print('Original DataFrame\n--------------')
print(df_marks) df_marks['geometry'] = [81, 92, 67, 76]
print('\n\nDataFrame after adding "geometry" column\n--------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('Original+DataFrame\n--------------') print(df_marks) %23add+column df_marks['geometry']+%3D+[81%2C+92%2C+67%2C+76] print('\n\nDataFrame+after+adding+"geometry"+column\n--------------') print(df_marks))

**Output**

```python
Original DataFrame
-------------- names physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87 DataFrame after adding "geometry" column
-------------- names physics chemistry algebra geometry
0 Somu 68 84 78 81
1 Kiku 74 56 88 92
2 Amol 77 73 82 67
3 Lini 78 69 87 76
```

The column is added to the dataframe with the specified list as column values.

The length of the list you provide for the new column should equal the number of rows in the dataframe. If this condition fails, you will get an error similar to the following.

```python
ValueError: Length of values does not match length of index
```

[Run](https://pythonexamples.org/run.php?pgm=ValueError%3A+Length+of+values+does+not+match+length+of+index)

##### Example 2: Add Column to Pandas DataFrame with a Default Value

In this example, we will create a dataframe **df_marks** and add a new column called **geometry** with a default value for each of the rows in the dataframe.

**Python Program**

```python
import pandas as pd mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} df_marks = pd.DataFrame(mydictionary)
print('Original DataFrame\n--------------')
print(df_marks) df_marks['geometry'] = 65
print('\n\nDataFrame after adding "geometry" column\n--------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('Original+DataFrame\n--------------') 

**Output**

```python
Original DataFrame
-------------- names physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87 DataFrame after adding "geometry" column
-------------- names physics chemistry algebra geometry
0 Somu 68 84 78 65
1 Kiku 74 56 88 65
2 Amol 77 73 82 65
3 Lini 78 69 87 65
```

The column is added to the dataframe with the specified value as default column value.

#### [Pandas – Delete Column](https://pythonexamples.org/pandas-dataframe-delete-column/)

Pandas DataFrame.pop() function is used to delete a column from the DataFrame.

In this tutorial, we shall go through examples to learn how to use pop() to delete a column from Pandas DataFrame.



##### Example 1: Delete a column using pandas pop() function

In this example, we deleted a specific column, using column name, from the DataFrame with pop(). pandas pop() function updates the original dataframe. The data in the deleted column is lost.

**Python Program**

```python
import pandas as pd 
mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(mydictionary)
print('Original DataFrame\n--------------')
print(df_marks) 
df_marks.pop('algebra')
print('\n\nDataFrame after deleting column\n--------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('Original+DataFrame\n--------------') print(df_marks) %23delete+column df_marks.pop('algebra') print('\n\nDataFrame+after+deleting+column\n--------------') print(df_marks))

**Output**

![pandas pop function example](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-drop-single-column.png)pandas dataframe.pop()



##### Example 2: Delete a non-existing column using pandas pop() function

In this example, we will try deleting a column that is not present in the DataFrame.

When you try to delete a non-existing column of DataFrame using pop(), the function pop() throws KeyError.

**Python Program**

```python
import pandas as pd mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 
df_marks = pd.DataFrame(mydictionary)
print('Original DataFrame\n--------------')
print(df_marks) 
df_marks.pop('geometry')
print('\n\nDataFrame after deleting column\n--------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('Original+DataFrame\n--------------') print(df_marks) %23delete+column+that+is+not+present df_marks.pop('geometry') print('\n\nDataFrame+after+deleting+column\n--------------') print(df_marks))

**Output**

![pandas pop function throwing KeyError](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-pop-example.png)pandas pop() throwing KeyError





#### [Pandas – Set Column as Index](https://pythonexamples.org/pandas-set-column-as-index/)

By default an index is created for DataFrame. But, you can set a specific column of DataFrame as index, if required.

To set a column as index for a DataFrame, use `DataFrame.set_index()` function, with the column name passed as argument.

![Pandas DataFrame - Set Column as Index](https://pythonexamples.org/images/python-pandas-dataframe-set-column-as-index.svg)

You can also setup MultiIndex with multiple columns in the index. In this case, pass the array of column names required for index, to set_index() method.



##### Syntax of set_index()

The syntax of set_index() to setup a column as index is

```python
myDataFrame.set_index('column_name')
```

where `myDataFrame` is the DataFrame for which you would like to set `column_name` column as index.

To setup MultiIndex, use the following syntax.

```python
myDataFrame.set_index(['column_name_1', column_name_2])
```

[Run](https://pythonexamples.org/run.php?pgm=myDataFrame.set_index(['column_name_1'%2C+column_name_2]))

You can pass as many column names as required.

Note that `set_index()` method does not modify the original DataFrame, but returns the DataFrame with the column set as index.



##### Example 1: Set Column as Index in Pandas DataFrame

In this example, we take a DataFrame, and try to set a column as index.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 'Amol', 72, 67], [23, 'Lini', 78, 69], [32, 'Kiku', 74, 56], [52, 'Ajit', 54, 76]], columns=['rollno', 'name', 'physics', 'botony']) print('DataFrame with default index\n', df) df = df.set_index('rollno') print('\nDataFrame with column as index\n',df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+'Amol'%2C+72%2C+67]%2C [23%2C+'Lini'%2C+78%2C+69]%2C [32%2C+'Kiku'%2C+74%2C+56]%2C [52%2C+'Ajit'%2C+54%2C+76]]%2C columns%3D['rollno'%2C+'name'%2C+'physics'%2C+'botony']) print('DataFrame+with+default+index\n'%2C+df) %23set+column+as+index df+%3D+df.set_index('rollno') print('\nDataFrame+with+column+as+index\n'%2Cdf))

**Output**

![Pandas - Set Column as Index](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-set-column-as-index.png)

The column `rollno` of the DataFrame is set as index.

Also, observe the output of original dataframe and the output of dataframe with `rollno` as index. In the original dataframe, there is a separate index column (first column) with no column name. But in our second dataframe, as existing column is acting as index, this column took the first place.



##### Example 2: Set MultiIndex for Pandas DataFrame

In this example, we will pass multiple column names as an array to set_index() method to setup MultiIndex for the Pandas DataFrame.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 'Amol', 72, 67], [23, 'Lini', 78, 69], [32, 'Kiku', 74, 56], [52, 'Ajit', 54, 76]], columns=['rollno', 'name', 'physics', 'botony']) print('DataFrame with default index\n', df) df = df.set_index(['rollno','name']) print('\nDataFrame with MultiIndex\n',df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+'Amol'%2C+72%2C+67]%2C [23%2C+'Lini'%2C+78%2C+69]%2C [32%2C+'Kiku'%2C+74%2C+56]%2C [52%2C+'Ajit'%2C+54%2C+76]]%2C columns%3D['rollno'%2C+'name'%2C+'physics'%2C+'botony']) print('DataFrame+with+default+index\n'%2C+df) %23set+multiple+columns+as+index df+%3D+df.set_index(['rollno'%2C'name']) print('\nDataFrame+with+MultiIndex\n'%2Cdf))

**Output**

```python
D:\>python example1.py
DataFrame with default index rollno name physics botony
0 21 Amol 72 67
1 23 Lini 78 69
2 32 Kiku 74 56
3 52 Ajit 54 76 DataFrame with MultiIndex physics botony
rollno name
21 Amol 72 67
23 Lini 78 69
32 Kiku 74 56
52 Ajit 54 76
```

#### [Pandas – Pop a Column](https://pythonexamples.org/pandas-dataframe-pop/)

Pandas DataFrame.pop() function is used to delete a column from the DataFrame.

In this tutorial, we shall go through examples to learn how to use pop() to delete a column from Pandas DataFrame.



##### Example 1: Delete a column using pandas pop() function

In this example, we deleted a specific column, using column name, from the DataFrame with pop(). pandas pop() function updates the original dataframe. The data in the deleted column is lost.

**Python Program**

```python
import pandas as pd mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} df_marks = pd.DataFrame(mydictionary)
print('Original DataFrame\n--------------')
print(df_marks) df_marks.pop('algebra')
print('\n\nDataFrame after deleting column\n--------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('Original+DataFrame\n--------------') print(df_marks) %23delete+column df_marks.pop('algebra') print('\n\nDataFrame+after+deleting+column\n--------------') print(df_marks))

**Output**

![pandas pop function example](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-drop-single-column.png)pandas dataframe.pop()



##### Example 2: Delete a non-existing column using pandas pop() function

In this example, we will try deleting a column that is not present in the DataFrame.

When you try to delete a non-existing column of DataFrame using pop(), the function pop() throws KeyError.

**Python Program**

```python
import pandas as pd mydictionary = {'names': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} df_marks = pd.DataFrame(mydictionary)
print('Original DataFrame\n--------------')
print(df_marks) df_marks.pop('geometry')
print('\n\nDataFrame after deleting column\n--------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd mydictionary+%3D+{'names'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} %23create+dataframe df_marks+%3D+pd.DataFrame(mydictionary) print('Original+DataFrame\n--------------') print(df_marks) %23delete+column+that+is+not+present df_marks.pop('geometry') print('\n\nDataFrame+after+deleting+column\n--------------') print(df_marks))

**Output**

![pandas pop function throwing KeyError](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-pop-example.png)pandas pop() throwing KeyError

#### [Pandas – Change Column Datatype](https://pythonexamples.org/how-to-change-datatype-of-columns-in-pandas-dataframe/)

You can change the datatype of DataFrame columns using DataFrame.astype() method, DataFrame.infer_objects() method, or pd.to_numeric, etc.

In this tutorial, we will go through some of these processes in detail using examples.



##### Method 1 – Using DataFrame.astype()

DataFrame.astype() casts this DataFrame to a specified datatype. Following is the syntax of astype() method.

```python
astype(dtype, copy=True, errors='raise', **kwargs)
```

[Run](https://pythonexamples.org/run.php?pgm=astype(dtype%2C+copy%3DTrue%2C+errors%3D'raise'%2C+**kwargs))

we are interested only in the first argument **dtype.** dtype is data type, or dict of column name -> data type.

So, let us use astype() method with dtype argument to change datatype of one or more columns of DataFrame.

##### Change Datatype of One Colum

Let us first start with changing datatype of just one column.

In the following program, we shall change the datatype of column **a** to **float**.

**Python Program**

```python
import pandas as pd
import numpy as np 
df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) print('Previous Datatypes\n', df.dtypes, sep='') 
df = df.astype({'a': np.float}) 
print('\nNew Datatypes\n', df.dtypes, sep='') print('\nDataFrame\n', df, sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Previous+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ %23change+datatype+of+column df+%3D+df.astype({'a'%3A+np.float}) %23print+results print('\nNew+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ print('\nDataFrame\n'%2C+df%2C+sep%3D''))

**Output**

```python
Previous Datatypes
a int64
b int64
c int64
dtype: object New Datatypes
a float64
b int64
c int64
dtype: object DataFrame a b c
0 21.0 72 67
1 23.0 78 62
2 32.0 74 54
3 52.0 54 76
```

##### Change Datatype of Multiple Columns

Now, let us change datatype of more than one column. All, we have to do is provide more column_name:datatype key:value pairs in the argument to astype() method.

In the following program, we shall change the datatype of column **a** to **float**, and **b** to **int8**.

**Python Program**

```python

import pandas as pd
import numpy as np df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) print('Previous Datatypes\n', df.dtypes, sep='') 
df = df.astype({'a': np.float, 'b': np.int8}) 
print('\nNew Datatypes\n', df.dtypes, sep='') 
print('\nDataFrame\n', df, sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Previous+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ %23change+datatype+of+column df+%3D+df.astype({'a'%3A+np.float%2C+'b'%3A+np.int8}) %23print+results print('\nNew+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ print('\nDataFrame\n'%2C+df%2C+sep%3D''))

**Output**

```python
Previous Datatypes
a int64
b int64
c int64
dtype: object New Datatypes
a float64
b int8
c int64
dtype: object DataFrame a b c
0 21.0 72 67
1 23.0 78 62
2 32.0 74 54
3 52.0 54 76
```

##### Change Datatype of All Columns

If you would like to change the datatype of all columns of DataFrame, you can just pass this datatype as argument to astype() method, without the need of dictionary.

In the following program, we shall change the datatype of all column to **float**.

**Python Program**

```python
import pandas as pd
import numpy as np 
df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) 
print('Previous Datatypes\n', df.dtypes, sep='') df = df.astype(np.float) print('\nNew Datatypes\n', df.dtypes, sep='') 
print('\nDataFrame\n', df, sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Previous+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ %23change+datatype+of+column df+%3D+df.astype(np.float) %23print+results print('\nNew+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ print('\nDataFrame\n'%2C+df%2C+sep%3D''))

**Output**

```python
Previous Datatypes
a int64
b int64
c int64
dtype: object New Datatypes
a float64
b float64
c float64
dtype: object DataFrame a b c
0 21.0 72.0 67.0
1 23.0 78.0 62.0
2 32.0 74.0 54.0
3 52.0 54.0 76.0
```



##### Method 2 – pd.to_numeric

Consider that you have imported a DataFrame from Excel, CSV, or some other source, and you got all string values for DataFrame Elements. The datatype of these columns could be object. And you would like to convert the datatype of all these columns to fitting numeric datatypes.

Use the following syntax to convert datatype of DataFrame columns to numeric.

```python
df = df.apply(pd.to_numeric)
```

**Python Program**

```python
import pandas as pd
import numpy as np 
df = pd.DataFrame( [['21', '72', '67'], ['23', '78', '62'], ['32', '74', '54'], ['52', '54', '76']], columns=['a', 'b', 'c']) 
print('Previous Datatypes\n', df.dtypes, sep='') 
df = df.apply(pd.to_numeric) 
print('\nNew Datatypes\n', df.dtypes, sep='') 
print('\nDataFrame\n', df, sep='')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np %23initialize+a+dataframe df+%3D+pd.DataFrame( [['21'%2C+'72'%2C+'67']%2C ['23'%2C+'78'%2C+'62']%2C ['32'%2C+'74'%2C+'54']%2C ['52'%2C+'54'%2C+'76']]%2C columns%3D['a'%2C+'b'%2C+'c']) print('Previous+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ %23change+datatype+of+all+columns df+%3D+df.apply(pd.to_numeric) %23print+results print('\nNew+Datatypes\n'%2C+df.dtypes%2C+sep%3D'')+ print('\nDataFrame\n'%2C+df%2C+sep%3D''))

**Output**

```python
Previous Datatypes
a object
b object
c object
dtype: object New Datatypes
a int64
b int64
c int64
dtype: object DataFrame a b c
0 21 72 67
1 23 78 62
2 32 74 54
3 52 54 76
```



#### [Pandas – Change Order of Columns](https://pythonexamples.org/how-to-change-order-of-columns-in-pandas-dataframe/)

##### Method 1 – Using DataFrame.reindex()

You can change the order of columns by calling DataFrame.reindex() on the original dataframe with rearranged column list as argument.

```python
new_dataframe = dataframe.reindex(columns=['a', 'c', 'b'])
```

The reindex() function returns a new DataFrame with the given order of columns.

In the following program, we will take a DataFrame with columns `a, b, c` and change the order of columns to `a, c, b`.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) df_new = df.reindex(columns=['a', 'c', 'b']) print(df_new)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23change+order+of+columns df_new+%3D+df.reindex(columns%3D['a'%2C+'c'%2C+'b']) %23print+new+dataframe print(df_new))

**Output**

```python
 a c b
0 21 67 72
1 23 62 78
2 32 54 74
3 52 76 54
```



##### Method 2 – Using DataFrame Indexing

DataFrame indexing can be used change the order of columns in a given DataFrame.

Following is the syntax to use DataFrame indexing.

```python
new_dataframe = dataframe[['a', 'c', 'b']]
```

In the following program, we will take a DataFrame with columns `a, b, c` and change the order of columns to `a, c, b`.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) df_new = df[['a', 'c', 'b']] print(df_new)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23change+order+of+columns df_new+%3D+df[['a'%2C+'c'%2C+'b']] %23print+new+dataframe print(df_new))

**Output**

```python
 a c b
0 21 67 72
1 23 62 78
2 32 54 74
3 52 76 54
```



##### Method 3 – Using DataFrame Constructor

You can also use DataFrame Constructor to rearrange the order of columns. Consider the existing DataFrame as raw data, and create a new DataFrame, with this raw data and desired order of columns.

Following is the syntax to create a DataFrame with updated column order.

```python
new_dataframe = pd.dataframe(raw_data, index=['a', 'c', 'b'])
```

In the following program, we will take a DataFrame with columns `a, b, c` and change the order of columns to `a, c, b`.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) df_new = pd.DataFrame(df, columns=['a', 'c', 'b']) print(df_new)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23change+order+of+columns df_new+%3D+pd.DataFrame(df%2C+columns%3D['a'%2C+'c'%2C+'b']) %23print+new+dataframe print(df_new))

**Output**

```python
 a c b
0 21 67 72
1 23 62 78
2 32 54 74
3 52 76 54
```



#### [Pandas – Replace Multiple Values in Column(s)](https://pythonexamples.org/pandas-dataframe-replace-multiple-values/)

To replace multiple values in a DataFrame, you can use DataFrame.replace() method with a dictionary of different replacements passed as argument.



##### Example 1: Replace Multiple Values in a Column

The syntax to replace multiple values in a column of DataFrame is

```python
DataFrame.replace({'column_name' : { old_value_1 : new_value_1, old_value_2 : new_value_2}})
```

In the following example, we will use replace() method to replace **1** with **11** and **2** with **22** in column **a**.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame([ [4, -9, 8], [1, 2, -4], [2, 2, -8], [0, 7, -4], [2, 5, 1]], columns=['a', 'b', 'c']) 
df = df.replace({'a':{1:11, 2:22}})
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame([ [4%2C+-9%2C+8]%2C [1%2C+2%2C+-4]%2C ++++[2%2C+2%2C+-8]%2C ++++[0%2C+7%2C+-4]%2C [2%2C+5%2C+1]]%2C columns%3D['a'%2C+'b'%2C+'c']) df+%3D+df.replace({'a'%3A{1%3A11%2C+2%3A22}}) print(df))

**Output**

```python
 a b c
0 4 -9 8
1 11 2 -4
2 22 2 -8
3 0 7 -4
4 22 5 1
```



##### Example 2: Replace Multiple Values in Multiple Column

The syntax to replace multiple values in multiple columns of DataFrame is

```python
DataFrame.replace({'column_name_1' : { old_value_1 : new_value_1, old_value_2 : new_value_2}, 'column_name_2' : { old_value_1 : new_value_1, old_value_2 : new_value_2}})
```

In the following example, we will use replace() method to replace **1** with **11** and **2** with **22** in column **a**; **5** with **55** and **2** with **22** in column **b**.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame([ [4, -9, 8], [1, 2, -4], [2, 2, -8], [0, 7, -4], [2, 5, 1]], columns=['a', 'b', 'c']) 
df = df.replace({'a':{1:11, 2:22}, 'b':{5:55, 2:22}})
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame([ [4%2C+-9%2C+8]%2C [1%2C+2%2C+-4]%2C ++++[2%2C+2%2C+-8]%2C ++++[0%2C+7%2C+-4]%2C [2%2C+5%2C+1]]%2C columns%3D['a'%2C+'b'%2C+'c']) df+%3D+df.replace({'a'%3A{1%3A11%2C+2%3A22}%2C+'b'%3A{5%3A55%2C+2%3A22}}) print(df))

**Output**

```python
 a b c
0 4 -9 8
1 11 22 -4
2 22 22 -8
3 0 7 -4
4 22 55 1
```



#### [Pandas – Replace Values in DataFrame Column(s) based on Condition](https://pythonexamples.org/pandas-dataframe-replace-values-in-column-based-on-condition/)

To replace values in column based on condition in a Pandas DataFrame, you can use DataFrame.loc property, or numpy.where(), or DataFrame.where().

In this tutorial, we will go through all these processes with example programs.



##### Method 1: DataFrame.loc – Replace Values in Column based on Condition

To replace a values in a column based on a condition, using DataFrame.loc, use the following syntax.

```python
DataFrame.loc[condition, column_name] = new_value
```

In the following program, we will replace those values in the column ‘a’ that satisfy the condition that the value is less than zero.

**Python Program**

```python
import pandas as pd df = pd.DataFrame([ [-10, -9, 8], [6, 2, -4], [-8, 5, 1]], columns=['a', 'b', 'c']) df.loc[(df.a < 0), 'a'] = 0
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame([ [-10%2C+-9%2C+8]%2C [6%2C+2%2C+-4]%2C [-8%2C+5%2C+1]]%2C columns%3D['a'%2C+'b'%2C+'c']) df.loc[(df.a+%26lt%3B+0)%2C+'a']+%3D+0 print(df))

**Output**

```python
 a b c
0 0 -9 8
1 6 2 -4
2 0 5 1
```

You can also replace the values in multiple values based on a single condition. Pass the columns as tuple to loc.

```python
DataFrame.loc[condition, (column_1, column_2)] = new_value
```

In the following program, we will replace those values in columns ‘a’ and ‘b’ that satisfy the condition that the value is less than zero.

**Python Program**

```python
import pandas as pd df = pd.DataFrame([ [-10, -9, 8], [6, 2, -4], [-8, 5, 1]], columns=['a', 'b', 'c']) df.loc[(df.a < 0), ('a', 'b')] = 0
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame([ [-10%2C+-9%2C+8]%2C [6%2C+2%2C+-4]%2C [-8%2C+5%2C+1]]%2C columns%3D['a'%2C+'b'%2C+'c']) df.loc[(df.a+%26lt%3B+0)%2C+('a'%2C+'b')]+%3D+0 print(df))

**Output**

```python
 a b c
0 0 0 8
1 6 2 -4
2 0 0 1
```



##### Method 2: Numpy.where – Replace Values in Column based on Condition

To replace a values in a column based on a condition, using numpy.where, use the following syntax.

```python
DataFrame['column_name'] = numpy.where(condition, new_value, DataFrame.column_name)
```

In the following program, we will use numpy.where() method and replace those values in the column ‘a’ that satisfy the condition that the value is less than zero.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame([ [-10, -9, 8], [6, 2, -4], [-8, 5, 1]], columns=['a', 'b', 'c']) df['a'] = np.where((df.a < 0), 0, df.a)
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame([ [-10%2C+-9%2C+8]%2C [6%2C+2%2C+-4]%2C [-8%2C+5%2C+1]]%2C columns%3D['a'%2C+'b'%2C+'c']) df['a']+%3D+np.where((df.a+%26lt%3B+0)%2C+0%2C+df.a) print(df))

**Output**

```python
 a b c
0 0 -9 8
1 6 2 -4
2 0 5 1
```



##### Method 3: DataFrame.where – Replace Values in Column based on Condition

To replace a values in a column based on a condition, using numpy.where, use the following syntax.

```python
DataFrame['column_name'].where(~(condition), other=new_value, inplace=True)
```

- **column_name** is the column in which values has to be replaced.
- **condition** is a boolean expression that is applied for each value in the column.
- **new_value** replaces (since inplace=True) existing value in the specified column based on the condition.

In the following program, we will use DataFrame.where() method and replace those values in the column ‘a’ that satisfy the condition that the value is less than zero.

**Python Program**

```python
import pandas as pd df = pd.DataFrame([ [-10, -9, 8], [6, 2, -4], [-8, 5, 1]], columns=['a', 'b', 'c']) df['a'].where(~(df.a < 0), other=0, inplace=True)
print(df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd df+%3D+pd.DataFrame([ [-10%2C+-9%2C+8]%2C [6%2C+2%2C+-4]%2C [-8%2C+5%2C+1]]%2C columns%3D['a'%2C+'b'%2C+'c']) df['a'].where(~(df.a+%26lt%3B+0)%2C+other%3D0%2C+inplace%3DTrue) print(df))

**Output**

```python
 a b c
0 0 -9 8
1 6 2 -4
2 0 5 1
```

### Pandas DataFrame Row Operations

#### [Pandas DataFrame – Iterate Rows – iterrows()](https://pythonexamples.org/pandas-dataframe-iterate-rows-iterrows/)

To iterate over rows of a Pandas DataFrame, use DataFrame.iterrows() function which returns an iterator yielding index and row data for each row.

In this tutorial, we will go through examples demonstrating how to iterate over rows of a DataFrame using iterrows().



##### Syntax of iterrows()

The syntax of iterrows() is

```python
DataFrame.iterrows(self)
```

iterrows yields

- **index** – index of the row in DataFrame. This could be a label for single index, or tuple of label for multi-index.
- **data** – data is the row data as Pandas Series.
- **it** – it is the generator that iterates over the rows of DataFrame.



##### Example 1: Pandas iterrows() – Iterate over Rows

In this example, we will [initialize a DataFrame](https://pythonexamples.org/pandas-create-initialize-dataframe/) with four rows and iterate through them using [Python For Loop](https://pythonexamples.org/python-for-loop-example/) and iterrows() function.

**Python Program**

```python
import pandas as pd df_marks = pd.DataFrame({ 'name': ['apple', 'banana', 'orange', 'mango'], 'calories': [68, 74, 77, 78]}) for index, row in df_marks.iterrows(): print(index, ': ', row['name'], 'has', row['calories'], 'calories.')
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23create+dataframe df_marks+%3D+pd.DataFrame({ ++++'name'%3A+['apple'%2C+'banana'%2C+'orange'%2C+'mango']%2C 'calories'%3A+[68%2C+74%2C+77%2C+78]}) %23iterate+through+each+row+of+dataframe for+index%2C+row+in+df_marks.iterrows()%3A ++++print(index%2C+'%3A+'%2C+row['name']%2C+'has'%2C+row['calories']%2C+'calories.'))

During each iteration, we are able to access the index of row, and the contents of row.

**Output**

```python
0 : apple has 68 calories.
1 : banana has 74 calories.
2 : orange has 77 calories.
3 : mango has 78 calories.
```

Please note that the calories information is not factual. The example is for demonstrating the usage of iterrows().



##### Example 2: iterrows() yeilds index, Series

In the previous example, we have seen that we can access index and row data.

In this example, we will investigate the type of row data that iterrows() returns during iteration.

**Python Program**

```python
import pandas as pd df_marks = pd.DataFrame({ 'name': ['apple', 'banana', 'orange', 'mango'], 'calories': [68, 74, 77, 78]}) for index, row in df_marks.iterrows(): print(type(index), type(row))
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23create+dataframe df_marks+%3D+pd.DataFrame({ ++++'name'%3A+['apple'%2C+'banana'%2C+'orange'%2C+'mango']%2C 'calories'%3A+[68%2C+74%2C+77%2C+78]}) %23iterate+through+each+row+of+dataframe for+index%2C+row+in+df_marks.iterrows()%3A ++++print(type(index)%2C+type(row)))

**Output**

```python
<class 'int'> <class 'pandas.core.series.Series'>
<class 'int'> <class 'pandas.core.series.Series'>
<class 'int'> <class 'pandas.core.series.Series'>
<class 'int'> <class 'pandas.core.series.Series'>
```

We did not provide any index to the DataFrame, so the default index would be integers from zero and incrementing by one. So, iterrows() returned index as integer.

iterrows() returns the row data as [Pandas Series](https://pythonexamples.org/pandas-series-example/).

#### [Pandas DataFrame – Add Row](https://pythonexamples.org/pandas-dataframe-add-append-row/)

To append or add a row to DataFrame, create the new row as Series and use DataFrame.append() method.

In this tutorial, we shall learn how to append a row to an existing DataFrame, with the help of illustrative example programs.



##### Syntax – append()

Following is the syntax of DataFrame.appen() function.

```python
mydataframe = mydataframe.append(new_row, ignore_index=True)
```

where the resulting DataFrame contains **new_row** added to **mydataframe**.

append() is immutable. It does not change the DataFrame, but returns a new DataFrame with the row appended.

![Pandas Add Row to DataFrame](https://pythonexamples.org/images/pandas-dataframe-add-row.svg)



##### Example 1: Add Row to DataFrame

In this example, we will create a DataFrame and append a new row to this DataFrame. The new row is initialized as a Python Dictionary and append() function is used to append the row to the dataframe.

When you are adding a Python Dictionary to append(), make sure that you pass `ignore_index=True`.

The append() method returns the dataframe with the newly added row.

**Python Program**

```python
import pandas as pd 
data = {'name': ['Somu', 'Kiku', 'Amol', 'Lini'], 'physics': [68, 74, 77, 78], 'chemistry': [84, 56, 73, 69], 'algebra': [78, 88, 82, 87]} 

df_marks = pd.DataFrame(data)
print('Original DataFrame\n------------------')
print(df_marks) 
new_row = {'name':'Geo', 'physics':87, 'chemistry':92, 'algebra':97} 
df_marks = df_marks.append(new_row, ignore_index=True) 
print('\n\nNew row added to DataFrame\n--------------------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd data+%3D+{'name'%3A+['Somu'%2C+'Kiku'%2C+'Amol'%2C+'Lini']%2C 'physics'%3A+[68%2C+74%2C+77%2C+78]%2C 'chemistry'%3A+[84%2C+56%2C+73%2C+69]%2C 'algebra'%3A+[78%2C+88%2C+82%2C+87]} 	 %23create+dataframe df_marks+%3D+pd.DataFrame(data) print('Original+DataFrame\n------------------') 

**Output**

Run the above Python program, and you shall see the original dataframe, and the dataframe appended with the new row.

```python
Original DataFrame
------------------ 
name physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87 

New row added to DataFrame
-------------------------- 
name physics chemistry algebra
0 Somu 68 84 78
1 Kiku 74 56 88
2 Amol 77 73 82
3 Lini 78 69 87
4 Geo 87 92 97
```



##### Example 2: Add Row to Pandas DataFrame (ignoreIndex = False)

If you do not provide the parameter `ignoreIndex=False`, you will get TypeError.

In the following example, we will try to append a row to DataFrame with the parameter `ignoreIndex=False`.

**Python Program**

```python
import pandas as pd 
data = {'name': ['Amol', 'Lini'], 'physics': [77, 78], 'chemistry': [73, 85]} 
df_marks = pd.DataFrame(data)
print('Original DataFrame\n------------------')
print(df_marks) 
new_row = {'name':'Geo', 'physics':87, 'chemistry':92} 
df_marks = df_marks.append(new_row, ignore_index=False) 
print('\n\nNew row added to DataFrame\n--------------------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd data+%3D+{'name'%3A+['Amol'%2C+'Lini']%2C 'physics'%3A+[77%2C+78]%2C 'chemistry'%3A+[73%2C+85]} %23create+dataframe df_marks+%3D+pd.DataFrame(data) print('Original+DataFrame\n------------------')



**Output**

```python
Original DataFrame
------------------ 
name physics chemistry
0 Amol 77 73
1 Lini 78 85

Traceback (most recent call last): File "example1.py", line 14, in <module> df_marks = df_marks.append(new_row, ignore_index=False) File "C:\Users\PythonExamples\AppData\Local\Programs\Python\Python37\lib\site-packages\pandas\core\frame.py", line 6658, in append raise TypeError('Can only append a Series if ignore_index=True'
TypeError: Can only append a Series if ignore_index=True or if the Series has a name
```

As the error message says, we need to either provide the parameter `ignore_index=True` or append the row, that is Series with a name.

We have already seen in Example 1, how to add row to the DataFrame with `ignore_index=True`. Now we will see how to add a row with `ignore_index=False`.

**Python Program**

```python
import pandas as pd 
data = {'name': ['Amol', 'Lini'], 'physics': [77, 78], 'chemistry': [73, 85]} 
df_marks = pd.DataFrame(data)
print('Original DataFrame\n------------------')
print(df_marks) 
new_row = pd.Series(data={'name':'Geo', 'physics':87, 'chemistry':92}, name='x') 
df_marks = df_marks.append(new_row, ignore_index=False) 
print('\n\nNew row added to DataFrame\n--------------------------')
print(df_marks)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd data+%3D+{'name'%3A+['Amol'%2C+'Lini']%2C 'physics'%3A+[77%2C+78]%2C 'chemistry'%3A+[73%2C+85]} %23create+dataframe df_marks+%3D+pd.DataFrame(data) print('Original+DataFrame\n------------------') 

We have named the Series as `data`. Therefore `ignore_index=False` does not return a TypeError and the row is appended to the DataFrame.

**Output**

```python
Original DataFrame
------------------ 
name physics chemistry
0 Amol 77 73
1 Lini 78 85 

New row added to DataFrame
-------------------------- 
name physics chemistry
0 Amol 77 73
1 Lini 78 85
x Geo 87 92
```

#### [Pandas DataFrame – Get First N Rows – head()](https://pythonexamples.org/pandas-dataframe-head-get-first-n-rows/)

To get the first N rows of a Pandas DataFrame, use the function `pandas.DataFrame.head()`. You can pass an optional integer that represents the first N rows. If you do not pass any number, it returns the first 5 rows. Meaning, the default N is 5.



##### Example 1: DataFrame.head(N)

In this example, we will get the first 3 rows of the DataFrame.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 56], [73, 88, 67], [32, 74, 56], [43, 78, 69], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) df1 = df.head(3) print(df1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+56]%2C [73%2C+88%2C+67]%2C [32%2C+74%2C+56]%2C [43%2C+78%2C+69]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23get+first+3+rows df1+%3D+df.head(3) %23print+the+dataframe print(df1))

**Output**

![Pandas DataFrame - Get First N Rows - head()](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-dataframe-get-first-n-rows.png)



##### Example 2: DataFrame.head()

In this example, we will not pass any number to the function head(). By default, head() function returns first 5 rows.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67], [23, 78, 62], [32, 74, 56], [73, 88, 67], [32, 74, 56], [43, 78, 69], [32, 74, 54], [52, 54, 76]], columns=['a', 'b', 'c']) df1 = df.head() print(df1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+62]%2C [32%2C+74%2C+56]%2C [73%2C+88%2C+67]%2C [32%2C+74%2C+56]%2C [43%2C+78%2C+69]%2C [32%2C+74%2C+54]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) %23get+first+default+number+of+rows df1+%3D+df.head() %23print+the+dataframe print(df1))

**Output**

![Pandas DataFrame - Get First N Rows - head()](https://pythonexamples.org/wp-content/uploads/2019/06/pandas-dataframe-get-first-n-rows-1.png)



#### [Pandas DataFrame – Count Rows](https://pythonexamples.org/pandas-dataframe-count-rows/)

To count number of rows in a DataFrame, you can use DataFrame.shape property or DataFrame.count() method.

DataFrame.shape returns a tuple containing number of rows as first element and number of columns as second element. By indexing the first element, we can get the number of rows in the DataFrame

DataFrame.count(), with default parameter values, returns number of values along each column. And in a DataFrame, each column contains same number of values equal to number of rows. By indexing the first element, we can get the number of rows in the DataFrame



##### Example 1: Count Rows – DataFrame.shape

In this example, we shall use DataFrame.shape property to get the number of rows in a DataFrame.

**Python Program**

```python
import pandas as pd df = pd.DataFrame({'a': [1, 4, 7, 2], 'b': [2, 0, 8, 7]}) num_rows = df.shape[0] print('Number of Rows in DataFrame :',num_rows)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[1%2C+4%2C+7%2C+2]%2C+'b'%3A+[2%2C+0%2C+8%2C+7]}) %23number+of+rows+in+dataframe num_rows+%3D+df.shape[0] print('Number+of+Rows+in+DataFrame+%3A'%2Cnum_rows))

**Output**

```python
Number of Rows in DataFrame : 4
```



##### Example 2: Count Rows – DataFrame.count()

In this example, we shall use DataFrame.count() method, to count the number of rows in a DataFrame.

**Python Program**

```python
import pandas as pd df = pd.DataFrame({'a': [1, 4, 7, 2], 'b': [2, 0, 8, 7]}) num_rows = df.count()[0] print('Number of Rows in DataFrame :',num_rows)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[1%2C+4%2C+7%2C+2]%2C+'b'%3A+[2%2C+0%2C+8%2C+7]}) %23number+of+rows+in+dataframe num_rows+%3D+df.count()[0] print('Number+of+Rows+in+DataFrame+%3A'%2Cnum_rows))

**Output**

```python
Number of Rows in DataFrame : 4
```



#### [Pandas DataFrame – Filter Rows](https://pythonexamples.org/pandas-dataframe-filter-rows/)重点

To filter rows of Pandas DataFrame, you can use [DataFrame.isin()](https://pythonexamples.org/pandas-dataframe-isin/) function. isin() returns a dataframe of boolean which when used with the original dataframe, filters rows that obey the filter criteria.

You can also use [DataFrame.query()](https://pythonexamples.org/pandas-dataframe-query/) to filter out the rows that satisfy a given boolean expression.

In this tutorial, we shall learn how to filter rows of a DataFrame based on a condition applied on the column values.



##### Example 1: Filter DataFrame Rows – DataFrame.isin()

In this example, we shall take a DataFrame with two columns named `a` and `b` and four rows. We shall filter this DataFrame, based on the condition that the values of column `a` lies in a given range.

**Python Program**

```python
import pandas as pd
df = pd.DataFrame({'a': [2, 4, 8, 5], 'b': [2, 0, 9, 7]}) 
out = df['a'].isin(range(3,6)) 
filtered_df = df[out] 
print('Original DataFrame\n-------------------\n',df)
print('\nFiltered DataFrame\n-------------------\n',filtered_df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[2%2C+4%2C+8%2C+5]%2C+'b'%3A+[2%2C+0%2C+9%2C+7]}) %23check+if+the+values+of+df['a']+are+in+the+range(3%2C6) out+%3D+df['a'].isin(range(3%2C6)) 

isin() function returns True for the rows whose column `a` values are in the range(3,6). Else the function returns false.

df[out] returns only those rows whose value is True, thus resulting in the filtered output.

**Output**

```python
Original DataFrame
------------------- a b
0 2 2
1 4 0
2 8 9
3 5 7 Filtered DataFrame
------------------- a b
1 4 0
3 5 7
```



##### Example 2: Filter DataFrame Frames – DataFrame.query()

In this example, we shall initialize a DataFrame with two columns `a` and `b`, containing four rows. We shall filter those rows whose column `b` value is greater than 4.

We shall use DataFrame.query() to filter the DataFrame rows.

**Python Program**

```python
import pandas as pd 
df = pd.DataFrame({'a': [1, 4, 7, 2], 'b': [2, 0, 8, 7]}) 
filtered_df = df.query('b>4') 
print('Original DataFrame\n-------------------\n',df)
print('\nFiltered DataFrame\n-------------------\n',filtered_df)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+dataframe df+%3D+pd.DataFrame({'a'%3A+[1%2C+4%2C+7%2C+2]%2C+'b'%3A+[2%2C+0%2C+8%2C+7]}) %23get+rows+where+that+b%26gt%3B4 filtered_df+%3D+df.query('b%26gt%3B4') print('Original+DataFrame\n-------------------\n'%2Cdf) print('\nFiltered+DataFrame\n-------------------\n'%2Cfiltered_df))

**Output**

```python
Original DataFrame
------------------- a b
0 1 2
1 4 0
2 7 8
3 2 7 Filtered DataFrame
------------------- a b
2 7 8
3 2 7
```

#### [Pandas DataFrame – Sort by Index](https://pythonexamples.org/pandas-dataframe-sort-by-index/)

To sort a Pandas DataFrame by index, you can use DataFrame.sort_index() method.

To specify whether the method has to sort the DataFrame in ascending or descending order of index, you can set the named boolean argument `ascending` to True or False respectively.

When the index is sorted, respective rows are rearranged.

![Pandas DataFrame - Sort by Index](https://pythonexamples.org/images/python-pandas-dataframe-sort-by-index.svg)



##### Example 1: Sort DataFrame by Index in Ascending Order

In this example, we shall create a dataframe with some rows and index with an array of numbers. We shall sort the rows of this dataframe, so that the index shall be in ascending order.

To sort the index in ascending order, we call sort_index() method with the argument `ascending=True` as shown in the following Python program. Or you may ignore the **ascending** parameter, since the default value for argument `ascending` is `True`.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Arjun', 70, 86], ['Kiku', 80, 76], ['Mama', 99, 99], ['Lini', 79, 92]], index = [2, 1, 6, 5], columns=['name', 'aptitude', 'cooking']) print(df_1) df_1 = df_1.sort_index(ascending=True) print('\nDataFrame after sorting by index\n')
print(df_1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23create+a+dataframe df_1+%3D+pd.DataFrame( ++++[['Arjun'%2C+70%2C+86]%2C +++++['Kiku'%2C+80%2C+76]%2C +['Mama'%2C+99%2C+99]%2C +++++['Lini'%2C+79%2C+92]]%2C ++++index+%3D+[2%2C+1%2C+6%2C+5]%2C ++++columns%3D['name'%2C+'aptitude'%2C+'cooking']) print(df_1) %23sort+dataframe+by+index+in+ascending+order df_1+%3D+df_1.sort_index(ascending%3DTrue) print('\nDataFrame+after+sorting+by+index\n') print(df_1))

**Output**

Run the above program. We have printed the original DataFrame to the console, followed by sorted DataFrame.

```python
 name aptitude cooking
2 Arjun 70 86
1 Kiku 80 76
6 Mama 99 99
5 Lini 79 92 DataFrame after sorting by index name aptitude cooking
1 Kiku 80 76
2 Arjun 70 86
5 Lini 79 92
6 Mama 99 99
```



##### Example 2: Sort DataFrame by Index in Descending Order

In this example, we shall sort the DataFrame based on the descending order of index. For that, we shall pass `ascending=False` to the sort_index() method.

**Python Program**

```python
import pandas as pd df_1 = pd.DataFrame( [['Arjun', 70, 86], ['Kiku', 80, 76], ['Mama', 99, 99], ['Lini', 79, 92]], index = [2, 1, 6, 5], columns=['name', 'aptitude', 'cooking']) print(df_1) df_1 = df_1.sort_index(ascending=False) print('\nDataFrame after sorting by index\n')
print(df_1)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23create+a+dataframe df_1+%3D+pd.DataFrame( ++++[['Arjun'%2C+70%2C+86]%2C +++++['Kiku'%2C+80%2C+76]%2C +['Mama'%2C+99%2C+99]%2C +++++['Lini'%2C+79%2C+92]]%2C ++++index+%3D+[2%2C+1%2C+6%2C+5]%2C ++++columns%3D['name'%2C+'aptitude'%2C+'cooking']) print(df_1) %23sort+dataframe+by+index+in+descending+order df_1+%3D+df_1.sort_index(ascending%3DFalse) print('\nDataFrame+after+sorting+by+index\n') print(df_1))

**Output**

Run the program. The sorted dataframe has index `[6 5 5 1]` in descending order.

```python
 name aptitude cooking
2 Arjun 70 86
1 Kiku 80 76
6 Mama 99 99
5 Lini 79 92 DataFrame after sorting by index name aptitude cooking
6 Mama 99 99
5 Lini 79 92
2 Arjun 70 86
1 Kiku 80 76
```

#### [Pandas DataFrame – Iterate over Elements of Row](https://pythonexamples.org/pandas-dataframe-iterate-over-elements-of-row/)

To iterate over the elements of a Row in Pandas DataFrame, you can use incremental index with DataFrame.at[] or get the row and use Series.items().



##### Example 1 – Iterate over Elements of Row – Using Index

In this example, we will

- Initialize a DataFrame with some numbers.
- Get the specific row.
- Get the number of columns.
- Use for loop to iterate over the elements.

**Python Program**

```python
import pandas as pd
import numpy as np 
df = pd.DataFrame( [['a', 'b', 'c'], ['d', 'e', 'f'], ['g', 'h', 'i'], ['j', 'k', 'l']]) 
row = df.iloc[1] 
length = row.size
for i in range(length): print(row[i])
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [['a'%2C+'b'%2C+'c']%2C ['d'%2C+'e'%2C+'f']%2C ['g'%2C+'h'%2C+'i']%2C ['j'%2C+'k'%2C+'l']]) row+%3D+df.iloc[1]+%23index%3D1+%3D%26gt%3B+second+row length+%3D+row.size for+i+in+range(length)%3A ++++print(row[i]))

**Output**

```python
d
e
f
```



##### Example 2 – Iterate over Elements of Row – Using Series.items()

In this example, we will

- Initialize a DataFrame with some numbers.
- Get the specific row as Series using DataFrame.iloc property.
- Iterate over items of this row using Series.items()

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [['a', 'b', 'c'], ['d', 'e', 'f'], ['g', 'h', 'i'], ['j', 'k', 'l']]) row = df.iloc[1] for index, item in row.items(): print(item)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [['a'%2C+'b'%2C+'c']%2C ['d'%2C+'e'%2C+'f']%2C ['g'%2C+'h'%2C+'i']%2C ['j'%2C+'k'%2C+'l']]) row+%3D+df.iloc[1]+%23index%3D1+%3D%26gt%3B+second+row for+index%2C+item+in+row.items()%3A ++++print(item))

**Output**

```python
d
e
f
```

#### [Pandas DataFrame – Get Specific Row using Index](https://pythonexamples.org/pandas-dataframe-get-specific-row-using-index/)

To get the specific row of Pandas DataFrame using index, use DataFrame.iloc property and give the index of row in square brackets.

```python
DataFrame.iloc[row_index]
```

DataFrame.iloc returns the row as Series object.



##### Example 1: Get Specific Row in Pandas

In this example, we will

- Initialize a DataFrame with some numbers.
- Get the specific row (index = 1) using DataFrame.iloc property.

**Python Program**

```python
import pandas as pd
import numpy as np 
df = pd.DataFrame( [['a', 'b', 'c'], ['d', 'e', 'f'], ['g', 'h', 'i'], ['j', 'k', 'l']]) 
row = df.iloc[1] 
print(row)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np df+%3D+pd.DataFrame( [['a'%2C+'b'%2C+'c']%2C ['d'%2C+'e'%2C+'f']%2C ['g'%2C+'h'%2C+'i']%2C ['j'%2C+'k'%2C+'l']]) row+%3D+df.iloc[1]+%23index%3D1+%3D%26gt%3B+second+row print(row))

**Output**

```python
0 d
1 e
2 f
Name: 1, dtype: object
```

In the output: 0, 1 and 2 is the column index; and d, e, f is the row.

### Pandas Conversions
#### [Pandas – Convert DataFrame to Numpy Array](https://pythonexamples.org/convert-pandas-dataframe-to-numpy-array/)

You can convert a Pandas DataFrame to Numpy Array to perform some high-level mathematical functions supported by Numpy package.

To convert Pandas DataFrame to Numpy Array, use the function `DataFrame.to_numpy()`. to_numpy() is applied on this DataFrame and the method returns object of type Numpy ndarray. Usually the returned ndarray is 2-dimensional.

![Convert Pandas DataFrame to Numpy Array](https://pythonexamples.org/wp-content/uploads/2019/09/Convert-Pandas-DataFrame-to-Numpy-Array.jpg)



##### Example 1: DataFrame to Numpy Array

In the following example, we convert the DataFrame to numpy array.

**Python Program**

```python
import pandas as pd df = pd.DataFrame( [[21, 72, 67], [23, 78, 69], [32, 74, 56], [52, 54, 76]], columns=['a', 'b', 'c']) print('DataFrame\n----------\n', df) arr = df.to_numpy() print('\nNumpy Array\n----------\n', arr)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67]%2C [23%2C+78%2C+69]%2C [32%2C+74%2C+56]%2C [52%2C+54%2C+76]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('DataFrame\n----------\n'%2C+df) %23convert+dataframe+to+numpy+array arr+%3D+df.to_numpy() print('\nNumpy+Array\n----------\n'%2C+arr))

`df.to_numpy()` statement converts the dataframe to numpy array and returns the numpy array.

**Output**

![Convert Pandas DataFrame to NumPy Array](https://pythonexamples.org/wp-content/uploads/2019/06/convert-pandas-dataframe-to-numpy-array.png)



##### Example 2: Pandas DataFrame to Numpy Array when DataFrame has Different Datatypes

When you have a DataFrame with columns of different datatypes, the returned NumPy Array consists of elements of a single datatype. The lowest datatype of DataFrame is considered for the datatype of the NumPy Array.

In the following example, the DataFrame consists of columns of datatype int64 and float64. When this DataFrame is converted to NumPy Array, the lowest datatype of int64 and float64, which is float64 is selected.

**Python Program**

```python
import pandas as pd
import numpy as np df = pd.DataFrame( [[21, 72, 67.1], [23, 78, 69.5], [32, 74, 56.6], [52, 54, 76.2]], columns=['a', 'b', 'c']) print('DataFrame\n----------\n', df)
print('\nDataFrame datatypes :\n', df.dtypes) arr = df.to_numpy() print('\nNumpy Array\n----------\n', arr)
print('\nNumpy Array Datatype :', arr.dtype)
```

[Run](https://pythonexamples.org/run.php?pgm=import+pandas+as+pd import+numpy+as+np %23initialize+a+dataframe df+%3D+pd.DataFrame( [[21%2C+72%2C+67.1]%2C [23%2C+78%2C+69.5]%2C [32%2C+74%2C+56.6]%2C [52%2C+54%2C+76.2]]%2C columns%3D['a'%2C+'b'%2C+'c']) print('DataFrame\n----------\n'%2C+df) print('\nDataFrame+datatypes+%3A\n'%2C+df.dtypes) %23convert+pandas+dataframe+to+numpy+array arr+%3D+df.to_numpy() print('\nNumpy+Array\n----------\n'%2C+arr) print('\nNumpy+Array+Datatype+%3A'%2C+arr.dtype))

**Output**

![Convert Pandas DataFrame to NumPy Array](https://pythonexamples.org/wp-content/uploads/2019/06/convert-dataframe-to-numpy-array-1.png)

The returned Numpy Array is of type float64.

