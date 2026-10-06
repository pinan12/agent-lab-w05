# 學習紀錄與驗收總覽 (Learning Record & Verification Summary)

## 基本資訊
- **學生/組別代碼**：pinan12
- **使用工具**：Antigravity Agent (Google Gemini / Claude)
- **實作路線**：individual 個人路線
- **實作題材**：NDHU classroom tasks 東華校園實作課堂版

---

## 題組完成清單與驗收紀錄

### 任務 A：社團檔案整理 (`practice/01-club-files`)
- **輸入**：12 個檔案。
- **輸出**：`output/` 下 5 大分類（01-proposals, 02-planning, 03-equipment, 04-publicity, 05-feedback）共 12 份原檔副本。
- **產出文件**：`output/manifest.json`（12 筆對照清單）、`output/report.md`（完整整理報告）。
- **驗證要點**：
  - 原檔完全未更動（SHA-256 逐一驗證相符）。
  - 重複檔（`announcement.txt` / `announcement_copy.txt`、`equipment_list.txt` / `equipment_backup.txt`）均保留副本。
  - 不同版本企劃（`proposal_final.txt` 戶外30分 vs `proposal_final2.txt` 室內20分）均保留，未擅自認定定稿。
- **Commit**：`2f3e477 A: organize club files`

---

### 任務 B：課間活動挑選器 (`practice/02-campus-picker`)
- **輸入**：`activities.json`（12 筆模擬資料，唯讀不改）。
- **輸出**：`output/index.html`（單頁離線工具，無 CDN / 無外部套件依賴，雙擊即可執行）。
- **功能檢驗**：
  - 地點（室內/室外/不限）、可用時間（15/30/60分，$\le$ 條件）、活動強度（低/中/不限）嚴格連動。
  - 成功抽樣最近 5 筆紀錄（最新在最前，具清除紀錄按鈕）。
  - 重設篩選（回到不限/30/不限，不清空紀錄）。
  - 清楚顯示警語「教學模擬活動，不是校方公告」。
- **一次修改 (Revision - B v2)**：
  - 新增「中英雙語對照模式（Bilingual Mode）」，右上角提供 `[ 中文 | English | 中英雙語 ]` 快速切換。
  - 抽中活動同時顯示中英文主副標題，各標籤與歷史紀錄均雙語並列。
- **Commit**：
  - `eea9193 B v1: activity picker`
  - `244f519 B v2: add bilingual display mode`

---

### 任務 C：社團器材記錄清理 (`practice/03-equipment`)
- **輸入**：`equipment.json`（10 筆資料）。
- **輸出**：`output/normalized.json`（9 筆有效正規化資料）、`output/issues.md`（清理問題報告）。
- **成果**：
  - 成功剔除全空之無效列（第 6 列）。
  - 狀態正規化為 `available`、`borrowed`、`unknown`。
  - `EQ04` 缺失數量（`""`）與 `EQ05` 負數數量（`-1`）原樣保留並記錄。
  - `EQ01` 與 `EQ02` 相同 ID 資料全部保留，標記數量衝突（2 vs 3）。
- **Commit**：`faca33b C: clean equipment records`

---

### 任務 D：共同討論與退回不合理計畫 (`practice/04-review`)
- **輸入**：`bad-plan.txt`（刻意寫錯的模擬計畫）。
- **輸出**：`my-rejection.md`（退回聲明與替代方案）。
- **成果**：
  - 圈出五大問題：越權掃描 Downloads、逕自刪除檔案、依檔名妄斷定稿、臆測補齊缺失值、未經驗收自動公開。
  - 提出可接受之五大替代原則：限定工作範圍、原檔唯讀留副本、所有版本保存供人工決策、缺失原樣記錄、本地人工驗收後才發布。
- **Commit**：`7bb7091 D: rejection`

---

## 總結
本實作完整體驗了身為人類審查者（Human-in-the-Loop）在指揮與監督 AI Agent 執行任務時的關鍵職責：
1. **看懂計畫（Plan Review）**：動手前檢查讀取與寫入範圍，確保原檔安全。
2. **親自驗收（Verification）**：利用雜湊比對、極端邊界測試（如無符合結果）與程式結構驗證產出。
3. **退回失控操作（Rejection）**：辨認越權存取與捏造數據，堅守資料誠信與安全性。
