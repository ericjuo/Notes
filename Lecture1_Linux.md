# Lecture 1. Linux
課程時間: 4小時


# 🐧 Linux 基礎操作入門
---

## 什麼是 Linux？

Linux 是一個自由開源的作業系統，廣泛應用於伺服器、超級電腦、嵌入式裝置等。常見的發行版本有：

- Ubuntu
- Debian
- CentOS / RHEL
- Arch Linux

---

## 終端機與指令列

在 Linux 中，我們透過「終端機」輸入文字指令來與系統互動。

```bash
$ 這是提示字元，代表你可以開始輸入指令
```

---

## 常用指令

### `pwd`：顯示目前所在的路徑
```bash
$ pwd
/home/user
```

### `ls`：列出目錄內容
```bash
$ ls
file1.txt  folder1  script.sh
```

加上參數 `-l` 可顯示詳細資訊(long information)：
```bash
$ ls -l
```

### `cd`：切換目錄
```bash
$ cd folder1
```

回到上層目錄：
```bash
$ cd ..
```

回到使用者主目錄：
```bash
$ cd ~
```
### `touch`：建立檔案
```
touch file.txt
```

### `mkdir`：建立新資料夾
```bash
$ mkdir new_folder
```
加上參數 `-p`，可以在路徑上缺少資料夾時自動建立，這對於建立子資料夾非常有用，例如:
```
$ mkdir -p data/raw data/processed data/result
```
可以一次生成三個子資料夾，同時自動建立data這個母資料夾。
### `cp`：複製檔案或資料夾
```bash
$ cp file1.txt backup.txt
$ cp -r folder1 folder2
```
加上參數 `-r`，可以用來複製資料夾及資料夾底下的內容。
### `mv`：移動或重新命名
```bash
$ mv file.txt new_folder/
$ mv oldname.txt newname.txt
```

### `rm`：刪除檔案或資料夾
```bash
$ rm file.txt
$ rm -r folder1
```
加上參數 `-r`，可以刪除資料夾和底下的內容。
### `cat`, `less`：顯示檔案內容
```bash
$ cat file.txt
$ less file.txt
```
`cat`會將file.txt檔案中的內容讀進記憶體並全部印在終端機，如果目標檔案很大的時候不建議使用，因為記憶體耗盡會使電腦當機。

`less`以批次讀入記憶體，每次只提供一小部分的內容，對電腦負擔比較小，建議使用!


### `head`：檢視檔案前頭資料
```
$ head file.txt
```
常用在csv及tsv檔，用來了解檔案的表頭進行資料表處理。同樣不會耗用大量記憶體，可以安全使用。

### `grep`：文字搜尋工具
grep 是一個非常強大的文字搜尋工具，用來在檔案或輸出中尋找符合特定字串或正規表達式的行。
```
$ grep "hello" file.txt
```
加上參數 `-i`，可以忽略字詞大小寫。搜尋 `hello`、`Hello`、`HELLO` 等不區分大小寫的字串。
```
$ grep -i "hello" file.txt
```
顯示行號（-n）：
```
$ grep -n "error" logfile.txt
```

使用正規表達式（-E）：
```
$ grep -E "cat|dog" pets.txt
```
排除結果（-v），顯示不包含 `DEBUG` 的行。：
```
$ grep -v "DEBUG" logfile.txt
```
如果想知道某個字串在檔案中出現了幾次，可以使用：

```bash
grep -o "字串" 檔案名稱 | wc -l
```

#### 範例：
```bash
echo "apple banana apple orange apple" | grep -o "apple" | wc -l
```

輸出：
```
3
```

這表示 `apple` 出現了三次。


---

## 檔案與目錄權限

使用 `ls -l` 可看到權限欄位，例如：
```
-rw-r--r--  1 user group  1234 Apr 25 12:00 file.txt
```

- `r`：讀取權限
- `w`：寫入權限
- `x`：執行權限

修改權限：
```bash
$ chmod +x script.sh     # 加上執行權限
$ chmod 755 script.sh    # 使用數字設定權限
```

---

## 使用者與群組管理

建立使用者（需 root 權限）：
```bash
$ sudo adduser newuser
```

