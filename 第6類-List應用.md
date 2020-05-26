# 第六大類 串列(List)的運作(一維、二維以及多維)
###### 內容簡要: 串列的建立、串列的函式、串列參數傳遞、串列應用

## 601. 偶數索引值加總
**題目設計要求:**  
利用一維串列存放使用者輸入的12個正整數（範圍1~99）。顯示這些數字，接著將串列索引為偶數的數字相加並輸出結果。  
**Tips. 輸出每一個數字欄寬設定為3，每3個一列，靠右對齊**
> **Example Input:`12`,`75`,`23`,`45`,`76`,`19`,`92`,`24`,`75`,`62`,`11`,`66`**  
> ```py
> N, sum = [], 0
> for i in range(12):
>     N.append(eval(input()))
>     if(i % 2 == 0): #如果輸入到2倍數的次數時進行加總
>         sum += N[i]
> for i in range(12):
>     print("%3d" % N[i], end="")
>     if((i+1) % 3 == 0): #如果輸出到三的倍數就換行
>         print()
> print(sum)
> ```
>> **Example Output:**
>> ```
>>  12 75 23
>>  45 76 19
>>  92 24 75
>>  62 11 66
>> 289
>> ```

## 602. 撲克牌總和
**題目設計要求:**  
輸入52張牌中的5張，計算並輸出其總和。  
**Tips. J、Q、K以及A分別代表11、12、13以及1**
> **Example Input:`J`,`K`,`7`,`8`,`9`**  
> ```py
> poke={'J':'11','Q':'12','K':'13','A':'1'} #這邊解題方法使用後面大類會用到的字典較簡潔 也可使用if多重判斷
> sum=0
> for i in range(5):
>     tmp=input()
>     if tmp in poke: #搜尋輸入內容是否存在字典當中
>         sum+=eval(poke[tmp]) 
>     else:
>         sum+=eval(tmp)
> print(sum)
> ```
>> **Example Output:**
>> ```
>> 48
>> ```

## 603. 數字排序
**題目設計要求:**  
輸入十個數字並存放在串列中。接著由大到小的順序顯示最大的3個數字。
> **Example Input:`11`,`23`,`97`,`45`,`67`,`87`,`34`,`77`,`69`,`40`**  
> ```py
> N = []
> for i in range(10):
>     N.append(eval(input()))
> N.sort(reverse=True) #.sort依照小到大排序(這邊使用降冪->大到小)
> print(N[0], N[1], N[2])
> ```
>> **Example Output:**
>> ```
>> 97 87 77
>> ```

## 604. 眾數
**題目設計要求:**  
輸入十個整數作為樣本數，輸出眾數（樣本中出現最多次的數字）及其出現的次數。  
**Tips. 假設樣本中只有一個眾數**
> **Example Input:`74`,`21`,`56`,`82`,`43`,`74`,`63`,`95`,`74`,`11`**  
> ```py
> N, times = [], [] #times記錄每個數字出現次數
> for i in range(10):
>     N.append(eval(input()))
>     times.append(N.count(N[i])) #紀錄輸入字元的出現次數至times內
> print(N[times.index(max(times))]) #將N套用索引time當中出現次數最高的數字
> print(max(times))
> ```
>> **Example Output:**
>> ```
>> 74
>> 3
>> ```

## 605. 成績計算
**題目設計要求:**  
輸入十個成績，接下來將十個成績中最小和最大值（最小、最大值不重複）以外的成績作加總及平均，並輸出結果。  
**Tips. 平均值輸出到小數點後第二位**
> **Example Input:`98`,`72`,`67`,`86`,`89`,`92`,`87`,`77`,`93`,`69`**  
> ```py
> score = []
> for i in range(10):
>     score.append(eval(input()))
> score.remove(max(score)) #從list中刪除最大數
> score.remove(min(score)) #從list中刪除最小數
> print(sum(score))
> print("%.2f" % (sum(score)/8))
> ```
>> **Example Output:**
>> ```
>> 665
>> 83.12
>> ```

## 606. 二維串列行列數
**題目設計要求:**  
輸入兩個正整數rows、cols，分別表示二維串列lst 的「第一個維度大小」與「第二個維度大小」。  
串列元素\[row]\[col]所儲存的數字，其規則為：row、col 的交點值 = 第二個維度的索引col – 第一個維度的索引row。
接著以該串列作為參數呼叫函式compute()輸出串列。
**Tips. 欄寬為4**
> **Example Input:`4`,`7`**  
> ```py
> def compute(rows, cols):
>     for i in range(rows):
>         for j in range(cols):
>             print("%4d" % (j-i), end="")
>         print()
>         
> compute(eval(input()), eval(input()))
> ```
>> **Example Output:**
>> ```
>>    0   1   2   3   4   5   6
>>   -1   0   1   2   3   4   5
>>   -2  -1   0   1   2   3   4
>>   -3  -2  -1   0   1   2   3
>> ```

