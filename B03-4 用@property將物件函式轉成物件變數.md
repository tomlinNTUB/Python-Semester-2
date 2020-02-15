# B03-4 用@property將物件函式轉成物件變數

## 1. 建立空物件, 再增加物件變數

#### 1-1 學習重點
``` python
(1) |__ p01.py

(2) 在物件函式寫@property的修飾語, 將物件函式轉成物件變數. 如:
    原來應寫: s.salary()
    現在可寫: s.salary
    
(3) 用@property修飾語式轉變的物件變數, 只可讀, 不可寫. 如:
    s.salary=50000 (錯誤! 不可寫值)
```

#### 1-2 程式範例(p01.py)

``` python
#---------------------------
# 員工[類別]
#---------------------------
class Employee():
    # 建構元
    def __init__(self, no, name, rank='C'):
        self.no = no
        self.name = name
        self.rank = rank

    # 薪水(將[物件方法]轉為[物件變數]的使用方式)
    @property
    def salary(self):
        if self.rank=='A':
            return 50000
        elif self.rank=='B':
            return 40000
        else:
            return 30000

#===========================
# 主程式
#===========================
# 建立物件
e = Employee('001', '王小明', 'B')
print('編號:{}'.format(e.no))
print('姓名:{}'.format(e.name))
print('職等:{}'.format(e.rank))

# 以使用物件變數的方式, 取出薪水
print('薪水:{:,}元'.format(e.salary))
```


#### 1-3 執行結果
``` python
>> 編號:001
>> 姓名:王小明
>> 職等:B
>> 薪水:40,000元
```