切換使用者：
```bash
$ su - newuser
```

---

## 套件安裝

以 Ubuntu 為例：

更新套件清單：
```bash
$ sudo apt update
```

安裝套件：
```bash
$ sudo apt install vim
```
:::danger
千萬!拜託!不要用以下指令:
```
sudo apt upgrade
```
這個指令會升級内核，高機率讓已經安裝的軟體無法使用，就像升級Windows一樣，新版的作業系統不相容舊版程式。
:::

---

## 簡易 Shell Script 範例

建立檔案 `hello.sh`：
```bash
#!/bin/bash
echo "Hello, Linux!"
```

給予執行權限並執行：
```bash
$ chmod +x hello.sh
$ ./hello.sh
```

平常使用的腳本可以直接用bash指令執行即可:
```bash
$ bash ./hello.sh
```

## Bash Script基礎教學
### 🔧 set — 設定 Shell 行為
set 可控制 shell 的行為，常見選項如下：
```bash=
set -e  # 如果任一指令失敗，立即結束 script
set -u  # 使用未定義的變數會報錯
set -x  # 顯示執行過程中每一行指令（除錯用）

```
### 📦 變數（Variables）
Bash 指定變數時不需要加 $，但在引用時要加 $。
```bash
name="Alice"
echo "Hello, $name"
```
🔁 變數可以與命令結合：
```bash
today=$(date +%Y-%m-%d)
echo "今天是 $today"
```
### 🔗 管線（Pipe）
管線（|）將前一個指令的輸出作為下一個指令的輸入：
```bash
cat file.txt | grep "error"
```
### 🔀 if/else 條件判斷
```bash=
#!/bin/bash

x=5

if [ $x -gt 3 ]; then
    echo "x 大於 3"
else
    echo "x 小於或等於 3"
fi
```

### 🔁 `for` 迴圈
```bash
for i in 1 2 3; do
    echo "第 $i 次"
done
```

### 📥 `tee` — 同時輸出到螢幕與檔案
這個功能可以將stdout寫到檔案中，同時維持顯示stdout在terminal
```bash
echo "Hello" | tee output.txt

```

## 壓縮及解壓縮
Linux 系統中常見的壓縮與解壓縮工具包括 tar 和 unzip。以下介紹它們的基本用法與常見範例。

### 🗜️ tar — 打包與解壓縮 .tar, .tar.gz, .tgz 檔案
```bash
# 解壓縮 .tar.gz 或 .tgz 檔案
tar -xzvf file.tar.gz

# 解壓縮 .tar 檔案
tar -xvf file.tar
```
說明:
`-x`: 解壓縮
`-z`: 使用`gzip`格式
`-v`: verbose模式
`-f`: 指定要被解壓縮的檔案名稱

#### 📁 解壓縮到指定資料夾
```bash
tar -xzvf file.tar.gz -C /path/to/folder
```
#### 🔹 建立壓縮檔（反向操作）
```bash
tar -czvf archive.tar.gz folder/
```

### 📂 unzip — 解壓縮 .zip 檔案
```bash
unzip file.zip
```
#### 📁 解壓縮到指定資料夾
```bash
unzip file.zip -d /path/to/folder
```

#### 🚫 如果檔案已存在，不覆蓋
```bash
unzip -n file.zip
```


## 資源監控
在進行系統維運或效能監控時，了解 CPU、記憶體與 GPU 使用情況是非常重要的。這裡介紹兩個常用的監控工具：

`top`：監控 CPU 和記憶體資源

`nvtop`：監控 NVIDIA GPU 使用狀況

### 🧠 `top` — 監控 CPU 與記憶體使用情況
#### 🔹 執行方式
```
top
```

### 🎮 `nvtop` — NVIDIA GPU 實時監控工具
nvtop 是針對 NVIDIA GPU 的類似 top 的工具，可即時查看 GPU 使用率、溫度、記憶體、執行程序等資訊。
#### 🔹 執行方式
```
nvtop
```


## 軟體安裝
Linux 系統中常見的套件管理與說明文件工具包括：

- `apt-get`：經典的 Debian/Ubuntu 套件管理工具

