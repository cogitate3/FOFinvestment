# pandas常用代码

Date Created: Dec 3, 2020 8:25 PM
Status: Doing

### 1、删除一列或者一行数据

```python
import pandas as pd

df1 = pd.DataFrame([['Snow','M',22],['Tyrion','M',32],['Sansa','F',18],['Arya','F',14]], columns=['name','gender','age'])
print(df1)

print('---------删除行或列:DataFrame.drop()--------')
# drop默认对原表不生效，如果要对原表生效，需要加参数：inplace=True

print("----删除单行----")
df2=df1.drop(labels=0)   # axis默认等于0，即按行删除，这里表示按行删除第0行
print(df2)

print("------删除多行------")
# 通过labels来控制删除行或列的个数，如果是删多行/多列，需写成labels=[1,3]，不能写成labels=[1:2],用:号会报错
# 删除指定的某几行（非连续的）
df21=df1.drop(labels=[1,3],axis=0)   # axis=0 表示按行删除，删除第1行和第3行
print(df21)

# 要删除连续的多行可以用range(),删除连续的多列不能用此方法
df22=df1.drop(labels=range(1,4),axis=0)   # axis=0 表示按行删除，删除索引值是第1行至第3行的正行数据
print(df22)

print("----删除单列----")
df3=df1.drop(labels='gender',axis=1)  # axis=1 表示按列删除，删除gender列
print(df3)

print("----删除多列----")
# 删除指定的某几列
df4=df1.drop(labels=['gender',"age"],axis=1)  # axis=1 表示按列删除，删除gender、age列print(df4)
```

### 2、更换某个值

```python
import pandas as pd
df1 = pd.DataFrame([['Snow','M',22],['Tyrion','M',32],['Sansa','F',18],['Arya','F',14]], columns=['name','gender','age'])

print("--------更换单个值----------")
# loc和iloc 可以更换单行、单列、多行、多列的值
df1.loc[0,'age']=25      # 思路：先用loc找到要更改的值，再用赋值（=）的方法实现更换值
df1.iloc[0,2]=25         # iloc：用索引位置来查找

# at 、iat只能更换单个值
df1.at[0,'age']=25      # iat 用来取某个单值,参数只能用数字索引
df1.iat[0,2]=25         # at 用来取某个单值,参数只能用index和columns索引名称
print(df1)
```

### 3、增加一行或一列数据

```python
import pandas as pd

df1 = pd.DataFrame([['Snow','M',22],['Tyrion','M',32],['Sansa','F',18],['Arya','F',14]], columns=['name','gender','age'])

print("----------在最后新增一列---------------")
print("-------案例1----------")
# 在数据框最后加上score一列，元素值分别为：80，98，67，90
df1['score']=[80,98,67,90]   # 增加列的元素个数要跟原数据列的个数一样
print(df1)

print("-------案例2----------")
print("---------在指定位置新增列:用insert（）--------")
# 在gender后面加一列城市
# 在具体某个位置插入一列可以用insert的方法
# 语法格式：列表.insert(index, obj)
# index --->对象 obj 需要插入的索引位置。
# obj ---> 要插入列表中的对象（列名）

col_name=df1.columns.tolist()                   # 将数据框的列名全部提取出来存放在列表里
print(col_name)

col_name.insert(2,'city')                      # 在列索引为2的位置插入一列,列名为:city，刚插入时不会有值，整列都是NaN
df1=df1.reindex(columns=col_name)              # DataFrame.reindex() 对原行/列索引重新构建索引值

df1['city']=['北京','山西','湖北','澳门']   # 给city列赋值
print(df1)

print("----------新增行---------------")
# 重要！！先创建一个DataFrame，用来增加进数据框的最后一行
new=pd.DataFrame({'name':'lisa',
                  'gender':'F',
                  'city':'北京',
                  'age':19,
                  'score':100},
                 index=[1])   # 自定义索引为：1 ，这里也可以不设置index
print(new)

print("-------在原数据框df1最后一行新增一行，用append方法------------")
df1=df1.append(new,ignore_index=True)   # ignore_index=True,表示不按原来的索引，从0开始自动递增
print(df1)
```

### 4、更改列标签据

```python

```

### 5、更改列标签据

```python

```


## **分组**

根据研究目的，将所有样本点按照一个或多个属性划分为多个组，就是分组。

pandas中，数据表就是DataFrame对象，分组就是groupby方法。将DataFrame中所有行按照一列或多列来划分，分为多个组，列值相同的在同一组，列值不同的在不同组。

分组后，就得到一个groupby对象，代表着已经被分开的各个组。后续所有的动作，比如计数，求平均值等，都是针对这个对象，也就是都是针对各个组。即在每个组组内进行计数，求平均值等。

### **分组的返回结果**

