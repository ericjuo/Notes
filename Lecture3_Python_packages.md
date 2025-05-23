# Lecture 3. Python packages
課程時間:4-6小時

## conda
conda是套件管理工具，同時也可以生成虛擬環境將不同程式隔離，避免軟體衝突

```
conda env list
conda activate <env>
conda install <package>
```

## numpy
NumPy（Numerical Python）是 Python 中用於 **高效數值運算** 的套件，主要功能包括：

- N 維陣列 `ndarray`
- 向量化運算（比 Python 內建迴圈快很多）
- 數學函式（如 sin、mean、dot 等）

```python
import numpy as np
a = np.array([1, 2, 3])
b = np.array([[1, 2], [3, 4]])
```
常用建立方式：
```python
np.zeros((2, 3))      # 全部是 0 的陣列
np.ones((3, 3))       # 全部是 1 的陣列
np.eye(3)             # 單位矩陣
np.arange(0, 10, 2)   # [0, 2, 4, 6, 8]
np.linspace(0, 1, 5)  # 等間距產生 5 個點

```
查看陣列屬性
```
a = np.array([[1, 2], [3, 4], [5, 6]])

a.shape      # (3, 2)
a.ndim       # 2
a.size       # 6
a.dtype      # int64
```
陣列運算
```
a = np.array([1, 2, 3])
b = np.array([10, 20, 30])

a + b        # array([11, 22, 33])
a * 2        # array([2, 4, 6])
a ** 2       # array([1, 4, 9])
np.sqrt(a)   # 開根號
np.sin(a)    # 三角函數
```
索引與切片
```python
a = np.array([[1, 2, 3], [4, 5, 6]])

a[0, 1]      # 取 0 行 1 列（值為 2）
a[:, 1]      # 所有列的第 1 欄 [2, 5]
a[1, :]      # 第 1 列所有欄 [4, 5, 6]
```
陣列操作
```
a.T                # 轉置
a.flatten()        # 攤平成 1D
```
常用統計函式
```
a = np.array([[1, 2], [3, 4]])

a.mean()           # 平均值
a.std()            # 標準差
```


## pandas
Pandas 是 Python 最常用的**資料處理與分析套件**，主要特點：

- 表格式資料操作（像 Excel 或資料庫）
- 支援 CSV、Excel、SQL、JSON 等格式
- 整合 NumPy 提供高效數值運算
- 廣泛應用於資料分析、機器學習前處理等領域

```python
import pandas as pd

```
#### 建立 Series（一維）
```python
s = pd.Series([10, 20, 30], index=["a", "b", "c"])
print(s)
```
#### 建立 DataFrame（表格）
```python
data = {
    "name": ["Alice", "Bob", "Charlie"],
    "age": [25, 30, 35],
    "score": [85, 90, 95]
}
df = pd.DataFrame(data)
print(df)
```
#### 讀取與儲存檔案
```python!
df = pd.read_csv("data.csv")
df.to_csv("output.csv", index=False)
pd.read_csv("data.tsv", delimiter=",")
pd.read_excel("data.xlsx")
pd.read_json("data.json")
```
#### 查看資料
```
df.head()         # 前 5 筆資料
df.tail(3)        # 最後 3 筆資料
df.shape          # (筆數, 欄位數)
df.columns        # 欄位名稱
df.info()         # 欄位摘要
df.describe()     # 數值欄位統計
```
#### 選取資料
```
df["name"]                  # 選一欄
df[["name", "age"]]         # 選多欄
df.iloc[0]                  # 第 0 列
df.loc[1, "score"]          # 第 1 列的 score 欄
df[df["age"] > 30]          # 篩選 age > 30
```

#### 合併資料

```
pd.concat([df1, df2])              # 垂直合併
pd.merge(df1, df2, on="id")        # 根據 id 合併
```

#### 排序與重設索引
```python
df.sort_values(by="score", ascending=False)
df.reset_index(drop=True)
```

#### apply
```python
s = pd.Series([1, 2, 3, 4])

# 將每個元素平方
s_squared = s.apply(lambda x: x ** 2)
print(s_squared)
```


## Matplotlib
Matplotlib 是 Python 中最常用的 2D 繪圖工具，功能強大且彈性高，主要模組為 `pyplot`

```python
import matplotlib.pyplot as plt

```

#### 繪製折線圖（Line Plot）
```python
x = [1, 2, 3, 4]
y = [10, 20, 25, 30]

plt.plot(x, y)
plt.title("Line Plot 範例")
plt.xlabel("X 軸")
plt.ylabel("Y 軸")
plt.show()

```
#### 長條圖（Bar Chart）
```python
x = ["A", "B", "C", "D"]
y = [3, 7, 1, 5]

plt.bar(x, y)
plt.title("Bar Chart 範例")
plt.show()

```
#### 散點圖（Scatter Plot）
```python
x = [1, 2, 3, 4, 5]
y = [5, 7, 6, 8, 7]

plt.scatter(x, y)
plt.title("Scatter Plot")
plt.show()
```

