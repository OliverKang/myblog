## 라이브러리 불러오기


```python
import pandas as pd
print(pd.__version__)
```

    1.1.5
    

### 테스트


```python
df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})
print(type(df))
```

    <class 'pandas.core.frame.DataFrame'>
    

## 구글 드라이브 연동


```python
from google.colab import drive
drive.mount('/content/drive')
```

    Drive already mounted at /content/drive; to attempt to forcibly remount, call drive.mount("/content/drive", force_remount=True).
    


```python
DATA_PATH = "경로를 입력하시기를 바랍니다."

# 필자의 경로는 다음과 같았습니다. 
DATA_PATH = '/content/drive/MyDrive/Colab Notebooks/lectures_211101/PART_I_Intro/data/Lemonade2016.csv'
lemonade = pd.read_csv(DATA_PATH)
lemonade.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 32 entries, 0 to 31
    Data columns (total 7 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   Date         31 non-null     object 
     1   Location     32 non-null     object 
     2   Lemon        32 non-null     int64  
     3   Orange       32 non-null     int64  
     4   Temperature  32 non-null     int64  
     5   Leaflets     31 non-null     float64
     6   Price        32 non-null     float64
    dtypes: float64(2), int64(3), object(2)
    memory usage: 1.9+ KB
    

## 데이터 둘러보기


```python
lemonade.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Location</th>
      <th>Lemon</th>
      <th>Orange</th>
      <th>Temperature</th>
      <th>Leaflets</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7/1/2016</td>
      <td>Park</td>
      <td>97</td>
      <td>67</td>
      <td>70</td>
      <td>90.0</td>
      <td>0.25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7/2/2016</td>
      <td>Park</td>
      <td>98</td>
      <td>67</td>
      <td>72</td>
      <td>90.0</td>
      <td>0.25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7/3/2016</td>
      <td>Park</td>
      <td>110</td>
      <td>77</td>
      <td>71</td>
      <td>104.0</td>
      <td>0.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7/4/2016</td>
      <td>Beach</td>
      <td>134</td>
      <td>99</td>
      <td>76</td>
      <td>98.0</td>
      <td>0.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7/5/2016</td>
      <td>Beach</td>
      <td>159</td>
      <td>118</td>
      <td>78</td>
      <td>135.0</td>
      <td>0.25</td>
    </tr>
  </tbody>
</table>
</div>




```python
lemonade.tail(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Location</th>
      <th>Lemon</th>
      <th>Orange</th>
      <th>Temperature</th>
      <th>Leaflets</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>29</th>
      <td>7/29/2016</td>
      <td>Park</td>
      <td>100</td>
      <td>66</td>
      <td>81</td>
      <td>95.0</td>
      <td>0.35</td>
    </tr>
    <tr>
      <th>30</th>
      <td>7/30/2016</td>
      <td>Beach</td>
      <td>88</td>
      <td>57</td>
      <td>82</td>
      <td>81.0</td>
      <td>0.35</td>
    </tr>
    <tr>
      <th>31</th>
      <td>7/31/2016</td>
      <td>Beach</td>
      <td>76</td>
      <td>47</td>
      <td>82</td>
      <td>68.0</td>
      <td>0.35</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(lemonade.info())
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 32 entries, 0 to 31
    Data columns (total 7 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   Date         31 non-null     object 
     1   Location     32 non-null     object 
     2   Lemon        32 non-null     int64  
     3   Orange       32 non-null     int64  
     4   Temperature  32 non-null     int64  
     5   Leaflets     31 non-null     float64
     6   Price        32 non-null     float64
    dtypes: float64(2), int64(3), object(2)
    memory usage: 1.9+ KB
    None
    


```python
lemonade.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Lemon</th>
      <th>Orange</th>
      <th>Temperature</th>
      <th>Leaflets</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>32.000000</td>
      <td>32.000000</td>
      <td>32.000000</td>
      <td>31.000000</td>
      <td>32.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>116.156250</td>
      <td>80.000000</td>
      <td>78.968750</td>
      <td>108.548387</td>
      <td>0.354687</td>
    </tr>
    <tr>
      <th>std</th>
      <td>25.823357</td>
      <td>21.863211</td>
      <td>4.067847</td>
      <td>20.117718</td>
      <td>0.113137</td>
    </tr>
    <tr>
      <th>min</th>
      <td>71.000000</td>
      <td>42.000000</td>
      <td>70.000000</td>
      <td>68.000000</td>
      <td>0.250000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>98.000000</td>
      <td>66.750000</td>
      <td>77.000000</td>
      <td>90.000000</td>
      <td>0.250000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>113.500000</td>
      <td>76.500000</td>
      <td>80.500000</td>
      <td>108.000000</td>
      <td>0.350000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>131.750000</td>
      <td>95.000000</td>
      <td>82.000000</td>
      <td>124.000000</td>
      <td>0.500000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>176.000000</td>
      <td>129.000000</td>
      <td>84.000000</td>
      <td>158.000000</td>
      <td>0.500000</td>
    </tr>
  </tbody>
