# 第七大類 數組（Tuple）、集合（Set）以及詞典（Dictionary）
###### 內容簡要: 數組、集合、詞典的建立、運作及應用

## 701. 串列數組轉換
**題目設計要求:**  
輸入數個整數並儲存至串列中，以輸入-9999為結束點（串列中不包含-9999），再將此串列轉換成數組，最後顯示該數組以及其長度（Length）、最大值（Max）、最小值（Min）、總和（Sum）。
> **Example Input:`7`,`12`,`-7`,`-15`,`0`,`13`,`72`,`9`,`-9999`**  
> ```py
> N = []
> while(True): 
>     tmp = eval(input())
>     if(tmp == -9999):
>         break
>     N.append(tmp)
> N = tuple(N)
> print(N)
> print("Length: %d" % len(N)) #len(obj)計算物件長度
> print("Max: %d" % max(N)) 
> print("Min: %d" % min(N))
> print("Sum: %d" % sum(N))
> ```
>> **Example Output:**
>> ```
>> (7, 12, -7, -15, 0, 13, 72, 9)
>> Length: 8
>> Max: 72
>> Min: -15
>> Sum: 91
>> ```

## 702. 數組合併排序
**題目設計要求:**  
輸入並建立兩組數組，各以-9999為結束點（數組中不包含-9999）。將此兩數組合併並從小到大排序之，顯示排序前的數組和排序後的串列。
> **Example Input:`7`,`3`,`9`,`0`,`-2`,`-9999`;`42`,`33`,`76`,`-22`,`-9999`**  
> ```py
> t1, t2 = (), ()
> print("Create tuple1:")
> while(True):
>     tmp = eval(input())
>     if(tmp == -9999):
>         break
>     t1 += (tmp,) #tuple無法使用.append()函式
>
> print("Create tuple2:")
> while(True):
>     tmp = eval(input())
>     if(tmp == -9999):
>         break
>     t2 += (tmp,)
> print("Combined tuple before sorting:", t1+t2)
> print("Combined list after sorting:", sorted(t1+t2))
> ```
>> **Example Output:**
>> ```
>> Create tuple1:
>> Create tuple2:
>> Combined tuple before sorting: (7, 3, 9, 0, -2, 42, 33, 76, -22)
>> Combined list after sorting: [-22, -2, 0, 3, 7, 9, 33, 42, 76]
>> ```

## 703. 數組條件判斷
**題目設計要求:**  
輸入一些字串至數組（至少輸入五個字串），以字串"end"為結束點（數組中不包含字串"end"）。接著輸出該數組，再分別顯示該數組的第一個元素到第三個元素和倒數三個元素。
> **Example Input:`engineer`,`developer`,`technician`,`chairman`,`director`,`manager`,`assistant`,`end`**  
> ```py
> N = ()
> while(True):
>     tmp = input()
>     if(tmp == 'end'):
>         break
>     N += (tmp,)
> print(N)
> print(N[:3]) #印出0,1,2的元素
> print(N[len(N)-3:]) #印出(tuple長度-3)到最後一個元素
> ```
>> **Example Output:**
>> ```
>> ('engineer', 'developer', 'technician', 'chairman', 'director', 'manager', 'assistant')
>> ('engineer', 'developer', 'technician')
>> ('director', 'manager', 'assistant')
>> ```

## 704. 集合條件判斷
**題目設計要求:**  
輸入數個整數並儲存至集合，以輸入-9999為結束點（集合中不包含-9999），最後顯示該集合的長度（Length）、最大值（Max）、最小值（Min）、總和（Sum）。
> **Example Input:`72`,`44`,`-52`,`0`,`12`,`5`,`6`,`-9999`**  
> ```py
> N = set()
> while(True):
>     tmp = eval(input())
>     if(tmp == -9999):
>         break
>     N.add(tmp) #功能類似list的.append()
> print("Length:", len(N))
> print("Max:", max(N))
> print("Min:", min(N))
> print("Sum:", sum(N))
> ```
>> **Example Output:**
>> ```
>> Length: 7
>> Max: 72
>> Min: -52
>> Sum: 87
>> ```

