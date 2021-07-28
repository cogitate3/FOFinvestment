```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

### 创建一个Series,同时让pandas自动生成索引列

```python
s = pd.Series([1,3,5,np.nan,6,8])
# 查看s
s
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
```

### 创建一个DataFrame数据框

```python
### 创建一个DataFrame ，可以传入一个numpy array 可以自己构建索引以及列标
dates = pd.date_range('2018-11-01',periods=7)
#### 比如说生成一个时间序列，以20181101 为起始位置的，7个日期组成的时间序列，数据的类型为datetime64[ns]
dates
DatetimeIndex(['2018-11-01', '2018-11-02', '2018-11-03', '2018-11-04',
               '2018-11-05', '2018-11-06', '2018-11-07'],
              dtype='datetime64[ns]', freq='D')
df = pd.DataFrame(np.random.randn(7,4),index= dates,columns=list('ABCD'))
df
# 产生随机正态分布的数据，7行4列，分别对应的index的长度以及column的长度
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |

```python
### 同时用可以使用dict的实行创建DataFrame
df2 = pd.DataFrame({"A":1,
                   "B":"20181101",
                   'C':np.array([3]*4,dtype='int32'),
                   'D':pd.Categorical(['test','train','test','train']),
                   "E":1.5},
                  )
df2
```

|      |    A |        B |    C |     D |    E |
| ---: | ---: | -------: | ---: | ----: | ---: |
|    0 |    1 | 20181101 |    3 |  test |  1.5 |
|    1 |    1 | 20181101 |    3 | train |  1.5 |
|    2 |    1 | 20181101 |    3 |  test |  1.5 |
|    3 |    1 | 20181101 |    3 | train |  1.5 |

```python
df2.dtypes
### 查看数据框中的数据类型,常见的数据类型还有时间类型以及float类型
A       int64
B      object
C       int32
D    category
E     float64
dtype: object
```

### 查看数据

```python
# 比如说看前5行
df.head()
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |

```python
# 后4行
df.tail(4)
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |

```python
# 查看DataFrame的索引
df.index
DatetimeIndex(['2018-11-01', '2018-11-02', '2018-11-03', '2018-11-04',
               '2018-11-05', '2018-11-06', '2018-11-07'],
              dtype='datetime64[ns]', freq='D')
# 查看DataFrame的列索引
df.columns
Index(['A', 'B', 'C', 'D'], dtype='object')
# 查看DataFrame的数据,将DataFrame转化为numpy array 的数据形式
df.values
array([[-0.1703643 , -0.23754121,  0.52990284,  0.66007285],
       [-0.15844565, -0.48853537,  0.08296043, -1.91357255],
       [-0.51842554,  0.73086567, -1.03382969,  0.71262388],
       [ 1.01352712,  0.27016714,  0.08180539,  0.17819344],
       [-0.89749689, -0.01627937, -0.23499323,  0.08120819],
       [-0.03058032,  0.54556063,  1.09112723, -0.13157934],
       [-0.31334198, -0.68817881, -0.41775393,  0.85502652]])
```

### 数据的简单统计

```python
# 可以使用describe函数对DataFrame中的数值型数据进行统计
df.describe()
```

|       |         A |         B |         C |         D |
| ----: | --------: | --------: | --------: | --------: |
| count |  7.000000 |  7.000000 |  7.000000 |  7.000000 |
|  mean | -0.153590 |  0.016580 |  0.014174 |  0.063139 |
|   std |  0.590144 |  0.527860 |  0.680939 |  0.945526 |
|   min | -0.897497 | -0.688179 | -1.033830 | -1.913573 |
|   25% | -0.415884 | -0.363038 | -0.326374 | -0.025186 |
|   50% | -0.170364 | -0.016279 |  0.081805 |  0.178193 |
|   75% | -0.094513 |  0.407864 |  0.306432 |  0.686348 |
|   max |  1.013527 |  0.730866 |  1.091127 |  0.855027 |

