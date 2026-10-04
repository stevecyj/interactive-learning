# 額外互動學習工作流調查

調查日期：2026-10-04（GitHub API 星數首次查詢約 11:48 UTC；部分於 11:51 UTC 再核對）

這一輪補查 [Skill 候選詳查](skill-candidates.md) 以外的路線。目標是補查不同的 source → interactive／teaching／motion／presentation 路線，尤其是 H5P／Lumi、講義與簡報轉換、互動論文和動畫 authoring。

## 讀取範圍與限制

- 沒有安裝任何套件、Skill 或遠端腳本。
- 只讀官方 GitHub repo 的 README、官方文件或官方示例索引；沒有把搜尋摘要或第三方文章當成能力證據。
- 表中的 stars 是整個 repo 的星數，不是單一功能的品質評分；後續會變動。首次 API 查詢約 11:48 UTC。再次查詢的原始資料見 [快照](github-snapshot-2026-10-04.json)；Scrollama、Living Papers、Motion Canvas、Math-To-Manim 的首次查詢只保存精簡欄位，已一併收錄；這四項與 Fidyll 的重查遇到 API rate limit，另保留錯誤紀錄。Fidyll 的 10 stars 由官方 GitHub 頁面核對。
- 「驗證深度」標的是讀取證據，不代表我已驗收成品。這一輪沒有逐一在瀏覽器操作 live demo；標示「未操作成品」的項目不能視為已通過本專案的手機、鍵盤、離線或數值 QA。

## 候選工作流