## 705. 子集合與超集合
**題目設計要求:**  
依序輸入五個、三個、九個整數，並各自儲存到集合set1、set2、set3中。接著回答：set2是否為set1的子集合（subset）？set3是否為set1的超集合（superset）？  
**Tips. 依序分別輸入五個、三個、九個整數**
> **Example Input:`7`,`42`,`19`,`-8`,`0`;`-8`,`7`,`1`;`8`,`8`,`-8`,`0`,`66`,`42`,`77`,`19`,`48`**  
> ```py
> s1, s2, s3 = set(), set(), set()
> print("Input to set1:")
> for i in range(5):
>     s1.add(eval(input()))
>
> print("Input to set2:")
> for i in range(3):
>     s2.add(eval(input()))
>
> print("Input to set3:")
> for i in range(9):
>     s3.add(eval(input()))
> #判斷兩集合的內容是否與"較少的那個"樣本內容相同 較少的為較多的子集合 較多的為較少的超集合 條件會同時成立
> print("set2 is subset of set1:", s1 & s2 == s2)
> print("set3 is superset of set1:", s1 & s3 == s1)
> ```
>> **Example Output:**
>> ```
>> Input to set1:
>> Input to set2:
>> Input to set3:
>> set2 is subset of set1: False
>> set3 is superset of set1: True
>> ```

## 706. 全字母句
**題目設計要求:**  
全字母句（Pangram）是英文字母表所有的字母都出現至少一次（最好只出現一次）的句子。  
輸入一正整數k（代表有k筆測試資料），每一筆測試資料為一句子，程式判斷該句子是否為Pangram，並印出對應結果True（若是）或False（若不是）。  
**Tips. 不區分大小寫字母**
> **Example Input:`2`;`Bright vixens jump; dozy fowl quack`,`This sentence should return false`**  
> ```py
> def compute(): #使用函數撰寫 得出答案即跳出
>     user, word = input(), "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
>     for w in word:
>         if w not in user.upper(): #把輸入句子轉換大寫進行比對 如果有字母不在句子裡即回傳False
>             return False
>     return True
> 
> times = eval(input())
> for i in range(times):
>     print(compute())
> ```
>> **Example Output:**
>> ```
>> True
>> False
>> ```

## 707. 共同科目
**題目設計要求:**  
輸入X組和Y組各自的科目至集合中，以字串"end"作為結束點（集合中不包含字串"end"）。請依序分行顯示:  
1. X組和Y組的所有科目
2. X組和Y組的共同科目
3. Y組有但X組沒有的科目
4. X組和Y組彼此沒有的科目（不包含相同科目）  

**Tips. 輸出科目依字母由小至大進行排序**
> **Example Input:`Music`,`Math`,`English`,`History`,`Civics`,`end`;`History`,`Chemistry`,`Physics`,`Biology`,`Civics`,`end`**  
> ```py
> X, Y = set(), set()
> print("Enter group X's subjects:")
> while(True):
>     sub = input()
>     if(sub == 'end'):
>         break
>     X.add(sub)
> print("Enter group Y's subjects:")
> while(True):
>     sub = input()
>     if(sub == 'end'):
>         break
>     Y.add(sub)
> print(sorted(X | Y)) #聯集|  取出兩個集合中的所有元素,但不重複取出
> print(sorted(X & Y)) #交集&  取出兩個集合中共有的元素
> print(sorted(Y - X)) #差集-  從Y中減去和X重疊的部分
> print(sorted(X ^ Y)) #反交集^  取出兩個集合中不重疊的部分
> ```
>> **Example Output:**
>> ```
>> ['Biology', 'Chemistry', 'Civics', 'English', 'History', 'Math', 'Music', 'Physics']
>> ['Civics', 'History']
>> ['Biology', 'Chemistry', 'Physics']
>> ['Biology', 'Chemistry', 'English', 'Math', 'Music', 'Physics']
>> ```