```python
df2.describe()
### 对于其他的数据类型的数据describe函数会自动过滤掉
```

|       |    A |    C |    E |
| ----: | ---: | ---: | ---: |
| count |  4.0 |  4.0 |  4.0 |
|  mean |  1.0 |  3.0 |  1.5 |
|   std |  0.0 |  0.0 |  0.0 |
|   min |  1.0 |  3.0 |  1.5 |
|   25% |  1.0 |  3.0 |  1.5 |
|   50% |  1.0 |  3.0 |  1.5 |
|   75% |  1.0 |  3.0 |  1.5 |
|   max |  1.0 |  3.0 |  1.5 |

```python
### DataFrame 的转置，将列索引与行索引进行调换，行数据与列数进行调换
df.T
```

|      | 2018-11-01 00:00:00 | 2018-11-02 00:00:00 | 2018-11-03 00:00:00 | 2018-11-04 00:00:00 | 2018-11-05 00:00:00 | 2018-11-06 00:00:00 | 2018-11-07 00:00:00 |
| ---: | ------------------: | ------------------: | ------------------: | ------------------: | ------------------: | ------------------: | ------------------: |
|    A |           -0.170364 |           -0.158446 |           -0.518426 |            1.013527 |           -0.897497 |           -0.030580 |           -0.313342 |
|    B |           -0.237541 |           -0.488535 |            0.730866 |            0.270167 |           -0.016279 |            0.545561 |           -0.688179 |
|    C |            0.529903 |            0.082960 |           -1.033830 |            0.081805 |           -0.234993 |            1.091127 |           -0.417754 |
|    D |            0.660073 |           -1.913573 |            0.712624 |            0.178193 |            0.081208 |           -0.131579 |            0.855027 |

```python
df
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |

### 数据的排序

```python
df.sort_index(ascending=False)
### 降序，按照列进行降序，通过该索引列
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |

```python
print(df.sort_values(by=['B','A']))
#  默认是升序,可以选择多指排序，先照B，后排A，如果B中的数据一样，则按照A中的大小进行排序
df.sort_values(by='B')
                   A         B         C         D
2018-11-07 -0.313342 -0.688179 -0.417754  0.855027
2018-11-02 -0.158446 -0.488535  0.082960 -1.913573
2018-11-01 -0.170364 -0.237541  0.529903  0.660073
2018-11-05 -0.897497 -0.016279 -0.234993  0.081208
2018-11-04  1.013527  0.270167  0.081805  0.178193
2018-11-06 -0.030580  0.545561  1.091127 -0.131579
2018-11-03 -0.518426  0.730866 -1.033830  0.712624
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |

### 按位置选择数据



#### df['A']、df.A 选择单独一列

```python
df['A']
# 取出单独的一列数据，等价于df.A
2018-11-01   -0.170364
2018-11-02   -0.158446
2018-11-03   -0.518426
2018-11-04    1.013527
2018-11-05   -0.897497
2018-11-06   -0.030580
2018-11-07   -0.313342
Freq: D, Name: A, dtype: float64
```

列名里面有空格怎么办？有汉字怎么办？：



#### df.loc[:,["A","B"]] 、df[["A","B"]] 选择多列

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



#### df[0:3] 选择多行，通过[]进行行切片

```python
df[0:3]
```

|            |         A |         B |         C |         D |
| ---------: | --------: | --------: | --------: | --------: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |

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

**通过位置获取数据**

df.iloc[]基于列的序号

df.loc[]基于列名

#### df.iloc[3] 获得第四行的数据

```python
df.iloc[3]  # 获得第四行的数据
A    1.013527
B    0.270167
C    0.081805
D    0.178193
Name: 2018-11-04 00:00:00, dtype: float64
```
**通过位置获取连续的行和列**

#### df.iloc[1:3,1:4] 获得连续的行和列，行和列都从0开始编号

```python
df.iloc[1:3,1:4]  #  与numpy中的ndarray类似
```
|            |         B |        C |         D |
| ---------: | --------: | -------: | --------: |
| 2018-11-02 | -0.488535 |  0.08296 | -1.913573 |
| 2018-11-03 |  0.730866 | -1.03383 |  0.712624 |
#### df.iloc[[1,3],[1,3]] 获取不连续的行和列

```python