| 來源（類型；repo stars） | source → interactive／teaching 要解決什麼 | 成本與本專案邊界 | 驗證深度 |
|---|---|---|---|
| [H5P Course Presentation](https://h5p.org/presentation)／[Interactive Book](https://h5p.org/content-types/interactive-book)（官方內容類型／教學工作流；無單一 repo 星數） | 把課文、圖片、影片和小測驗組成投影片或多頁互動書；Course Presentation 支援逐頁導覽、選擇題、填空、互動摘要與分支式自訂導覽，Interactive Book 可把多種活動串成一課。這是「靜態教材段落 → 可操作內容區塊」的成熟內容模型。 | 通常需要 H5P 編輯器或 LMS，輸出是 H5P package／平台內容；不會直接讀本專案的 `brief.md`，也不保證一個無外部資源的 HTML。可借用頁／活動／作答／摘要的資料模型，不能當現有單檔生成器。 | 已讀 H5P 官方內容說明與作者教程；未實際建立或操作內容。 |
| [Lumi](https://github.com/Lumieducation/Lumi)（桌面 H5P authoring；194）／[offline editor 說明](https://lumi.education/en/lumi-h5p-offline-desktop-editor/) | 在桌面離線建立、編輯、預覽 H5P；官方站列出 HTML、SCORM、H5P 等匯出路徑。適合把參考講義先整理成可試做的互動課件，再分發或嵌入。 | 需要安裝桌面編輯器和 H5P content libraries；匯出的 HTML 是否完全符合本專案的單檔、`file://`、無 CDN 條件，要逐份檢查。它是 authoring tool，不是 Agent skill，也沒有 `brief`／source ledger 契約。 | README 很簡短；已讀 repo 說明和官方離線／匯出文件，未安裝或操作匯出結果。 |
| [h5p-standalone](https://github.com/tunapanda/h5p-standalone)（H5P 播放器；346） | 將 `.h5p` 解壓後的 `content.json` 和 libraries 在一般 HTML 中播放，讓 H5P 互動脫離 LMS；可作為既有 H5P 內容嵌入 Astro 的橋接層。 | README 的手動流程仍需要 player 的 `main.bundle.js`、`frame.bundle.js`、CSS、內容資料夾和可存取路徑；通常不是單一 HTML，而且 `file://` 可能遇到路徑／資源限制。它只負責 render／player，不負責把 source 轉成教學狀態或回饋。 | 已讀官方 repo README、使用方式和範例連結；未下載 release、未啟動本地 server 或瀏覽器驗證。 |
| [Quarto](https://github.com/quarto-dev/quarto-cli)（Markdown／notebook publishing；6,051）／[HTML self-contained](https://quarto.org/docs/output-formats/html-basics)／[Reveal presentations](https://quarto.org/docs/presentations/revealjs/presenting) | 以 `.qmd`、Markdown 或 notebook 維持「敘事文字＋可執行程式＋引用」，一次產生 HTML、PDF、Word、書籍或 Reveal.js 簡報；可插入 Jupyter／Observable／htmlwidgets，適合把 reference 教材保留為可重建的 source。`embed-resources: true` 可將 CSS、JS、圖片嵌入單檔。 | 需要 Quarto／Pandoc，互動程式又可能需要 Python、R、Julia、Jupyter 或外部 widget；官方也說動態載入的 JavaScript 可能無法被嵌入，某些 speaker／zoom 功能在離線 self-contained 輸出會失效。它能補 source-to-output 的出版管線，但不會自動做 prerequisite map、三題逐步解答。 | 已讀官方 README、HTML self-contained、authoring 與 Reveal 文件；未在本機 render 或檢查產物。 |
| [MyST Markdown](https://github.com/jupyter-book/mystmd)（科學文件／互動書；525）／[官方 overview](https://mystmd.org/overview) | 從 MyST Markdown／Jupyter Notebook 產生互動網站、線上書、論文、PDF、LaTeX 和 Word；內建 citations、cross-reference、AST 與可執行文件觀念，適合將來源講義轉成可引用的長篇教材。 | Node／npm、主題與 web libraries 是主要成本；互動計算可連 JupyterHub、Binder 或瀏覽器 Python，與真正離線單檔有明顯差距。它提供出版結構和來源可追溯性，不提供本專案的單一 state、互動圖形同步或 answer-gated feedback。 | 已讀 repo README、官方 overview／quickstart；未安裝、未啟動 MyST site、未操作 gallery。 |
| [Slidev](https://github.com/slidevjs/slidev)（Markdown → 可互動簡報；48,921）／[syntax guide](https://sli.dev/guide/syntax) | 以 Markdown 分隔投影片，必要時嵌入 Vue component、live code、Mermaid、LaTeX；支援 presenter mode、逐步內容、畫筆、錄影和 PDF／PNG／PPTX 匯出。可參考「每一步只 reveal 一個結構」和「簡報 source 與互動元件同檔」的做法。 | Node 22.12+、Vite、Vue、UnoCSS 和 npm ecosystem；不是 zero-dependency 單檔 authoring，且 slide deck 不是自然的手機 reflow lesson。它適合動態簡報輸出或 prototype，仍須自行加入 `brief`／references grounding、狀態模型和情境題。 | 已讀官方 README、syntax guide 和輸出能力；未建立 deck、未操作 presenter／mobile／PDF。 |
| [reveal.js](https://github.com/hakimel/reveal.js)（HTML／Markdown presentation runtime；72,376）／[official docs](https://revealjs.com/) | 將 HTML 或 Markdown 變成瀏覽器簡報，提供巢狀投影片、fragments、Auto-Animate、speaker notes、LaTeX、PDF export 和 API；適合作為現有「上一步／下一步／鍵盤」的 presentation runtime。 | 需要打包或自帶 framework assets；它只定義 slide／fragment／transition，沒有學習前置、來源證據、互動計算或答題回饋。可借導覽和 reveal sequencing，不能取代教學 prompt；離線是否完整取決於資產是否內嵌。 | 已讀官方 repo README 和 docs 索引；未實際 build、開啟 demo 或檢查 offline bundle。 |
| [Observable Framework](https://github.com/observablehq/framework)（Markdown + reactive JavaScript data app；3,657）／[docs](https://observablehq.com/framework/)／[examples](https://github.com/observablehq/framework/tree/main/examples) | Markdown 頁面可混合 reactive JavaScript、inputs、D3／Observable Plot 和 build-time data loaders；同一變數改變時，圖、表和其他輸出會重算。這是「單一 state 驅動多個表示」與「資料來源 → 圖形探索」的直接參考。 | Node／npm build、資料 loader 和 library imports 是必要成本；預設輸出 static site 而不是單一 HTML，外部資料或 CDN 也會破壞完全離線。它解決 state/render，不處理教學依賴、定義／推導標記或三題解答。 | 已讀 README、官方 docs index 和官方 examples README；未跑 build、未操作 reactive example。 |
| [Scrollama](https://github.com/russellsamora/scrollama)（scrollytelling library；6,002）／[examples](https://russellsamora.github.io/scrollama/) | 把文章中的 `.step` 進入／離開 viewport 事件綁到 sticky graphic、progress 或 scene state；適合將「讀到這一段 → 圖形顯示這個階段」做成連續敘事，而不是讓讀者按下一頁。 | 它只提供 IntersectionObserver 觸發器和進度 callback；作者仍須自己寫 SVG／D3、狀態、語意文字、keyboard fallback、reduced motion 和手機版。需要 JS library（可自行內嵌），與本專案「真正離線單檔」相容性取決於 bundling。 | 已讀 README、API、mobile pattern 和官方範例索引；未操作範例或量測窄螢幕行為。 |
| [Living Papers](https://github.com/uwdata/living-papers)（Markdown → reactive scholarly article；161）／[template](https://github.com/uwdata/living-papers-template/)／[UIST paper](https://github.com/uwdata/living-papers-paper) | 以 Markdown 作為來源，經 AST／compiler／components／runtime 產生互動網頁或正式研究論文；runtime 支援 reactive output，適合研究型教材中將圖表、解釋和引用保持在同一份可編譯 source。 | 需要 Node、Pandoc；R／knitr、LaTeX／TeX 會再增加成本，repo 自稱 research testbed 且有 bugs。輸出偏網站／論文，不是簡單單檔；沒有本專案的學習者卡點、練習回饋或離線 QA。 | 已讀官方 repo README、套件結構和 example/template 連結；未安裝 CLI、未 build article 或操作 runtime。 |
| [Motion Canvas](https://github.com/motion-canvas/motion-canvas)（TypeScript vector animation authoring；19,228）／[introduction](https://motioncanvas.io/docs/)／[project variables](https://motioncanvas.io/docs/project-variables/) | 用 generator／signals 描述逐步動畫，編輯器即時預覽；可把 project variables 綁到文字或視覺屬性，並把聲音與動畫同步。適合把某個難懂的「變化過程」先做成精準 motion storyboard，或輸出 player／影片嵌入教材。 | Node、TypeScript、Vite 和專案套件；影片輸出可用 FFmpeg。它的主要產物是動畫／影片／player，不是單一教學 HTML，也沒有 source evidence、答題或手機／鍵盤規則；只能作為 motion authoring 層。 | 已讀 repo README、官方 introduction、quickstart、animation flow 和 variable docs；未啟動 editor、未 render 或檢查 player。 |
| [Math-To-Manim](https://github.com/HarleyCoops/Math-To-Manim)（AI 教學編排 → Manim motion；2,693）／[showcase](https://github.com/HarleyCoops/Math-To-Manim/tree/main/docs/showcase) | README 描述一條很接近本專案理想的 source-to-explanation 管線：問題／圖片 → learner & prerequisite brief → evidence audit → curriculum／math dossier → storyboard → Manim scene → render frame review；還有公式測試、contact-sheet review 和修復路由。它明確把「先決定學什麼與順序，再寫動畫」放在直接產生畫面之前。 | 強依賴 Manim、Python／FFmpeg，以及 README 所述的 Codex SDK、模型和 TypeSafe Jev；輸出是 MP4／影格／製作紀錄，不是互動 HTML，還是數學／物理專用。適合借用 brief、evidence、storyboard、render QA 的分段契約，不應直接移植成 offline HTML generator。 | 已讀 repo README、pipeline／gate 說明與 showcase 來源；未執行模型呼叫、Manim render 或影格驗收。 |

| [Fidyll](https://github.com/idyll-lang/fidyll)（跨格式敘事 compiler；10）／[論文](https://arxiv.org/abs/2205.09858) | 同一份來源分成 scene、stage、參數、控制項與敘事，再編譯成靜態文章、互動文章、捲動故事、簡報或影片。每個 stage 設定圖形參數；讀者操作控制項時，同一張圖重新呈現。非常貼近「先決定知識如何動起來，再決定輸出形式」。 | README 明示為尚未適合一般使用的研究原型；需要 Node、Idyll 與建置，影片另涉及 Google Cloud／FFmpeg。適合借 scene／stage 的中介結構，不宜現在導入。論文的作者案例與標記量比較不代表讀者學習成效。 | 已讀官方 README 的格式例子與論文摘要；未安裝、未編譯或操作成品。 |

## 這一批對本專案的實際價值

1. **最值得補進 prompt 的是 Quarto／MyST 的 source contract。** 它們把「文字、程式、引用、圖表、輸出格式」視為可重建的來源，適合轉寫成現有 `brief.md`／`references/` 的 evidence ledger；但需保留本專案的單檔與無外部依賴硬限制。
2. **最值得借用互動形狀的是 H5P、Observable、Scrollama。** H5P 示範活動與作答的內容模型，Observable 示範單一 state 對多個輸出的 reactive model，Scrollama 示範文字步驟如何觸發圖形階段。三者要合併時，仍需自己補定義／推導／情境規則和逐步解答。
3. **最值得借用 motion 前製的是 Math-To-Manim 加 Motion Canvas。** 它們把 prerequisite、storyboard、每個變化的視覺目的和 render review 分開；但輸出與依賴都比現有單一 HTML 路線重，適合當內容設計參考，不適合直接加入預設工具鏈。
4. **Slidev／reveal.js 是導覽與 reveal sequencing 參考。** 它們可以改善動態簡報形式，但不會自動讓教材有好的學習推理；現有 prompt 的教學與 QA 規則仍必須保留。
5. **Lumi／H5P 是另一條產品路線，而不是現有 HTML 的小幅擴充。** 如果未來要做 LMS、SCORM、xAPI 或非技術作者編輯，值得另開評估；如果目標仍是 Astro 中可直接開啟的單檔 HTML，直接沿用現有 vanilla HTML 會比較低成本。

## 搜尋後仍不列入的類別

- **Idyll／Tangle** 已在前一份調查處理；本輪不重複。Fidyll 是獨立的跨格式研究原型，已另外收錄，不能和 Idyll 混為一談。
- **一般動畫／視覺套件**（例如只提供 tween、canvas 或 UI transition 的 library）沒有 source grounding、教學編排或輸出契約，因此不列入；Motion Canvas 已代表「可用程式描述教學動畫」這一類。
- **一般 Markdown／PDF converter** 若沒有互動元件、狀態綁定或教學內容模型，不能回答本專案的核心問題，因此沒有為了數量納入。
- **Jupyter／Thebe 類可執行文件** 可以把程式碼變成互動教材，但通常需要 kernel／server 或 WASM runtime；和本專案單檔、離線、無外部套件的限制衝突，暫列為未投入路線。

