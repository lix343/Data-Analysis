# Pandas

### 3.1.1 Generate Series

What is Series?

Series can be a fixed length dictionary

``` python
import pandas as pd
eva = {'凌波丽': 0, '碇真嗣': 1}
eva_s = pd.Series(eva)
eva_s = ?

凌波丽    0
碇真嗣    1
dtype: int64
    
eva_s.values = ?
array([0, 1], dtype=int64)

eva_s.index
Index(['凌波丽', '碇真嗣'], dtype='object')
```

### 3.1.2 取值

``` python
eva_s[0]
eva_s[0] = ?
0

eva_s[0:1]
凌波丽    0

eva_s==0
凌波丽     True
碇真嗣    False
dtype: bool
    
eva_s[eva_s==0]
凌波丽    0
dtype: int64
    
```

### 3.2 Data Type -- DataFrame

#### 3.2.1 Select Distinct

``` python
import numpy as np
import pandas as pd
import pymysql
pd.set_option('display.max_rows', 9999)
pd.set_option('display.max_columns', 9999)
pd.set_option('display.float_format', lambda x: '%.3f' % x)

SQL:
SELECT DISTINCT (平台门店名称)
from >>>

python:
cpc = pd.read_csv(`./cpc.csv`,sep=',', encoding = 'gbk')
#We need to make sure that the code file is under the same directory as the csv
pd.Series(pd.unique(cpc['平台门店名称']))

0           蛙小辣火锅杯（合生汇店）
1        蛙小辣美蛙火锅杯（大宁国际店）
2      蛙小辣·美蛙火锅杯（长风大悦城店）
3      蛙小辣·美蛙火锅杯（虹口足球场店）
4        利芳·一人食大盘鸡(国定路店)
5      蛙小辣·美蛙火锅杯(虹口足球场店)
6         蛙小辣·美蛙火锅杯(宝山店)
7           蛙小辣火锅杯(五角场店)
8         蛙小辣·美蛙火锅杯(真如店)
9        蛙小辣·美蛙火锅杯(龙阳路店)
dtype: object
```

#### 3.2.8

0:56:24