```python
df = pd.DataFrame([['a', 'man', 120, 90],
                   ['b', 'woman', 130, 100],
                   ['a', 'man', 110, 108],
                   ['a', 'woman', 120, 118]], columns=['level', 'gender', 'math','chinese'])
group = df.groupby('gender')
```

df.groupby() 函数返回的对象是一系列键值对，其中键是分组的字段值，值是该字段值下的数据表。分组的结果是无法直接输出的，print()只能看到该结果的数据类型。可以用循环对分组后的结果进行遍历。

```python
print(group)
# <pandas.core.groupby.generic.DataFrameGroupBy object at 0x11cb60f50>
for key, value in group:
    print(key)
    print(value)
    print("")
man
  level gender  math  chinese
0     a    man   120       90
2     a    man   110      108

woman
  level gender  math  chinese
1     b  woman   130      100
3     a  woman   120      118
```

### **按一列分组：df.groupby(column)**

```python
group = df.groupby('gender') # 按照'gender'列的值来分组，创建一个groupby对象
# group = df.groupby(['gender']) # 等价写法
for key, df in group:
    print(key)
    print(df)
man
  level gender  math  chinese
0     a    man   120       90
2     a    man   110      108

woman
  level gender  math  chinese
1     b  woman   130      100
3     a  woman   120      118
```

### **按多列分组：df.groupby([column1, column2])**

```python
group = df.groupby(['gender', 'level'])
# 先按照'grade'列的值来分组。每组内，再按'level'列来分组。也返回一个groupby对象
for key, value in group:
    print(key)
    print(value)
    print("")
('man', 'a')
  level gender  math  chinese
0     a    man   120       90
2     a    man   110      108

('woman', 'a')
  level gender  math  chinese
3     a  woman   120      118

('woman', 'b')
  level gender  math  chinese
1     b  woman   130      100
```

### **查看每组的统计数据：df.groupby(column).describe()**

对数据表中的数值列进行统计，给出包括count = 计数，mean = 平均数，std = 方差，min = 最小值，25% = 四分位数，50% = 二分位数，75% = 四分之三分位数，max = 最大值的信息。不会对非数值列统计。

返回的是一个dataframe。

- 查看所有列的统计信息
```

```
```python
group = df.groupby(['gender'])
df1 = group.describe()
# df1 = df.groupby(['gender']).describe() # 等价写法

print(type(df1)) 
print(df1)
<class 'pandas.core.frame.DataFrame'>

 math                                                     chinese  \
       count   mean       std    min    25%    50%    75%    max   count   
gender                                                                     
man      2.0  115.0  7.071068  110.0  112.5  115.0  117.5  120.0     2.0   
woman    2.0  125.0  7.071068  120.0  122.5  125.0  127.5  130.0     2.0   

         mean        std    min    25%    50%    75%    max  
gender                                                       
man      99.0  12.727922   90.0   94.5   99.0  103.5  108.0  
woman   109.0  12.727922  100.0  104.5  109.0  113.5  118.0
```

- 查看指定列的统计信息

```python
group = df.groupby(['gender'])
df1 = group.describe()['math'] # 只看math列的统计信息
print(df1)
count   mean    std    min    25%    50%    75%    max
gender                                                           
man       2.0  115.0  7.071068  110.0  112.5  115.0  117.5  120.0
woman     2.0  125.0  7.071068  120.0  122.5  125.0  127.5  130.0
```

- 查看纵向视图

unstack()可以将每列的统计信息垂直排列。

```python
group = df.groupby(['gender'])
df1 = group.describe().unstack()
print(df1)
gender
math     count  man         2.000000
                woman       2.000000
         ...
         max    man       120.000000
                woman     130.000000
chinese  count  man         2.000000
                woman       2.000000
         ...
                woman     113.500000
         max    man       108.000000
                woman     118.000000
dtype: float64
```

### **组内离散列计数：df.groupby(column)[column2].value_counts()**

```python
数据表中的列按值是否连续，可以分为连续值列、离散值列。对于离散值列，可以统计其不重复值的个数。对于连续值列，统计不重复值一般没有意义。统计结果是一个Series对象。
```

`group = df.groupby(['gender'])
df1 = group['level'].value_counts() # 统计'level'列的不重复值个数

print(type(df1))
print(df1)
<class 'pandas.core.series.Series'>

gender  level
man     a        2
woman   a        1
        b        1
Name: level, dtype: int64`

### **组内数值列和：df.groupby(column).sum()**

```python
每组内，只有数值列能求和，非数值列不可以。
```

`group = df.groupby(['gender'])
df1 = group.sum()
print(df1)
math  chinese
gender               
man      230      198
woman    250      218`

### **组内成员数：df.groupby(column).count()**

每组内，按列统计每组的成员数。每列的统计结果是一样的。

