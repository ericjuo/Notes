# PyMol
課程時間:2小時
## 基本操作
-    style
-    color
-    label
-    rename
-    drag
-    transparency
-    grid_mode
-    align   

## 什麼是 PyMOL？

PyMOL 是一個強大的分子可視化軟體，廣泛用於蛋白質結構分析與展示，支援腳本控制與高品質圖像輸出。

---

## 基本操作
### Style
```
show cartoon
show sticks
show surface
```

### Color
```
color red, resi 50
```

### Selection
```
select active_site, resi 145+146+147
show sticks, active_site
```

### Align
`align` 是 PyMOL 用來**結構比對（superposition）**的指令，能將兩個蛋白質結構進行序列對齊與三維結構比對。
```
align mobile, target
```
Pymol會同時計算完成比對後，兩結構的差異程度(RMSD)

### RMSD
計算「不對齊」的 RMSD (僅計算 RMSD，不進行位置或旋轉對齊。)
```
rms mobile, target
```
### Grid
grid_mode 會將每個物件（object）在視窗中分開顯示，方便同時觀看多個蛋白質的外觀。

```
# 開啟grid_mode
set grid_mode, 1
# 關閉grid_mode
set grid_mode, 0
```
grid_slot可以指定蛋白質要放在哪格:
```
set grid_slot, 1, protein_A
set grid_slot, 1, protein_B
set grid_slot, 2, protein_C
set grid_slot, 2, protein_D
set grid_slot, -2, protein_E
```
### View
`view`可以儲存目前的觀察角度，並且可以重新叫回觀察角度
```
view 0,store
view 0
```

### Rotate
`rotate`可以依照指定軸旋轉
```
rotate x, 180, protein
rotate y, 180, protein
rotate z, 180, protein
```

## show_contacts.py
### 1. 匯入此插件腳本
從Plugin分頁開啟Plugin Manager，點擊Install New Plugin後，點選Choose file，選擇show_contacts.py進行安裝。

### 2. 使用` contacts `指令

```
contacts chain A, chain B, result="contacts", cutoff=3.6, bigcutoff=4.0
```
支援的參數說明：
- cutoff=3.6: 極性接觸的距離閾值（Å）

- bigcutoff=4.0: 包含次理想接觸的更大閾值

- result="contacts": 結果名稱前綴（用於分組與物件命名）

### 📊 這個插件會產生哪些結果？
它會產生以下 PyMOL 距離物件：


| 名稱| 含義 |顏色/樣式 |
| -------- | -------- | -------- |
| contacts_polar    | 理想極性接觸    | dash, 粗線條     |
|contacts_polar_ok	|次理想極性接觸	|dash, 細線條|
|contacts_all	|所有 N/O 原子的接觸|	紫色 dash|
|contacts_dd|	donor-donor 衝突	|紅色 dash|
|contacts_aa	|acceptor-acceptor |衝突	紅色 dash|

這些結果會被自動放進一個` contacts` 的群組中。

### 選擇contacts之間的殘基
```
select [selection name], byres(chain A within 4 of chain B) or byres(chain B within 4 of chain A)
```

## 輸出圖檔
-    ray

## Python介面

## 套件
### color_h
胺基酸疏水程度是根據這個網站的值上色:

Source: http://us.expasy.org/tools/pscale/Hphob.Eisenberg.html
值越高，越疏水，顏色越紅。
```
color_h
show surface
```


### References
1. https://pymolwiki.org/index.php/Color_h
2. http://sts.bioe.uic.edu/castp/plugin.html
3. https://pymolwiki.org/index.php/Category:Commands