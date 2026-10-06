# My lab evidence / 我的實作紀錄

Use a group code, not real names or student IDs in shared files. / 共用檔只寫組別代碼，不寫姓名或學號。

- Group code / 組別：pinan12
- Tool / 工具：Antigravity Agent (Claude / Gemini)
- Route / 路線：individual 個人
- Tasks completed / 完成題目：A, B, C, D（全題組完成）
- Material / 素材：NDHU classroom tasks 東華課堂版
- For original-pack work: task number, author/source link and version / 原版實作：題號、作者來源連結與版本：無（使用東華課堂版）
- My role and what I checked / 我的角色與實際檢查：操作者與審查者（Operator & Inspector）。實際檢查：確認原檔 100% 完整保留、雜湊值 SHA-256 逐一比對相符；親測 B 題單頁離線工具 6 項測試條件；檢查 C 題異常數據與衝突 ID 留存；撰寫 D 題安全退回與替代方案。

## Scope and plan / 範圍與計畫

Allowed input and output folders / 可讀取與輸出的資料夾：
- 輸入：`practice/01-club-files/input`、`practice/02-campus-picker/activities.json`、`practice/03-equipment/equipment.json`、`practice/04-review/bad-plan.txt`
- 輸出：`practice/01-club-files/output/`、`practice/02-campus-picker/output/`、`practice/03-equipment/output/`、`practice/04-review/my-rejection.md`、`evidence/`

What I asked for / 原始需求：
1. 任務 A：整理社團 12 個檔案至 output 分類，原檔不動，保留重複檔副本與不同草案版本，產出 manifest.json 與 report.md。
2. 任務 B：製作單頁活動隨機挑選器（index.html），支援地點、時間、強度篩選與最近 5 次歷史紀錄、重設篩選、中英介面與雙語對照。
3. 任務 C：清理器材資料 10 列，正規化欄位，保留異常數值與重複 ID，移除空列。
4. 任務 D：審查刻意寫錯的模擬計畫，列出問題並撰寫具體退回替代方案。

What I checked before execution / 動手前我檢查了什麼：
檢查 AI 提出的計畫是否符合「原檔唯讀不更動」、「輸出限定當題 output 資料夾」、「未經授權不連外不掃描全機」等安全限制；確認不以檔名（如 final / final2）猜測定稿，不隨意刪除重複檔。

## Tests actually performed / 我真的做過的測試

| Test / 測試 | Expected / 預期 | Observed / 實際 | Evidence / 證據 |
|---|---|---|---|
| 1. B題「室外／15分鐘／中強度」 | 顯示「沒有符合條件的活動」，不偷改條件 | 畫面清楚顯示紅框「沒有符合條件的活動」，歷史紀錄未增加 | activities.json 中唯一室外中強度為 A09（30分鐘），無 $\le 15$ 分鐘項目，嚴格篩選生效 |
| 2. B題「室外／30分鐘／中強度」 | 每次抽取必定為 A09 | 連續抽 3 次皆抽中 A09（在合適位置快走 / 30分鐘 / 室外 / 中） | activities.json 只有 A09 符合 outdoor + $\le 30$m + medium |
| 3. A題 12 檔案雜湊驗證 | 輸出之 12 份副本與原檔雜湊 100% 一致 | PowerShell SHA-256 驗證全數通過，原檔未被修改或刪除 | 雜湊值與 manifest.json 12 筆完全吻合 |

## One revision / 一次修改

Before / 原來的情況：
第一版只有單一語系切換（點擊 English 切到純英文、點擊中文切到純中文），無法同時對照中英文名稱。

Request / 我提出的修改：
增加「中英雙語（Bilingual）」顯示模式，讓導航列提供三模式快速切換，抽中活動同時並列中英文主副標，歷史紀錄與選項亦完整呈現雙語。

After and retest / 修改後與重測結果：
在右上角成功加入 `[ 中文 | English | 中英雙語 ]` 膠囊切換列。點擊中英雙語後，標題、按鈕、抽中活動卡（如 `整理書包` / `Organize your bag`）均正確並列雙語，各項篩選功能重測正常。

New requirement or defect? / 新需求還是原規格未做到？：
新需求（New requirement）。

## One rejection / 一次退回

Which action I reject and why / 退回哪個動作、為什麼：
退回 `practice/04-review/bad-plan.txt` 中「整理 Downloads 全部、逕自刪除重複檔、把 final2 當最新版、缺失資料猜合理值補齊、完成後自動公開成果」的危險計畫。這違反了最小權限原則、資料真實性原則，且擅自推定版本定稿與自動公開會造成不可逆的檔案破壞與安全風險。

An acceptable alternative / 可以怎麼改：
嚴格限縮工作範圍於指定 input 目錄；原檔保持唯讀，在 output 保留副本；所有版本完整保存由人類決策；缺漏值原樣保留並列出問題報告；成果儲存本地，經人工驗收後才發布。

## Still unverified / 還沒驗證

What I cannot claim is complete / 哪些事不能說已完成：
1. 企劃案最終定稿（戶外 30 分鐘 vs 室內 20 分鐘）需由真實社團開會決議，AI 無法代替人類做實質決策。
2. 挑選器僅經由幾次功能測試驗證篩選邏輯，不能證明隨機抽取在統計上的嚴格均勻機率分佈。
3. 器材資料中 EQ02 數量衝突（2 vs 3）與 EQ05 負數數量，仍需實地盤點器材庫房實物。