</table>
</div>




```python
lemonade['Location'].value_counts()
```




    Beach    17
    Park     15
    Name: Location, dtype: int64



## 데이터 다뤄보기


```python
lemonade['Sold'] = 0 
print(lemonade.head(3))
```

           Date Location  Lemon  Orange  Temperature  Leaflets  Price  Sold
    0  7/1/2016     Park     97      67           70      90.0   0.25     0
    1  7/2/2016     Park     98      67           72      90.0   0.25     0
    2  7/3/2016     Park    110      77           71     104.0   0.25     0
    


```python
lemonade['Sold'] = lemonade['Lemon'] + lemonade['Orange']
print(lemonade.head(3))
```

           Date Location  Lemon  Orange  Temperature  Leaflets  Price  Sold
    0  7/1/2016     Park     97      67           70      90.0   0.25   164
    1  7/2/2016     Park     98      67           72      90.0   0.25   165
    2  7/3/2016     Park    110      77           71     104.0   0.25   187
    


```python
lemonade['Revenue'] = lemonade['Price'] * lemonade['Sold']
print(lemonade.head(3))
```

           Date Location  Lemon  Orange  ...  Leaflets  Price  Sold  Revenue
    0  7/1/2016     Park     97      67  ...      90.0   0.25   164    41.00
    1  7/2/2016     Park     98      67  ...      90.0   0.25   165    41.25
    2  7/3/2016     Park    110      77  ...     104.0   0.25   187    46.75
    
    [3 rows x 9 columns]
    


```python
pd.set_option('display.max_columns', None)

lemonade['Revenue'] = lemonade['Price'] * lemonade['Sold']
print(lemonade.head(3))
```

           Date Location  Lemon  Orange  Temperature  Leaflets  Price  Sold  \
    0  7/1/2016     Park     97      67           70      90.0   0.25   164   
    1  7/2/2016     Park     98      67           72      90.0   0.25   165   
    2  7/3/2016     Park    110      77           71     104.0   0.25   187   
    
       Revenue  
    0    41.00  
    1    41.25  
    2    46.75  
    


```python
pd.set_option('display.max_columns', 0)

lemonade['Revenue'] = lemonade['Price'] * lemonade['Sold']
print(lemonade.head(3))
```

           Date Location  Lemon  Orange  ...  Leaflets  Price  Sold  Revenue
    0  7/1/2016     Park     97      67  ...      90.0   0.25   164    41.00
    1  7/2/2016     Park     98      67  ...      90.0   0.25   165    41.25
    2  7/3/2016     Park    110      77  ...     104.0   0.25   187    46.75
    
    [3 rows x 9 columns]
    


```python
lemonade_column_drop = lemonade.drop('Sold', axis=1)
print(lemonade_column_drop.head(3))
```

           Date Location  Lemon  Orange  Temperature  Leaflets  Price  Revenue
    0  7/1/2016     Park     97      67           70      90.0   0.25    41.00
    1  7/2/2016     Park     98      67           72      90.0   0.25    41.25
    2  7/3/2016     Park    110      77           71     104.0   0.25    46.75
    


```python
lemonade_row_drop = lemonade_column_drop.drop(0, axis=0)
print(lemonade_row_drop.head(3))
```

           Date Location  Lemon  Orange  Temperature  Leaflets  Price  Revenue
    1  7/2/2016     Park     98      67           72      90.0   0.25    41.25
    2  7/3/2016     Park    110      77           71     104.0   0.25    46.75
    3  7/4/2016    Beach    134      99           76      98.0   0.25    58.25
    

