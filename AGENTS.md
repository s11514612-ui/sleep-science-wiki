# AGENTS.md - 睡眠科學 LLM Wiki 運作規則與知識庫規範

本檔案為本專案的核心規範與運作指令庫（Schema）。所有維護此知識庫的 LLM Agent 必須嚴格遵循以下架構、流程與寫作規範。

---

## 1. 知識庫架構理念（Karpathy LLM Wiki 模式）

知識庫採取三層架構（Three-layer Architecture）：

1. **原始資料層 (`raw/`)**：
   - 包含書籍摘錄、Podcast 逐字稿/筆記（如 Huberman Lab、Matthew Walker）、醫學機構指引（AASM、Sleep Foundation）與論文摘要。
   - **此層不可變（Immutable）**：LLM 僅能讀取，不可修改或刪除原始檔案。
2. **Wiki 知識層 (`wiki/`)**：
   - 經 LLM 提煉、交叉引用、去蕪存菁後的 Markdown 知識網絡。
   - **LLM 全權擁有並動態維護**：負責建立實體頁、概念頁、介入方案、補充品評估，維護雙向連結，隨新資料進行複利增量更新。
3. **規則規範層 (`AGENTS.md`)**：
   - 定義目錄結構、工作流（Ingest, Query, Lint）、語意標準、衝突處理機制與視覺化規範。

---

## 2. 目錄結構規範

```text
sleep-wiki/
├── AGENTS.md                  # 本規範手冊
├── raw/                       # 原始素材庫（不可變，唯讀）
│   ├── books/                 # 書籍筆記與摘錄
│   ├── podcasts/              # Podcast 筆記與逐字稿
│   ├── guidelines/            # 醫學指引與機構發布內容
│   └── papers/                # 同儕審查論文與文獻
└── wiki/                      # 知識庫主體
    ├── index.md               # 內容目錄（分類、標籤、單行摘要與連結）
    ├── log.md                 # 時間軸事件日誌（append-only）
    ├── concepts/              # 核心生理與神經科學概念（如：晝夜節律、腺苷、睡眠週期）
    ├── interventions/         # 睡眠衛生與行為/環境介入（如：光照管理、臥室溫度、咖啡因代謝）
    ├── supplements/           # 營養素與補充品科學評估（如：鎂、褪黑激素、茶胺酸）
    ├── sources/               # 針對 raw 資料的結構化摘要頁
    └── guides/                # 綜合應用指南與實踐手冊（可落地的行動清單）
```

---

## 3. 核心工作流程（Operations）

### 操作 A：資料匯入（Ingest Workflow）
當使用者指令：「請匯入 `raw/...`」或提供新資料時，依序執行：
1. **讀取原始文獻**：通讀檔案，提煉核心生理機制、數據、研究論點與實用建議。
2. **生成來源摘要頁**：在 `wiki/sources/<source-slug>.md` 建立摘要，包含文獻來源資訊、核心要點、關聯實體。
3. **擴增或更新 Wiki 頁面**（平均每篇新資料會更新或新建 3~8 個 Wiki 頁面）：
   - 若為全新概念/營養素/介入措施，於對應目錄新建頁面。
   - 若概念已存在，**更新現有頁面**，融入新證據，不可無腦覆蓋或重複建檔。
4. **觀點矛盾處理（Conflict Resolution）**：
   - 若新資料與既有 Wiki 頁面觀點衝突（例如：某補充品對深睡是否有顯著效益、藍光濾鏡鏡片的實際效果），**不可悄悄覆蓋舊觀點**。
   - 必須使用 GitHub Alert 語法明確標記爭議：
     ```markdown
     > [!WARNING] 觀點爭議 / Contradiction
     > - **觀點 A（來源: [[source-a]]）**：主張褪黑激素僅對時差有效，無法增加健康成人深層睡眠。
     > - **觀點 B（來源: [[source-b]]）**：指出高齡者因內源分泌減少，低劑量補充可改善睡眠連續性。
     ```
5. **視覺化與圖解生成**：當涉及生理時鐘波動、激素消長、代謝半衰期或因果步驟時，必須繪製 Mermaid.js 圖表。
6. **更新目錄與日誌**：
   - 在 `wiki/index.md` 更新/新增條目。
   - 在 `wiki/log.md` 末尾追加一行/一段事件紀錄（格式見後文）。