# 可以选取不连续的行或者列进行取值
df.iloc[[1,3],[1,3]]
```

|            |         B |         D |
| ---------: | --------: | --------: |
| 2018-11-02 | -0.488535 | -1.913573 |
| 2018-11-04 |  0.270167 |  0.178193 |

#### df.iloc[1:3,:] 选择部分行和全部列，也叫行切片
```python
#  对行进行切片处理
df.iloc[1:3,:]
```

|            |         A |         B |        C |         D |
| ---------: | --------: | --------: | -------: | --------: |
| 2018-11-02 | -0.158446 | -0.488535 |  0.08296 | -1.913573 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.03383 |  0.712624 |

#### df.iloc[:,1:4] 选择全部行和部分列，也叫列切片
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

#### df.iloc[1,3] 获取特定位置的值
```python
# 获取特定的值
df.iloc[1,3]
-1.9135725473596013
```

### 按条件选择数据

#### df.query

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

- ***实例1**

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

- **实例2**

```c
# 实例2：@符合来标记本地变量
Cmean = df['C'].mean() #6.0
result1 = df[(df.A < Cmean) & (df.B < Cmean)]
result1 = df.query('A < @Cmean and B < @Cmean')#等价
result1
 
  A B C D
0 0 1 2 3
1 4 5 6 7
123456789
```

- **实例3：多索引**

```c
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

- **实例4：多索引MultiIndex**

```c
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

- **实例5：多数据df - 具有相同列名（或索引级别/名称）**

```c
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

- **实例6：Python与pandas语法比较**

```c
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

To select rows whose column value equals a scalar, `some_value`, use `==`:

```py
df.loc[df['column_name'] == some_value]
```

To select rows whose column value is in an iterable, `some_values`, use `isin`:

```py
df.loc[df['column_name'].isin(some_values)]
```

Combine multiple conditions with `&`:

```py
df.loc[(df['column_name'] >= A) & (df['column_name'] <= B)]
```

Note the parentheses. Due to Python's [operator precedence rules](https://docs.python.org/3/reference/expressions.html#operator-precedence), `&` binds more tightly than `<=` and `>=`. Thus, the parentheses in the last example are necessary. Without the parentheses

```py
df['column_name'] >= A & df['column_name'] <= B
```

is parsed as

```py
df['column_name'] >= (A & df['column_name']) <= B
```

which results in a [Truth value of a Series is ambiguous error](https://stackoverflow.com/questions/36921951/truth-value-of-a-series-is-ambiguous-use-a-empty-a-bool-a-item-a-any-o).

------

To select rows whose column value *does not equal* `some_value`, use `!=`:

```py
df.loc[df['column_name'] != some_value]
```

`isin` returns a boolean Series, so to select rows whose value is *not* in `some_values`, negate the boolean Series using `~`:

```py
df.loc[~df['column_name'].isin(some_values)]
```

------

For example,

```py
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

```py
     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

------

If you have multiple values you want to include, put them in a list (or more generally, any iterable) and use `isin`:

```py
print(df.loc[df['B'].isin(['one','three'])])
```

yields

```py
     A      B  C   D
0  foo    one  0   0
1  bar    one  1   2
3  bar  three  3   6
6  foo    one  6  12
7  foo  three  7  14
```

------

Note, however, that if you wish to do this many times, it is more efficient to make an index first, and then use `df.loc`:

```py
df = df.set_index(['B'])
print(df.loc['one'])
```

yields

```py
       A  C   D
B              
one  foo  0   0
one  bar  1   2
one  foo  6  12
```

or, to include multiple values from the index use `df.index.isin`:

```py
df.loc[df.index.isin(['one','two'])]
```

yields

```py
       A  C   D
