```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

### 按位置选择数据

#### 1. 选择单独一列：df[['A']]、df[["A"]]、df.A 

```python
df['A']
# 取出单独的一列数据，等价于df.A，等价于df["A"]
2018-11-01   -0.170364
2018-11-02   -0.158446
2018-11-03   -0.518426
2018-11-04    1.013527
2018-11-05   -0.897497
2018-11-06   -0.030580
2018-11-07   -0.313342
Freq: D, Name: A, dtype: float64
```

列名里面有空格怎么办？有汉字怎么办？df['A']、df["A"]都能处理特殊字符。

用两个中括号df[["A"]]或者df[[‘A’]]取出的是一个dataframe，用一个中括号df["A"]或者df['A']取出的是一个？？？



#### 2. 选择多列：df[["A","B"]] 、df.loc[:,["A","B"]] 

注意选择多列的时候用两个中括号，中间用双引号。

```python
df.loc['2018-11-01']
A   -0.170364
B   -0.237541
C    0.529903
D    0.660073
Name: 2018-11-01 00:00:00, dtype: float64
#### 通过标签来进行多个轴上的进行选择
df.loc[:,["A","B"]] # 等价于df[["A","B"]]
### 注意此处是用两个方括号，里面的方括号表示一个list，外面的方括号是选择列
```

|            |         A |         B |
| ---------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |
| 2018-11-02 | -0.158446 | -0.488535 |
| 2018-11-03 | -0.518426 |  0.730866 |
| 2018-11-04 |  1.013527 |  0.270167 |
| 2018-11-05 | -0.897497 | -0.016279 |
| 2018-11-06 | -0.030580 |  0.545561 |
| 2018-11-07 | -0.313342 | -0.688179 |

```python
df.loc["2018-11-01":"2018-11-03",["A","B"]]
```

|            |         A |         B |
| ---------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |
| 2018-11-02 | -0.158446 | -0.488535 |
| 2018-11-03 | -0.518426 |  0.730866 |

```python
#### 获得一个标量数据
df.loc['2018-11-01','A']
-0.17036430076617162
```



#### 3. 选择全部列和部分行，也叫行切片：df.iloc[1:3,:] 

```python
#  对行进行切片处理
df.iloc[1:3,:]
```

|            |         A |         B |        C |         D |
| ---------: | --------: | --------: | -------: | --------: |
| 2018-11-02 | -0.158446 | -0.488535 |  0.08296 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.03383 |  0.712624 |

#### 4. 选择单独一行：df.iloc[3] ，获得第四行的数据

```python
df.iloc[3]  # 获得第四行的数据
A    1.013527
B    0.270167
C    0.081805
D    0.178193
Name: 2018-11-04 00:00:00, dtype: float64
```

#### 5. 选择多行：df[0:3] 

```python
df[0:3]
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |

选择多行是一个中括号，选择多列是两个中括号，中间的中括号是一个list。

```python
# 同时对于时间索引而言，可以直接使用比如
df['2018-11-01':'2018-11-04']
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |

#### 6. 选择全部行和部分列：df.iloc[:,1:4] ，也叫列切片

```python
# 对列进行切片
df.iloc[:,1:4]
```

|            |         B |         C |         D |
| ---------: | --------: | --------: | --------: |
| 2018-11-01 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 |  0.730866 | -1.033830 |  0.712624 |
| 2018-11-04 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-05 | -0.016279 | -0.234993 |  0.081208 |
| 2018-11-06 |  0.545561 |  1.091127 | -0.131579 |
| 2018-11-07 | -0.688179 | -0.417754 |  0.855027 |

#### 7. df.iloc[1,3] 获取特定位置的值

**通过位置获取数据，可以使用下述两个通用方法**

df.iloc[]基于列的序号

df.loc[]基于列名

#### 8. df.iloc[1:3,1:4] 获得连续的行和列，一个中括号

```python
df.iloc[1:3,1:4]  #  与numpy中的ndarray类似,行和列都从0开始编号
```
|            |         B |        C |         D |
| ---------: | --------: | -------: | --------: |
| 2018-11-02 | -0.488535 |  0.08296 | -1.913573 |
| 2018-11-03 |  0.730866 | -1.03383 |  0.712624 |
#### 9. df.iloc[[1,3],[1,3]] 获取不连续的行和列，中间的中括号是行和列的序号的list

```python

