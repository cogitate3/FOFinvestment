# [pandas练习-多层索引的创建和各种操作(multiindex)第一部分](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/)

微博@mlln-cn, 并附上文章url链接, 我就能回答你的问题奥!

2019年01月22日

**文章目录**

1. \1. 创建MultiIndex
   1. [1.1. from_tuples](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
   2. [1.2. from_arrays](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
   3. [1.3. from_product](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
2. [2. MultiIndex.names](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
3. [3. MultiIndex可以作为列名称](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
4. [4. 获取各水平的值](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
5. [5. 选择数据](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
6. [6. 选择行](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)
7. [7. 数据对齐](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/#undefined)



分层/多级索引非常令人兴奋，因为它为一些非常复杂的数据分析和操作提供了可能性，特别是对于处理更高维度的数据。从本质上讲，它使你能在较低维度的数据结构(如Series（1d）和DataFrame（2d）)中存储和操作具有任意数量维度的数据。

在这篇文章中, 你将会学到什么是”MultiIndex”, 以及如何创建和操作MultiIndex。

### 创建MultiIndex

MultiIndex对象是标准Index对象的扩展, 你可以将MultiIndex视为元组构成的列表，其中每个元组都是唯一的, 它与Index的区别是, Index可以视为数字或者字符串构成的列表。可以从数组列表（使用MultiIndex.from_arrays），元组列表（使用MultiIndex.from_tuples）或交叉迭代集（使用MultiIndex.from_product）创建MultiIndex。当构造函数传递元组列表时，它将尝试返回MultiIndex。以下示例演示了创建MultiIndexes的不同方法。

#### from_tuples

下面先创建一个元祖构成的列表:

```
import pandas as pd

arrays = [['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'],
            ['one', 'two', 'one', 'two', 'one', 'two', 'one', 'two']]

tuples = list(zip(*arrays))
tuples
```

输出(plain):
     [('bar', 'one'),    
 ('bar', 'two'),    
 ('baz', 'one'),    
 ('baz', 'two'),    
 ('foo', 'one'),    
 ('foo', 'two'),    
 ('qux', 'one'),    
 ('qux', 'two')]

使用from_tuples来创建MultiIndex:

```
index = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])
index
```

输出(plain):
     MultiIndex(levels=[['bar', 'baz', 'foo', 'qux'], ['one', 'two']],    
           labels=[[0, 0, 1, 1, 2, 2, 3, 3], [0, 1, 0, 1, 0, 1, 0, 1]],    
           names=['first', 'second'])

创建一个series, 并设置它的index:

```
import numpy as np
s = pd.Series(np.random.randn(8), index=index)
s
```

输出(plain):
     first  second    
bar    one       1.457857    
       two       0.999506    
baz    one      -1.556818    
       two       1.716127    
foo    one      -1.562564    
       two       0.313624    
qux    one       0.537644    
       two       1.178401    
dtype: float64

#### from_arrays

如果说from_tuples接受的参数是”行”的列表, 那么 from_arrays接受的参数是就是”列”的列表:

```
arrays = [['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'],
            ['one', 'two', 'one', 'two', 'one', 'two', 'one', 'two']]

index = pd.MultiIndex.from_arrays(arrays)
s = pd.Series(np.random.randn(8), index=index)
s
```

输出(plain):
     bar  one   -1.754944    
     two    1.111560    
baz  one   -1.291416    
     two    1.556595    
foo  one    0.147699    
     two    1.379124    
qux  one   -0.981192    
     two    0.292709    
dtype: float64

不过为了简便, 我们通常可以直接在Series的构造函数中使用:

```
arrays = [['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'],
            ['one', 'two', 'one', 'two', 'one', 'two', 'one', 'two']]

s = pd.Series(np.random.randn(8), index=arrays)
s
```

输出(plain):
     bar  one    0.507618    
     two   -2.190117    
baz  one   -0.138124    
     two   -2.175832    
foo  one   -0.570554    
     two   -0.851560    
qux  one   -0.784552    
     two    0.003748    
dtype: float64

#### from_product

假如我们有两个list, 这两个list内的元素相互交叉, 两两搭配, 这就是两个list的product:

```
lists = [['bar', 'baz', 'foo', 'qux'], ['one', 'two']]

index = pd.MultiIndex.from_product(lists, names=['first', 'second'])
s = pd.Series(np.random.randn(len(index)), index=index)
s
```

输出(plain):
     first  second    
bar    one      -1.209379    
       two       0.497207    
baz    one       0.592290    
       two      -0.769594    
foo    one      -0.935071    
       two       0.201014    
qux    one      -0.176715    
       two      -0.183346    
dtype: float64

### MultiIndex.names

你可以为MultiIndex的各个层起名字, 这就是names属性:

```
# 我们还没有设置名称
s.index.names
```

输出(plain):
     FrozenList([None, None])

```
s.index.names = ['FirstLevel', 'SecondLevel']

s.index
```

输出(plain):
     MultiIndex(levels=[['bar', 'baz', 'foo', 'qux'], ['one', 'two']],    
           labels=[[0, 0, 1, 1, 2, 2, 3, 3], [0, 1, 0, 1, 0, 1, 0, 1]],    
           names=['FirstLevel', 'SecondLevel'])

### MultiIndex可以作为列名称

Series和DataFrame的列名称属性就是columns, 他也可以是一个MultiIndex对象:

```
df = pd.DataFrame(np.random.randn(3, 8), index=['A', 'B', 'C'], columns=index)
df
```

输出(html):

| FirstLevel  | bar       | baz       | foo       | qux       |           |          |           |           |
| :---------- | :-------- | :-------- | :-------- | :-------- | :-------- | :------- | :-------- | :-------- |
| SecondLevel | one       | two       | one       | two       | one       | two      | one       | two       |
| A           | 1.014034  | 1.464162  | -0.753476 | -0.163394 | -0.198990 | 0.116046 | -0.555008 | -0.965797 |
| B           | -1.314244 | -1.263142 | 1.523974  | 0.541391  | -0.217874 | 0.019695 | 1.188791  | -1.003912 |
| C           | -1.175155 | -0.587370 | 0.352587  | -0.047469 | -0.896502 | 0.280792 | 0.806554  | 0.132662  |

### 获取各水平的值

方法get_level_values将返回特定级别的每个位置的标签向量：

```
index.get_level_values(0)
```

输出(plain):
     Index(['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'], dtype='object', name='FirstLevel')

如果你给index设置了名称, 那么你可以直接使用名称来获取水平值:

```
index.get_level_values('FirstLevel')
```

输出(plain):
     Index(['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'], dtype='object', name='FirstLevel')

### 选择数据

这可能是MultiIndex最重要的功能之一。

先看下我们的df的结构:

```
df
```

输出(html):

| FirstLevel  | bar       | baz       | foo       | qux       |           |          |           |           |
| :---------- | :-------- | :-------- | :-------- | :-------- | :-------- | :------- | :-------- | :-------- |
| SecondLevel | one       | two       | one       | two       | one       | two      | one       | two       |
| A           | 1.014034  | 1.464162  | -0.753476 | -0.163394 | -0.198990 | 0.116046 | -0.555008 | -0.965797 |
| B           | -1.314244 | -1.263142 | 1.523974  | 0.541391  | -0.217874 | 0.019695 | 1.188791  | -1.003912 |
| C           | -1.175155 | -0.587370 | 0.352587  | -0.047469 | -0.896502 | 0.280792 | 0.806554  | 0.132662  |

获取FirstLevel是bar的所有数据:

```
df['bar']
```

输出(html):

| SecondLevel | one       | two       |
| :---------- | :-------- | :-------- |
| A           | 1.014034  | 1.464162  |
| B           | -1.314244 | -1.263142 |
| C           | -1.175155 | -0.587370 |

获取FirstLevel是bar, SecondLevel是one的所有数据:

```
df['bar', 'one']
```

输出(plain):
     A    1.014034    
B   -1.314244    
C   -1.175155    
Name: (bar, one), dtype: float64

我更喜欢这样来用, 意义更明确:

```
df['bar']['one']
```

输出(plain):
     A    1.014034    
B   -1.314244    
C   -1.175155    
Name: one, dtype: float64

需要注意的是, 结果选择输出的结果的columns已经改变:

```
df['bar'].columns
```

输出(plain):
     Index(['one', 'two'], dtype='object', name='SecondLevel')

如果你要选择第二层的列名为one的所有数据, 你需要借助xs方法:

```
df.xs('one', level=1, axis=1)
```

输出(html):

| FirstLevel | bar       | baz       | foo       | qux       |
| :--------- | :-------- | :-------- | :-------- | :-------- |
| A          | 1.014034  | -0.753476 | -0.198990 | -0.555008 |
| B          | -1.314244 | 1.523974  | -0.217874 | 1.188791  |
| C          | -1.175155 | 0.352587  | -0.896502 | 0.806554  |

或者使用名称代替数字:

```
df.xs('one', level='SecondLevel', axis='columns')
```

输出(html):

| FirstLevel | bar       | baz       | foo       | qux       |
| :--------- | :-------- | :-------- | :-------- | :-------- |
| A          | 1.014034  | -0.753476 | -0.198990 | -0.555008 |
| B          | -1.314244 | 1.523974  | -0.217874 | 1.188791  |
| C          | -1.175155 | 0.352587  | -0.896502 | 0.806554  |

我喜欢xs的原因是, 它不仅可以用来选择列, 也可以用来选择行:

```
s
```

输出(plain):
     FirstLevel  SecondLevel    
bar         one           -1.754944    
            two            1.111560    
baz         one           -1.291416    
            two            1.556595    
foo         one            0.147699    
            two            1.379124    
qux         one           -0.981192    
            two            0.292709    
dtype: float64

```
s.xs('one', level='SecondLevel', axis='index')
```

输出(plain):
     FirstLevel    
bar   -1.754944    
baz   -1.291416    
foo    0.147699    
qux   -0.981192    
dtype: float64

### 选择行

下面我们把df进行转置, 然后看看一些选择行的操作:

```
df = df.T

df
```

输出(html):

|            |             | A         | B         | C         |
| :--------- | :---------- | :-------- | :-------- | :-------- |
| FirstLevel | SecondLevel |           |           |           |
| bar        | one         | 1.014034  | -1.314244 | -1.175155 |
| two        | 1.464162    | -1.263142 | -0.587370 |           |
| baz        | one         | -0.753476 | 1.523974  | 0.352587  |
| two        | -0.163394   | 0.541391  | -0.047469 |           |
| foo        | one         | -0.198990 | -0.217874 | -0.896502 |
| two        | 0.116046    | 0.019695  | 0.280792  |           |
| qux        | one         | -0.555008 | 1.188791  | 0.806554  |
| two        | -0.965797   | -1.003912 | 0.132662  |           |

选择FirstLevel是bar, SecondLevel是two的数据:

```
df.loc[('bar', 'two')]
```

输出(plain):
     A    1.464162    
B   -1.263142    
C   -0.587370    
Name: (bar, two), dtype: float64

下面的用法是等效的:

```
df.loc['bar'].loc['two']
```

输出(plain):
     A    1.464162    
B   -1.263142    
C   -0.587370    
Name: two, dtype: float64

选择行的同时也能选择列:

```
df.loc[('bar', 'two'), 'A']
```

输出(plain):
     1.4641615518687836

我们还能使用切片操作:

```
df.loc['baz': 'foo']
```

输出(html):

|            |             | A         | B         | C         |
| :--------- | :---------- | :-------- | :-------- | :-------- |
| FirstLevel | SecondLevel |           |           |           |
| baz        | one         | -0.753476 | 1.523974  | 0.352587  |
| two        | -0.163394   | 0.541391  | -0.047469 |           |
| foo        | one         | -0.198990 | -0.217874 | -0.896502 |
| two        | 0.116046    | 0.019695  | 0.280792  |           |

或许, 使用更多的是这样:

```
df.loc[('bar', 'two'): ('baz', 'two')]
```

输出(html):

|            |             | A         | B         | C         |
| :--------- | :---------- | :-------- | :-------- | :-------- |
| FirstLevel | SecondLevel |           |           |           |
| bar        | two         | 1.464162  | -1.263142 | -0.587370 |
| baz        | one         | -0.753476 | 1.523974  | 0.352587  |
| two        | -0.163394   | 0.541391  | -0.047469 |           |

当然, 我还是推荐大家使用xs, 它可以使你的代码更容易被别人理解, 而且选择行和列都用统一的方式:

```
df.xs('two', level='SecondLevel', axis='index')
```

输出(html):

|            | A         | B         | C         |
| :--------- | :-------- | :-------- | :-------- |
| FirstLevel |           |           |           |
| bar        | 1.464162  | -1.263142 | -0.587370 |
| baz        | -0.163394 | 0.541391  | -0.047469 |
| foo        | 0.116046  | 0.019695  | 0.280792  |
| qux        | -0.965797 | -1.003912 | 0.132662  |

### 数据对齐

如果你需要对数据进行运算, 那么设置好了index可以给你带来很多便利:

```
s
```

输出(plain):
     FirstLevel  SecondLevel    
bar         one           -1.754944    
            two            1.111560    
baz         one           -1.291416    
            two            1.556595    
foo         one            0.147699    
            two            1.379124    
qux         one           -0.981192    
            two            0.292709    
dtype: float64

假设我们只需要对第二个元素之后的数据进行运算, 我们的pandas为我们做了按照index的自动数据对齐:

```
s + s[2:]
```

输出(plain):
     FirstLevel  SecondLevel    
bar         one                 NaN    
            two                 NaN    
baz         one           -2.582832    
            two            3.113191    
foo         one            0.295398    
            two            2.758247    
qux         one           -1.962383    
            two            0.585417    
dtype: float64

或许下面这个看起来更有用:

```
s + s[::2]
```

输出(plain):
     FirstLevel  SecondLevel    
bar         one           -3.509889    
            two                 NaN    
baz         one           -2.582832    
            two                 NaN    
foo         one            0.295398    
            two                 NaN    
qux         one           -1.962383    
            two                 NaN    
dtype: float64

> **注意**
> 本文由jupyter notebook转换而来, 您可以在这里下载[notebook](https://mlln.cn/2019/01/22/pandas练习-多层索引的创建和各种操作(multiindex)第一部分/pandas练习-多层索引的创建和各种操作(multiindex)第一部分.ipynb)
> 有问题可以直接在下方留言
> 或者给我发邮件675495787[at]qq.com
> 请记住我的网址: mlln.cn 或者 jupyter.cn

 [#PANDAS](https://mlln.cn/tags/pandas/)

# [pandas练习-多层索引的创建和各种操作(multiindex)第二部分](https://mlln.cn/2019/01/24/pandas练习-多层索引的创建和各种操作(multiindex)第二部分/)

微博@mlln-cn, 并附上文章url链接, 我就能回答你的问题奥!

2019年01月24日

**文章目录**

1. [1. 使用切片(slicers)](https://mlln.cn/2019/01/24/pandas练习-多层索引的创建和各种操作(multiindex)第二部分/#undefined)
2. [2. 按索引聚合数据和数据对齐](https://mlln.cn/2019/01/24/pandas练习-多层索引的创建和各种操作(multiindex)第二部分/#undefined)
3. [3. 交换多层索引的层序](https://mlln.cn/2019/01/24/pandas练习-多层索引的创建和各种操作(multiindex)第二部分/#undefined)
4. [4. 排序](https://mlln.cn/2019/01/24/pandas练习-多层索引的创建和各种操作(multiindex)第二部分/#undefined)



### 使用切片(slicers)

你可以使用切片来选择MultiIndex, `slice`是python内置的函数(其实是一个类), 他的用法是这样的:

```
alist = list('abcdefg' * 3)
selector = slice(1, 6, 2)
alist[selector]
```

输出(plain):
     ['b', 'd', 'f']

我们可以使用`slice`来选择MultiIndex。

下面先创建一个DataFrame:

```
import pandas as pd
import numpy as np
def mklbl(prefix,n):
    return ["%s%s" % (prefix,i)  for i in range(n)]


miindex = pd.MultiIndex.from_product([mklbl('A',4),
                                     mklbl('B',2),
                                mklbl('C',4),
                                   mklbl('D',2)])


micolumns = pd.MultiIndex.from_tuples([('a','foo'),('a','bar'),
                                   ('b','foo'),('b','bah')],
                                 names=['lvl0', 'lvl1'])


dfmi = pd.DataFrame(np.arange(len(miindex)*len(micolumns)).reshape((len(miindex),len(micolumns))),
                  index=miindex,
                columns=micolumns).sort_index().sort_index(axis=1)

dfmi.head()
```

输出(html):

|      |      |      | lvl0 | a    | b    |      |      |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|      |      |      | lvl1 | bar  | foo  | bah  | foo  |
| A0   | B0   | C0   | D0   | 1    | 0    | 3    | 2    |
| D1   | 5    | 4    | 7    | 6    |      |      |      |
| C1   | D0   | 9    | 8    | 11   | 10   |      |      |
| D1   | 13   | 12   | 15   | 14   |      |      |      |
| C2   | D0   | 17   | 16   | 19   | 18   |      |      |

下面我们需要选择出MultiIndex第一层为A1或A2或A3, 第二层不做选择, 第三层只包括C1和C3的行:

```
dfmi.loc[(slice('A1', 'A3'), slice(None), ['C1', 'C3']), :]
```

输出(html):

|      |      |      | lvl0 | a    | b    |      |      |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|      |      |      | lvl1 | bar  | foo  | bah  | foo  |
| A1   | B0   | C1   | D0   | 73   | 72   | 75   | 74   |
| D1   | 77   | 76   | 79   | 78   |      |      |      |
| C3   | D0   | 89   | 88   | 91   | 90   |      |      |
| D1   | 93   | 92   | 95   | 94   |      |      |      |
| B1   | C1   | D0   | 105  | 104  | 107  | 106  |      |
| D1   | 109  | 108  | 111  | 110  |      |      |      |
| C3   | D0   | 121  | 120  | 123  | 122  |      |      |
| D1   | 125  | 124  | 127  | 126  |      |      |      |
| A2   | B0   | C1   | D0   | 137  | 136  | 139  | 138  |
| D1   | 141  | 140  | 143  | 142  |      |      |      |
| C3   | D0   | 153  | 152  | 155  | 154  |      |      |
| D1   | 157  | 156  | 159  | 158  |      |      |      |
| B1   | C1   | D0   | 169  | 168  | 171  | 170  |      |
| D1   | 173  | 172  | 175  | 174  |      |      |      |
| C3   | D0   | 185  | 184  | 187  | 186  |      |      |
| D1   | 189  | 188  | 191  | 190  |      |      |      |
| A3   | B0   | C1   | D0   | 201  | 200  | 203  | 202  |
| D1   | 205  | 204  | 207  | 206  |      |      |      |
| C3   | D0   | 217  | 216  | 219  | 218  |      |      |
| D1   | 221  | 220  | 223  | 222  |      |      |      |
| B1   | C1   | D0   | 233  | 232  | 235  | 234  |      |
| D1   | 237  | 236  | 239  | 238  |      |      |      |
| C3   | D0   | 249  | 248  | 251  | 250  |      |      |
| D1   | 253  | 252  | 255  | 254  |      |      |      |

你还可以使用`pandas.IndexSlic`类来实现类似的选择:

```
idx = pd.IndexSlice

dfmi.loc[idx['A1': 'A3', :, ['C1', 'C3']], :]
```

输出(html):

|      |      |      | lvl0 | a    | b    |      |      |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|      |      |      | lvl1 | bar  | foo  | bah  | foo  |
| A1   | B0   | C1   | D0   | 73   | 72   | 75   | 74   |
| D1   | 77   | 76   | 79   | 78   |      |      |      |
| C3   | D0   | 89   | 88   | 91   | 90   |      |      |
| D1   | 93   | 92   | 95   | 94   |      |      |      |
| B1   | C1   | D0   | 105  | 104  | 107  | 106  |      |
| D1   | 109  | 108  | 111  | 110  |      |      |      |
| C3   | D0   | 121  | 120  | 123  | 122  |      |      |
| D1   | 125  | 124  | 127  | 126  |      |      |      |
| A2   | B0   | C1   | D0   | 137  | 136  | 139  | 138  |
| D1   | 141  | 140  | 143  | 142  |      |      |      |
| C3   | D0   | 153  | 152  | 155  | 154  |      |      |
| D1   | 157  | 156  | 159  | 158  |      |      |      |
| B1   | C1   | D0   | 169  | 168  | 171  | 170  |      |
| D1   | 173  | 172  | 175  | 174  |      |      |      |
| C3   | D0   | 185  | 184  | 187  | 186  |      |      |
| D1   | 189  | 188  | 191  | 190  |      |      |      |
| A3   | B0   | C1   | D0   | 201  | 200  | 203  | 202  |
| D1   | 205  | 204  | 207  | 206  |      |      |      |
| C3   | D0   | 217  | 216  | 219  | 218  |      |      |
| D1   | 221  | 220  | 223  | 222  |      |      |      |
| B1   | C1   | D0   | 233  | 232  | 235  | 234  |      |
| D1   | 237  | 236  | 239  | 238  |      |      |      |
| C3   | D0   | 249  | 248  | 251  | 250  |      |      |
| D1   | 253  | 252  | 255  | 254  |      |      |      |

同样是上面的例子, 我们可以选择出列索引第二层为bar的列:

```
dfmi.loc[idx['A1': 'A3', :, ['C1', 'C3']], idx[:, 'foo']]
```

输出(html):

|      |      |      | lvl0 | a    | b    |
| :--- | :--- | :--- | :--- | :--- | :--- |
|      |      |      | lvl1 | foo  | foo  |
| A1   | B0   | C1   | D0   | 72   | 74   |
| D1   | 76   | 78   |      |      |      |
| C3   | D0   | 88   | 90   |      |      |
| D1   | 92   | 94   |      |      |      |
| B1   | C1   | D0   | 104  | 106  |      |
| D1   | 108  | 110  |      |      |      |
| C3   | D0   | 120  | 122  |      |      |
| D1   | 124  | 126  |      |      |      |
| A2   | B0   | C1   | D0   | 136  | 138  |
| D1   | 140  | 142  |      |      |      |
| C3   | D0   | 152  | 154  |      |      |
| D1   | 156  | 158  |      |      |      |
| B1   | C1   | D0   | 168  | 170  |      |
| D1   | 172  | 174  |      |      |      |
| C3   | D0   | 184  | 186  |      |      |
| D1   | 188  | 190  |      |      |      |
| A3   | B0   | C1   | D0   | 200  | 202  |
| D1   | 204  | 206  |      |      |      |
| C3   | D0   | 216  | 218  |      |      |
| D1   | 220  | 222  |      |      |      |
| B1   | C1   | D0   | 232  | 234  |      |
| D1   | 236  | 238  |      |      |      |
| C3   | D0   | 248  | 250  |      |      |
| D1   | 252  | 254  |      |      |      |

另外, 我们可以使用布尔的蒙版来配合`IndexSlice`选择数据, 下面我们选择出foo列的数值小于100的行:

```
mask = (dfmi[('a', 'foo')] < 100) & (dfmi[('b', 'foo')] < 100)

dfmi.loc[idx[mask, :, ['C1', 'C2']], idx[:, 'foo']]
```

输出(html):

|      |      |      | lvl0 | a    | b    |
| :--- | :--- | :--- | :--- | :--- | :--- |
|      |      |      | lvl1 | foo  | foo  |
| A0   | B0   | C1   | D0   | 8    | 10   |
| D1   | 12   | 14   |      |      |      |
| C2   | D0   | 16   | 18   |      |      |
| D1   | 20   | 22   |      |      |      |
| B1   | C1   | D0   | 40   | 42   |      |
| D1   | 44   | 46   |      |      |      |
| C2   | D0   | 48   | 50   |      |      |
| D1   | 52   | 54   |      |      |      |
| A1   | B0   | C1   | D0   | 72   | 74   |
| D1   | 76   | 78   |      |      |      |
| C2   | D0   | 80   | 82   |      |      |
| D1   | 84   | 86   |      |      |      |

### 按索引聚合数据和数据对齐

在多层索引中, 我们可以依据某一层进行数据聚合, 比如求和, 求均值, 下面我们先来创建一个dataframe:

```
midx = pd.MultiIndex(levels=[['zero', 'one'], ['x','y']],
                      labels=[[1,1,0,0],[1,0,1,0]])


df = pd.DataFrame(np.random.randn(4,2), index=midx)

df
```

输出(html):

|      |           | 0         | 1         |
| :--- | :-------- | :-------- | :-------- |
| one  | y         | -0.634407 | 0.272985  |
| x    | -0.546991 | 0.001771  |           |
| zero | y         | 1.801089  | -1.132311 |
| x    | 0.213100  | 2.339203  |           |

求第一层索引的均值:

```
df2 = df.mean(level=0)
df2
```

输出(html):

|      | 0         | 1        |
| :--- | :-------- | :------- |
| one  | -0.590699 | 0.137378 |
| zero | 1.007094  | 0.603446 |

如果我们想用均值替换原先的所有值, 我们可以恢复到原始数据的形状和索引:

```
df3 = df2.reindex(df.index, level=0)
df3
```

输出(html):

|      |           | 0         | 1        |
| :--- | :-------- | :-------- | :------- |
| one  | y         | -0.590699 | 0.137378 |
| x    | -0.590699 | 0.137378  |          |
| zero | y         | 1.007094  | 0.603446 |
| x    | 1.007094  | 0.603446  |          |

上面就是一个数据对齐的过程, df2的索引和df的索引按照第一层对齐, 也就是[one, zero]对齐, 假如不对齐, 我们会得到什么结果?

```
df4 = df2.reindex(df.index)
df4
```

输出(html):

|      |      | 0    | 1    |
| :--- | :--- | :--- | :--- |
| one  | y    | NaN  | NaN  |
| x    | NaN  | NaN  |      |
| zero | y    | NaN  | NaN  |
| x    | NaN  | NaN  |      |

我们可以使用更直观的方式去对齐数据:

```
df_a, df2_a = df.align(df2, level=0)
df2_a
```

输出(html):

|      |           | 0         | 1        |
| :--- | :-------- | :-------- | :------- |
| one  | y         | -0.590699 | 0.137378 |
| x    | -0.590699 | 0.137378  |          |
| zero | y         | 1.007094  | 0.603446 |
| x    | 1.007094  | 0.603446  |          |

需要注意的是, 上面的方法可能会更改df和df2, 所以有两个返回值。

### 交换多层索引的层序

直接看例子就好了, 对比交换前后的index:

```
df
```

输出(html):

|      |           | 0         | 1         |
| :--- | :-------- | :-------- | :-------- |
| one  | y         | -0.634407 | 0.272985  |
| x    | -0.546991 | 0.001771  |           |
| zero | y         | 1.801089  | -1.132311 |
| x    | 0.213100  | 2.339203  |           |

```
df.swaplevel(0, 1, axis=0)
```

输出(html):

|      |      | 0         | 1         |
| :--- | :--- | :-------- | :-------- |
| y    | one  | -0.634407 | 0.272985  |
| x    | one  | -0.546991 | 0.001771  |
| y    | zero | 1.801089  | -1.132311 |
| x    | zero | 0.213100  | 2.339203  |

另外, 可以使用reorder_levels达到相同的目的, 只不过它可以一次性修改多层index的次序:

```
df.reorder_levels([1, 0], axis=0)
```

输出(html):

|      |      | 0         | 1         |
| :--- | :--- | :-------- | :-------- |
| y    | one  | -0.634407 | 0.272985  |
| x    | one  | -0.546991 | 0.001771  |
| y    | zero | 1.801089  | -1.132311 |
| x    | zero | 0.213100  | 2.339203  |

### 排序

我们可以使用sort_index对索引进行排序。

```
import random; 

arrays = [['bar', 'bar', 'baz', 'baz', 'foo', 'foo', 'qux', 'qux'],
          ['one', 'two', 'one', 'two', 'one', 'two', 'one', 'two']]
 

tuples = list(zip(*arrays))
random.shuffle(tuples)
index = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])
s = pd.Series(np.random.randn(8), index=pd.MultiIndex.from_tuples(tuples))
s
```

输出(plain):
     baz  one    0.035299    
foo  one   -1.021257    
baz  two   -0.225705    
foo  two   -0.369259    
bar  one   -0.681788    
     two    0.873609    
qux  two    0.325956    
     one   -1.330222    
dtype: float64

默认情况下, sort_index可以逐层排序, 首先排level=0的层:

```
s.sort_index()
```

输出(plain):
     bar  one   -0.681788    
     two    0.873609    
baz  one    0.035299    
     two   -0.225705    
foo  one   -1.021257    
     two   -0.369259    
qux  one   -1.330222    
     two    0.325956    
dtype: float64

但是我们可以选择只对某一层排序:

```
s.sort_index(level=1)
```

输出(plain):
     bar  one   -0.681788    
baz  one    0.035299    
foo  one   -1.021257    
qux  one   -1.330222    
bar  two    0.873609    
baz  two   -0.225705    
foo  two   -0.369259    
qux  two    0.325956    
dtype: float64

如果多层索引设置了names属性, 我们可以使用名称作为参数:

```
s.index.names=['a', 'b']
s.sort_index(level='b')
```

输出(plain):
     a    b      
bar  one   -0.681788    
baz  one    0.035299    
foo  one   -1.021257    
qux  one   -1.330222    
bar  two    0.873609    
baz  two   -0.225705    
foo  two   -0.369259    
qux  two    0.325956    
dtype: float64

除了对索引进行排序, 我们还可以对DataFrame.columns排序, 先来看一下我们的数据:

```
dft = df.T
dft
```

输出(html):

|      | one       | zero      |           |          |
| :--- | :-------- | :-------- | :-------- | :------- |
|      | y         | x         | y         | x        |
| 0    | -0.634407 | -0.546991 | 1.801089  | 0.213100 |
| 1    | 0.272985  | 0.001771  | -1.132311 | 2.339203 |

```
dft.sort_index(level=1, axis=1)
```

输出(html):

|      | one       | zero     | one       | zero      |
| :--- | :-------- | :------- | :-------- | :-------- |
|      | x         | x        | y         | y         |
| 0    | -0.546991 | 0.213100 | -0.634407 | 1.801089  |
| 1    | 0.001771  | 2.339203 | 0.272985  | -1.132311 |

index排序后有一个好处, 就是你可以使用切片来选择数据, 但是如果index没有排序, 你可能会遇到错误:

```
s.loc[('baz', 'one' ): ('bar', 'one')]
---------------------------------------------------------------------------

UnsortedIndexError                        Traceback (most recent call last)

<ipython-input-62-4b4f60d21813> in <module>
----> 1 s.loc[('baz', 'one' ): ('bar', 'one')]


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexing.py in __getitem__(self, key)
   1476 
   1477             maybe_callable = com._apply_if_callable(key, self.obj)
-> 1478             return self._getitem_axis(maybe_callable, axis=axis)
   1479 
   1480     def _is_scalar_access(self, key):


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexing.py in _getitem_axis(self, key, axis)
   1864         if isinstance(key, slice):
   1865             self._validate_key(key, axis)
-> 1866             return self._get_slice_axis(key, axis=axis)
   1867         elif com.is_bool_indexer(key):
   1868             return self._getbool_axis(key, axis=axis)


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexing.py in _get_slice_axis(self, slice_obj, axis)
   1509         labels = obj._get_axis(axis)
   1510         indexer = labels.slice_indexer(slice_obj.start, slice_obj.stop,
-> 1511                                        slice_obj.step, kind=self.name)
   1512 
   1513         if isinstance(indexer, slice):


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexes\base.py in slice_indexer(self, start, end, step, kind)
   4105         """
   4106         start_slice, end_slice = self.slice_locs(start, end, step=step,
-> 4107                                                  kind=kind)
   4108 
   4109         # return a slice


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexes\multi.py in slice_locs(self, start, end, step, kind)
   2144         # This function adds nothing to its parent implementation (the magic
   2145         # happens in get_slice_bound method), but it adds meaningful doc.
-> 2146         return super(MultiIndex, self).slice_locs(start, end, step, kind=kind)
   2147 
   2148     def _partial_tup_index(self, tup, side='left'):


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexes\base.py in slice_locs(self, start, end, step, kind)
   4306         start_slice = None
   4307         if start is not None:
-> 4308             start_slice = self.get_slice_bound(start, 'left', kind)
   4309         if start_slice is None:
   4310             start_slice = 0


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexes\multi.py in get_slice_bound(self, label, side, kind)
   2088         if not isinstance(label, tuple):
   2089             label = label,
-> 2090         return self._partial_tup_index(label, side=side)
   2091 
   2092     def slice_locs(self, start=None, end=None, step=None, kind=None):


d:\mysites\deeplearning.ai-master\.env\lib\site-packages\pandas\core\indexes\multi.py in _partial_tup_index(self, tup, side)
   2151                 'Key length (%d) was greater than MultiIndex'
   2152                 ' lexsort depth (%d)' %
-> 2153                 (len(tup), self.lexsort_depth))
   2154 
   2155         n = len(tup)


UnsortedIndexError: 'Key length (2) was greater than MultiIndex lexsort depth (0)'
```

我们可以使用is_lexsorted来判断是否经过了排序:

```
s.index.is_lexsorted()
```

输出(plain):
     False

```
ss = s.sort_index()
ss.loc[('bar', 'one' ): ('baz', 'one')]
```

输出(plain):
     a    b      
bar  one   -0.681788    
     two    0.873609    
baz  one    0.035299    
dtype: float64

> **注意**
> 本文由jupyter notebook转换而来, 您可以在这里下载[notebook](https://mlln.cn/2019/01/24/pandas练习-多层索引的创建和各种操作(multiindex)第二部分/pandas练习-多层索引的创建和各种操作(multiindex)第二部分.ipynb)
> 有问题可以直接在下方留言
> 或者给我发邮件675495787[at]qq.com
> 请记住我的网址: mlln.cn 或者 jupyter.cn

 [#PANDAS](https://mlln.cn/tags/pandas/)