B              
one  foo  0   0
one  bar  1   2
two  foo  2   4
two  foo  4   8
two  bar  5  10
one  foo  6  12
```



#### 布尔值索引

```python
# 使用单列的数据作为条件进行筛选
df[df.A>0]
```

|            |        A |        B |        C |        D |
| ---------: | -------: | -------: | -------: | -------: |
| 2018-11-04 | 1.013527 | 0.270167 | 0.081805 | 0.178193 |

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

```python
# 使用isin()方法过滤
df2.head()
```

|      |    A |        B |    C |     D |    E |
| ---: | ---: | -------: | ---: | ----: | ---: |
|    0 |    1 | 20181101 |    3 |  test |  1.5 |
|    1 |    1 | 20181101 |    3 | train |  1.5 |
|    2 |    1 | 20181101 |    3 |  test |  1.5 |
|    3 |    1 | 20181101 |    3 | train |  1.5 |

```python
df2[df2['D'].isin(['test'])]
```

|      |    A |        B |    C |    D |    E |
| ---: | ---: | -------: | ---: | ---: | ---: |
|    0 |    1 | 20181101 |    3 | test |  1.5 |
|    2 |    1 | 20181101 |    3 | test |  1.5 |

443



+500



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

# **1. Boolean indexing**

... Boolean indexing requires finding the true value of each row's `'A'` column being equal to `'foo'`, then using those truth values to identify which rows to keep. Typically, we'd name this series, an array of truth values, `mask`. We'll do so here as well.

```py
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

------

# **2. Positional indexing**

Positional indexing (`df.iloc[...]`) has its use cases, but this isn't one of them. In order to identify where to slice, we first need to perform the same boolean analysis we did above. This leaves us performing one extra step to accomplish the same task.

```py
mask = df['A'] == 'foo'
pos = np.flatnonzero(mask)
df.iloc[pos]

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

# **3. Label indexing**

*Label* indexing can be very handy, but in this case, we are again doing more work for no benefit

```py
df.set_index('A', append=True, drop=False).xs('foo', level=1)

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

# **4. `df.query()` API**

*`pd.DataFrame.query`* is a very elegant/intuitive way to perform this task, but is often slower. **However**, if you pay attention to the timings below, for large data, the query is very efficient. More so than the standard approach and of similar magnitude as my best suggestion.

```py
df.query('A == "foo"')

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

------

My preference is to use the `Boolean` `mask`

Actual improvements can be made by modifying how we create our `Boolean` `mask`.

**`mask` alternative 1** *Use the underlying NumPy array and forgo the overhead of creating another `pd.Series`*

```py
mask = df['A'].values == 'foo'
```

I'll show more complete time tests at the end, but just take a look at the performance gains we get using the sample data frame. First, we look at the difference in creating the `mask`

```py
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

```py
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

```py
%%timeit
mask = d1['A'].values == 7
d1[mask]

179 µs ± 8.73 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```

Versus

```py
%%timeit
mask = d1['A'].values == 7
pd.DataFrame(d1.values[mask], d1.index[mask], d1.columns)

87 µs ± 5.12 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```

We cut the time in half.

------

**`mask` alternative 3**

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

However, as before, we can utilize NumPy to improve performance while sacrificing virtually nothing. We'll use `np.in1d`

```py
mask = np.in1d(df['A'].values, ['foo'])
df[mask]

     A      B  C   D
0  foo    one  0   0
2  foo    two  2   4
4  foo    two  4   8
6  foo    one  6  12
7  foo  three  7  14
```

------

**Timing**

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



[Share](https://stackoverflow.com/a/46165056)

[Improve this answer](https://stackoverflow.com/posts/46165056/edit)

Follow

### 设定数值（类似于sql update 或者add）

- 设定一个新的列

```python
df['E'] = [1,2,3,4,5,6,7]
df
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |    1 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |    2 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |    3 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |    4 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |    5 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |    6 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |    7 |

- 通过标签设定新的值

