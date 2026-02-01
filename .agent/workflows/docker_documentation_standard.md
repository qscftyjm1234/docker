---
description: 確保 Docker 教學過程被記錄為繁體中文教學手冊的標準作業程序
---

# Docker 教學與文件化標準 (Docker Teaching & Documentation Protocol)

此 Workflow 用於規範「前端 Docker 實戰課程」的執行與紀錄方式。

## 1. 語言規範 (Language Standard)
*   **所有** 解說、計畫書 (Implementation Plan)、任務清單 (Task List) 與對話 **必須** 使用 **繁體中文 (Traditional Chinese)**。
*   專有名詞 (如 Image, Container, Volume) 可保留英文，但初次出現時需附上中文解釋。

## 2. 文件化要求 (Documentation Requirement)
在進行每一個教學單元 (Module) 或實作步驟後，必須將詳細過程寫入以下文件：
*   **目標檔案**: `<appDataDir>/brain/<conversation-id>/docker_teaching_manual.md` (Docker 實戰教學手冊)
*   **內容結構**:
    1.  **觀念講解**: 簡單易懂的譬喻 (例如：便當盒 vs 廚房)。
    2.  **操作步驟**: 清楚的 Command Line 指令。
    3.  **預期結果**: 執行後會看到什麼畫面或 Log。
    4.  **常見雷點**: 初學者容易報錯的地方 (例如 Port 被佔用)。

## 3. 執行流程 (Execution Flow)
每當完成一個教學段落 (如 "Run Nginx"):
1.  確認使用者執行成功。
2.  使用 `multi_replace_file_content` 或 `write_to_file` 更新 `docker_teaching_manual.md`。
3.  在 `notify_user` 中告知使用者該步驟已記錄，方便未來教學使用。