### 操作 B：查詢與合成（Query & Synthesis Workflow）
當使用者針對睡眠科學提問時：
1. 先閱讀 `wiki/index.md` 定位相關概念與介入措施頁面。
2. 跨檔案讀取相關 Markdown 內容，合成嚴謹且具體可行的回答，並註明資料來源引用。
3. **沉澱回答（Compounding Insight）**：若該次問答產出了具代表性、跨主題的深度比較或行動方案，詢問或主動將其沉澱至 `wiki/guides/<guide-topic>.md`，讓知識庫持續增厚。

### 操作 C：健康檢查（Lint Workflow）
當使用者要求檢查知識庫（或定期執行）時：
1. **孤島檢查（Orphan Check）**：尋找沒有被任何其他頁面或 `index.md` 連結的孤立頁面。
2. **未連結實體檢查（Missing Link Check）**：檢查各頁面中是否頻繁出現重要專業名詞（如「皮質醇」、「慢波睡眠」），但尚未轉換為 `[[wiki-link]]` 或未建置專屬頁面。
3. **矛盾追蹤（Open Conflicts）**：彙整全庫中所有標記有觀點爭議的區塊，提供使用者進一步查證的建議。
4. 將檢查結果與建議記錄於 `wiki/log.md`。

---

## 4. 寫作與格式標準

### 4.1 頁面 Frontmatter 標準
所有 `wiki/` 內的頁面（除 index/log 外）頂部均須包含 YAML Frontmatter：
```yaml
---
title: 鎂（Magnesium）與睡眠品質
category: supplements
evidence_level: Moderate (初步人體研究支持，受試者群體異質性高)
tags: [supplement, deep-sleep, gaba, minerals]
updated: 2026-11-22
sources:
  - "[[sources/huberman-sleep-toolkit]]"
  - "[[sources/sleep-foundation-magnesium]]"
---
```

### 4.2 實證等級標籤（Evidence Level）
涉及營養補充品、介入手段時，必須標明實證強度：
- `High`：多項同儕審查人體隨機對照試驗（RCT）或統合分析（Meta-analysis）
- `Moderate`：初步或小規模人體試驗，機制明確但大規模證據不足
- `Low / Mechanistic`：動物實驗、體外細胞研究、或純推論生理機制
- `Mixed / Inconclusive`：文獻結果顯著分歧，尚未達成共識

### 4.3 雙向連結格式
- 支援 Obsidian 與標準 Markdown：統一使用 `[[路徑/檔名|顯示名稱]]` 或 `[顯示名稱](../路徑/檔名.md)`。
- 名詞首次在段落出現時應附帶雙向連結與英文原文，例如：`[[concepts/circadian-rhythm|晝夜節律（Circadian Rhythm）]]`。

### 4.4 必備 Mermaid.js 圖解標準
下列主題必須附帶 Mermaid 圖表輔助理解：
1. **時序與晝夜波動**：如光照驅動 SCN → 抑制褪黑激素 → 皮質醇甦醒反應（CAR）。
2. **雙歷程睡眠模型（Two-Process Model）**：過程 C（晝夜節律）與過程 S（腺苷睡眠壓力）交互關係。
3. **藥物/物質半衰期**：咖啡因、酒精對睡眠結構（REM/NREM）干擾機制的因果流程圖。
4. **決策樹**：睡前改善行動流程圖、補充品選擇決策樹。

---

## 5. 日誌（log.md）格式規範

所有事件必須以標準前綴記錄，確保可用指令迅速篩選與統計：
```markdown
## [YYYY-MM-DD] ingest | <來源名稱或檔案名稱>
- 新增檔案：[[sources/...]]
- 更新頁面：[[concepts/...]], [[interventions/...]]
- 標記爭議：<若有觀點衝突，簡述其一兩句話，無則填無>

## [YYYY-MM-DD] query | <問題主題>
- 檢索頁面：[[...]], [[...]]
- 產出沉澱：[[guides/...]]（若無則略過）

## [YYYY-MM-DD] lint | 定期知識庫健康檢查
- 孤立頁面修復：...
- 發現並補充未連結關鍵詞：...
```
