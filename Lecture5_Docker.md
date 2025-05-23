# Docker

課程時間:2小時


## 使用
Docker 是一套「容器化（Containerization）」平台，讓開發者能夠將應用程式及其相依環境打包成「容器（Container）」，確保在任何機器上都能一致執行。

### 基本概念
- **Image（映像檔）**：應用程式和其依賴的快照（模板）
- **Container（容器）**：從映像檔啟動的執行實例
- **Dockerfile**：自動化建構映像的腳本檔案
- **Docker Hub**：Docker 官方的映像檔託管平台

###  映像檔操作
```
docker pull python:3.10         # 下載映像檔
docker images                   # 列出本地映像檔
docker rmi 映像名稱             # 刪除映像檔
```

### 容器操作
```
docker run -it python:3.10 bash   # 啟動互動式容器
docker ps                         # 查看執行中容器
docker ps -a                      # 包含已結束的容器
docker stop 容器ID
docker rm 容器ID
```

### Dockerfile 範例
```
# 使用官方 Python 映像檔作為基底
FROM python:3.10

# 設定工作目錄
WORKDIR /app

# 複製檔案
COPY . /app

# 安裝相依套件
RUN pip install -r requirements.txt

# 執行主程式
CMD ["python", "main.py"]
```
建構與執行：

```
docker build -t my-python-app .
docker run my-python-app
```
### 使用 volumes 掛載資料
```
docker run -v --rm /host/path:/container/path image
```




###    References
1. https://github.com/twtrubiks/docker-tutorial