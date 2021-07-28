# python数据清洗入门教程（完整版）

![img](https://csdnimg.cn/release/blogv2/dist/pc/img/original.png)

[幸福的小猴子qiqi](https://blog.csdn.net/liumengqi11) 2021-01-27 09:59:58 ![img](https://csdnimg.cn/release/blogv2/dist/pc/img/articleReadEyes.png) 119 ![img](https://csdnimg.cn/release/blogv2/dist/pc/img/tobarCollect.png) 收藏 8

分类专栏： [python](https://blog.csdn.net/liumengqi11/category_10730927.html) [数据清洗](https://blog.csdn.net/liumengqi11/category_10774124.html) 文章标签： [python](https://www.csdn.net/tags/MtjaQg4sNDk0LWJsb2cO0O0O.html) [数据分析](https://www.csdn.net/tags/MtTaEg0sNDc1NTAtYmxvZwO0O0OO0O0O.html)

版权

> 数据清洗是整个数据分析过程的第一步，也是整个数据分析项目中最耗费时间的一步。数据清洗的过程决定了数据分析的准确性。随着大数据的越来越普及，数据清洗是必备的技能之一，本教程将较为完整地介绍利用python进行数据清洗的整个过程。即适合零基础的小白也可作为数据清洗大佬的复习指南。文章较长，干货较多，建议大家先收藏后观看，希望对大家有所帮助。

为了方便阅读和复习，本教程中的代码均采用图片形式，源代码和所需要的数据在下面的链接里
链接：https://pan.baidu.com/s/1-3PMsSs5XKjhszVXQIABpw
提取码：23uk



### 课程大纲

- [1.数据清洗之常用工具](https://blog.csdn.net/liumengqi11/article/details/113174269#1_16)
- - [1.1 Numpy](https://blog.csdn.net/liumengqi11/article/details/113174269#11_Numpy_30)
  - - [Numpy常用数据结构](https://blog.csdn.net/liumengqi11/article/details/113174269#Numpy_31)
    - [Numpy常用方法](https://blog.csdn.net/liumengqi11/article/details/113174269#Numpy_43)
    - [数组访问方法](https://blog.csdn.net/liumengqi11/article/details/113174269#_54)
    - [Numpy常用数据清洗函数](https://blog.csdn.net/liumengqi11/article/details/113174269#Numpy_59)
  - [1.2 Pandas](https://blog.csdn.net/liumengqi11/article/details/113174269#12_Pandas_73)
  - - [Pandas常用数据结构series和方法](https://blog.csdn.net/liumengqi11/article/details/113174269#Pandasseries_75)
    - [Pandas常用数据结构dataframe和方法](https://blog.csdn.net/liumengqi11/article/details/113174269#Pandasdataframe_87)
    - [series和dataframe常用方法](https://blog.csdn.net/liumengqi11/article/details/113174269#seriesdataframe_99)
- [2.数据清洗之文件操作](https://blog.csdn.net/liumengqi11/article/details/113174269#2_129)
- - [2.1 csv文件读写](https://blog.csdn.net/liumengqi11/article/details/113174269#21_csv_136)
  - [2.2 excel文件读写](https://blog.csdn.net/liumengqi11/article/details/113174269#22_excel_147)
  - [2.3 数据库文件读写](https://blog.csdn.net/liumengqi11/article/details/113174269#23__156)
- [3. 数据清洗之数据表处理](https://blog.csdn.net/liumengqi11/article/details/113174269#3__198)
- - [3.1 数据常用筛选方法](https://blog.csdn.net/liumengqi11/article/details/113174269#31__200)
  - [3.2 数据增加和删除](https://blog.csdn.net/liumengqi11/article/details/113174269#32__213)
  - [3.3 数据修改和查找](https://blog.csdn.net/liumengqi11/article/details/113174269#33__225)
  - [3.4 数据整理](https://blog.csdn.net/liumengqi11/article/details/113174269#34__239)
  - [3.5层次化索引](https://blog.csdn.net/liumengqi11/article/details/113174269#35_258)
- [4. 数据清洗之数据转换](https://blog.csdn.net/liumengqi11/article/details/113174269#4__272)
- - [4.1 日期格式数据处理](https://blog.csdn.net/liumengqi11/article/details/113174269#41__274)
  - [4.2 字符串数据处理](https://blog.csdn.net/liumengqi11/article/details/113174269#42__288)
  - [4.3 高阶函数数据处理](https://blog.csdn.net/liumengqi11/article/details/113174269#43__301)
- [5. 数据清洗之数据统计](https://blog.csdn.net/liumengqi11/article/details/113174269#5__320)
- - [5.1 数据分组运算](https://blog.csdn.net/liumengqi11/article/details/113174269#51__322)
  - [5.2 聚合函数使用](https://blog.csdn.net/liumengqi11/article/details/113174269#52__334)
  - [5.3 分组对象与apply函数](https://blog.csdn.net/liumengqi11/article/details/113174269#53_apply_345)
  - [5.4 透视图与交叉表](https://blog.csdn.net/liumengqi11/article/details/113174269#54__355)
- [6. 数据清洗之数据预处理](https://blog.csdn.net/liumengqi11/article/details/113174269#6__391)
- - [6.1 重复值处理](https://blog.csdn.net/liumengqi11/article/details/113174269#61__393)
  - [6.2 缺失值处理](https://blog.csdn.net/liumengqi11/article/details/113174269#62__404)
  - [6.3 异常值处理](https://blog.csdn.net/liumengqi11/article/details/113174269#63__413)
  - [6.4 数据离散化处理](https://blog.csdn.net/liumengqi11/article/details/113174269#64__434)
- [7. 总结与梳理](https://blog.csdn.net/liumengqi11/article/details/113174269#7__466)
- - [7.1 数据清洗步骤](https://blog.csdn.net/liumengqi11/article/details/113174269#71__468)
  - [7.2 函数大全](https://blog.csdn.net/liumengqi11/article/details/113174269#72__478)
  - [7.3 数据清洗之总结](https://blog.csdn.net/liumengqi11/article/details/113174269#73__488)



# 1.数据清洗之常用工具

**数据清洗意义**

1. 现实生活中，数据并非完美的, 需要进行清洗才能进行后面的数据分析
2. 数据清洗是整个数据分析项目最消耗时间的一步
3. 数据的质量最终决定了数据分析的准确性
4. 数据清洗是唯一可以提高数据质量的方法,使得数据分析的结果也变得更加可靠

**数据清洗常用工具**

1. 目前在Python中, numpy和pandas是最主流的工具
2. Numpy中的向量化运算使得数据处理变得高效
3. Pandas提供了大量数据清洗的高效方法
4. 在Python中，尽可能多的使用numpy和pandas中的函数，提高数据清洗的效率

## 1.1 Numpy

### Numpy常用数据结构

1. Numpy中常用的数据结构是ndarray格式
2. 使用array函数创建，语法格式为array(列表或元组)
3. 可以使用其他函数例如arange、linspace、zeros等创建

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126105223493.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

### Numpy常用方法

1. ndim： 返回int,表示ndarray的维度
2. shape：返回尺寸，几行几列
3. size：返回数组元素的个数
4. dtype：返回数组中元素的类型
5. 运算：直接可以在每个元素加减乘除

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126105753226.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

### 数组访问方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126110736990.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

### Numpy常用数据清洗函数

1. 排序函数
   • sort函数: 从小到大进行排序
   • argsort函数: 返回的是数据中从小到大的索引值
2. 数据的搜索
   • np.where: 可以自定义返回满足条件的情况
   • np.extract: 返回满足条件的元素值

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021012613225147.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 1.2 Pandas

### Pandas常用数据结构series和方法

1. 通过pandas.Series来创建Series数据结构。
2. pandas.Series(data,index,dtype,name)。
3. 上述参数中，data可以为列表，array或者dict。
4. 上述参数中， index表示索引，必须与数据同长度，name代表对象的名称

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126114743885.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

### Pandas常用数据结构dataframe和方法

1. 通过pandas.DataFrame来创建DataFrame数据结构。
2. pandas. DataFrame(data,index,dtype,columns)。
3. 上述参数中，data可以为列表，array或者dict。
4. 上述参数中， index表示行索引， columns代表列名或者列标签

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126114845811.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

### series和dataframe常用方法

1. values 返回对象所有元素的值
2. index 返回行索引
3. dtypes 返回索引
4. shape 返回对象数据形状
5. ndim 返回对象的维度
6. size 返回对象的个数
7. columns 返回列标签(只针对dataframe数据结构)

# 2.数据清洗之文件操作

1. Pandas读写CSV文件和相关参数解释
2. Pandas读写excel文件和相关参数解释
3. Pandas与mysql的交互

## 2.1 csv文件读写

1. pandas内置了10多种数据源读取函数,常见的就是CSV和EXCEL
2. 使用read_csv方法读取，结果为dataframe格式
3. 在读取csv文件时，文件名称尽量是英文
4. 参数较多，可以自行控制，但很多时候用默认参数
5. 读取csv时，注意编码，常用编码为utf-8、gbk 、gbk2312和gb18030等
6. 使用to_csv方法快速保存

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126121703454.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 2.2 excel文件读写

1. 使用read_excel读取,读取后的结果为dataframe格式
2. 读取excel文件和csv文件参数大致一样, 但要考虑工作sheet页
3. 参数较多，可以自行控制，但很多时候用默认参数
4. 读取excel时，注意编码，常用编码为utf-8、gbk 、gbk2312和gb18030等
5. 使用to_excel快速保存为xlsx格式

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126122216463.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 2.3 数据库文件读写

1. 使用sqlalchemy建立连接
2. 需要知道数据库的相关参数，如数据库IP地址、用户名和密码等
3. 通过pandas中read_sql 函数读入, 读取完以后是dataframe格式
4. 通过dataframe的to_sql方法保存

**数据库建立连接参数**
conn =create_engine(‘mysql+pymysql://user:passward@IP:3306/test01’)
• root: 用户名
• passward: 密码
• IP : 服务器IP，本地电脑用localhost
• 3306： 端口号
• test01 : 数据库名称

df.to_sql(name, con=engine, if_exists=‘replace/append/fail’,index=False)
• name是表名
• con是连接
• if_exists：表如果存在怎么处理。三个选项 append代表追加, replace代表删除原表，建立新表，fail代表什么都不干
• index=False：不插入索引index

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126123839466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

# 3. 数据清洗之数据表处理

## 3.1 数据常用筛选方法

1. 在数据中,选择需要的行或者列
2. 基础索引方式,就是直接引用
3. ioc[行索引名称或者条件,列索引名称或者标签]
4. iloc[行索引位置,列索引位置]
5. 注意, 区分loc和iloc

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126133602221.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126133818224.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 3.2 数据增加和删除

1. 在数据中,直接添加列
2. 使用df.insert方法在数据中添加一列
3. 掌握drop(labels,axis,inplace=True) 的用法
4. labels表示删除的数据, axis表示作用轴，inplace=True表示是否对原数据生效
5. axis=0按行操作, axis=1按列操作
6. 使用del函数直接删除其中一列

**参数解释**
![在这里插入图片描述](https://img-blog.csdnimg.cn/202101261339257.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/2021012613544026.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 3.3 数据修改和查找

1. 在数据中, 可以使用rename修改列名称或者行索引名称
2. 使用loc方法修改数据
3. 使用loc方法查找符合条件的数据
4. 条件与条件之间用&或者|连接，分别代表‘且’和‘或’
5. 使用between和isin选择满足条件的行

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126142034805.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126142120476.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 3.4 数据整理

**定义**：在数据清洗过程中,很多时候需要将不用的数据整理在一起，方便后续的分析，这个过程也叫数据合并

**合并方法**：常见的合并方法有堆叠和按主键进行合并，堆叠又分为横向堆叠和纵向堆叠，按主键合并类似于sql里面的关联操作

1. 横向堆叠将两张表或多张表在X轴方向，即横向拼接在一起
2. 纵向堆叠将两张表或多张表在Y轴方向，即纵向拼接在一起
3. 注意使用concat时,axis =1用于横向，0代表纵向
4. 注意join取inner或者outer时，分别代表交集和并集

**关联操作**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126142548430.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)**纵向合并**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126142630265.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126143449689.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 3.5层次化索引

**定义**：在一个轴上拥有两个或者两个以上的索引
• 使用loc语句进行访问
• loc里面接受tuple,如loc[(a,b),:]

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126142755539.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126144048629.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

# 4. 数据清洗之数据转换

## 4.1 日期格式数据处理

1. Pandas中使用to_datetime()方法将文本格式转换为日期格式
2. dataframe数据类型如果为datetime64,可以使用dt方法取出年月日等
3. 对于时间差数据,可以使用timedelta函数将其转换为指定时间单位的数值
4. 时间差数据,可以使用dt方法访问其常用属性

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126151053929.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 4.2 字符串数据处理

1. Pandas中提供了字符串的函数,但只能对字符型变量进行使用
2. 通过str方法访问相关属性
3. 可以使用字符串的相关方法进行数据处理
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126144841197.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126151810917.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 4.3 高阶函数数据处理

1. 在dataframe中使用apply方法，调用自定义函数对数据进行处理
2. 函数apply, axis=0表示对行进行操作,axis=1表示对列进行操作
3. 可以使用astype函数对数据进行转换
4. 可以使用map函数进行数据转换

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021012615224683.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

# 5. 数据清洗之数据统计

## 5.1 数据分组运算

分组计算根据某个或者某几个字段对数据集进行分组，然后运用特定的函数，得到结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126152602923.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

1. 使用groupby方法进行分组计算，得到分组对象GroupBy
2. 语法为df.groupby(by=)
3. 分组对象GroupBy可以运用描述性统计方法, 如count、mean 、median 、max和min等

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126153736539.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 5.2 聚合函数使用

1. 对分组对象使用agg聚合函数
2. Groupby.agg(func)
3. 针对不同的变量使用不同的统计方法
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126154303299.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 5.3 分组对象与apply函数

1. 函数apply即可用于分组对象,也可以作用于dataframe数据
2. Groupby.apply(func)
3. 需要注意axis=0和axis=1的区别

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126154953284.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 5.4 透视图与交叉表

在数据分析中，数据透视表是常见的工具之一，需要根据行或列对数据进行各个维度数据的汇总，在pandas中，提供了相关函数解决此类问题，交叉表更多用于频数的分析。

pivot_table( data, index, columns,values, aggfunc, fill_value,margins, margins_name=)

```
Index :      行分组键
columns:     列分组键
values:      分组的字段，只能为数值型变量
aggfunc:     聚合函数
margins:     是否需要总计
12345
```

交叉表用于计算分组频率
pd.crosstab(index,columns,normalize)

```
Index: 行索引
Columns: 列索引
Normalize:  数据对数据进行标准化，index表示行，column表示列
123
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126155738604.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

# 6. 数据清洗之数据预处理

## 6.1 重复值处理

1. 数据清洗一般先从重复值和缺失值开始处理
2. 重复值一般采取删除法来处理
3. 但有些重复值不能删除，例如订单明细数据或交易明细数据等
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210127090034974.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 6.2 缺失值处理

1. 缺失值首先需要根据实际情况定义
2. 可以采取直接删除法
3. 有时候需要使用替换法或者插值法
4. 常用的替换法有均值替换、前向、后向替换和常数替换
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210127091451645.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 6.3 异常值处理

1. 指那些偏离正常范围的值，不是错误值
2. 异常值出现频率较低，但又会对实际项目分析造成偏差
3. 异常值一般用过箱线图法(分位差法)或者分布图(标准差法)来判断
4. 异常值往往采取盖帽法或者数据离散化

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210126160212808.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210127092618726.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

## 6.4 数据离散化处理

1. 数据离散化就是分箱
2. 一般常用分箱方法是等频分箱或者等宽分箱
3. 一般使用pd.cut或者pd.qcut函数

pandas.cut(x, bins, right=True, labels=None, retbins=False, precision=3, include_lowest=False)

```
x，类array对象，且必须为一维，待切割的原形式
bins, 整数、序列尺度、或间隔索引。如果bins是一个整数，它定义了x宽度范围内的等宽面元数量，
	但是在这种情况下，x的范围在每个边上被延长1%，以保证包括x的最小值或最大值。
	如果bin是序列，它定义了允许非均匀bin宽度的bin边缘。在这种情况下没有x的范围的扩展。
right,布尔值。是否是左开右闭区间，right=True,左开右闭，right=False,左闭右开
labels,用作结果箱的标签。必须与结果箱相同长度。如果FALSE，只返回整数指标面元。
retbins,布尔值。是否返回面元
precision，整数。返回面元的小数点几位
include_lowest，布尔值。第一个区间的左端点是否包含
123456789
```

pandas.qcut(x, q, labels=None, retbins=False, precision=3, duplicates=’raise’)

```
x 
q,整数或分位数组成的数组。
q, 整数 或分位数数组 整数比如 4 代表 按照4分位数 进行切割 
labels, 用作结果箱的标签。必须与结果箱相同长度。如果FALSE，只返回整数指标面元。
1234
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210127093732576.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdW1lbmdxaTEx,size_16,color_FFFFFF,t_70)

# 7. 总结与梳理

## 7.1 数据清洗步骤

1. 数据获取,使用read_csv或者read_excel
2. 数据探索,使用shape,describe或者info函数
3. 行列操作，使用loc或者iloc函数
4. 数据整合,对不同数据源进行整理
5. 数据类型转换，对不同字段数据类型进行转换
6. 分组汇总，对数据进行各个维度的计算
7. 处理重复值、缺失值和异常值以及数据离散化

## 7.2 函数大全

1. merge,concat函数常常用于数据整合
2. pd.to_datetime常常用于日期格式转换
3. str函数用于字符串操作
4. 函数astype用于数据类型转换
5. 函数apply和map用于更加高级的数据处理
6. Groupby用于创建分组对象
7. 透视表函数pd.pivot_table和交叉表pd.crosstab
8. 分组对象和agg结合使用，统计需要的信息

## 7.3 数据清洗之总结

数据清洗实质上是将实际业务问题中，脏数据清洗干净,转换为’干净的数据’, 所谓的脏
，指数据可能存在以下几种问题（主要问题）:

1. 数据缺失 （Incomplete） 是属性值为空的情况。如 Occupancy = “ ”
2. 数据噪声 （Noisy）是数据值不合常理的情况。如 Salary = “-100”
3. 数据不一致 （Inconsistent）是数据前后存在矛盾的情况。如 Age = “042” 或者
   Birthday = “01/09/1985”
4. 数据冗余 （Redundant）是数据量或者属性数目超出数据分析需要的情况
5. 离群点/异常值 （Outliers）是偏离大部分值的数据
6. 数据重复是在数据集中出现多次的数据

**❤本教程到这终于结束了，希望对大家有所帮助❤**