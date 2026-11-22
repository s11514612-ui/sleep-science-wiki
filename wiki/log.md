# 睡眠科學 LLM Wiki 運作日誌（Log）

本檔案為追加式紀錄（Append-only），記錄所有知識庫的匯入（Ingest）、深度查詢沉澱（Query）與健康檢查（Lint）事件。

---

## [2026-11-22] init | 睡眠科學 LLM Wiki 系統初始化
- 建立規則手冊：`AGENTS.md`
- 建立知識庫三層架構：`raw/`、`wiki/`、`AGENTS.md`
- 建立內容導航：`wiki/index.md` 與時間軸日誌 `wiki/log.md`

## [2026-11-22] ingest | Huberman Lab Sleep Toolkit (raw/podcasts/huberman-sleep-toolkit.md)
- 新增來源頁：[[sources/huberman-sleep-toolkit]]
- 建立概念頁：[[concepts/circadian-rhythm]]、[[concepts/sleep-pressure-adenosine]]
- 建立介入頁：[[interventions/light-exposure]]、[[interventions/bedroom-temperature]]
- 建立補充品頁：[[supplements/magnesium]]
- 建立實踐指南：[[guides/evening-routine-checklist]]
- 標記爭議：褪黑激素高劑量使用風險與替代放鬆配方。

## [2026-11-22] ingest | Sleep Foundation & AASM Guidelines (raw/guidelines/sleep-foundation-caffeine-and-melatonin.md)
- 新增來源頁：[[sources/sleep-foundation-guidelines]]
- 擴增介入頁：[[interventions/caffeine-and-alcohol]]（補強 PSG 腦波研究、CYP1A2 代謝多態性）
- 擴增補充品頁：[[supplements/melatonin]]（明確界定生物節律調節劑定位與 0.3-1mg 生理劑量）
- 標記爭議：標記主觀睡眠感受與 PSG 客觀腦波監測間的落差；褪黑激素對高齡者有效但對一般慢性失眠非一線選擇之臨床爭端。

## [2026-11-22] ingest | 睡眠四階段與睡眠循環 (raw/guidelines/tamhd-sleep-stages.md)
- 新增來源頁：[[sources/tamhd-sleep-stages]]
- 新增概念頁：[[concepts/sleep-stages-and-cycles]]（涵蓋 N1/N2/N3 與 REM 做夢特徵、90 分鐘週期、前半夜慢波優勢）
- 關聯更新：[[concepts/sleep-pressure-adenosine]]、[[interventions/caffeine-and-alcohol]]
- 標記爭議：無觀點衝突，結構化統整舊版第 3 與第 4 階段合併為慢波睡眠之歷史沿革。

## [2026-11-22] ingest | 褪黑激素與晝夜節律（生理時鐘） (raw/guidelines/tendays-melatonin-circadian.md)
- 新增來源頁：[[sources/tendays-melatonin-circadian]]
- 擴增補充品頁：[[supplements/melatonin]]（新增台灣衛福部「藥品列管」法規限制、高風險禁止自行使用族群與就醫警訊）
- 擴增指南頁：[[guides/evening-routine-checklist]]（新增就寢環境人體工學支持與醫療警訊檢核）
- 標記爭議：強調褪黑激素非安眠藥，對非節律性失眠（如疼痛、睡眠呼吸中止症）無效。

## [2026-11-22] ingest | 咖啡因劑量、時間點與睡眠干擾 (raw/papers/sleep321-caffeine-dosage-timing.md)
- 新增來源頁：[[sources/sleep321-caffeine-study]]
- 擴增介入頁：[[interventions/caffeine-and-alcohol]]（導入 2025 澳洲隨機交叉 RCT 數據：400mg 削奪 30 分鐘 N3 慢波深睡、12 小時長滯留效應；100mg 劑量依賴無顯著干擾；台灣衛福部紅黃綠標籤制度與常見飲品含量）
- 擴增概念頁：[[concepts/sleep-pressure-adenosine]]、[[concepts/sleep-stages-and-cycles]]
- 擴增指南頁：[[guides/evening-routine-checklist]]（升級分級咖啡因截止機制）
- 標記爭議：受試者「自覺睡得好」但客觀 PSG 監測「深層慢波睡眠遭到嚴重破壞」之主客觀感知斷層。

## [2026-11-22] lint | 全庫健全度檢查（Health Check）
- 孤立頁面檢查（Orphan Check）：全庫 14 篇 Markdown 均已納入 [[wiki/index.md]]，且各篇皆具備至少 2 個以上出站與入站雙向連結，無孤立頁面。
- 衝突標記檢查（Conflict Check）：褪黑激素定位與台灣法規列管、咖啡因主客觀知覺斷層均已使用 `> [!WARNING]` 與 `> [!CAUTION]` 標記。
- 視覺化檢查（Mermaid Check）：所有新增概念頁與介入頁均已配置 Mermaid.js 流程圖或架構圖。