```python
df.loc['2018-11-01','E']= 10  # 第一行，E列的数据修改为10
df
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |   10 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 |    2 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |    3 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |    4 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |    5 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |    6 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |    7 |

```python
df.iloc[1,4]=5000  # 第二行第五列数据修改为5000
df
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |   10 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 | 5000 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |    3 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |    4 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |    5 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |    6 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |    7 |

```python
df3 =df.copy()
df3[df3<0]= -df3
df3  # 都变成非负数
```

|            |        A |        B |        C |        D |    E |
| ---------: | -------: | -------: | -------: | -------: | ---: |
| 2018-11-01 | 0.170364 | 0.237541 | 0.529903 | 0.660073 |   10 |
| 2018-11-02 | 0.158446 | 0.488535 | 0.082960 | 1.913573 | 5000 |
| 2018-11-03 | 0.518426 | 0.730866 | 1.033830 | 0.712624 |    3 |
| 2018-11-04 | 1.013527 | 0.270167 | 0.081805 | 0.178193 |    4 |
| 2018-11-05 | 0.897497 | 0.016279 | 0.234993 | 0.081208 |    5 |
| 2018-11-06 | 0.030580 | 0.545561 | 1.091127 | 0.131579 |    6 |
| 2018-11-07 | 0.313342 | 0.688179 | 0.417754 | 0.855027 |    7 |

#### 缺失值处理

```python
df
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |  0.660073 |   10 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | -1.913573 | 5000 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |  0.712624 |    3 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |    4 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |    5 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |    6 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |    7 |

```python
df['E']=[1,np.nan,2,np.nan,4,np.nan,6]
df.loc['2018-11-01':'2018-11-03','D']=np.nan
df
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |       NaN |  1.0 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 |       NaN |  NaN |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |       NaN |  2.0 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |  NaN |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |  4.0 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |  NaN |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |  6.0 |

- 去掉缺失值的行

```python
df4 = df.copy()
df4.dropna(how='any')
```

|            |         A |         B |         C |        D |    E |
| ---------: | --------: | --------: | --------: | -------: | ---: |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 | 0.081208 |  4.0 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 | 0.855027 |  6.0 |

```python
df4.dropna(how='all')
# """DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)""" 
# aixs 轴0或者1 index或者columns
# how 方式
# thresh 超过阈值个数的缺失值
# subset 那些字段的处理
# inplace 是否直接在原数据框中的替换
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |       NaN |  1.0 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 |       NaN |  NaN |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |       NaN |  2.0 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |  NaN |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |  4.0 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |  NaN |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |  6.0 |

- 对缺失值就行填充

```python
df4.fillna(1000)
```

|            |         A |         B |         C |           D |      E |
| ---------: | --------: | --------: | --------: | ----------: | -----: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 | 1000.000000 |    1.0 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 | 1000.000000 | 1000.0 |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 | 1000.000000 |    2.0 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |    0.178193 | 1000.0 |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |    0.081208 |    4.0 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 |   -0.131579 | 1000.0 |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |    0.855027 |    6.0 |

- 对数据进行布尔值进行填充

```python
pd.isnull(df4)
```

|            |     A |     B |     C |     D |     E |
| ---------: | ----: | ----: | ----: | ----: | ----: |
| 2018-11-01 | False | False | False |  True | False |
| 2018-11-02 | False | False | False |  True |  True |
| 2018-11-03 | False | False | False |  True | False |
| 2018-11-04 | False | False | False | False |  True |
| 2018-11-05 | False | False | False | False | False |
| 2018-11-06 | False | False | False | False |  True |
| 2018-11-07 | False | False | False | False | False |

#### 数据操作

```python
#统计的工作一般情况下都不包含缺失值，
df4.mean() 
#  默认是对列进行求平均，沿着行方向也就是axis=0
A   -0.153590
B    0.016580
C    0.014174
D    0.245712
E    3.250000
dtype: float64
df4.mean(axis=1)
#  沿着列方向求每行的平均
2018-11-01    0.280499
2018-11-02   -0.188007
2018-11-03    0.294653
2018-11-04    0.385923
2018-11-05    0.586488
2018-11-06    0.368632
2018-11-07    1.087150
Freq: D, dtype: float64
 # 对于拥有不同维度，需要对齐的对象进行操作。Pandas会自动的沿着指定的维度进行广播：
