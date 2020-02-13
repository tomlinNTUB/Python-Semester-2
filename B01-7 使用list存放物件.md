# B01-7 使用list存放物件


## 1. 將成績物件存在list中 

#### 1-1 學習重點
``` python
(1) 儲存架構
      |__ m01.py
      |__ p01.py

(2) 使用list物件存放Score物件.
```

#### 1-2 程式範例(m01.py)

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


#### 1-3 程式範例(p01.py)

``` python
# 匯入模組中的類別
from m01 import Score

# 建立儲存成績物件的list
scores = []

scores.append(Score(60, 80, 90))
scores.append(Score(65, 65, 70))
scores.append(Score(85, 70, 85))

# 印出物件內容
for s in scores:
    print('總分:{}'.format(s.total()))
    print('平均:{:.2f}'.format(s.average()))
    print('等第:{}'.format(s.rank()))
    print()
```


#### 1-4 執行結果
``` python
>> 總分:230
>> 平均:76.67
>> 等第:乙等
>> 
>> 總分:200
>> 平均:66.67
>> 等第:丙等
>> 
>> 總分:240
>> 平均:80.00
>> 等第:甲等
```

