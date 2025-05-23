# Lecture 4. Git
課程時間:2小時

## 紀錄
### Markdown
Markdown 是一種輕量級的標記語言，使用純文字就能撰寫格式化的文件，可轉換成 HTML，廣泛應用於：

- 撰寫技術文件與教學
- 編輯 GitHub README
- 網誌、Wiki、筆記應用（如 Notion、Obsidian）
- Markdown文件結尾為.md
- hackmd是以markdown語言撰寫的筆記軟體
#### 基本文字格式
```
**粗體字**
*斜體字*
~~刪除線~~
`程式碼區塊`
```
#### 標題（Title / Heading）

```
# 標題1
## 標題2
### 標題3
#### 標題4

```

#### 清單（Lists）

```
- 蘋果
- 香蕉
- 葡萄

1. 準備食材
2. 加熱鍋子
3. 放入食材

```

#### 連結與圖片
```
[Google](https://www.google.com)
![圖片說明](https://example.com/image.jpg)
```

#### 表格（Tables）
```
| 名字 | 年齡 | 城市     |
|------|------|----------|
| 小明 | 25   | 台北     |
| 小美 | 30   | 高雄     |

```

#### 水平線（Horizontal Rule）
```
---
```
### LaTex表示數學式
LaTeX 提供一套清晰、專業的語法來排版數學公式，廣泛應用於學術論文、簡報、筆記與論文排版中，尤其在：

- Markdown 文件（支援 `$...$` 語法）
- Jupyter Notebook
- Overleaf（LaTeX 文件）
- GitHub README（支援部分 MathJax 語法
#### 上標與下標
```
x_i
x^2
x_i^2
```

#### 分數、開根號

```
\frac{a}{b} 
\sqrt{2} 
\sqrt[n]{x}

```

####  希臘字母
```
\alpha \beta \gamma \pi \sigma \Omega
```

## Git

Git 是一套分散式版本控制系統，可追蹤檔案的變更、還原歷史版本、協作開發。由 Linus Torvalds 開發，是目前最常見的版本控制工具。
- 分散式架構（每個人都有完整版本歷史）
- 快速且穩定
- 與 GitHub / GitLab / Bitbucket 整合良好
```bash
git config --global user.name "你的名字"
git config --global user.email "you@example.com"
```
### 初始化版本控制
```
git init          # 初始化一個 git 專案
```
### 檢查狀態與變更
```
git status        # 查看目前狀態
git diff          # 查看尚未加入的變更
```

### 加入暫存區與提交
```
git add filename      # 加入單一檔案
git add .             # 加入所有變更
git commit -m "描述訊息"
```

### 檢視紀錄與版本
```
git log               # 查看提交紀錄
git show COMMIT_ID    # 顯示特定版本內容
```

### 分支管理（branch）

```
git branch             # 查看分支
git branch new-branch  # 建立新分支
git checkout new-branch # 切換分支
git merge branch-name  # 合併其他分支到目前分支
```

## Github

### 連線與推送
```
git remote add origin https://github.com/your/repo.git
git push -u origin main   # 第一次推送
git push                  # 後續推送
```

### 拉取與同步

```
git pull          # 從遠端拉回更新並合併
git fetch         # 只拉更新，不合併
```

###  .gitignore 設定
`.gitignore` 檔案用來排除不想加入版本控制的檔案，例如：
通常原始檔跟config檔案都不會上傳到github，一個是因為檔案太大，另一個是因為安全隱私
```
__pycache__/
*.pyc
.env
.DS_Store
```

### References
1. https://gitbook.tw/chapters/introduction/what-is-git
2. https://hackmd.io/s/tutorials-tw
3. https://hackmd.io/@CynthiaChuang/Basic-LaTeX-Commands