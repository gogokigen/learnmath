# 顯示多點趨勢的直線

## 程式與 Python

### 從 CSV 檔案讀資料

#### 建構 .csv 資料檔 score.csv

```
28,111
26,97
28,102
27,105
27,108
20,74
26,116
22,92
23,112
19,88
26,116
23,101
25,93
21,74
20,87
18,71
24,94
19,67
24,105
25,99
```

#### 讀檔與確認讀到的值

```
import csv

#打開檔案
f = open('score.csv')

#宣告容器
dx = []
dy = []

#讀檔
for row in csv.reader(f):
    dx.append(int(row[0]))  # 1列目
    dy.append(int(row[1]))  # 2列目
    
# 關檔案
f.close()

#確認 dx 和 dy 的值
print(dx)
print(dy)
```

![](<../.gitbook/assets/圖片 (1).png>)

#### 畫圖

```
plt.scatter(dx, dy)
plt.show()
```

## 數學

### 散佈圖

#### 數學意義

//

#### 範例程式

```
import matplotlib.pyplot as plt

# 資料
dx = [28, 26, 28, 27, 27, 20, 26, 22, 23, 19, 26, 23, 25, 21, 20, 18, 24, 19, 24, 25]
dy = [111, 97, 102, 105, 108, 74, 116, 92, 112, 88, 116, 101, 93, 74, 87, 71, 94, 67, 105, 99]

#作圖
plt.scatter(dx, dy)
plt.show()
```

![](<../.gitbook/assets/圖片 (4).png>)

#### Homework

在這張圖中，你觀察到什麼？

### 散佈圖到直線

//

### 最小平方法

//

### 實際資料與直線的偏差

//

#### 程式範例

```
dx = [28, 26, 28, 27, 27, 20, 26, 22, 23, 19, 26, 23, 25, 21, 20, 18, 24, 19, 24, 25]           # 気温
dy = [111, 97, 102, 105, 108, 74, 116, 92, 112, 88, 116, 101, 93, 74, 87, 71, 94, 67, 105, 99]  # 販売数

# 假設直線 y = 0
a = 0.0  # 斜率
b = 0.0  # x軸距

# 差的平方和
min_res = 0.0
for i in range(20):
    y = a * dx[i] + b
    min_res += (dy[i]-y)**2 #差的平方和
print(min_res)
```

#### Homework

* 使用 numpy 改寫：min\_res += (dy\[i]-y)\*\*2 #差的平方和
* 目前的 a, b 找出來的直線，誤差夠小嗎？不夠的話該怎麼辦？

### 利用亂數

#### 學習使用亂數生成 7個數字

```
import random
for i in range(7):
    print(random.random())
```

<div align="left">

<img src="../.gitbook/assets/圖片 (7).png" alt="">

</div>

\-0.5 \~ 0.5 間的亂數\
<img src="../.gitbook/assets/圖片 (2).png" alt="" data-size="original">

### 利用亂數找出迴歸直線

#### 畫流程圖分析

//

#### 使用亂數，找出 a, b

```
import random

for i in range(500000):
    # 微小的變動量
    wa = (random.random() - 0.5) * 0.001
    wb = (random.random() - 0.5) * 0.001
    
    # 差的平方和, 目標是要讓誤差最小
    res = 0
    for j in range(20):
        y = (a + wa) * dx[j] + (b + wb)
        res += (dy[j] - y)**2
        
    # 更新值
    if res < min_res:
        min_res = res  # 誤差res 比之前小的話, 就更新
        a = a + wa     # 新的斜率
        b = b + wb     # 新的距離
print(a, b, min_res)
```

### 更有效率的找出迴歸直線？

//

