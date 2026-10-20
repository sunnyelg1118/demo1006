# 依洛嘉面膜保養官方旗艦店

依洛嘉 E.L.G（平價保養品第一品牌）官方網站 — 純 HTML／CSS 打造，莫蘭迪色系、雜誌編輯風格，支援 RWD（桌機／平板／手機）。

## 頁面

| 頁面 | 說明 |
|------|------|
| [index.html](index.html) | 首頁：主視覺輪播、分類快捷、促銷橫幅、新品上市、品牌信任區、社群連結 |
| [contact.html](contact.html) | 聯絡我們：聯絡資訊、線上留言表單、Google Maps 門市地圖 |
| [downloads.html](downloads.html) | 面膜相關檔案下載：`files/原料` 資料夾內 MSDS／COA 等 PDF 文件下載列表 |
| [cloud-downloads.html](cloud-downloads.html) | 面膜雲端相關檔案下載：同一批文件的 Google 雲端硬碟連結列表 |

## 技術

- **純 HTML + CSS**，無前端框架、無建置流程
- 僅有一處用到原生 JavaScript：`IntersectionObserver` 實作區塊滾動淡入效果（沒有 JS 時內容仍會正常顯示，不影響閱讀）
- 圖示系統：所有圖示皆為內嵌 SVG sprite（`<symbol>` + `<use>`），無外部圖示套件／CDN 依賴
- 字體：Google Fonts（Noto Serif TC／Noto Sans TC）

## 設計系統

- **色系**：莫蘭迪低飽和灰調，色票定義於 [css/style.css](css/style.css) 的 `:root`
- **風格**：雜誌編輯風，大留白、不對稱版面
- **RWD 斷點**：桌機 ≥1024px／平板 768–1023px／手機 <768px，手機選單為手風琴（`<details>`／checkbox hack，不需 JS）

## 本機預覽

專案根目錄沒有安裝 Node／Python，改用 PowerShell 內建 `HttpListener` 寫了一個簡易靜態伺服器：

```bash
# 使用 Claude Code 內建瀏覽器預覽（會自動依 .claude/launch.json 啟動）
# 或手動執行：
powershell -NoProfile -ExecutionPolicy Bypass -File .claude/serve.ps1
```

伺服器會在 `.claude/launch.json` 指定的 port 啟動，正確處理含中文檔名的路徑（`[uri]::UnescapeDataString`）與 PDF 等常見 MIME type。

## 目錄結構

```
├── index.html              # 首頁
├── contact.html             # 聯絡我們
├── downloads.html            # 原料檔案下載（本機 PDF）
├── cloud-downloads.html      # 原料檔案下載（Google 雲端連結）
├── css/style.css             # 全站樣式（色票、版面、RWD、互動效果）
├── files/原料/                # MSDS／COA 等原料文件 PDF
├── assets/                   # 靜態資源（預留）
├── elg-*.md                  # 原站（elg.com.tw）選單／輪播／商品／社群資料整理
└── .claude/                  # 本機預覽伺服器設定
```

## 待補事項

- 主選單中「保養／彩妝／膠囊系列…」等分類子項目、以及「分類快捷區」卡片目前連結皆為 `#` 佔位，對應的分類頁面尚未建置
- 聯絡我們的線上留言表單目前為純前端（`action="#"`），尚未串接後端或第三方表單服務，送出不會真的寄出訊息
