## 라이브러리 불러오기


```python
import numpy as np
print(np.__version__)
```

    1.19.5
    


```python
temp = np.array([1, 2, 3])
print(type(temp))
```

    <class 'numpy.ndarray'>
    

## Numpy 배열 생성 및 둘러보기


```python
data1 = [1,2,3]
data1
```




    [1, 2, 3]




```python
data2= [1,1,2,2,3,4]
data2
```




    [1, 1, 2, 2, 3, 4]




```python
my_array1 = np.array(data1)
print(my_array1) 
print(my_array1.shape)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-1-cc1150ccb3a3> in <module>()
    ----> 1 my_array1 = np.array(data1)
          2 print(my_array1)
          3 print(my_array1.shape)
    

    NameError: name 'np' is not defined



```python
my_array2 = np.array(data2)
print(my_array2) 
print(my_array2.shape)
```

    [1 1 2 2 3 4]
    (6,)
    


```python
my_array3 = np.array([3,6,9,12])
print(my_array3)
print(my_array3.shape)
print(my_array3.dtype)
```

    [ 3  6  9 12]
    (4,)
    int64
    


```python
my_array4 = np.array([[2,4,6],[8,10,12],[14,16,18],[20,22,24]])
my_array4
```




    array([[ 2,  4,  6],
           [ 8, 10, 12],
           [14, 16, 18],
           [20, 22, 24]])




```python
my_array4.shape
```




    (4, 3)




```python
my_array5 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
my_array5.shape
```




    (2, 2, 2)



## Numpy 기본 함수들

### arange


```python
arrange_array = np.arange(5)
arrange_array
```




    array([0, 1, 2, 3, 4])




```python
arrange_array2 = np.arange(1, 9, 3)
arrange_array2
```




    array([1, 4, 7])



### zeroes, ones


```python
zeros_array = np.zeros((3,2))
print(zeros_array)
print("Data Type is:", zeros_array.dtype)
print("Data Shape is:", zeros_array.shape)
```

    [[0. 0.]
     [0. 0.]
     [0. 0.]]
    Data Type is: float64
    Data Shape is: (3, 2)
    


```python
ones_array = np.ones((3,4), dtype='int32')
print(ones_array)
print("Data Type is:", ones_array.dtype)
print("Data Shape is:", ones_array.shape)
```

    [[1 1 1 1]
     [1 1 1 1]
     [1 1 1 1]]
    Data Type is: int32
    Data Shape is: (3, 4)
    

### reshape



```python
after_reshape = ones_array.reshape(6,2)
print(after_reshape)
print("Data Shape is:", after_reshape.shape)
```

    [[1 1]
     [1 1]
     [1 1]
     [1 1]
     [1 1]
     [1 1]]
    Data Shape is: (6, 2)
    


```python
after_reshape = ones_array.reshape(5,3)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-25-94cac763be50> in <module>()
    ----> 1 after_reshape = ones_array.reshape(5,3)
    

    ValueError: cannot reshape array of size 12 into shape (5,3)



```python
after_reshape = ones_array.reshape(2,3,2)
print(after_reshape)
print("Data Shape is:", after_reshape.shape)
```

    [[[1 1]
      [1 1]
      [1 1]]
    
     [[1 1]
      [1 1]
      [1 1]]]
    Data Shape is: (2, 3, 2)
    


```python
after_reshape2= ones_array.reshape(-1,6)
print("reshape(-1,6)? \n")
print(after_reshape2)
```

    reshape(-1,6)? 
    
    [[1 1 1 1 1 1]
     [1 1 1 1 1 1]]
    


```python
after_reshape3= ones_array.reshape(3,-1)
print("reshape(3, -1)? \n")
print(after_reshape3)
print("Data Shape is:", after_reshape3.shape)
```

    reshape(3, -1)? 
    
    [[1 1 1 1]
     [1 1 1 1]
     [1 1 1 1]]
    Data Shape is: (3, 4)
    

## Numpy 인덱싱과 슬라이딩


```python
my_array = np.arange(start=0, stop=4)
print(my_array)
```

    [0 1 2 3]
    


```python
print("my_array의 1번째 요소, 즉 위치값이 0인 것은: ", my_array[0])
```

    my_array의 1번째 요소, 즉 위치값이 0인 것은:  0
    


```python
print("my_array[0:3]:", my_array[0:3])
```

    my_array[0:3]: [0 1 2]
    


```python
my_array2 = np.arange(start=3,stop=30,step=3)
my_array2 = my_array2.reshape(3,3)
my_array2
```




    array([[ 3,  6,  9],
           [12, 15, 18],
           [21, 24, 27]])




```python
my_array2[0:2,0:2]
```




    array([[ 3,  6],
           [12, 15]])




```python
my_array2[1:3,:]
```




    array([[12, 15, 18],
           [21, 24, 27]])




```python
my_array2[:,:]
```




    array([[ 3,  6,  9],
           [12, 15, 18],
           [21, 24, 27]])



## Numpy 정렬

### sort()


```python
height_arr = np.array([174, 165, 180, 182, 168])
sorted_height_arr = np.sort(height_arr)

print('Height Matrix: ', height_arr)
print('np.sort() Matrix: ', sorted_height_arr)
```

    Height Matrix:  [174 165 180 182 168]
    np.sort() Matrix:  [165 168 174 180 182]
    


```python
desc_sorted_height_arr = np.sort(height_arr)[::-1]
print('np.sort()[::-1] : ', desc_sorted_height_arr)
```

    np.sort()[::-1] :  [182 180 174 168 165]
    

### argsort()


```python
fives = np.array([10, 5, 15, 20])
fives_order = fives.argsort()

print("The original data", fives)
print("The argsort(): ", fives_order)
print("The asending:", fives[fives_order])
```

    The original data [10  5 15 20]
    The argsort():  [1 0 2 3]
    The asending: [ 5 10 15 20]
    
