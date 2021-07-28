## [pandas 数据类型转换](https://www.cnblogs.com/onemorepoint/p/9404753.html)

### 数据处理过程的数据类型

- 当利用pandas进行数据处理的时候，经常会遇到数据类型的问题，当拿到数据的时候，首先需要确定拿到的是正确类型的数据，一般通过数据类型的转化，这篇文章就介绍pandas里面的数据类型（data types也就是常用的dtyps），以及pandas与numpy之间的数据对应关系。
- ![img](http://ww1.sinaimg.cn/large/9ebd4c2bgy1fto9860xy9j20sl0bfgrk.jpg)
- 主要介绍object，int64，float64，datetime64，bool等几种类型，category与timedelta两种类型会单独的在其他文章中进行介绍。当然本文中也会涉及简单的介绍。

数据类型的问题一般都是出了问题之后才会发现的，所以有了一些经验之后就会拿到数据之后，就直接看数据类型，是否与自己想要处理的数据格式一致，这样可以从一开始避免一些尴尬的问题出现。那么我们以一个简单的例子，利用jupyter notebook进行一个数据类型的介绍。

```python
####按照惯例导入两个常用的数据处理的包，numpy与pandas
import numpy as np
import pandas as pd
# 从csv文件读取数据，数据表格中只有5行，里面包含了float，string，int三种数据python类型，也就是分别对应的pandas的float64，object，int64
# csv文件中共有六列，第一列是表头，其余是数据。
df = pd.read_csv("sales_data_types.csv")
print(df)
   Customer Number     Customer Name          2016            2017  \
0            10002  Quest Industries  $125,000.00     $162,500.00    
1           552278    Smith Plumbing  $920,000.00   $1,012,000.00    
2            23477   ACME Industrial   $50,000.00      $62,500.00    
3            24900        Brekke LTD  $350,000.00     $490,000.00    
4           651029         Harbor Co   $15,000.00      $12,750.00    

  Percent Growth Jan Units  Month  Day  Year Active  
0         30.00%       500      1   10  2015      Y  
1         10.00%       700      6   15  2014      Y  
2         25.00%       125      3   29  2016      Y  
3          4.00%        75     10   27  2015      Y  
4        -15.00%    Closed      2    2  2014      N  
df.dtypes
Customer Number     int64
Customer Name      object
2016               object
2017               object
Percent Growth     object
Jan Units          object
Month               int64
Day                 int64
Year                int64
Active             object
dtype: object
# 假如想得到2016年与2017年的数据总和，可以尝试,但并不是我们需要的答案，因为这两列中的数据类型是object，执行该操作之后，得到是一个更加长的字符串，
# 当然我们可以通过df.info() 来获得关于数据框的更多的详细信息，
df['2016']+df['2017']
0      $125,000.00 $162,500.00 
1    $920,000.00 $1,012,000.00 
2        $50,000.00 $62,500.00 
3      $350,000.00 $490,000.00 
4        $15,000.00 $12,750.00 
dtype: object
df.info()
# Customer Number 列是float64，然而应该是int64
# 2016 2017两列的数据是object，并不是float64或者int64格式
# Percent以及Jan Units 也是objects而不是数字格式
# Month，Day以及Year应该转化为datetime64[ns]格式
# Active 列应该是布尔值
# 如果不做数据清洗，很难进行下一步的数据分析，为了进行数据格式的转化，pandas里面有三种比较常用的方法
# 1. astype()强制转化数据类型
# 2. 通过创建自定义的函数进行数据转化
# 3. pandas提供的to_nueric()以及to_datetime()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 10 columns):
Customer Number    5 non-null int64
Customer Name      5 non-null object
2016               5 non-null object
2017               5 non-null object
Percent Growth     5 non-null object
Jan Units          5 non-null object
Month              5 non-null int64
Day                5 non-null int64
Year               5 non-null int64
Active             5 non-null object
dtypes: int64(4), object(6)
memory usage: 480.0+ bytes
```

### 首先介绍最常用的astype()

比如可以通过astype()将第一列的数据转化为整数int类型

```python
df['Customer Number'].astype("int")
#  这样的操作并没有改变原始的数据框，而只是返回的一个拷贝
0     10002
1    552278
2     23477
3     24900
4    651029
Name: Customer Number, dtype: int32
# 想要真正的改变数据框，通常需要通过赋值来进行，比如
df["Customer Number"] = df["Customer Number"].astype("int")
print(df)
print("--------"*10)
print(df.dtypes)
   Customer Number     Customer Name          2016            2017  \
0            10002  Quest Industries  $125,000.00     $162,500.00    
1           552278    Smith Plumbing  $920,000.00   $1,012,000.00    
2            23477   ACME Industrial   $50,000.00      $62,500.00    
3            24900        Brekke LTD  $350,000.00     $490,000.00    
4           651029         Harbor Co   $15,000.00      $12,750.00    

  Percent Growth Jan Units  Month  Day  Year Active  
0         30.00%       500      1   10  2015      Y  
1         10.00%       700      6   15  2014      Y  
2         25.00%       125      3   29  2016      Y  
3          4.00%        75     10   27  2015      Y  
4        -15.00%    Closed      2    2  2014      N  
--------------------------------------------------------------------------------
Customer Number     int32
Customer Name      object
2016               object
2017               object
Percent Growth     object
Jan Units          object
Month               int64
Day                 int64
Year                int64
Active             object
dtype: object
# 通过赋值在原始的数据框基础上进行了数据转化，可以重新看一下我们新生成的数据框
print(df)
   Customer Number     Customer Name          2016            2017  \
0            10002  Quest Industries  $125,000.00     $162,500.00    
1           552278    Smith Plumbing  $920,000.00   $1,012,000.00    
2            23477   ACME Industrial   $50,000.00      $62,500.00    
3            24900        Brekke LTD  $350,000.00     $490,000.00    
4           651029         Harbor Co   $15,000.00      $12,750.00    

  Percent Growth Jan Units  Month  Day  Year Active  
0         30.00%       500      1   10  2015      Y  
1         10.00%       700      6   15  2014      Y  
2         25.00%       125      3   29  2016      Y  
3          4.00%        75     10   27  2015      Y  
4        -15.00%    Closed      2    2  2014      N  
# 然后像2016,2017 Percent Growth，Jan Units 这几列带有特殊符号的object是不能直接通过astype("flaot)方法进行转化的，
# 这与python中的字符串转化为浮点数，都要求原始的字符都只能含有数字本身，不能含有其他的特殊字符
# 我们可以试着将将Active列转化为布尔值，看一下到底会发生什么,五个结果全是True，说明并没有起到什么作用
#df["Active"].astype("bool")
df['2016'].astype('float')
---------------------------------------------------------------------------

ValueError                                Traceback (most recent call last)

<ipython-input-19-47cc9d68cd65> in <module>()
----> 1 df['2016'].astype('float')


C:\Anaconda3\lib\site-packages\pandas\core\generic.py in astype(self, dtype, copy, raise_on_error, **kwargs)
   3052         # else, only a single dtype is given
   3053         new_data = self._data.astype(dtype=dtype, copy=copy,
-> 3054                                      raise_on_error=raise_on_error, **kwargs)
   3055         return self._constructor(new_data).__finalize__(self)
   3056 


C:\Anaconda3\lib\site-packages\pandas\core\internals.py in astype(self, dtype, **kwargs)
   3187 
   3188     def astype(self, dtype, **kwargs):
-> 3189         return self.apply('astype', dtype=dtype, **kwargs)
   3190 
   3191     def convert(self, **kwargs):


C:\Anaconda3\lib\site-packages\pandas\core\internals.py in apply(self, f, axes, filter, do_integrity_check, consolidate, **kwargs)
   3054 
   3055             kwargs['mgr'] = self
-> 3056             applied = getattr(b, f)(**kwargs)
   3057             result_blocks = _extend_blocks(applied, result_blocks)
   3058 


C:\Anaconda3\lib\site-packages\pandas\core\internals.py in astype(self, dtype, copy, raise_on_error, values, **kwargs)
    459                **kwargs):
    460         return self._astype(dtype, copy=copy, raise_on_error=raise_on_error,
--> 461                             values=values, **kwargs)
    462 
    463     def _astype(self, dtype, copy=False, raise_on_error=True, values=None,


C:\Anaconda3\lib\site-packages\pandas\core\internals.py in _astype(self, dtype, copy, raise_on_error, values, klass, mgr, **kwargs)
    502 
    503                 # _astype_nansafe works fine with 1-d only
--> 504                 values = _astype_nansafe(values.ravel(), dtype, copy=True)
    505                 values = values.reshape(self.shape)
    506 


C:\Anaconda3\lib\site-packages\pandas\types\cast.py in _astype_nansafe(arr, dtype, copy)
    535 
    536     if copy:
--> 537         return arr.astype(dtype)
    538     return arr.view(dtype)
    539 


ValueError: could not convert string to float: '$15,000.00 '
```

以上的问题说明了一些问题

- 如果数据是纯净的数据，可以转化为数字
- astype基本也就是两种用作，数字转化为单纯字符串，单纯数字的字符串转化为数字，含有其他的非数字的字符串是不能通过astype进行转化的。
- 需要引入其他的方法进行转化，也就有了下面的自定义函数方法

### 通过自定义函数清理数据

- 通过下面的函数可以将货币进行转化

```python
def convert_currency(var):
    """
    convert the string number to a float
    _ 去除$
    - 去除逗号，
    - 转化为浮点数类型
    """
    new_value = var.replace(",","").replace("$","")
    return float(new_value)
# 通过replace函数将$以及逗号去掉，然后字符串转化为浮点数，让pandas选择pandas认为合适的特定类型，float或者int，该例子中将数据转化为了float64
# 通过pandas中的apply函数将2016列中的数据全部转化
df["2016"].apply(convert_currency)
0    125000.0
1    920000.0
2     50000.0
3    350000.0
4     15000.0
Name: 2016, dtype: float64
# 当然可以通过lambda 函数将这个比较简单的函数一行带过
df["2016"].apply(lambda x: x.replace(",","").replace("$","")).astype("float64")
0    125000.0
1    920000.0
2     50000.0
3    350000.0
4     15000.0
Name: 2016, dtype: float64
#同样可以利用lambda表达式将PercentGrowth进行数据清理
df["Percent Growth"].apply(lambda x: x.replace("%","")).astype("float")/100
0    0.30
1    0.10
2    0.25
3    0.04
4   -0.15
Name: Percent Growth, dtype: float64
# 同样可以通过自定义函数进行解决，结果同上
# 最后一个自定义函数是利用np.where() function 将Active 列转化为布尔值。
df["Active"] = np.where(df["Active"] == "Y", True, False)

df["Active"]
0     True
1     True
2     True
3     True
4    False
Name: Active, dtype: bool
# 此时可查看一下数据格式
df["2016"]=df["2016"].apply(lambda x: x.replace(",","").replace("$","")).astype("float64")
df["2017"]=df["2017"].apply(lambda x: x.replace(",","").replace("$","")).astype("float64")
df["Percent Growth"]=df["Percent Growth"].apply(lambda x: x.replace("%","")).astype("float")/100
df.dtypes
Customer Number      int32
Customer Name       object
2016               float64
2017               float64
Percent Growth     float64
Jan Units           object
Month                int64
Day                  int64
Year                 int64
Active                bool
dtype: object
# 再次查看DataFrame
# 此时只有Jan Units中格式需要转化，以及年月日的合并，可以利用pandas中自带的几个函数进行处理
print(df)
   Customer Number     Customer Name      2016       2017  Percent Growth  \
0            10002  Quest Industries  125000.0   162500.0            0.30   
1           552278    Smith Plumbing  920000.0  1012000.0            0.10   
2            23477   ACME Industrial   50000.0    62500.0            0.25   
3            24900        Brekke LTD  350000.0   490000.0            0.04   
4           651029         Harbor Co   15000.0    12750.0           -0.15   

  Jan Units  Month  Day  Year Active  
0       500      1   10  2015   True  
1       700      6   15  2014   True  
2       125      3   29  2016   True  
3        75     10   27  2015   True  
4    Closed      2    2  2014  False  
```

### 利用pandas中函数进行处理

```python
# pandas中pd.to_numeric()处理Jan Units中的数据
pd.to_numeric(df["Jan Units"],errors='coerce').fillna(0)
0    500.0
1    700.0
2    125.0
3     75.0
4      0.0
Name: Jan Units, dtype: float64
# 最后利用pd.to_datatime()将年月日进行合并
pd.to_datetime(df[['Month', 'Day', 'Year']])
0   2015-01-10
1   2014-06-15
2   2016-03-29
3   2015-10-27
4   2014-02-02
dtype: datetime64[ns]
# 做到这里不要忘记重新赋值，否则原始数据并没有变化
df["Jan Units"] = pd.to_numeric(df["Jan Units"],errors='coerce')
df["Start_date"] = pd.to_datetime(df[['Month', 'Day', 'Year']])
df
```

|      | Customer Number | Customer Name    | 2016     | 2017      | Percent Growth | Jan Units | Month | Day  | Year | Active | Start_date |
| ---- | --------------- | ---------------- | -------- | --------- | -------------- | --------- | ----- | ---- | ---- | ------ | ---------- |
| 0    | 10002           | Quest Industries | 125000.0 | 162500.0  | 0.30           | 500.0     | 1     | 10   | 2015 | True   | 2015-01-10 |
| 1    | 552278          | Smith Plumbing   | 920000.0 | 1012000.0 | 0.10           | 700.0     | 6     | 15   | 2014 | True   | 2014-06-15 |
| 2    | 23477           | ACME Industrial  | 50000.0  | 62500.0   | 0.25           | 125.0     | 3     | 29   | 2016 | True   | 2016-03-29 |
| 3    | 24900           | Brekke LTD       | 350000.0 | 490000.0  | 0.04           | 75.0      | 10    | 27   | 2015 | True   | 2015-10-27 |
| 4    | 651029          | Harbor Co        | 15000.0  | 12750.0   | -0.15          | NaN       | 2     | 2    | 2014 | False  | 2014-02-02 |

```python
df.dtypes
Customer Number             int32
Customer Name              object
2016                      float64
2017                      float64
Percent Growth            float64
Jan Units                 float64
Month                       int64
Day                         int64
Year                        int64
Active                       bool
Start_date         datetime64[ns]
dtype: object
# 将这些转化整合在一起
def convert_percent(val):
    """
    Convert the percentage string to an actual floating point percent
    - Remove %
    - Divide by 100 to make decimal
    """
    new_val = val.replace('%', '')
    return float(new_val) / 100

df_2 = pd.read_csv("sales_data_types.csv",dtype={"Customer_Number":"int"},converters={
    "2016":convert_currency,
    "2017":convert_currency,
    "Percent Growth":convert_percent,
    "Jan Units":lambda x:pd.to_numeric(x,errors="coerce"),
    "Active":lambda x: np.where(x=="Y",True,False)
})
df_2.dtypes
Customer Number      int64
Customer Name       object
2016               float64
2017               float64
Percent Growth     float64
Jan Units          float64
Month                int64
Day                  int64
Year                 int64
Active              bool
dtype: object
df_2
```

|      | Customer Number | Customer Name    | 2016     | 2017      | Percent Growth | Jan Units | Month | Day  | Year | Active |
| ---- | --------------- | ---------------- | -------- | --------- | -------------- | --------- | ----- | ---- | ---- | ------ |
| 0    | 10002           | Quest Industries | 125000.0 | 162500.0  | 0.30           | 500.0     | 1     | 10   | 2015 | True   |
| 1    | 552278          | Smith Plumbing   | 920000.0 | 1012000.0 | 0.10           | 700.0     | 6     | 15   | 2014 | True   |
| 2    | 23477           | ACME Industrial  | 50000.0  | 62500.0   | 0.25           | 125.0     | 3     | 29   | 2016 | True   |
| 3    | 24900           | Brekke LTD       | 350000.0 | 490000.0  | 0.04           | 75.0      | 10    | 27   | 2015 | True   |
| 4    | 651029          | Harbor Co        | 15000.0  | 12750.0   | -0.15          | NaN       | 2     | 2    | 2014 | False  |

至此，pandas里面数据类型目前还有timedelta以及category两个,之后会着重介绍category类型，这是类型是参考了R中的category设计的，在pandas 0.16 之后添加的，之后还会根据需要进行整理pandas的常用方法。

分类: [pandas](https://www.cnblogs.com/onemorepoint/category/988857.html), [python](https://www.cnblogs.com/onemorepoint/category/846820.html)

标签: [pandas](https://www.cnblogs.com/onemorepoint/tag/pandas/)