- `apt`：較新的簡化介面（整合 apt-get、apt-cache 等）

- `man`：查看指令的說明手冊（manual）

### `apt-get` — 傳統軟體安裝/管理工具
#### 🔹 常見用法
```bash
sudo apt-get update        # 更新套件清單
sudo apt-get install vim   # 安裝 vim
sudo apt-get remove vim    # 移除 vim（保留設定檔）
sudo apt-get purge vim     # 完全移除 vim（含設定檔）
```

### `apt` 
`apt` 整合了 `apt-get`, `apt-cache`, `dpkg` 等工具的功能，界面簡潔，適合在終端機直接操作。

#### 🔹 常見用法

```bash
sudo apt update            # 更新套件清單
sudo apt install git       # 安裝 git
sudo apt remove git        # 移除 git
apt list --installed       # 列出已安裝的套件
apt search python          # 搜尋套件名稱含 "python"
```

### 📖 `man` — 指令說明文件（manual）
`man` 是 Linux 提供的內建說明系統，可查詢幾乎所有系統指令與函式庫的使用方式。
#### 🔹 使用方式
```bash
man ls         # 查詢 ls 指令的手冊
man apt        # 查詢 apt 的使用說明
man 5 passwd   # 查詢 passwd 的格式說明（章節 5）
```



## `tmux` 終端機管理程式
`tmux` 是一個功能強大的終端機多工器，可讓你在一個終端視窗中同時操作多個視窗、面板，並支援背景執行與**斷線重連**，非常適合遠端作業與多工作流程的管理。

### 🧑‍💻 基本指令 (terminal)
```bash
tmux                 # 啟動 tmux（預設新建一個 session）
tmux new -s myname   # 建立一個名為 myname 的 session
tmux ls              # 查看目前所有 session
tmux attach -t myname # 連回名為 myname 的 session
tmux kill-session -t myname # 關閉指定 session
```
### 🧑‍ 操作指令 (tmux內)
#### 常用快捷鍵（預設前綴為 Ctrl + b）


| 動作 | 	快捷鍵 | 
| -------- | -------- |
| 顯示命令列    | `Ctrl + b` 然後 `:`   | 
|分割為上下面板|`Ctrl + b` 然後 `%`|
|分割為左右面板|`Ctrl + b` 然後 `"`|
|在面板之間切換|`Ctrl + b` 然後方向鍵|
|關閉當前面板|`Ctrl + d`|
|新建視窗|`Ctrl + b` 然後 `c`|
|切換視窗（下/上）|`Ctrl + b` 然後 `n` / `p`|
|重命名視窗|`Ctrl + b` 然後 `,`|
|查看所有視窗與面板|`Ctrl + b` 然後 `w`|
|離開 tmux（不中斷工作）|`Ctrl + b` 然後 `d`|


## 遠端連線

###  🔐 SSH 使用教學：遠端安全連線與管理工具
SSH（Secure Shell）是 Linux 和類 Unix 系統中最常用的遠端連線工具，它可透過加密連線，安全地操作遠端伺服器，並支援檔案傳輸、連線轉送、金鑰認證等功能。

#### 🔑 使用 SSH 金鑰驗證（取代密碼登入）
1. 產生金鑰
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
- 預設會產生：
    - 私鑰：~/.ssh/id_rsa
    - 公鑰：~/.ssh/id_rsa.pub

2. 將公鑰上傳至遠端伺服器

```
ssh-copy-id username@remote_host
```
成功後即可使用金鑰登入，無需密碼。

#### 🚀 基本使用
```
ssh username@remote_host
```
#### SSH連線建議軟體
-    VScode
-    MobaXterm

#### `SCP`：用 SSH 傳送檔案
```
# 將本機檔案傳送到遠端
scp file.txt username@remote_host:/path/to/destination

# 將遠端檔案傳送到本機
scp username@remote_host:/path/to/file.txt .
```

#### `rsync`: 高效檔案同步工具
`rsync` 是 Linux 中用於「同步備份」與「資料傳輸」的強大工具，支援本地與遠端傳輸、增量同步、壓縮、保留權限等功能。

##### 🚀 基本語法
```bash=
rsync [options] source destination
```
範例：

