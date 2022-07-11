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

![](<../.gitbook/assets/圖片 (4).png>)

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

![](<../.gitbook/assets/圖片 (5).png>)

