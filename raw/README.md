# 原始素材庫（Raw Sources）

本目錄為「睡眠科學 LLM Wiki」的原始資料層，所有存放於此的檔案均為**唯讀且不可變（Immutable）**。

## 建議存放分類
- `podcasts/`：音訊節目的重點筆記或逐字稿（如 Huberman Lab、The Peter Attia Drive、FoundMyFitness）
- `books/`：睡眠權威書籍摘要與摘錄（如 Matthew Walker《為什麼要睡覺》）
- `guidelines/`：臨床與專業睡眠醫學機構發布指南（如 AASM 美國睡眠醫學會、Sleep Foundation、NSF）
- `papers/`：同儕審查學術期刊論文（PubMed 摘要、文獻全文）

## 使用說明
當您將新的 Markdown 或純文字檔案放置於本資料夾中後，只需對 LLM 說：
> 「請幫我將 `raw/podcasts/xxxx.md` 匯入知識庫」

LLM 即會依據 `AGENTS.md` 中的 **Ingest Workflow**，自動建立來源摘要、萃取概念與介入方式、檢查觀點矛盾、更新 `wiki/index.md` 並記錄於 `wiki/log.md`。