# 可以选取不连续的行或者列进行取值
df.iloc[[1,3],[1,3]]
```

|            |         B |         D |
| ---------: | --------: | --------: |
| 2018-11-02 | -0.488535 | -1.913573 |
| 2018-11-04 |  0.270167 |  0.178193 |

### 按条件选择数据





There are several ways to select rows from a Pandas data frame:

1. **Boolean indexing (`df[df['col'] == value`] )**
2. **Positional indexing (`df.iloc[...]`)**
3. **Label indexing (`df.xs(...)`)**
4. **`df.query(...)` API**

Below I show you examples of each, with advice when to use certain techniques. Assume our criterion is column `'A'` == `'foo'`

(Note on performance: For each base type, we can keep things simple by using the Pandas API or we can venture outside the API, usually into NumPy, and speed things up.)

------

**Setup**

The first thing we'll need is to identify a condition that will act as our criterion for selecting rows. We'll start with the OP's case `column_name == some_value`, and include some other common use cases.

Borrowing from @unutbu:

```py
import pandas as pd, numpy as np

df = pd.DataFrame({'A': 'foo bar foo bar foo bar foo foo'.split(),
                   'B': 'one one two three two two one three'.split(),
                   'C': np.arange(8), 'D': np.arange(8) * 2})
```

------

#### **1. Boolean indexing**, df[mask]

... Boolean indexing requires finding the true value of each row's `'A'` column being equal to `'foo'`, then using those truth values to identify which rows to keep. Typically, we'd name this series, an array of truth values, `mask`. We'll do so here as well.

```py
# 定义一个mask用于条件筛选
mask = df['A'] == 'foo'

```

We can then use this mask to slice or index the data frame

```py
df[mask]

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

This is one of the simplest ways to accomplish this task and if performance or intuitiveness isn't an issue, this should be your chosen method. However, if performance is a concern, then you might want to consider an alternative way of creating the `mask`.

Actual improvements can be made by modifying how we create our `Boolean` `mask`.

##### **`mask` alternative 1：mask = df['A'].values == 'foo'**

**`mask` alternative 1** *Use the underlying NumPy array and forgo the overhead of creating another `pd.Series`*

```py
mask = df['A'].values == 'foo'
```

I'll show more complete time tests at the end, but just take a look at the performance gains we get using the sample data frame. First, we look at the difference in creating the `mask`

```python
%timeit mask = df['A'].values == 'foo'
%timeit mask = df['A'] == 'foo'

5.84 µs ± 195 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
166 µs ± 4.45 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```

Evaluating the `mask` with the NumPy array is ~ 30 times faster. This is partly due to NumPy evaluation often being faster. It is also partly due to the lack of overhead necessary to build an index and a corresponding `pd.Series` object.

Next, we'll look at the timing for slicing with one `mask` versus the other.

```py
mask = df['A'].values == 'foo'
%timeit df[mask]
mask = df['A'] == 'foo'
%timeit df[mask]

219 µs ± 12.3 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
239 µs ± 7.03 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```

The performance gains aren't as pronounced. We'll see if this holds up over more robust testing.

------

##### **`mask` alternative 2** ：pd.DataFrame(df.values[mask], df.index[mask], df.columns).astype(df.dtypes)

**`mask` alternative 2** We could have reconstructed the data frame as well. There is a big caveat when reconstructing a dataframe—you must take care of the `dtypes` when doing so!

Instead of `df[mask]` we will do this

```py
pd.DataFrame(df.values[mask], df.index[mask], df.columns).astype(df.dtypes)
```

If the data frame is of mixed type, which our example is, then when we get `df.values` the resulting array is of `dtype` `object` and consequently, all columns of the new data frame will be of `dtype` `object`. Thus requiring the `astype(df.dtypes)` and killing any potential performance gains.

```py
%timeit df[m]
%timeit pd.DataFrame(df.values[mask], df.index[mask], df.columns).astype(df.dtypes)

216 µs ± 10.4 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
1.43 ms ± 39.6 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```

However, if the data frame is not of mixed type, this is a very useful way to do it.

Given

```python
np.random.seed([3,1415])
d1 = pd.DataFrame(np.random.randint(10, size=(10, 5)), columns=list('ABCDE'))

d1

   A  B  C  D  E
0  0  2  7  3  8
1  7  0  6  8  6
2  0  2  0  4  9
3  7  3  2  4  3
4  3  6  7  7  4
5  5  3  7  5  9
6  8  7  6  4  7
7  6  2  6  6  5
8  2  8  7  5  8
9  4  7  6  1  5
```

------

```python
%%timeit
mask = d1['A'].values == 7
d1[mask]

179 µs ± 8.73 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```

Versus

```python
%%timeit
mask = d1['A'].values == 7
pd.DataFrame(d1.values[mask], d1.index[mask], d1.columns)

87 µs ± 5.12 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```

We cut the time in half.

------

##### **`mask` alternative 3：mask = df['A'].isin(['foo'])**

@unutbu also shows us how to use `pd.Series.isin` to account for each element of `df['A']` being in a set of values. This evaluates to the same thing if our set of values is a set of one value, namely `'foo'`. But it also generalizes to include larger sets of values if needed. Turns out, this is still pretty fast even though it is a more general solution. The only real loss is in intuitiveness for those not familiar with the concept.

```py
mask = df['A'].isin(['foo'])
df[mask]

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

##### **`mask` alternative 4：mask= np.in1d(df.values[:,1],d[1],invert=False) **

However, as before, we can utilize NumPy to improve performance while sacrificing virtually nothing. We'll use `np.in1d`. 

in1d()函数与excel中vlookup函数和MATLAB中ismember函数有相似之处。其作用在于在序列B中寻找与序列A相同的值，并返回一逻辑值（True,False）或逻辑值构成的向量.mask是由一系列True和False值构成，True代表找到相同的值，而False代表没找到相同的值。演示如下：

```python
mask= np.in1d(x.values[:,1],d[1],invert=False) 
# x为DataFrame型数据，x.values[:,1]表示取第二列值,d是个list
x_temp=x[mask]    
```

该例旨在查找 x 的第二列值中与d向量中第二个元素相同的部分 ，并返回mask逻辑向量；然后x_temp返回x中mask逻辑值为True的行。mask向量的类型为bool，查看具体值下图所示：

![img](https://img-blog.csdn.net/20171128231908447?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzU3NTE3OTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

![img](https://img-blog.csdn.net/20171128231932073?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzU3NTE3OTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

   值得注意的地方在于in1d函数中invert参数的设置。当invert=True时，mask中的元素值为True的部分对x.values[:,1]中与当前查找的元素d[i]不同的部分(i为当前查找位置)，相同的部分则为false；当invert=False时，mask中的元素值为True的部分对x.values[:,1]中与当前查找的元素d[i]相同的部分(i为当前查找位置)。演示见下图：

当mask= np.in1d(x.values[:,1],d[2],invert=True)

![img](https://img-blog.csdn.net/20171128234217121?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzU3NTE3OTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

  当mask= np.in1d(x.values[:,1],d[2],invert=False)时

![img](https://img-blog.csdn.net/20171128234348699?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzU3NTE3OTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

```py
mask = np.in1d(df['A'].values, ['foo'])
# 在df的A列中，找到值为foo的位置，赋值为true，其他位置赋值为false
df[mask]

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

------

##### **Timing**

I'll include other concepts mentioned in other posts as well for reference.

*Code Below*

Each *column* in this table represents a different length data frame over which we test each function. Each column shows relative time taken, with the fastest function given a base index of `1.0`.

```py
res.div(res.min())

                         10        30        100       300       1000      3000      10000     30000
mask_standard         2.156872  1.850663  2.034149  2.166312  2.164541  3.090372  2.981326  3.131151
mask_standard_loc     1.879035  1.782366  1.988823  2.338112  2.361391  3.036131  2.998112  2.990103
mask_with_values      1.010166  1.000000  1.005113  1.026363  1.028698  1.293741  1.007824  1.016919
mask_with_values_loc  1.196843  1.300228  1.000000  1.000000  1.038989  1.219233  1.037020  1.000000
query                 4.997304  4.765554  5.934096  4.500559  2.997924  2.397013  1.680447  1.398190
xs_label              4.124597  4.272363  5.596152  4.295331  4.676591  5.710680  6.032809  8.950255
mask_with_isin        1.674055  1.679935  1.847972  1.724183  1.345111  1.405231  1.253554  1.264760
mask_with_in1d        1.000000  1.083807  1.220493  1.101929  1.000000  1.000000  1.000000  1.144175
```

You'll notice that the fastest times seem to be shared between `mask_with_values` and `mask_with_in1d`.

```py
res.T.plot(loglog=True)
```

[![Enter image description here](https://i.stack.imgur.com/ljeTd.png)](https://i.stack.imgur.com/ljeTd.png)

**Functions**

```py
def mask_standard(df):
    mask = df['A'] == 'foo'
    return df[mask]

def mask_standard_loc(df):
    mask = df['A'] == 'foo'
    return df.loc[mask]

def mask_with_values(df):
    mask = df['A'].values == 'foo'
    return df[mask]

def mask_with_values_loc(df):
    mask = df['A'].values == 'foo'
    return df.loc[mask]

def query(df):
    return df.query('A == "foo"')

def xs_label(df):
    return df.set_index('A', append=True, drop=False).xs('foo', level=-1)

def mask_with_isin(df):
    mask = df['A'].isin(['foo'])
    return df[mask]

def mask_with_in1d(df):
    mask = np.in1d(df['A'].values, ['foo'])
    return df[mask]
```

------

**Testing**

```py
res = pd.DataFrame(
    index=[
        'mask_standard', 'mask_standard_loc', 'mask_with_values', 'mask_with_values_loc',
        'query', 'xs_label', 'mask_with_isin', 'mask_with_in1d'
    ],
    columns=[10, 30, 100, 300, 1000, 3000, 10000, 30000],
    dtype=float
)

for j in res.columns:
    d = pd.concat([df] * j, ignore_index=True)
    for i in res.index:a
        stmt = '{}(d)'.format(i)
        setp = 'from __main__ import d, {}'.format(i)
        res.at[i, j] = timeit(stmt, setp, number=50)
```

------

**Special Timing**

Looking at the special case when we have a single non-object `dtype` for the entire data frame.

*Code Below*

```py
spec.div(spec.min())

                     10        30        100       300       1000      3000      10000     30000
mask_with_values  1.009030  1.000000  1.194276  1.000000  1.236892  1.095343  1.000000  1.000000
mask_with_in1d    1.104638  1.094524  1.156930  1.072094  1.000000  1.000000  1.040043  1.027100
reconstruct       1.000000  1.142838  1.000000  1.355440  1.650270  2.222181  2.294913  3.406735
```

Turns out, reconstruction isn't worth it past a few hundred rows.

```py
spec.T.plot(loglog=True)
```

[![Enter image description here](https://i.stack.imgur.com/K1bNc.png)](https://i.stack.imgur.com/K1bNc.png)

**Functions**

```py
np.random.seed([3,1415])
d1 = pd.DataFrame(np.random.randint(10, size=(10, 5)), columns=list('ABCDE'))

def mask_with_values(df):
    mask = df['A'].values == 'foo'
    return df[mask]

def mask_with_in1d(df):
    mask = np.in1d(df['A'].values, ['foo'])
    return df[mask]

def reconstruct(df):
    v = df.values
    mask = np.in1d(df['A'].values, ['foo'])
    return pd.DataFrame(v[mask], df.index[mask], df.columns)

spec = pd.DataFrame(
    index=['mask_with_values', 'mask_with_in1d', 'reconstruct'],
    columns=[10, 30, 100, 300, 1000, 3000, 10000, 30000],
    dtype=float
)
```

**Testing**

```py
for j in spec.columns:
    d = pd.concat([df] * j, ignore_index=True)
    for i in spec.index:
        stmt = '{}(d)'.format(i)
        setp = 'from __main__ import d, {}'.format(i)
        spec.at[i, j] = timeit(stmt, setp, number=50)
```





------

#### **2. Positional indexing**, df.iloc[pos]

Positional indexing (`df.iloc[...]`) has its use cases, but this isn't one of them. In order to identify where to slice, we first need to perform the same boolean analysis we did above. This leaves us performing one extra step to accomplish the same task.

```python
mask = df['A'] == 'foo'
pos = np.flatnonzero(mask)
# numpy.flatnonzero()，该函数输入一个矩阵，返回扁平化后矩阵中非零元素的位置（index）
df.iloc[pos]
# 此处用df.iloc[]返回不连续位置的行和全部列，此处的位置就来自上述flatnonzero()函数

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

#### **3. Label indexing**，df.xs()

*Label* indexing can be very handy, but in this case, we are again doing more work for no benefit.

Pandas **Series.xs() ** function return a cross-section from the Series/DataFrame for the given key value.

| FirstLevel  | bar       | baz       | foo       | qux       |           |          |           |           |
| :---------- | :-------- | :-------- | :-------- | :-------- | :-------- | :------- | :-------- | :-------- |
| SecondLevel | one       | two       | one       | two       | one       | two      | one       | two       |
| A           | 1.014034  | 1.464162  | -0.753476 | -0.163394 | -0.198990 | 0.116046 | -0.555008 | -0.965797 |
| B           | -1.314244 | -1.263142 | 1.523974  | 0.541391  | -0.217874 | 0.019695 | 1.188791  | -1.003912 |
| C           | -1.175155 | -0.587370 | 0.352587  | -0.047469 | -0.896502 | 0.280792 | 0.806554  | 0.132662  |

df.xs()用于含多级索引的df中，通过索引的值取得数据.

**Syntax:**Series.xs(key, axis=0, level=None, drop_level=True)

**Parameters :**
**key :** Label contained in the index, or partially in a MultiIndex.
**axis :** Axis to retrieve cross-section on.
**level :** In case of a key partially contained in a MultiIndex, indicate which levels are used. Levels can be referred by label or position.
**drop_level :** If False, returns object with same levels as self.

**Returns :** Series or DataFrame

```py
df.set_index('A', append=True, drop=False).xs('foo', level=1)

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

#### **4. `df.query()` API**

*`pd.DataFrame.query`* is a very elegant/intuitive way to perform this task, but is often slower. **However**, if you pay attention to the timings below, for large data, the query is very efficient. More so than the standard approach and of similar magnitude as my best suggestion.

```python
df.query('A == "foo"')

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

##### 1. df.query语法

今天看到了query的用法，被这个函数的简洁所折服…

```html
df.query（expr，inplace = False，** kwargs ）# 使用布尔表达式查询帧的列
 
参数：
# expr：str要评估的查询字符串。你可以在环境中引用变量，在它们前面添加一个'@'字符 。@a + b
# inplace=False：是否修改数据或返回副本
# kwargs：dict关键字参数
 
返回：DataFrame
 
注意：
# 默认修改Python语法'&'/'and'和'|'/'or'位运算符优先级高于布尔表达式，不同于Python
# 关键字参数parser='python'执行Python评估。
# engine='python' 用Python本身作为后端来传递评估表达式。不建议效率低。
 
# 默认实例df.index和 df.columns属性 DataFrame放在查询命名空间中，
# 这允许您将框架的索引和列视为框架中的列。标识符index用于帧索引; 
# 您还可以使用索引的名称在查询中标识它。
1234567891011121314151617
性能：
    # 涉及NumPy数组或Pandas DataFrames的复合表达式都会导致隐式创建临时数组
    # eval/query用在数据（df.values.nbytes>1万）性能提升明显；传统方法在小数组时运行得更快；
    # eval/query好处主要时节省内存，以及有时候简洁得语法
    # 可用指定不同解析器和引擎来运行这些查询；参见"Enhancing Performance" 。
12345
```

##### 2. 实例1：多列的值，df.query('A < 8 and B < 9')

```c
df = pd.DataFrame(np.arange(12).reshape(3, 4), columns=list('ABCD'))
 
  A B  C  D
0 0 1  2  3
1 4 5  6  7
2 8 9 10 11
 
# 实例1.1：python,numexpr 方式比较
result1 = df[(df.A < 8) & (df.B < 9)] #python方式
result2 = pd.eval('df[(df.A < 8) & (df.B < 9)]')#numexpr 方式
 
np.allclose(result1, result2) # True
# numpy的allclose方法，比较两个array是不是每一元素都相等，默认在1e-05的误差范围内
 
# 实例1.2：eval,query,比较
# 相同点：计算表达式结果
# 不同点：eval若表达式为逻辑，结果返回bool数组;query则返回bool数组的数据
 
import numexpr
 
result3= df[df.eval('A<8 & B<9')]
result4 = df.query('A < 8 and B < 9')
result3.equals(result4)                        #True 结果result1==result2==result3==result4
 
a=df.A;b=df.B
result5= df[numexpr.evaluate('(a<8) &(b < 9)')]#等效；表达式不能含df.A
12345678910111213141516171819202122232425
```

##### 3. 实例2：@符号来标记本地变量

```c
# 实例2：@符号来标记本地变量
Cmean = df['C'].mean() #6.0
result1 = df[(df.A < Cmean) & (df.B < Cmean)]
result1 = df.query('A < @Cmean and B < @Cmean')#等价
result1
 
  A B C D
0 0 1 2 3
1 4 5 6 7
123456789
```

##### 4. 实例3：多索引，列与列比较

```python
# 实例3.1：列名
df.query('(A < B) & (B < C)') #numexpr 方式 A,B,C为列名
 
# 实例3.2：单索引名+列名
df.query('a < B and B < C')   #a为单索引名，B,C为列名
df.query('index < B < C')     #index为单索引(非索引名)，B,C为列名
 
# 实例3.3：单索引名a与列名a相同
df.query('a > 2')             # 用列'a',单索引名a与列名a相同列名称优先
df.query('index > 2')         #index为单索引(非索引名),单索引名a与列名a相同列名称优先
 
# 实例3.4：列名为index- 应该考虑将列重命名
df.query('ilevel_0 > 2')      #ilevel_0为单索引(非索引名)

1234567891011121314
```

##### 5. 实例4：多索引MultiIndex，类似df.xs()

```python
colors = np.random.choice(['red', 'blue'], size=6)
foods = np.random.choice(['eggs', 'meat'], size=6)
index = pd.MultiIndex.from_arrays([colors, foods], names=['color', 'food'])
df = pd.DataFrame(np.arange(12).reshape(6, 2), index=index)
df
 
            0  1
color food
blue meat   0  1
     eggs   2  3
     meat   4  5
red  meat   6  7
blue meat   8  9
     eggs   10 11
 
# 实:4.1：索引名
df.query('color == "red"')
 
# 实例4.2：索引无名称
df.index.names = [None, None]
df.query('ilevel_0 == "red"') #ilevel_0第0级的索引级别
df.query('ilevel_1 == "meat"')#ilevel_1第1级的索引级别

123456789101112131415161718192021222324
```

##### 6.实例5：多数据df - 具有相同列名（或索引级别/名称）

```python
df1 = pd.DataFrame(np.arange(12).reshape(4,3), columns=list('abc'))+10
df2=df1+10
 
expr = '19 <= a <= c <= 22'
result=list(map(lambda frame: frame.query(expr), [df1, df2]))
 
# df1      df2        result
   a  b  c    a  b  c [ a b c
0 10 11 12 0 20 21 22 3 19 20 21,
1 13 14 15 1 23 24 25 a b c
2 16 17 18 2 26 27 28 0 20 21 22]
3 19 20 21 3 29 30 31

1234567891011121314
```

##### 7.实例6：Python与pandas语法比较

```python
# 完全类似numpy的语法
 
# 实例6.1：比较运算符，逻辑运算符
df = pd.DataFrame(np.random.randint(10, size=(10, 3)), columns=list('ABC'))
 
df.query('(A< B) & (B< C)')
df[(df.A < df.B) & (df.B < df.C)]
df.query('A< B & B < C')
df.query('A< B and B < C')
df.query('A < B < C') #全部等价
 
============================================================
# 实例6.2：==操作符与list对象的特殊用法
# ==/ !=工程，以类似in/not in
 
df.query('b == ["a", "b", "c"]')==df[df.b.isin(["a", "b", "c"])]
 
df.query('c == [1, 2]')
df.query('c != [1, 2]')
 
# using in/not in
df.query('[1, 2] in c')
df.query('[1, 2] not in c')
df[df.c.isin([1, 2])]# pure Python
============================================================
# 实例6.3：in与not in
df = pd.DataFrame({'a': list('abcdef'), 'b': list('fedfed'),'c': 5, 'd':5})
 
  a b c d
0 a f 5 5
1 b e 5 5
2 c d 5 5
3 d f 5 5
4 e e 5 5
5 f d 5 5
 
df.query('a in b and c < d') #与其他表达式结合获得非常简洁查询
df[df.b.isin(df.a) & (df.c < df.d)]
 
result1=df[df.a.isin(df.b)]
result2=df.query('a not in b')
result3=df[~df.a.isin(df.b)] # pure Python
 
# result1   result2      result3
  a b c d     a b c d      a b c d
3 d f 5 5   0 a f 5 5    0 a f 5 5
4 e e 5 5   1 b e 5 5    1 b e 5 5
5 f d 5 5   2 c d 5 5    2 c d 5 5
 
============================================================
# 实例6.4：布尔运算符not或~运算符否定布尔表达式
 
df = pd.DataFrame(np.arange(9).reshape(3,3), columns=list('ABC'))
df['bools'] = df.eval('C>=5')
 
result1=df.query('not bools')
result2=(df.query('not bools') == df[~df.bools])
 
# df            result1           result2
  A B C bools     A B C bools        A    B     C bools
0 0 1 2 False   0 0 1 2 False    0 True True True True
1 3 4 5 True 
2 6 7 8 True 
 
# 复杂表达式：
df.query('A < B< C and (not bools) or bools > 2')               #短查询语法
df[(df.A < df.B) & (df.B < df.C) & (~df.bools) | (df.bools > 2)]#等效于纯Python
```



#### 5. 使用单列的数据作为条件进行筛选

```python
# 使用单列的数据作为条件进行筛选
df[df.A>0]
# 等价于如下，在列名出现中文或空格等特殊字符时使用
df[df["A"]>0]
```

|            |        A |        B |        C |        D |
| ---------: | -------: | -------: | -------: | -------: |
| 2018-11-04 | 1.013527 | 0.270167 | 0.081805 | 0.178193 |

To select rows whose column value equals a scalar, `some_value`, use `==`:

```python
df.loc[df['column_name'] == some_value]
```

To select rows whose column value is in an iterable, `some_values`, use `isin`:

```python
df.loc[df['column_name'].isin(some_values)]
```

To select rows whose column value *does not equal* `some_value`, use `!=`:

```python
df.loc[df['column_name'] != some_value]
```

`isin` returns a boolean Series, so to select rows whose value is *not* in `some_values`, negate the boolean Series using `~`:

```python
df.loc[~df['column_name'].isin(some_values)]
```

For example,

```python
import pandas as pd
import numpy as np
df = pd.DataFrame({'A': 'foo bar foo bar foo bar foo foo'.split(),
                   'B': 'one one two three two two one three'.split(),
                   'C': np.arange(8), 'D': np.arange(8) * 2})
print(df)
#      A      B  C   D
# 0  foo    one  0   0
# 1  bar    one  1   2
# 2  foo    two  2   4
# 3  bar  three  3   6
# 4  foo    two  4   8
# 5  bar    two  5  10
# 6  foo    one  6  12
# 7  foo  three  7  14

print(df.loc[df['A'] == 'foo'])
```

yields

```python
     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

------

#### 6. 使用几个列的组合作为条件筛选数据

Combine multiple conditions with `&`:

```python
df.loc[(df['column_name'] >= A) & (df['column_name'] <= B)]
```

Note the parentheses. Due to Python's [operator precedence rules](https://docs.python.org/3/reference/expressions.html#operator-precedence), `&` binds more tightly than `<=` and `>=`. Thus, the parentheses in the last example are necessary. Without the parentheses

```python
df['column_name'] >= A & df['column_name'] <= B
```

is parsed as

```python
df['column_name'] >= (A & df['column_name']) <= B
```

which results in a [Truth value of a Series is ambiguous error](https://stackoverflow.com/questions/36921951/truth-value-of-a-series-is-ambiguous-use-a-empty-a-bool-a-item-a-any-o).

If you have multiple values you want to include, put them in a list (or more generally, any iterable) and use `isin`:

```python
print(df.loc[df['B'].isin(['one','three'])])
```

yields

```python
     A      B  C   D
0  foo    one  0   0
1  bar    one  1   2
3  bar  three  3   6
6  foo    one  6  12
7  foo  three  7  14
```

------

Note, however, that if you wish to do this many times, it is more efficient to make an index first, and then use `df.loc`:

```python
df = df.set_index(['B'])
print(df.loc['one'])
```

yields

```python
       A  C   D
B              
one  foo  0   0
one  bar  1   2
one  foo  6  12
```

or, to include multiple values from the index use `df.index.isin`:

```python
df.loc[df.index.isin(['one','two'])]
```

yields

```python
       A  C   D
B              
one  foo  0   0
one  bar  1   2
two  foo  2   4
two  foo  4   8
two  bar  5  10
one  foo  6  12
```



#### 7. 使用整个df的数据作为条件筛选

```python
 #很少用到，很少使用这种大范围的条件进行筛选
df[df>0] 
```

|            |        A |        B |        C |        D |
| ---------: | -------: | -------: | -------: | -------: |
| 2018-11-01 |      NaN |      NaN | 0.529903 | 0.660073 |
| 2018-11-02 |      NaN |      NaN | 0.082960 |      NaN |
| 2018-11-03 |      NaN | 0.730866 |      NaN | 0.712624 |
| 2018-11-04 | 1.013527 | 0.270167 | 0.081805 | 0.178193 |
| 2018-11-05 |      NaN |      NaN |      NaN | 0.081208 |
| 2018-11-06 |      NaN | 0.545561 | 1.091127 |      NaN |
| 2018-11-07 |      NaN |      NaN |      NaN | 0.855027 |

#### 8.  对单列使用isin()方法过滤

```python
df2.head()
```

|      |    A |        B |    C |     D |    E |
| ---: | ---: | -------: | ---: | ----: | ---: |
|    0 |    1 | 20181101 |    3 |  test |  1.5 |
|    1 |    1 | 20181101 |    3 | train |  1.5 |
|    2 |    1 | 20181101 |    3 |  test |  1.5 |
|    3 |    1 | 20181101 |    3 | train |  1.5 |

```python
# 使用isin()方法过滤
df2[df2['D'].isin(['test'])]
# isin()的参数即使只有一个值，参数也要用中括号，表示是个只有一个元素的list
```

|      |    A |        B |    C |    D |    E |
| ---: | ---: | -------: | ---: | ---: | ---: |
|    0 |    1 | 20181101 |    3 | test |  1.5 |
|    2 |    1 | 20181101 |    3 | test |  1.5 |



#### 9. The [`where()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.where.html#pandas.DataFrame.where) Method and Masking

10. 



### Pandas Series.xs

- Last Updated : 28 Jan, 2019

Python is a great language for doing data analysis, primarily because of the fantastic ecosystem of data-centric python packages. ***Pandas\*** is one of those packages and makes importing and analyzing data much easier.

Pandas series is a One-dimensional ndarray with axis labels. The labels need not be unique but must be a hashable type. The object supports both integer- and label-based indexing and provides a host of methods for performing operations involving the index.

##### **Syntax:**

Pandas` **Series.xs()**` function return a cross-section from the Series/DataFrame for the given key value.

> **Syntax:**Series.xs(key, axis=0, level=None, drop_level=True)
>
> **Parameters :**
> **key :** Label contained in the index, or partially in a MultiIndex.
> **axis :** Axis to retrieve cross-section on.
> **level :** In case of a key partially contained in a MultiIndex, indicate which levels are used. Levels can be referred by label or position.
> **drop_level :** If False, returns object with same levels as self.
>
> 
>
> **Returns :** Series or DataFrame

##### **Example #1:** Use `Series.xs()` function to return a cross-section of the given Series object for the passed key value.

```python
# importing pandas as pd
import pandas as pd 
# Creating the Series
sr = pd.Series(['New York', 'Chicago', 'Toronto', 'Lisbon', 'Rio'])
# Creating the row axis labels
sr.index = ['City 1', 'City 2', 'City 3', 'City 4', 'City 5']
# Print the series
print(sr) 
```

**Output :**
![img](https://media.geeksforgeeks.org/wp-content/uploads/1-1647.png)
Now we will use `Series.xs()` function to return the cross-section for the given series object.

```python
# return cross-section corresponding to the 'City 4' label 
sr.xs(key = 'City 4') 
```

**Output :**
![img](https://media.geeksforgeeks.org/wp-content/uploads/1-1653.png)

As we can see in the output, the `Series.xs()` function has returned ‘Lisbon’ as the cross-section for the given Series object.


##### **Example #2 :** Use `Dataframe.xs()` function to return a cross-section of the given Dataframe object for the passed key value.

```python
# importing pandas as pd 
import pandas as pd   
# Creating the Dataframe 
df = pd.DataFrame({'num_legs': [4, 4, 2, 2],  'num_wings': [0, 0, 2, 2],  'class': ['Mammal', 'Mammal', 'Mammal', 'Bird'], 'animal': ['Cow', 'Elephant', 'Deer', 'Sparrow'], 'locomotion': ['Walks', 'Walks', 'Walks', 'Flies']})   
# setting the index 
df = df.set_index(['class', 'animal', 'locomotion'])   
# Print the Dataframe 
print(df) 
```

**Output :**
![img](https://media.geeksforgeeks.org/wp-content/uploads/1-1654.png)

Now we will use `Dataframe.xs()` function to return the cross-section for the given Dataframe object.

```python
# return cross-section corresponding to the 'Mammal' label 
sr.xs(key = 'Mammal') 
```

**Output :**
![img](https://media.geeksforgeeks.org/wp-content/uploads/2-438.png)
As we can see in the output, the `Dataframe.xs()` function has returned the cross-section of the given Dataframe object for the passed key value.