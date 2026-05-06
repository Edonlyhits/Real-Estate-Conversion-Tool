# 房地產換算神器 · Real Estate Converter

> 專為業務設計的單頁換算工具，快速將迪拜房產的面積與價格換算成台灣買家熟悉的單位與幣別。

---

## 功能總覽

### 01 · 面積換算
- 支援三種單位雙向即時換算：**m²（平方公尺）、ft²（平方英尺）、坪**
- 任一欄位輸入後，其他兩欄自動同步更新
- 換算常數：`1 m² = 10.7639104 ft²`、`1 m² = 0.3025 坪`

### 02 · 單價計算
- 輸入 AED 總價 + 面積，自動計算：
  - **AED / m²**（每平方公尺，國際慣用）
  - **AED / ft²**（每平方英尺，迪拜市場主流）
  - **TWD / 坪**（每坪台幣，台灣買家直覺單位）

### 03 · 總價換算
- AED 總價自動換算為：
  - **TWD**（新台幣）
  - **USD**（美元）
  - **EUR**（歐元）

### 04 · 即時匯率
- 串接 [open.er-api.com](https://www.exchangerate-api.com) 取得即時匯率（Base: AED）
- 顯示 USD、EUR、TWD 三組匯率
- 顯示最後更新時間（HH:MM 格式）
- 刷新按鈕帶旋轉動畫，防止重複點擊期間 UI 誤操作

### 05 · 點擊複製
- 所有結果數值（單價 × 3 + 總價 × 3）均可**點擊直接複製**至剪貼簿
- 支援 `navigator.clipboard` API，並附 `execCommand` 降級備援
- 複製成功後底部顯示 Toast 提示「已複製 ✓」

### 06 · 輸入驗證
- 輸入負數 → 顯示紅色錯誤提示「數值不可為負數」
- 輸入非數字內容 → 顯示「請輸入有效數字」
- 錯誤狀態時輸入框呈紅色外框

### 07 · 一鍵清除
- 標題列的「✕ 清除」按鈕一次清空所有輸入欄位與錯誤訊息

---

## 技術規格

| 項目 | 說明 |
|---|---|
| 類型 | 純前端單頁應用（Single HTML file，無框架、無依賴） |
| 字型 | Inter（UI）、IBM Plex Mono（數字/代碼）via Google Fonts |
| 匯率 API | `https://open.er-api.com/v6/latest/AED`（免費公開，無需 API key） |
| RWD 斷點 | `≤ 440px`：面積輸入欄與單價結果格由 3 欄改為 2 欄 |
| 主題 | 白底淺灰配色，點陣背景，卡片載入帶 `fadeUp` 動畫 |
| 複製機制 | `navigator.clipboard.writeText` + `execCommand('copy')` 降級備援 |

---

## 使用方式

無需安裝，直接用瀏覽器開啟 `index.html` 即可。

```
open index.html
```

或部署至任何靜態網頁主機（GitHub Pages、Vercel、Netlify 等）。

---

## 檔案結構

```
Real-Estate-Conversion-Tool/
└── index.html     # 工具本體（CSS + HTML + JS 全部內嵌）
└── README.md
```

---

## 資料來源

匯率資料由 [ExchangeRate-API](https://www.exchangerate-api.com)（open.er-api.com）提供，每次開啟頁面或手動點擊刷新時更新。匯率僅供參考，實際交易請以銀行報價為準。
