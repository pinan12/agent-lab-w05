# 器材資料清理問題報告 (Equipment Data Cleaning Issues Report)

## 一、清理統計摘要
- **原始筆數（Original rows）**：10 列
- **有效筆數（Valid rows）**：9 列
- **移除筆數（Removed rows）**：1 列（第 6 列所有欄位皆為空值 `{}`，予以移除）

---

## 二、異常數值與待確認項目 (Quantity & Status Issues)

1. **第 7 列（source_row: 7, item_id: EQ04, 紙張包）**
   - **問題**：`qty` 欄位為空字串 `""`（缺失數量）。
   - **處置**：依規範不自行補 0 或猜測數量，維持空字串原貌並列入待確認。
2. **第 8 列（source_row: 8, item_id: EQ05, 膠帶）**
   - **問題**：`qty` 欄位為負數 `-1`（不符合非負整數規則）。
   - **處置**：依規範不取絕對值或猜測數量，維持原值 `-1` 並列入待確認。
3. **第 9 列（source_row: 9, item_id: EQ06, 剪刀）**
   - **問題**：`status` 原始值為「待盤點」，非可借出或已借出狀態。
   - **處置**：統一標註為 `unknown` 並列入待盤點追蹤。

---

## 三、相同 item_id 比對分析 (Duplicate item_id Analysis)

依規範，相同 `item_id` 之有效資料全部完整保留，列出來源列號與欄位比對：

1. **`EQ01`（Marker / 白板筆）**
   - **來源列號**：第 1 列（source_row: 1）與 第 4 列（source_row: 4）
   - **欄位比較**：
     - `name`: 兩列皆為「Marker / 白板筆」（第 1 列清理了前後空白）
     - `qty`: 兩列皆為 `4`（數值相符）
     - `status`: 兩列正規化後皆為 `available`（第 1 列原為「可借」，第 4 列原為「available」）
   - **結論**：兩列內容完全一致，皆予保留並備註可能為重複登錄。
2. **`EQ02`（Extension cord / 延長線）**
   - **來源列號**：第 2 列（source_row: 2）與 第 5 列（source_row: 5）
   - **欄位比較**：
     - `name`: 兩列皆為「Extension cord / 延長線」
     - `status`: 兩列正規化後皆為 `borrowed`（第 2 列原為「borrowed」，第 5 列原為「借出」）
     - **衝突欄位**：`qty` 數值衝突（第 2 列登記數量為 `2`，第 5 列登記數量為 `3`）
   - **結論**：兩列數量存在衝突，嚴禁自行合併或平均，兩列均完整保留，需由器材管理員核實實際外借數量。