```
# 本地同步資料夾
rsync -av ~/project/ /backup/project/

# 傳送檔案到遠端主機
rsync -avz ~/data/ user@remote:/home/user/data/

# 從遠端拉回資料
rsync -avz user@remote:/home/user/data/ ./data/
```

##### 🧰 常見選項說明



| 選項 | 	說明 | 
| -------- | -------- | 
| Text     | Text     | 
|`-a`|保留權限、時間戳、符號連結（archive 模式）|
|`-v`|顯示過程（verbose）|
|`-z`|傳輸時壓縮資料，適合遠端同步|
|`-P`|顯示進度條 + 支援中斷續傳（等同 `--partial` `--progress`）|
|`--delete`|刪除目標中多餘的檔案（保持一致）|

### 💡 小技巧
結尾的斜線有差異：
```bash
rsync -av dir1/ dir2/   # 將 dir1 內容同步到 dir2
rsync -av dir1  dir2/   # 將 dir1 整個目錄放進 dir2 下
```

## Slurm 使用教學

Slurm（Simple Linux Utility for Resource Management）是一套廣泛使用於高效能運算叢集（HPC）的作業排程系統。以下是常見的 Slurm 基本用法教學。

---


## 1. Slurm 簡介

Slurm 是一個開源的作業排程與資源管理系統，常用於提交與管理 HPC 作業。使用者通常透過 Job Script 指定資源需求、執行指令等。

---

## 2. 基本指令

| 指令       | 說明 |
|------------|------|
| `sinfo`    | 查看叢集節點狀態 |
| `squeue`   | 查詢目前排隊與執行中的作業 |
| `sbatch`   | 提交作業腳本 |
| `scancel`  | 取消作業 |
| `sacct`    | 查詢作業完成後的記錄與資源使用情況 |

---

## 3. Job Script 撰寫

### 3.1 轉寫slurm腳本
檔案名稱job_script.sh

```bash
#!/bin/bash
#SBATCH --job-name=test_gpu_job   # Job名稱，影響squeue或sacct看到的名稱
#SBATCH --output=gpu_output_%j.log # 將stdout寫入log檔案方便之後除錯用，%j為提交後的Job id
#SBATCH --error=gpu_error_%j.log # 將stderr寫入log檔案方便之後除錯用，%j為提交後的Job id
#SBATCH --ntasks=4                # 並行計算任務數，通常和--cpus-per-task一起設定
#SBATCH --cpus-per-task=8         # 每個task用8個threads計算  
#SBATCH --gres=gpu:1              # 要求 1 顆 GPU
#SBATCH --mem=64G                 # 限制記憶體使用量
#SBATCH --time=5-06:30:00            # 限制計算時間，避免程式卡死無法完成，這個設定會跑5天6個半小時
#SBATCH --partition=debug         # 指定分區，目前只有建立debug和batch分區，debug用於不超過24H時長的測試，batch沒有時間上限

module load cuda/11.8

# 設定 OpenMP threads 數
export OMP_NUM_THREADS=$SLURM_CPUS_PER_TASK


# 執行程式 (使用srun讓slurm管理資源而不是由gmx自己偵測)
srun gmx mdrun -s topol.tpr -deffnm prod -ntomp $OMP_NUM_THREADS -nb gpu 

```
### 3.2 提交job
```
sbatch job_script.sh
```

### 3.3 查詢job狀態
```
squeue
```

### 3.4 取消job
```
scancel <JobID>
```

### 3.5 查詢job紀錄
```
sacct -j <JobID>
```








##    References
1. https://linux.vbird.org/linux_basic/redhat6.1/linux_06command.php
2. https://note.drx.tw/2008/04/command.html
3. https://codelove.tw/@tony/post/AqJe4a
4. https://xenby.com/b/220-%E6%95%99%E5%AD%B8-%E7%94%A2%E7%94%9Fssh-key%E4%B8%A6%E4%B8%94%E9%80%8F%E9%81%8Ekey%E9%80%B2%E8%A1%8C%E5%85%8D%E5%AF%86%E7%A2%BC%E7%99%BB%E5%85%A5