#### 直方圖（Histogram）
```python
import numpy as np

data = np.random.randn(1000)
plt.hist(data, bins=30, color="skyblue", edgecolor="black")
plt.title("Histogram 範例")
plt.show()
```

#### 自訂圖表樣式
```python
plt.plot(x, y, color="green", linestyle="--", marker="o")
plt.grid(True)
```
- 顏色：'red', 'blue', 'green', '#FF00FF'
- 樣式：'-', '--', ':', '-.'
- 標記：'o', 's', '^', '*'

#### 顯示圖例（Legend）
```python!
plt.plot(x, y, label="實驗數據")
plt.legend()
plt.show()
```

#### 儲存圖片
```
plt.savefig("plot.png", dpi=300)
```

#### 繪製子圖
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = np.sin(x)

fig, ax = plt.subplots()   # 建立一個 Figure 和一個 Axes
ax.plot(x, y)
ax.set_title("單一子圖")
ax.set_xlabel("X 軸")
ax.set_ylabel("Y 軸")

plt.show()
```
#### plt.subplots() 參數
```python
fig, axs = plt.subplots(nrows=2, ncols=2, figsize=(8, 6))
```
#### 畫多個子圖範例

```python
fig, axs = plt.subplots(2, 2, figsize=(10, 8))

x = np.linspace(0, 2 * np.pi, 100)

axs[0, 0].plot(x, np.sin(x))
axs[0, 0].set_title("sin(x)")

axs[0, 1].plot(x, np.cos(x), 'r--')
axs[0, 1].set_title("cos(x)")

axs[1, 0].plot(x, np.tan(x), 'g:')
axs[1, 0].set_title("tan(x)")
axs[1, 0].set_ylim(-10, 10)  # 限制 Y 軸範圍避免過大

axs[1, 1].plot(x, np.log1p(x), 'm-.')
axs[1, 1].set_title("log(1+x)")

fig.tight_layout()  # 自動調整子圖間距
plt.show()
```


## Seaborn
Seaborn 是基於 Matplotlib 之上的 Python 資料視覺化套件，專注於統計圖表，提供更簡潔、漂亮且易用的繪圖介面。
- 預設美觀風格，圖表好看
- 方便做統計類圖表（分布圖、箱型圖、熱力圖…）
- 與 Pandas 資料結構整合良好
- 支援複雜的多變量資料視覺化


```python=
import seaborn as sns
import matplotlib.pyplot as plt
```
Seaborn 範例資料集
```python
tips = sns.load_dataset("tips")
print(tips.head())

```
### 散佈圖（Scatter Plot）
```python
sns.scatterplot(data=tips, x="total_bill", y="tip", hue="sex")
plt.title("Scatter Plot")
plt.show()
```


## Biopython
Biopython 是一個用 Python 撰寫的生物資訊學函式庫，提供多種方便的工具來處理 DNA、RNA、蛋白質序列，進行序列比對、讀寫生物資料格式、操作生物分子結構等。

#### 建立與操作序列
```python
from Bio.Seq import Seq
dna_seq = Seq("ATGCGTACGTA")
print("序列長度:", len(dna_seq))
print("反向互補:", dna_seq.reverse_complement())
print("轉譯蛋白質序列:", dna_seq.translate())
```

#### 讀取 FASTA 檔案

```python
from Bio import SeqIO

for record in SeqIO.parse("example.fasta", "fasta"):
    print(record.id)
    print(record.seq)
```

#### 從 NCBI 下載序列

```python
from Bio import Entrez, SeqIO

Entrez.email = "your.email@example.com"
handle = Entrez.efetch(db="nucleotide", id="NM_000558", rettype="fasta", retmode="text")
record = SeqIO.read(handle, "fasta")
handle.close()

print(record.id)
print(record.description)
print(record.seq)

```

## re
正規表達式（Regular Expression）是一種字串模式語法，能用來查找、比對、取代特定文字模式，常用於：


```python 

import re
```
### 常用函式
```python
text = "Email: user123@example.com"
match = re.search(r"\w+@\w+\.\w+", text)
if match:
    print(match.group())

```
群組與命名群組

```python
text = "電話：02-12345678"
match = re.search(r"(\d{2})-(\d+)", text)
if match:
    area_code = match.group(1)
    number = match.group(2)
    print("區碼:", area_code, "號碼:", number)

```




###    References
1. https://matplotlib.org/stable/gallery/
2. https://seaborn.pydata.org/examples/index.html
3. https://pandas.pydata.org/docs/user_guide/index.html#user-guide