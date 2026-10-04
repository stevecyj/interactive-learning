# 查閱與驗證範圍

日期：2026-10-04（Asia/Taipei）。這是調查資料的檢查紀錄，不是教材或候選 Skill 的驗收報告。

## 本地文件

- 檢查專案 README 與本目錄 Markdown 的相對檔案連結和章節 anchor，沒有發現失效項目。
- 兩份 JSON 可解析；GitHub 快照包含 17 個 repository，候選文件包含 26 個編號項目。
- IPv4 `index.html` 的調查前後 SHA-256 一致：`cc89d4f54b6297f5d6220bad1520f3b4cb3db9932040bd6689b348baffb0437d`。
- 六組色值對比是依 WCAG sRGB relative luminance 公式計算不透明純色，不是讀取渲染畫面；精度與適用範圍見 [基線 JSON](current-style-observations.json)。

## 外部來源的補查

2026-10-04 13:00:23 UTC（台北 21:00:23）另以直接 HTTPS GET 抽查下列 12 個來源，讀取回應前 512 bytes。11 個回傳 200；1 個憑證驗證失敗。這只檢查當下入口可用性，不證明全文內容、服務品質，也沒有測全部外部連結。

| 來源 | 結果 |
|---|---|
| [DTCG Color 2025.10](https://www.designtokens.org/tr/2025.10/color/) | 200 |
| [Digital.gov visual preference](https://digital.gov/guides/research-collaboration/testing/visual-preference) | 200 |
| [Khan Academy color system](https://blog.khanacademy.org/how-we-rebuilt-khan-academys-color-system-from-the-ground-up/) | 200 |
| [Duolingo core tabs redesign](https://blog.duolingo.com/core-tabs-redesign/) | 200 |
| [Impeccable new-work 原檔](https://raw.githubusercontent.com/pbakaus/impeccable/main/.agents/skills/impeccable/reference/new-work.md) | 200 |
| [visual-design-direction 原檔](https://raw.githubusercontent.com/sonyabirch/skills/main/visual-design-direction/SKILL.md) | 200 |
| [Realtime Colors 作者文件](https://www.realtimecolors.com/docs/about-realtime-colors) | 200 |
| [Carbon Color](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview) | 200 |
| [UEQ Handbook PDF](https://www.ueq-online.org/Material/Handbook.pdf) | 200 |
| [UI/UX Pro Max brand 原檔](https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/brand/SKILL.md) | 200 |
| [Taste Skill 原檔](https://raw.githubusercontent.com/Leonxlnx/taste-skill/main/skills/taste-skill/SKILL.md) | 200 |
| [Samantha Warren podcast](https://styleguides.io/podcast/samantha-warren/) | TLS 憑證 hostname 不符；未繞過驗證。搜尋工具仍提供原站逐字稿，本輪只讀文字，未聽音訊 |

原始 Skill 與網站文件的連結通常指向 `main` 或現行頁面，未保存全文或固定 commit；日後投入前需重查。Stars 及維護資訊另保存查詢時間，不能當成永久數值。

## 實際操作與未驗證事項

- 六個網站頁面的視覺拆解，見 [視覺指紋](reference-sites-and-videos.md#本輪新增實際畫面指紋)；這是畫面觀察，不是受眾反應或完整操作驗收。
- Realtime Colors 改 Primary hue、Huemint 按 Generate，均確認同版面預覽連動；見 [操作紀錄](audience-and-reference-analysis.md#實際瀏覽器操作紀錄)。沒有登入、匯出方案或為專案選定配色。
- 影片以官方入口／metadata 為主，部分演講另讀逐字稿；逐項標記，未將搜尋標題當成已觀看內容。部分 YouTube 觀看頁擷取失敗，未補成完整字幕分析。
- 沒有安裝或執行候選 Skill，沒有修改教材、共用 prompt 或 AGENTS.md，沒有建立新 Skill／DESIGN.md／token pipeline。
- 沒有招募受眾、施測量表或比較學習效果；也沒有對現有教材做完整手機、鍵盤、讀屏或 WCAG audit。
