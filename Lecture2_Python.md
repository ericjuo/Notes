# Lecture 2. Python
課程時間:8-12小時


## 認識 Python

### 為什麼選擇 Python？

- 語法簡潔易讀
- 社群活躍，資源豐富
- 適合資料分析、人工智慧、網頁開發等領域

```
python
import this
```

### 安裝 Python


- 安裝建議：使用 Miniconda 及 VSCode + Python

---

## 基礎語法與變數

### Hello, World!

```python=
python
print("Hello, World!")
```

### 變數與型態

```
# String
name = "Eric"
# Integer
age = 33
# float
height = 1.75
# Boolean
is_student = True
```
### 內建函式
```
# 印出變數型態
print(type(age))
# 印出長度
print(len(name))
```
###   資料結構
```
# List
fruits = ["apple", "banana", "cherry"]
prices = [10, 12, 40]
weigts = [30.2, 41.9, 12.0]
# Tuple  //不可變的串列，用於不可修改的資料。
point = (3, 4)
# Set //不重複、無序的元素集合。
nums = {1, 2, 3, 3, 2}
# Dictionary 鍵值對（key-value）的資料結構。
person = {
    "name": "Eric",
    "age": 33,
    "city": "Tainan"
}
# Iterator //可以逐個取出元素的物件
nums = [10, 20, 30]
it = iter(nums)

print(next(it))  # 10
print(next(it))  # 20
print(next(it))  # 30


```
### 操作子
#### String
Slice
```
name = "Eric"
print(name[0])
# E
print(name[-1])
# c
```
Concatenate
```
description = name + " is " + str(age) + " years old"
print(description)
```
Multiply
```
print(name *3)
```
Split
```
fruits_csv = "apple,banana,cheery"
ls_fruits = fruits_csv.split(",")
print(ls_fruits)
```
Join
```
print(",".join(ls_fruits))
```

#### List
Slice
```
fruits = ["apple", "banana", "cherry"]
print(fruites[1])
# banana
```
Concatenate
```
new_fruits = fruits + ["mango"]
print(new_fruits)
```


Assign/Index
```
fruits[1]="peach"
print(fruits)
# ['apple', 'peach', 'cherry']
```
Multiply
```
print(fruits *3)
# ['apple', 'peach', 'cherry', 'apple', 'peach', 'cherry', 'apple', 'peach', 'cherry']
```

#### Tuple
Slice
```
point = (3, 4, 5)
print(point[1:])
#(4, 5)

print(point[::2])
#(3, 5)
```

### 條件判斷
if...else
```
score = 85

if score >= 60:
    print("及格")
else:
    print("不及格")

```
多重判斷

```
if score >= 90:
    print("優等")
elif score >= 75:
    print("中等")
else:
    print("需加強")
```

### 迴圈
while 迴圈
```
i = 1
while i <= 5:
    print(i)
    i += 1
```
for 迴圈
```
for i in range(5):
    print(i)
```
搭配條件與集合
```
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    if fruit.startswith("b"):
        print(fruit)
```
enumerate
```
fruits = ["apple", "banana", "cherry"]
for i, fruit in enumerate(fruits):
    print(f"第{i}種水果是{fruit}")
```
zip
```
fruits = ["apple", "banana", "cherry"]
prices = [10, 12, 40]
for price, fruit in zip(prices, fruits):
    print(f"{fruit}:${price}")
```
range
```
for i in range(3):
    print(i)
# 0
# 1
# 2

for i in range(3,5):
    print(i)
# 3
# 4

for i in range(3,8,2):
    print(i)
# 3
# 5
# 7

```
Comprehension
```
odds = [i for i in range(1,10,2)]
print(odds)
# [1, 3, 5, 7, 9]

odds = [i for i in range(1,10) if i%2==1]
print(odds)
```

### 函式
定義與呼叫函式
```
def greet(name):
    print(f"Hello, {name}!")

greet("Eric")
```
傳回值
```
def add(x, y):
    return x + y

result = add(3, 5)
print(result)
```
練習:fibonacci
```
# 0, 1, 1, 2, 3, 5, 8 ...
def fibonacci_list(n):
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[i-1] + fib[i-2])
    return fib[:n]
print(fibonacci_list(10))  
# [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]

```
練習:BMI計算機
```
BMI = 體重（公斤） / 身高（公尺）²
def bmi(weight, height):
    return weight/height**2

print(f"BMI:{bmi(65, 1.75):.2f}")
```
匿名函式(Lambda)
```
num = [1, 2, 3]
converted_num = map(lambda x: 2*x+1, num)
print(converted_num)

```
Coding style
```
from typing import List
def linear_conversion(num: List[int])-> List[int]:
    return list(map(lambda x: 2*x+1, num))
print(linear_conversion([1, 2, 3]))
# [3,5,7]
```
### 類別
建立模板
```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self):
        print(f"{self.name}：汪汪！")

# 建立物件
my_dog = Dog("Lucky")
my_dog.bark()
```

繼承
```python
class Animal:
    def speak(self):
        print("動物叫聲")

class Cat(Animal):
    def speak(self):
        print("喵喵！")

a = Animal()
a.speak()  # 動物叫聲

c = Cat()
c.speak()  # 喵喵！

```

## 檔案處理
```python
open("example.csv", "r") as f:
    content = f.read()
    print(content)
f.close() #使用open開啟檔案記得要close，不然會一直占用記憶體!!

# 或者可以用with來避免忘記關閉的情況:
with open("example.csv", "r") as f:
    content = f.readline()
    
```
`read()``— 一次讀取整個檔案（字串）

```python
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()
    print(content)
```
`readline()` — 一次讀一行（字串）
```python
with open("data.txt", "r", encoding="utf-8") as f:
    line1 = f.readline()
    line2 = f.readline()
    print(line1.strip())
    print(line2.strip())
```
`readlines()` — 一次讀所有行（回傳 list）
```python
with open("data.txt", "r", encoding="utf-8") as f:
    lines = f.readlines()
    print(lines)

```
使用迴圈處理
```python
with open("data.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip())
```
os.path.join(*paths)

```python=
DIR=/home/ncku3/JJJ/test
file_path = os.path.join(DIR, "info.txt")
print(file_path)  
```

## 檔案類型
#### CSV
```
apple,banana,pineapple

```

#### TSV
```
apple    banana    pineapple
```

#### json
```
{
  "name": "Alice",
  "age": 25,
  "is_student": false,
  "skills": ["Python", "C++"],
  "address": {
    "city": "Taipei",
    "zip": "100"
  }
}
```
## 編譯器(IDE)
-    Colab
-    Jupyter notebook
-    VScode

## 自訂套件
-    import
-    sys
-    argparse






## References
1. 精通Python: https://www.books.com.tw/products/0010858475?srsltid=AfmBOoobe8PVY4w_BAYBG9gzOvfVNL91kGz1nA04kOTEJAXdTYm2gY6e
2. https://www.w3schools.com/python/default.asp