## 607. 成績計算
**題目設計要求:**  
輸入三位學生各五筆成績，接著再計算並輸出每位學生的總分及平均分數。  
**Tips. 平均分數輸出到小數點後第二位**  
**Tips. 先顯示學生順序後輸入(輸出:*The 1st student:* 然後輸入資料,依序進行)**
> **Example Input:`97`,`64`,`85`,`94`,`72`;`65`,`91`,`90`,`85`,`82`;`99`,`74`,`85`,`67`,`99`**  
> ```py
> info = ["The 1st student:", "The 2nd student:", "The 3rd student:"]
> score = [[], [], []] #建立儲存三個學生資料的維度
> for i in range(3):
>     print(info[i])
>     for j in range(5):
>         score[i].append(eval(input()))
> for i in range(3):
>     print("Student %d" % (i+1))
>     print("#Sum %d" % sum(score[i]))
>     print("#Average %.2f" % (sum(score[i])/5))
> ```
>> **Example Output:**
>> ```
>> The 1st student: *input in here*
>> The 2nd student: *input in here*
>> The 3rd student: *input in here*
>> Student 1
>> #Sum 412
>> #Average 82.40
>> Student 2
>> #Sum 413
>> #Average 82.60
>> Student 3
>> #Sum 424
>> #Average 84.80
>> ```

## 608. 最大最小值索引
**題目設計要求:**  
建立一個3*3的矩陣，其內容為從鍵盤輸入的整數（不重複），接著輸出矩陣最大值與最小值的索引。
> **Example Input:`11`,`32`,`77`,`46` ,`29`,`61`,`59`,`-9`,`42`**  
> ```py
> N = []
> for i in range(9):
>     N.append(eval(input()))
> largest = N.index(max(N))
> smallest = N.index(min(N))
> print("Index of the largest number %d is: (%d, %d)" %
>       (max(N), largest//3, largest % 3))
> print("Index of the smallest number %d is: (%d, %d)" %
>       (min(N), smallest//3, smallest % 3))
> ```
>> **Example Output:**
>> ```
>> Index of the largest number 77 is: (0, 2)
>> Index of the smallest number -9 is: (2, 1)
>> ```

## 609. 矩陣相加
**題目設計要求:**  
建立兩個2*2的矩陣，其內容為從鍵盤輸入的整數，接著輸出這兩個矩陣的內容以及它們相加的結果。  
**Tips. 注意輸出格式**  
**Tips. 先顯示當前矩陣後輸入(輸出:[1, 2]: 然後輸入資料,依序進行)**
> **Example Input:`1`,`3`,`6`,`6`;`9`,`0`,`2`,`8`**  
> ```py
> m1 = [0, 0], [0, 0]
> m2 = [0, 0], [0, 0]
> #這題看懂輸出邏輯比較重要 說明太簡扼
> print("Enter matrix 1:")
> for i in range(2):
>       for j in range(2):
>             m1[i][j] = eval(input("[%d, %d]: "%(i+1,j+1)))
> 
> print("Enter matrix 2:")
> for i in range(2):
>       for j in range(2):
>             m2[i][j] = eval(input("[%d, %d]: "%(i+1,j+1)))
> 
> print("Matrix 1:")
> for i in range(2):
>       for j in range(2):
>             print(m1[i][j], end=" ")
>       print()
> print("Matrix 2:")
> for i in range(2):
>       for j in range(2):
>             print(m2[i][j], end=" ")
>       print()
> print("Sum of 2 matrices:")
> for i in range(2):
>       for j in range(2):
>             print(m1[i][j]+m2[i][j], end=" ")
>       print()
> ```
>> **Example Output:**
>> ```
>> Enter matrix 1:
>> [1, 1]: *input in here*
>> [1, 2]: *input in here*
>> [2, 1]: *input in here*
>> [2, 2]: *input in here*
>> Enter matrix 2:
>> [1, 1]: *input in here*
>> [1, 2]: *input in here*
>> [2, 1]: *input in here*
>> [2, 2]: *input in here*
>> Matrix 1:
>> 1 3 
>> 6 6 
>> Matrix 2:
>> 9 0 
>> 2 8 
>> Sum of 2 matrices:
>> 10 3 
>> 8 14 
>> ```

## 610. 平均溫度
**題目設計要求:**  
輸入四週各三天的溫度，接著計算並輸出這四週的平均溫度及最高、最低溫度。  
**Tips. 平均溫度輸出到小數點後第二位**  
**Tips. 最高溫度及最低溫度的輸出，如為31時，則輸出31，如為31.1時，則輸出31.1**  
**Tips. 先顯示當前天數後輸入(輸出:Day 1: 然後輸入資料,依序進行)**  
> **Example Input:`29`,`28.4`,`27.7`;`29.8`,`29`,`30`;`32.1`,`34`,`33.3`;`35.10`,`30`,`28`**  
> ```py
> temperature = [] #這題用一維陣列來做就夠了
> for i in range(4):
>     print("Week %d:" % (i+1))
>     for j in range(3):
>         temperature.append(eval(input("Day %d:" % (j+1))))
> print("Average: %.2f" % (sum(temperature)/12))
> print("Highest: %g" % max(temperature)) #%g輸出可以忽視結尾0的小數點
> print("Lowest: %g" % min(temperature))
> ```
>> **Example Output:**
>> ```
>> Week 1:
>> Day 1: *input in here*
>> Day 2: *input in here*
>> Day 3: *input in here*
>> Week 2:
>> Day 1: *input in here*
>> Day 2: *input in here*
>> Day 3: *input in here*
>> Week 3:
>> Day 1: *input in here*
>> Day 2: *input in here*
>> Day 3: *input in here*
>> Week 4:
>> Day 1: *input in here*
>> Day 2: *input in here*
>> Day 3: *input in here*
>> Average: 30.53
>> Highest: 35.1
>> Lowest: 27.7
>> ```
