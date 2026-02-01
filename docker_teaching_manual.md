# Docker 實戰教學手冊

這份文件將記錄所有的實作過程，包含觀念講解、操作指令與預期結果。

## 單元 1: 環境確認
- **執行時間**: 2026-02-01
- **狀態**: Completed

## 單元 1: Docker Hello World (初次體驗)

### 1. 觀念講解 (Concepts)
- **Image (映像檔)**: 就像是食譜 (Recipe) 或遊戲光碟。它是靜態的、唯讀的檔案，包含了執行程式所需的所有東西。
- **Container (容器)**: 就像是照著食譜做出來的蛋糕，或是正在執行的遊戲。它是從 Image 建立出來的執行實體。
- **關係**: 一個 Image 可以建立出無數個 Containers。

### 2. 操作步驟 (Steps)
1. 開啟終端機 (PowerShell / CMD)。
2. 輸入指令：
   ```bash
   docker run hello-world
   ```

### 3. 預期結果 (Expected Result)
當您看到以下訊息時，代表成功：
```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
```
Docker 會自動從 Docker Hub 下載 (Pull) `hello-world` 這個 Image，並建立一個 Container 執行它。

### 4. 常見問題 (Q&A)
- **Q**: 為什麼會出現 `Unable to find image 'hello-world:latest' locally`？
  - **A**: 這是正常的。Docker 發現您電腦裡沒有這個 Image，所以會自動去網路上抓。之後再跑一次就不會出現這行了。

## 單元 2: 運行 Nginx Web Server (真實網頁伺服器)

### 1. 觀念講解 (Concepts)
- **Web Server (網頁伺服器)**: 像 Nginx 或 Apache，用來提供網頁給瀏覽器看。
- **Port Mapping (端口對應)**: 
  - Container 是一個獨立的世界，它的 Port 80 只有它自己看得到。
  - 我們必須把 Container 的 Port 80 「接」到您電腦 (Host) 的 Port 8080，這樣您的瀏覽器才能連進去。
  - 語法：`-p [電腦 Port]:[Container Port]` (例如 `-p 8080:80`)。

### 2. 操作步驟 (Steps)
1. 執行以下指令 (這次指令稍長，請仔細看)：
   ```bash
   docker run -d -p 8080:80 --name my-nginx nginx
   ```
   - `-d`: 在背景執行 (Detach mode)，才不會卡住終端機。
   - `-p 8080:80`: 把電腦的 8080 對應到 Container 的 80。
   - `--name my-nginx`: 幫它取個名字叫 `my-nginx`，方便之後管理。
   - `nginx`: Image 名字。

### 3. 預期結果 (Expected Result)
1. 執行後會看到一串長長的 ID。
2. 開啟瀏覽器，輸入網址：[http://localhost:8080](http://localhost:8080)
3. 您應該會看到 **"Welcome to nginx!"** 的畫面。

### 4. 常見問題 (Q&A)
- **Q**: 我要怎麼看現在有哪些 Container 在跑？
  - **A**: 輸入 `docker ps`。
- **Q**: 如果我要停止它怎麼辦？
  - **A**: 輸入 `docker stop my-nginx`。
