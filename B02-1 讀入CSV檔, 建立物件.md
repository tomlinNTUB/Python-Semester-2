# B02-1 讀入CSV檔, 建立物件


## 1. 讀入成績CSV檔

#### 1-1 學習重點
``` python
(1) 儲存架構
      |__ scores.csv (資料檔)
      |__ m01.py
      |__ p01.py
```

#### 1-2 成績資料(scores.csv)
``` csv
85,90,75
67,89,64
50,90,98
100,85,90
72,63,55
``` 

#### 1-3 程式範例(m01.py)

``` python
#---------------------------
# 成績[類別]
#---------------------------
class Score():
    # 建構元
    def __init__(self, chi, eng, mat):
        self.chi = chi
        self.eng = eng
        self.mat = mat

    # 總分
    def total(self):
        return self.chi + self.eng + self.mat

    # 平均
    def average(self):
        return self.total() / 3

    # 等級
    def rank(self):
        a = self.average()

        if a>=90:
            return '優等'
        elif a>=80:
            return '甲等'
        elif a>=70:
            return '乙等'
        elif a>=60:
            return '丙等'
        else:
            return '丁等'         
```


#### 1-4 程式範例(p01.py)

``` python
#---------------------------------------
# 讀入CSV檔的格式
# 國文(0), 英文(1), 數學(2)
#---------------------------------------

# 匯入模組中的類別
from m01 import Score

# 開啟檔案, 逐筆處理
with open('scores.csv', 'r', encoding='UTF-8') as file:
    # 逐行處理讀入的資料
    for data in file.readlines():
        # 刪除前後空白, 以逗號分隔資料項目
        data=data.strip()
        items=data.split(',')

        # 原成績資料應為整數, 在以下進行轉型
        chi = int(items[0])
        eng = int(items[1])
        mat = int(items[2])

        # 建立物件
        s = Score(chi, eng, mat)

        # 印出物件內容
        print('總分:{}'.format(s.total()))
        print('平均:{:.2f}'.format(s.average()))
        print('等第:{}'.format(s.rank()))
        print()
```


#### 1-5 執行結果
``` python
>> 總分:250
>> 平均:83.33
>> 等第:甲等 
>> 
>> 總分:220  
>> 平均:73.33
>> 等第:乙等
>> 
>> 總分:238
>> 平均:79.33
>> 等第:乙等
>> 
>> 總分:275
>> 平均:91.67
>> 等第:優等
>> 
>> 總分:190
>> 平均:63.33
>> 等第:丙等
```