## 데이터 인덱싱



```python
print(lemonade[0:5])
```

           Date Location  Lemon  Orange  ...  Leaflets  Price  Sold  Revenue
    0  7/1/2016     Park     97      67  ...      90.0   0.25   164    41.00
    1  7/2/2016     Park     98      67  ...      90.0   0.25   165    41.25
    2  7/3/2016     Park    110      77  ...     104.0   0.25   187    46.75
    3  7/4/2016    Beach    134      99  ...      98.0   0.25   233    58.25
    4  7/5/2016    Beach    159     118  ...     135.0   0.25   277    69.25
    
    [5 rows x 9 columns]
    


```python
lemonade['Location'] == 'Beach'
```




    0     False
    1     False
    2     False
    3      True
    4      True
    5      True
    6      True
    7      True
    8      True
    9      True
    10     True
    11     True
    12     True
    13     True
    14     True
    15     True
    16     True
    17     True
    18    False
    19    False
    20    False
    21    False
    22    False
    23    False
    24    False
    25    False
    26    False
    27    False
    28    False
    29    False
    30     True
    31     True
    Name: Location, dtype: bool




```python
print(lemonade[lemonade['Location'] == 'Beach'].head(3))
```

           Date Location  Lemon  Orange  ...  Leaflets  Price  Sold  Revenue
    3  7/4/2016    Beach    134      99  ...      98.0   0.25   233    58.25
    4  7/5/2016    Beach    159     118  ...     135.0   0.25   277    69.25
    5  7/6/2016    Beach    103      69  ...      90.0   0.25   172    43.00
    
    [3 rows x 9 columns]
    


```python
print(lemonade.iloc[0:3, 0:2])
```

           Date Location
    0  7/1/2016     Park
    1  7/2/2016     Park
    2  7/3/2016     Park
    


```python
print(lemonade.loc[0:2, ['Date','Location']])
```

           Date Location
    0  7/1/2016     Park
    1  7/2/2016     Park
    2  7/3/2016     Park
    


```python
print(lemonade.loc[lemonade['Revenue']>45, ['Date','Revenue']].head(3))
```

           Date  Revenue
    2  7/3/2016    46.75
    3  7/4/2016    58.25
    4  7/5/2016    69.25
    

## 기본 데이터 전처리


```python
print(lemonade.sort_values(by=['Temperature']).head(5))
```

             Date Location  Lemon  Orange  ...  Leaflets  Price  Sold  Revenue
    0    7/1/2016     Park     97      67  ...      90.0   0.25   164    41.00
    20  7/20/2016     Park     71      42  ...       NaN   0.50   113    56.50
    2    7/3/2016     Park    110      77  ...     104.0   0.25   187    46.75
    1    7/2/2016     Park     98      67  ...      90.0   0.25   165    41.25
    16  7/16/2016    Beach     81      50  ...      90.0   0.50   131    65.50
    
    [5 rows x 9 columns]
    


```python
lemonade.sort_values(by=['Temperature', 'Revenue'], ascending= False, inplace = True)
print(lemonade.loc[:,['Date','Temperature', 'Revenue']].head(5))
```

             Date  Temperature  Revenue
    25  7/25/2016           84   134.50
    12  7/12/2016           84    56.25
    26  7/26/2016           83   106.75
    11  7/11/2016           83    70.50
    24  7/24/2016           82   101.50
    


```python
print(lemonade.groupby(by='Location').count())
```

              Date  Lemon  Orange  Temperature  Leaflets  Price  Sold  Revenue
    Location                                                                  
    Beach       16     17      17           17        17     17    17       17
    Park        15     15      15           15        14     15    15       15
    


```python
print(lemonade.groupby('Location')['Revenue'].agg([max,min]))
```

                max   min
    Location             
    Beach      95.5  43.0
    Park      134.5  41.0
    


```python
print(lemonade.groupby('Location')[['Revenue', 'Sold']].agg([max,min]))
```

             Revenue       Sold     
                 max   min  max  min
    Location                        
    Beach       95.5  43.0  282  123
    Park       134.5  41.0  305  113
    