## [2026-11-22] ingest | 睡眠體溫變化與環境降溫助眠法 (raw/guidelines/oghome-sleep-temperature.md)
- 新增來源頁：[[sources/oghome-sleep-temperature]]
- 擴增介入頁：[[interventions/bedroom-temperature]]（導入晝夜 24 小時體溫震盪軸、入睡後 4 小時最低點 36.6°C、荷蘭降溫服研究、被窩悶熱 vs. 過冷肌肉震顫產熱陷阱）
- 擴增概念頁：[[concepts/circadian-rhythm]]（將 24 小時體溫震盪納入 Process C 核心標記）
- 擴增指南頁：[[guides/evening-routine-checklist]]（補強睡前 4 小時避開劇烈運動與微氣候對流）
- 標記爭議：破除「環境越冷越好」迷思，標記低溫引發肌肉發抖產熱破壞深睡之生理陷阱。

## [2026-11-22] ingest | 午睡黃金時長與睡眠惰性 (raw/guidelines/tendays-nap-science.md)
- 新增來源頁：[[sources/tendays-nap-science]]
- 新增介入頁：[[interventions/nap-science]]（建立餐後低潮應對矩陣、NASA 飛行員研究、10-20 分鐘小憩 vs. 30-60 分鐘睡眠惰性地雷、16:00 嚴格截止線）
- 擴增概念頁：[[concepts/sleep-stages-and-cycles]]（解析喚醒自 N3 引發睡眠惰性）、[[concepts/sleep-pressure-adenosine]]（午睡對 Process S 腺苷壓力的動態調節）、[[concepts/circadian-rhythm]]（餐後低潮 Post-Lunch Dip）
- 擴增指南頁：[[guides/evening-routine-checklist]]（加入 16:00 午睡截止線檢核）
- 標記爭議：標記 30-60 分鐘午睡因強斷 N3 慢波引發嚴重睡眠惰性（越睡越累反效果）。

## [2026-11-22] lint | 知識庫擴充健全度檢查（Health Check）
- 孤立頁面檢查（Orphan Check）：全庫 17 篇 Markdown 均已納入 [[wiki/index.md]]，且篇篇具備 3 個以上入站與出站雙向連結，無孤立頁面。
- 衝突與警告檢查（Conflict Check）：針對「環境過冷發抖陷阱」與「30-60 分鐘午睡引發睡眠惰性」均已加上 `> [!WARNING]` Alert 標籤。
- 視覺化驗證（Mermaid Check）：`interventions/nap-science.md` 及 `interventions/bedroom-temperature.md` 之 Mermaid 圖表語法均檢驗通過。

## [2026-11-22] query | 睡眠科學全景簡報投影片生成與導覽沉澱
- 檢索頁面：[[concepts/sleep-stages-and-cycles]], [[concepts/sleep-pressure-adenosine]], [[concepts/circadian-rhythm]], [[interventions/light-exposure]], [[interventions/bedroom-temperature]], [[interventions/caffeine-and-alcohol]], [[interventions/nap-science]], [[supplements/magnesium]], [[supplements/melatonin]], [[guides/evening-routine-checklist]]
- 產出檔案：`slides/index.html`（11 頁全景互動式 HTML 投影片，具備進度條、鍵盤控制、全螢幕與響應式深色主題）
- 產出沉澱：[[guides/sleep-science-slides-overview]]（建立投影片架構與知識庫全站交叉引用指南）

## [2026-11-22] query | 投影片設計風格升級（Editorial Warm Oatmeal Theme）
- 風格調整：依使用者訪談決策，將深色系全面改版為「暖米白紙質底色（#f9f8f5）」＋「深炭灰內文（#2a3138）」。
- 主色分工：導入「鼠尾草綠（#4a6e5b，生活與環境介入）」與「霧霾藍（#3d6075，神經機制與臨床文獻）」雙色語意。
- 警示降飽和：警示框與咖啡因紅標全面轉為莫蘭迪「陶土紅（#b2534a）」，營造沉穩、雅緻的精品健康雜誌視覺。
- 更新檔案：`slides/index.html`、[[guides/sleep-science-slides-overview]]。

## [2026-11-22] query | 投影片封面首頁視覺重構（Editorial Cover Upgrade）
- 結構升級：打破原單一置中排版，升級為高規格書刊雜誌（Editorial Magazine）封面架構。
- 視覺元素：
  1. 頂部 Meta 標籤列（`EVIDENCE-BASED SLEEP MEDICINE` 與呼吸綠燈識別）。
  2. 雙欄 Hero 區塊：左側高階字體排印（大標、修復導引與快捷鍵提示），右側內嵌雙歷程動態模型（Two-Process Dynamics）科學 SVG 曲線圖，標示睡眠之門。
  3. 三大支柱預覽卡片（Pillars Grid）：分立「01 晝夜節律 Process C」、「02 腺苷恆常 Process S」、「03 臨床協議 Protocols」。
  4. 底部嚴謹文獻引用對齊列。
- 更新檔案：`slides/index.html`。
