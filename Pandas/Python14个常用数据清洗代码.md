# Python：14个常用数据清洗代码

![img](https://csdnimg.cn/release/blogv2/dist/pc/img/original.png)

[cyber_1987](https://blog.csdn.net/weixin_42029733) 2019-12-23 15:16:51 ![img](https://csdnimg.cn/release/blogv2/dist/pc/img/articleReadEyes.png) 2321 ![img](https://csdnimg.cn/release/blogv2/dist/pc/img/tobarCollect.png) 收藏 62

分类专栏： [Pandas](https://blog.csdn.net/weixin_42029733/category_8818351.html) [数据分析](https://blog.csdn.net/weixin_42029733/category_9184072.html) 文章标签： [数据分析](https://www.csdn.net/tags/MtTaEg0sNDc1NTAtYmxvZwO0O0OO0O0O.html)

版权

# 常用库导入

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
warnings.filterwarnings("ignore")
pd.options.display.max_columns = None #显示所有列
pd.set_option('display.float_format', lambda x: '%.2f' % x) #取消科学计数法
12345678
```

## 1、数据整合（concat）

```python
train_data = pd.read_csv('training30.csv')
test_data = pd.read_csv('test30.csv')
total_data = pd.concat([train_data, test_data], axis=0)
total_data.info()
1234
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152417892.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 2、数据筛选

```python
cdma = pd.read_csv('cdma.xls', encoding='gbk', sep='\t')
print(cdma.shape)
cdma = cdma[(cdma['销售区局'] == '浦东电信局') & (cdma['渠道管理细分'].isin(['专营渠道', '中小渠道', '开放渠道']))]
print(cdma.shape)
# cdma = cdma[~cdma['发展部门名称'].str.contains('千秋')]
# print(cdma.shape)
123456
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152428394.png)

## 3、数据匹配（merge）

```python
match_table = pd.read_excel('数据说明与匹配公式.xlsx', sheet_name='部门匹配表')
new_cdma = cdma.merge(match_table, how='left', on=['发展部门名称', '渠道管理细分'])
new_cdma = new_cdma[new_cdma['渠道管理细分'] == '专营渠道']
new_cdma[['统计日期', '订单号', '所属部门', '所属代理商', '所属分局', '渠道经理']].head()
1234
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152444437.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 4、数据透视表（pivot_table）

```python
cdma_pivot = new_cdma.pivot_table(index='所属代理商', values='订单号', columns='所属分局', aggfunc='count', fill_value=0, margins=True, margins_name='合计')
cdma_pivot
12
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152455145.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 5、数据排序（sort_values）

```python
cdma_pivot.sort_values(by='合计',inplace=True, ascending=False)
cdma_pivot
12
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152505188.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 6、数据替换（replace）

```python
train_data = train_data.replace('?', np.nan) #精准匹配
train_data.head(10)
train_data2 = train_data.replace('Tai', 'Cy', regex=True) #模糊匹配
train_data2.head(10)
1234
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152518128.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 7、数据删除（dropna）

```python
print(train_data.shape)
train_data3 = train_data.dropna(subset=['gender', 'age'])
print(train_data3.shape)
123
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152530498.png)

## 8、降采样

```python
def lower_sample_data(df, labelname, percent=1):
    '''
    percent:多数类别下采样的数量相对于少数类别样本数量的比例
    '''
    data1 = df[df[labelname] == 1]  # 将少数类别的样本放在data1
    data0 = df[df[labelname] == 0]  # 将多数类别的样本放在data0
    index = np.random.randint(
        len(data0), size=percent * (len(data1)))  # 随机给定下采样取出样本的序号
    lower_data0 = data0.iloc[list(index)]  # 下采样
    return(pd.concat([lower_data0, data1]))

print(train_data["'Purchase or not'"].value_counts())
train_data4 = lower_sample_data(train_data, "'Purchase or not'", percent=1)
print(train_data4["'Purchase or not'"].value_counts())
1234567891011121314
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152540735.png)

## 9、缺失值处理（fillna）

```python
train_data5 = pd.read_csv('cs-training.csv')
per_columns = set(train_data5.columns) - set(['CustomerID', 'SeriousDlqin2yrs'])

for column in per_columns:
    temp_mean = train_data5[column].mean() #如果是中位数的话是median，众数的话是mode
    train_data5[column] = train_data5[column].fillna(temp_mean)
train_data5.describe()
1234567
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152552826.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 10、噪声处理

### 方法一：四分位法

```python
def cap(x, quantile=[0.05, 0.95]):
    """盖帽法处理异常值
    Args：
    x：pd.Series列，连续变量
    quantile：指定盖帽法的上下分位数范围
    """ 
    # 生成分位数
    Q05, Q95=x.quantile(quantile).values.tolist()
    # 替换异常值为指定的分位数
    if Q05 > x.min():
        x = x.copy()
        x.loc[x<Q05] = Q05
    if Q95 < x.max():
        x = x.copy()
        x.loc[x>Q95] = Q95
    return(x)

train_data6 = train_data5[per_columns]
train_data6 = train_data6.apply(cap)
train_data7 = pd.concat([train_data5[['CustomerID', 'SeriousDlqin2yrs']], train_data6], axis=1)
train_data7 = train_data7[train_data5.columns]
train_data7.describe()
12345678910111213141516171819202122
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152607251.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

### 方法二：平均值法

```python
def cap_mean(x):
    """盖帽法处理异常值
    Args：
    x：pd.Series列，连续变量
    """ 
    # 生成平均值和标准差的上下界限
    x_up = x.mean() + 3*x.std()
    x_down = x.mean() - 3*x.std()
    # 替换异常值
    if x_down > x.min():
        x = x.copy()
        x.loc[x<x_down] = x_down
    if x_up < x.max():
        x = x.copy()
        x.loc[x>x_up] = x_up
    return(x)

train_data8 = train_data5[per_columns]
train_data8 = train_data8.apply(cap_mean)
train_data9 = pd.concat([train_data5[['CustomerID', 'SeriousDlqin2yrs']], train_data8], axis=1)
train_data9 = train_data9[train_data5.columns]
train_data9.describe()
12345678910111213141516171819202122
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152617427.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 11、数据正规化/标准化

```python
from sklearn.preprocessing import MinMaxScaler
from sklearn.preprocessing import StandardScaler

mm_scaler = MinMaxScaler()
ss_scaler = StandardScaler()

print(train_data9['age'].head())
train_data9['age'] = mm_scaler.fit_transform(train_data9[['age']])
print(train_data9['age'].head())

print('-------------------------------------------------')

print(train_data9['MonthlyIncome'].head())
train_data9['MonthlyIncome'] = ss_scaler.fit_transform(train_data9[['MonthlyIncome']])
print(train_data9['MonthlyIncome'].head())
123456789101112131415
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152628160.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 12、数据泛化（map）

```python
print(cdma['发展渠道小类'].value_counts())
qd_map = {'自营营业厅': '自营渠道', '专营店': '专营渠道', '合作营业厅': '专营渠道', '核心渠道专区专柜':'专营渠道', '天翼小店':'中小渠道',
          '外包营业厅':'专营渠道', '全国连锁卖场': '开放渠道', '全网通（专营）':'专营渠道', '商圈店':'专营渠道', '天翼合作店':'中小渠道', '终端零售店（开放）':'中小渠道'}
cdma_2 = cdma.copy()
cdma_2['渠道统计归类'] = cdma_2['发展渠道小类'].map(qd_map)
print(cdma_2['渠道统计归类'].value_counts())
123456
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152638606.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

## 13、连续性指派（LabelEncoder）

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
cdma_2['渠道统计归类'] = le.fit_transform(cdma_2[['渠道统计归类']])
cdma_2['渠道统计归类'].value_counts()
12345
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152649357.png)

## 14、数据离散化（cut/qcut）

### 方法一：人工分离法

```python
age_range = list(range(0,111,10))
train_data5['age_cut1'] = pd.cut(train_data5['age'], age_range, include_lowest=True, right=False)
train_data5['age_cut1'].value_counts().sort_index()
123
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152652655.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

### 方法二：等宽装箱法

```python
train_data5['age_cut2'] = pd.cut(train_data5['age'], bins=10, include_lowest=True, right=False, precision=0)
train_data5['age_cut2'].value_counts().sort_index()
12
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019122315270944.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)

### 方法三：等深装箱法

```python
train_data5['age_cut3'] = pd.qcut(train_data5['age'], 10, precision=1)
train_data5['age_cut3'].value_counts().sort_index()
12
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191223152718645.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjAyOTczMw==,size_16,color_FFFFFF,t_70)