s = pd.Series([1,3,4,np.nan,6,7,8],index=dates)
s
2018-11-01    1.0
2018-11-02    3.0
2018-11-03    4.0
2018-11-04    NaN
2018-11-05    6.0
2018-11-06    7.0
2018-11-07    8.0
Freq: D, dtype: float64
df4.sub(s,axis='index')
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -1.170364 | -1.237541 | -0.470097 |       NaN |  0.0 |
| 2018-11-02 | -3.158446 | -3.488535 | -2.917040 |       NaN |  NaN |
| 2018-11-03 | -4.518426 | -3.269134 | -5.033830 |       NaN | -2.0 |
| 2018-11-04 |       NaN |       NaN |       NaN |       NaN |  NaN |
| 2018-11-05 | -6.897497 | -6.016279 | -6.234993 | -5.918792 | -2.0 |
| 2018-11-06 | -7.030580 | -6.454439 | -5.908873 | -7.131579 |  NaN |
| 2018-11-07 | -8.313342 | -8.688179 | -8.417754 | -7.144973 | -2.0 |

```python
df4
```

|            |         A |         B |         C |         D |    E |
| ---------: | --------: | --------: | --------: | --------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |       NaN |  1.0 |
| 2018-11-02 | -0.158446 | -0.488535 |  0.082960 |       NaN |  NaN |
| 2018-11-03 | -0.518426 |  0.730866 | -1.033830 |       NaN |  2.0 |
| 2018-11-04 |  1.013527 |  0.270167 |  0.081805 |  0.178193 |  NaN |
| 2018-11-05 | -0.897497 | -0.016279 | -0.234993 |  0.081208 |  4.0 |
| 2018-11-06 | -0.030580 |  0.545561 |  1.091127 | -0.131579 |  NaN |
| 2018-11-07 | -0.313342 | -0.688179 | -0.417754 |  0.855027 |  6.0 |

```python
df4.apply(np.cumsum)
```

|            |         A |         B |         C |        D |    E |
| ---------: | --------: | --------: | --------: | -------: | ---: |
| 2018-11-01 | -0.170364 | -0.237541 |  0.529903 |      NaN |  1.0 |
| 2018-11-02 | -0.328810 | -0.726077 |  0.612863 |      NaN |  NaN |
| 2018-11-03 | -0.847235 |  0.004789 | -0.420966 |      NaN |  3.0 |
| 2018-11-04 |  0.166292 |  0.274956 | -0.339161 | 0.178193 |  NaN |
| 2018-11-05 | -0.731205 |  0.258677 | -0.574154 | 0.259402 |  7.0 |
| 2018-11-06 | -0.761786 |  0.804237 |  0.516973 | 0.127822 |  NaN |
| 2018-11-07 | -1.075128 |  0.116059 |  0.099219 | 0.982849 | 13.0 |

```python
df4.apply(lambda x: x.max()-x.min())
A    1.911024
B    1.419044
C    2.124957
D    0.986606
E    5.000000
dtype: float64
```

### 统计个数与离散化

```python
s = pd.Series(np.random.randint(0,7,size=15))
s
0     5
1     4
2     1
3     2
4     1
5     0
6     2
7     6
8     4
9     3
10    1
11    1
12    1
13    3
14    2
dtype: int32
s.value_counts()
# 统计元素的个数，并按照元素统计量进行排序，未出现的元素不会显示出来
1    5
2    3
4    2
3    2
6    1
5    1
0    1
dtype: int64
s.reindex(range(0,7))
# 按照固定的顺序输出元素的个数统计
0    5
1    4
2    1
3    2
4    1
5    0
6    2
dtype: int32
s.mode()
#  众数 
0    1
dtype: int32
```

- 离散化

