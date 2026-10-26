# ETF 總報酬雷達 — 自動更新開發版

本版新增 `auto_update.py`、GitHub Actions 排程與 `market_data.json` 產出機制。

## 尚未完成
- 尚未部署；下載 HTML 不會自行執行雲端排程。
- 目前只有指定的 13 檔台美 ETF，不是全市場，也不含共同基金。
- 資料更新成功與否取決於第三方 API、速率限制、行情授權和服務穩定性。
- 還原價格只是含息報酬的近似計算，尚未獨立核對每筆現金股利、稅費、匯率與資料調整方法。

## 部署方式
1. 將此資料夾上傳至你自己的 GitHub 儲存庫（含 `.github/workflows/update.yml`）。
2. 在儲存庫 Settings → Secrets and variables → Actions 新增 `FINMIND_TOKEN`（從 FinMind 取得；不要寫進網頁）。
3. 在 Actions 頁面手動執行 `Update market snapshot` 測試；成功後會生成 `market_data.json`。
4. 在 Settings → Pages 設定從 main 分支根目錄部署。
5. 此排程採 UTC 23:15，週一至週五執行，並非保證所有市場最新收盤資料均已發布。

## 下一階段
- 從完整上市標的清單自動發現代碼，分批增量更新，控制 API 費用。
- 補上基金淨值與配息來源、美元換算台幣、股息現金流與股息再投入分別計算。
- 納入存活偏差、資料缺口和基金存續時間提示。