```python
group = df.groupby(['gender'])
df1 = group.count()
print(df1)
level  math  chinese
gender                      
man         2     2        2
woman       2     2        2
```

### **组内数值列均值：df.groupby(column).mean()**

每组内，统计所有数值列的均值，非数值列无均值。

- 所有组的均值

```python
group = df.groupby(['gender'])
df1 = group.mean()
print(df1)
math  chinese
gender               
man      115       99
woman    125      109
```

- 单组的均值

```python
group = df.groupby(['gender'])
df1 = group['math'].mean()
print(df1)
gender
man      115
woman    125
Name: math, dtype: int64
```

### **组内数值列中位数：df.groupby(column).median()**

每组内，统计所有数值列的中位数，非数值列无中位数。

- 统计所有数值列的中位数

```python
group = df.groupby(['gender'])
df1 = group.median()
print(df1)
math  chinese
gender               
man      115       99
woman    125      109
```

- 统计单个数值列的中位数

```python
group = df.groupby(['gender'])
df1 = group['math'].median() # 统计'math'列的中位数
print(df1)
gender
man      115
woman    125
Name: math, dtype: int64
```

### **组内数值列最大值：df.groupby(column).max()**

每组内，统计所有数值列的最大值，非数值列无最大值。

- 统计所有数值列的最大值

```python
group = df.groupby(['gender'])
df1 = group.max()
print(df1)
level  math  chinese
gender                     
man        a   120      108
woman      b   130      118
```

- 统计单个数值列的最大值

```python
group = df.groupby(['gender'])
df1 = group['math'].max()
print(df1)
gender
man      120
woman    130
Name: math, dtype: int64
```

### **组内数值列最小值：df.groupby(column).min()**

每组内，统计所有数值列的最小值，非数值列无最小值。

- 统计所有数值列的最小值

```python
group = df.groupby(['gender'])
df1 = group.min()
print(df1)
level  math  chinese
gender                     
man        a   110       90
woman      a   120      100
```

- 统计单个数值列的最小值

```python
group = df.groupby(['gender'])
df1 = group['math'].min()
print(df1)
gender
man      110
woman    120
Name: math, dtype: int64
```

### **组内数值列标准差：df.groupby(column).std()**

每组内，统计所有数值列的标准差，非数值列无标准差。

- 统计所有数值列的标准差

```python
group = df.groupby(['gender'])
df1 = group.std()
print(df1)
math    chinese
gender                     
man     7.071068  12.727922
woman   7.071068  12.727922
```

- 统计单个数值列的标准差

```python
group = df.groupby(['gender'])
df1 = group['math'].std()
print(df1)
gender
man      7.071068
woman    7.071068
Name: math, dtype: float64
```

### **组内数值列方差：df.groupby(column).var()**

每组内，统计所有数值列的方差，非数值列无方差。

- 统计所有数值列的方差

```python
group = df.groupby(['gender'])
df1 = group.var()
print(df1)
math  chinese
gender               
man       50      162
woman     50      162
```

- 统计单个数值列的方差

```python
group = df.groupby(['gender'])
df1 = group['math'].var()
print(df1)
gender
man      50
woman    50
Name: math, dtype: int64
```

### **组内数值列二分位数：df.groupby(column).quantile()**

```python
每组内，统计所有数值列的二分位数，非数值列无二分位数。
```

- 统计单个数值列的二分位数

`group = df.groupby(['gender'])
df1 = group['math'].quantile()
print(df1)
gender
man      115.0
woman    125.0
Name: math, dtype: float64`

### **组内数值列累计和：df.groupby(column).cumsum()**

每组内，统计所有数值列的累计和，非数值列无累计和。

[暂时没搞懂]

### **组内应用函数：df.groupby(column1)[column2].apply()**

每组内，可以指定只求某一列的统计指标，包括平均数，方差等。function 可以是mean，或者std等。

```python
group = df.groupby(['gender'])
df1 = group['math'].apply(np.mean) # 求组内均值
print(df1)
gender
man      115.0
woman    125.0
Name: math, dtype: float64
```

### **组内应用多个函数：df.groupby(column).agg([...])**

想同时查看每组内，某数值列的多个统计指标，可以用agg函数。它的参数是一个列表，列表中包含各个函数。

```python
group = df.groupby(['gender'])
df1 = group['math'].agg([np.mean,np.std]) # 组内应用均值，方差两个函数
print(df1)
mean       std
gender                
man      115  7.071068
woman    125  7.071068
```

### **组内不同列用不同函数：df.groupby(column).agg({column1:func, column2:func,...})**

```python
group = df.groupby(['gender'])
df1 = group.agg({'math':np.mean, 'chinese':np.std})
print(df1)
math    chinese
gender                 
man      115  12.727922
woman    125  12.727922
```

发布于 2020-06-18