```python
# 连续值转化为离散值，可以使用cut函数进行操作（bins based on vlaues） qcut （bins based on sample
# quantiles） 函数
arr = np.random.randint(0,20,size=15)  # 正态分布
arr
array([ 5, 18, 13, 16, 16,  1, 15, 11,  0, 17, 16, 18, 15, 12, 13])
factor = pd.cut(arr,3)
factor
[(-0.018, 6.0], (12.0, 18.0], (12.0, 18.0], (12.0, 18.0], (12.0, 18.0], ..., (12.0, 18.0], (12.0, 18.0], (12.0, 18.0], (6.0, 12.0], (12.0, 18.0]]
Length: 15
Categories (3, interval[float64]): [(-0.018, 6.0] < (6.0, 12.0] < (12.0, 18.0]]
pd.value_counts(factor)
(12.0, 18.0]     10
(-0.018, 6.0]     3
(6.0, 12.0]       2
dtype: int64
factor1 = pd.cut(arr,[-1,5,10,15,20])
pd.value_counts(factor1)
(15, 20]    6
(10, 15]    6
(-1, 5]     3
(5, 10]     0
dtype: int64
factor2 = pd.qcut(arr,[0,0.25,0.5,0.75,1])
pd.value_counts(factor2)
(11.5, 15.0]      5
(-0.001, 11.5]    4
(16.0, 18.0]      3
(15.0, 16.0]      3
dtype: int64
```

### 数据合并

- concat
- merge（类似于sql数据库中的join）
- append

#### 首先看concat合并数据框

```python
df = pd.DataFrame(np.random.randn(10,4))  #  10行列的标准正态分布数据框
df
```

|      |         0 |         1 |         2 |         3 |
| ---: | --------: | --------: | --------: | --------: |
|    0 |  0.949746 | -0.050767 |  1.478622 | -0.239901 |
|    1 | -0.297120 | -0.562589 |  0.371837 |  1.180715 |
|    2 |  0.953856 |  0.492295 |  0.821156 | -0.323328 |
|    3 |  0.016153 |  1.554225 | -1.166304 | -0.904040 |
|    4 |  0.204763 | -0.951291 | -1.317620 |  0.672900 |
|    5 |  2.241006 | -0.925746 | -1.961408 |  0.853367 |
|    6 |  2.217133 | -0.430812 |  0.518926 |  1.741445 |
|    7 | -0.571104 | -0.437305 | -0.902241 |  0.786231 |
|    8 | -2.511387 |  0.523760 |  1.811622 | -0.777296 |
|    9 |  0.252690 |  0.901952 |  0.619614 | -0.006631 |

```python
d1,d2,d3  = df[:3],df[3:7],df[7:]
d1,d2,d3
(          0         1         2         3
 0  0.949746 -0.050767  1.478622 -0.239901
 1 -0.297120 -0.562589  0.371837  1.180715
 2  0.953856  0.492295  0.821156 -0.323328,
           0         1         2         3
 3  0.016153  1.554225 -1.166304 -0.904040
 4  0.204763 -0.951291 -1.317620  0.672900
 5  2.241006 -0.925746 -1.961408  0.853367
 6  2.217133 -0.430812  0.518926  1.741445,
           0         1         2         3
 7 -0.571104 -0.437305 -0.902241  0.786231
 8 -2.511387  0.523760  1.811622 -0.777296
 9  0.252690  0.901952  0.619614 -0.006631)
pd.concat([d1,d2,d3])
#合并三个数据框，数据结构相同，通常合并相同结构的数据，数据框中的字段一致，类似于数据添加新的数据来源
```