## 708. 詞典合併
**題目設計要求:**  
自行輸入兩個詞典（以輸入鍵值"end"作為輸入結束點，詞典中將不包含鍵值"end"），將此兩詞典合併，並根據key值字母由小到大排序輸出，如有重複key值，後輸入的key值將覆蓋前一key值。  
**Tips. 重複輸入到key值為'end'時才跳出迴圈**
> **Example Input:`a`,`audi`,`b`,`benz`,`end`;`b`,`bmw`,`c`,`chevrolet`,`end`**  
> ```py
> dic1, dic2 = {}, {}
> print("Create dict1:")
> while(True):
>     KEY = input("Key: ")
>     if(KEY == 'end'):
>         break
>     dic1[KEY] = input("Value: ") #設定KEY值的value為輸入內容
> print("Create dict2:")
> while(True):
>     KEY = input("Key: ")
>     if(KEY == 'end'):
>         break
>     dic2[KEY] = input("Value: ")
> dic1.update(dic2) #將dic2的內容更新到dic1中
> for k in sorted(dic1.keys()): #把dic1的key值排序過後讀進迴圈
>     print("%s: %s" % (k, dic1[k])) #key值: value值(用key值去呼叫)
> ```
>> **Example Output:**
>> ```
>> Create dict1:
>> Key: **input in here**
>> Value: **input in here**
>> Create dict2:
>> Key: **input in here**
>> Value: **input in here**
>> a: audi
>> b: bmw
>> c: chevrolet
>> ```

## 709. 詞典排序
**題目設計要求:**  
輸入一顏色詞典color_dict（以輸入鍵值"end"作為輸入結束點，詞典中將不包含鍵值"end"），再根據key值的字母由小到大排序並輸出。
> **Example Input:`White`,`#FFFFFF`,`Blue`,`#0000FF`,`Yellow`,`#FFFF00`,`Midnight Blue`,`#003366`,`Dark Red`,`#8B0000`,`Lemon Green`,`#32CD32`,`end`**  
> ```py
> color_dict = {} #此題為708簡化版
> while(True):
>     KEY = input("Key: ")
>     if(KEY == 'end'):
>         break
>     color_dict[KEY] = input("Value: ")
> for k in sorted(color_dict.keys()):
>     print("%s: %s" % (k, color_dict[k]))
> ```
>> **Example Output:**
>> ```
>> Key: **input in here**
>> Value: **input in here**
>> Blue: #0000FF
>> Dark Red: #8B0000
>> Lemon Green: #32CD32
>> Midnight Blue: #003366
>> White: #FFFFFF
>> Yellow: #FFFF00
>> ```

## 710. 詞典搜尋
**題目設計要求:**  
為一詞典輸入資料（以輸入鍵值"end"作為輸入結束點，詞典中將不包含鍵值"end"），再輸入一鍵值並檢視此鍵值是否存在於該詞典中。
> **Example Input 1:`977-20-4083`,`Herry`,`001-22-3445`,`Terry`,`767-67-6777`,`Ray`,`end`,`767-67-6777`**   
> **Example Input 2:`1-32822-97`,`Mr`,`1-74779-00`,`Ms`,`end`,`2-90288-41`** 
> ```py
> dic = {}
> while(True):
>     KEY = input("Key: ")
>     if(KEY == 'end'):
>         break
>     dic[KEY] = input("Value: ")
> print(input("Search key: ") in dic) #印出輸入值是否在dic中的狀態
> ```
>> **Example Output 1:**
>> ```
>> Key: **input in here**
>> Value: **input in here**
>> Search key: **input in here**
>> True
>> ```
>> **Example Output 2:**
>> ```
>> Key: **input in here**
>> Value: **input in here**
>> Search key: **input in here**
>> False
>> ```