|      |         0 |         1 |         2 |         3 |
| ---: | --------: | --------: | --------: | --------: |
|    0 |  0.949746 | -0.050767 |  1.478622 | -0.239901 |
|    1 | -0.297120 | -0.562589 |  0.371837 |  1.180715 |
|    2 |  0.953856 |  0.492295 |  0.821156 | -0.323328 |
|    3 |  0.016153 |  1.554225 | -1.166304 | -0.904040 |
|    4 |  0.204763 | -0.951291 | -1.317620 |  0.672900 |
|    5 |  2.241006 | -0.925746 | -1.961408 |  0.853367 |
|    6 |  2.217133 | -0.430812 |  0.518926 |  1.741445 |
|    7 | -0.571104 | -0.437305 | -0.902241 |  0.786231 |
|    8 | -2.511387 |  0.523760 |  1.811622 | -0.777296 |
|    9 |  0.252690 |  0.901952 |  0.619614 | -0.006631 |

#### merge方式合并（数据库中的join）

```python
left = pd.DataFrame({'key':['foo','foo'],"lval":[1,2]})
right = pd.DataFrame({'key':['foo','foo'],'rval':[4,5]})
left
```

|      |  key | lval |
| ---: | ---: | ---: |
|    0 |  foo |    1 |
|    1 |  foo |    2 |

```python
right
```

|      |  key | rval |
| ---: | ---: | ---: |
|    0 |  foo |    4 |
|    1 |  foo |    5 |

```python
pd.merge(left,right,on='key')
```

|      |  key | lval | rval |
| ---: | ---: | ---: | ---: |
|    0 |  foo |    1 |    4 |
|    1 |  foo |    1 |    5 |
|    2 |  foo |    2 |    4 |
|    3 |  foo |    2 |    5 |

```python
left = pd.DataFrame({'key':['foo','bar'],"lval":[1,2]})
right = pd.DataFrame({'key':['foo','bar'],'rval':[4,5]})
pd.merge(left,right,on='key')
```

|      |  key | lval | rval |
| ---: | ---: | ---: | ---: |
|    0 |  foo |    1 |    4 |
|    1 |  bar |    2 |    5 |

```python
left
```

|      |  key | lval |
| ---: | ---: | ---: |
|    0 |  foo |    1 |
|    1 |  bar |    2 |

```python
right
```

|      |  key | rval |
| ---: | ---: | ---: |
|    0 |  foo |    4 |
|    1 |  bar |    5 |

#### Append方式合并数据

```python
#  与concat 类似，常用的方法可以参考一下日子
df = pd.DataFrame(np.random.randn(8,4),columns=['A','B','C','D'])
df
```

|      |         A |         B |         C |         D |
| ---: | --------: | --------: | --------: | --------: |
|    0 |  1.825997 | -0.331086 | -0.067143 |  0.747226 |
|    1 | -0.027497 |  0.861639 |  0.928621 | -2.549617 |
|    2 | -0.546645 | -0.072253 | -0.788483 |  0.484140 |
|    3 | -0.472240 | -1.776993 | -1.647407 |  0.170596 |
|    4 | -0.099453 |  0.380143 | -0.890510 |  1.233741 |
|    5 |  0.351915 |  0.137522 | -1.165938 |  1.128146 |
|    6 |  0.558442 | -1.047060 | -0.598197 | -1.979876 |
|    7 |  0.067321 | -1.037666 | -1.140675 | -0.098562 |

```python
## 
d1 = df.iloc[3]
df.append(d1,ignore_index= True)
```

|      |         A |         B |         C |         D |
| ---: | --------: | --------: | --------: | --------: |
|    0 |  1.825997 | -0.331086 | -0.067143 |  0.747226 |
|    1 | -0.027497 |  0.861639 |  0.928621 | -2.549617 |
|    2 | -0.546645 | -0.072253 | -0.788483 |  0.484140 |
|    3 | -0.472240 | -1.776993 | -1.647407 |  0.170596 |
|    4 | -0.099453 |  0.380143 | -0.890510 |  1.233741 |
|    5 |  0.351915 |  0.137522 | -1.165938 |  1.128146 |
|    6 |  0.558442 | -1.047060 | -0.598197 | -1.979876 |
|    7 |  0.067321 | -1.037666 | -1.140675 | -0.098562 |
|    8 | -0.472240 | -1.776993 | -1.647407 |  0.170596 |

