# 追加候選池：互動教學、工程知識與視覺敘事

調查日期：2026-10-04  
用途：在 [互動案例詳查](interactive-cases.md) 之外，擴大搜尋原作者／官方案例與製作方法。這份檔案是候選池，不是安裝清單，也不改變目前「單檔、離線、原生 HTML/CSS/JS 優先」的交付限制。  
篩選原則：優先使用原作者、官方專案、官方文件或原始研究論文；人氣、獎項與研究成效分開記錄；沒有實際操作的項目明確標示。

## 閱讀深度

- **深**：讀官方頁面／README／文件的主要說明，足以整理互動模式與限制；未必逐項操作。
- **中**：讀官方首頁與部分文件或程式碼摘要。
- **淺**：只核對官方入口、索引或論文摘要，留待後續深入。
- 本輪沒有安裝套件、執行建置或宣稱完成瀏覽器驗收；下表的「限制」優先記錄是否需要 framework、server、外部資料或帳號。

## 候選表

| URL | 分類 | 可借用的方法 | 讀取深度 | 限制／目前判斷 |
|---|---|---|---|---|
| [LearnGitBranching live](https://learngitbranching.js.org/)；[原始碼與 README](https://github.com/pcottle/learnGitBranching) | 工程／Git／步進 | 把 Git 指令放進安全沙盒；每個指令立即更新 commit tree，並以 level、challenge、undo、reset 形成「操作—結果—重試」循環 | 深：官方 README 與架構說明 | 產品是 client-side，但建置需要 Yarn／Gulp；產出的 JS/CSS 不會自動變成目前要求的單一 HTML。可借用狀態樹、可復原操作與逐題挑戰 |
| [SQLBolt](https://sqlbolt.com/) | 工程／資料庫／練習 | 每課只處理一個 SQL 任務，在編輯器中執行查詢、回饋結果，再進到下一個概念；資料集保持小而具體 | 中：官方課程入口與課程內容 | 查詢執行與課程 runtime 是網站的一部分；不應直接嵌入離線教材。可借用「真實任務先於語法總覽」與錯誤後立即說明 |
| [ASM Visualizer](https://asm.diveintosystems.org/)；[OS Simulator — NITK CSE OS Lab](https://rvbilimagga.github.io/OS-simulator-v2/index.html) | OS／CPU／編譯器／狀態轉移 | ASM 將指令、暫存器、stack 與執行步驟對照，並以算術／函式／完整程式三種模式逐步增加複雜度；其母教材 Dive into Systems 才是 high-level code 到 binary、circuits、OS 的垂直切片；OS Simulator 以 CPU scheduling、process、memory、storage 的 Gantt、buffer、resource-allocation 讓演算法逐步可見 | 深／中：前者讀官方課程定位，後者讀 live page 與模組描述 | 兩者都是大型教材／互動工具，非單檔模板；OS Simulator 顯示 17 個模組，實際維護／相容性仍要逐項驗證。可借用「每層只依賴上一層」與「同概念多案例、step／reset」 |
| [nand2web](https://cs.n10u.jp/) | 非數學 CS／硬體到網路 | 明確要求由 NAND gate 向上走，每層建立在前一層；compiler pipeline 可把小程式逐步展示成 lexer → token → parser → AST → evaluation | 深：官方首頁與 layer／compiler 說明 | 需要完整互動 runtime，且內容量大；可移植的是「跨層剖面」和「每層都有可破壞的 simulator」，不必照搬課程 |
| [Gapminder Tools](https://www.gapminder.org/tools/)；[官方操作指南](https://www.gapminder.org/tools/assets/guide.pdf) | 資料故事／統計／時間變化 | 讓讀者選國家、軸、顏色、泡泡大小、線性／對數尺度、時間播放與 trails；同一資料可切換視角而不失去來源資訊 | 深：官方工具入口與 PDF 指南 | 需資料服務與前端 runtime；動畫容易讓讀者只看趨勢而忽略尺度、選取與來源。可借用「固定一組資料、一次只換一個視角」及播放／停止／比較 |
| [Our World in Data — Grapher 文件](https://docs.owid.io/projects/grapher/)；[官方互動圖表](https://ourworldindata.org/) | 資料故事／來源／可重現圖表 | 圖表以 JSON config 加表格資料描述，能切換 entity、年份、指標與下載資料；資料與圖表設定分離 | 深：官方文件與網站說明 | `@ourworldindata/grapher` 目前是受限的私有套件，且常用 API／資料服務；不適合目前離線輸出。可借用「資料來源、圖表設定、讀者狀態」三層分離與可回溯設定 |
| [DAGitty](https://www.dagitty.net/)；[官方互動教學](https://www.dagitty.net/learn/index.html) | 因果／圖層／判斷 | 讀者新增、刪除、重新命名節點與箭頭；系統同步標示 causal path、biasing path、adjustment set、moral／correlation graph 等不同圖層 | 深：官方首頁、learn、manual 入口 | 工具是研究用 DAG 編輯器，完整分析比本專案複雜；官方 repo 說明部分功能可本地開啟，但載入／儲存模型仍可能需要網路。可借用「同一結構切換不同解讀圖層」與因果高亮 |
| [The Universe To Scale](https://universetoscale.com/) | zoom／morph／時間與尺度 | 拖曳、捲動、pinch、`+/-` 在 Planck length 到宇宙尺度與宇宙歷史之間移動；點擊 milestone 進入局部故事，另有 tour 與 compare spans | 深：官方頁面主要互動說明與控制項 | 依賴大量圖像、字型、音訊與 YouTube 影片；不適合單檔複製。可借用「大尺度先保留方位，再逐層放大」以及點擊後顯示局部敘事 |
| [HHMI BioInteractive Interactive Video Builder](https://interactive-video-tool.biointeractive.org/create?page=0)；[官方資源首頁](https://www.biointeractive.org/) | 非數學知識／生物／影片分段 | 在已有影片或動畫上加 labels、text boxes、multiple-choice、true／false、free-text；可依主題、年級與資源類型篩選，將觀看變成可回答的步驟 | 深：官方工具頁與資源分類 | 建立互動影片需要 BioInteractive 帳號，影片／平台不是單檔離線；可借用「媒體片段 → 暫停問題 → 即時回饋 → 進下一段」的教學節點 |
| [Chrome Music Lab](https://musiclab.chromeexperiments.com/)；[官方原始碼](https://github.com/googlecreativelab/chrome-music-lab)；[wavesurfer.js](https://wavesurfer.xyz/examples/) | 波形／音訊／非數學探索／zoom | Chrome Music Lab 的 Sound Waves、Spectrogram、Song Maker 把聲音、節奏、頻率、圖形與操作結果立即連起來；wavesurfer.js 補充播放、拖曳定位、zoom、region、timeline、spectrogram 與 pre-decoded peaks | 深／中：前者讀官方首頁、Google 介紹與 repo，後者讀 docs、repo 與 spectrogram API | Chrome Music Lab repo 已 archive，且多數實驗用 Web Audio、Tone.js、WebMIDI；wavesurfer 需要 library、CORS，預設解碼整個音檔並受檔案大小／記憶體限制。只借用「音訊輸入／參數 → 波形或頻譜 → 可聽見結果」，單檔時用原生 Canvas 與內嵌資料 |
| [Scrollama](https://github.com/russellsamora/scrollama)；[官方 examples](https://github.com/russellsamora/scrollama/tree/main/examples)；[Google scrollytell examples](https://google.github.io/scrollytell/examples/) | 互動文章／sticky／step trigger／原生 HTML | Scrollama 以 IntersectionObserver 觸發 step，支援 side-by-side sticky、overlay、progress、mobile offset；Google 範例則把 CSS／JS 嵌在 HTML，展示 no chart、centered chart、sticky chart、fullsize canvas | 深：兩者官方 README／examples | Scrollama 需要 library；舊瀏覽器可能需要 polyfill，手機 offset 與鍵盤導覽也需另外設計；Google 專案較早，需重查瀏覽器／無障礙，D3 範例不符合零依賴。可提供捲動同步，但不應取代鍵盤上／下一步 |
| [The Pudding `svelte-starter`](https://github.com/the-pudding/svelte-starter)；[responsive-scrollytelling starter](https://github.com/the-pudding/responsive-scrollytelling) | Svelte／D3／The Pudding 製作方法 | 前者提供資料驅動故事的 SvelteKit、LayerCake、CSV／JSON／SVG 匯入與 static build；後者把文字 steps 對到 visualization callbacks，並提供 CSS inlining 與部署流程 | 深：官方 GitHub README 與組織頁 | 明確需要 Node、npm、SvelteKit／Gulp／打包，且含字型、資料與資產流程；不是目前單檔方案。可借用目錄分工、文字／視圖 callback 對應與 build 時把 CSS 內嵌的思路 |
| [Svelte interactive tutorial](https://svelte.dev/tutorial/svelte/welcome-to-svelte)；[tutorial source](https://github.com/sveltejs/learn.svelte.dev) | 元件式互動／循序教學 | 每個小節用一個可執行 exercise，讀者可以在瀏覽器編輯、執行、比較初始／解答；教程本身把前一節概念作為下一節前置 | 深：官方 tutorial 與 repo README | 主要是學 Svelte 的平台，輸出視為 build artifact 而不是離線教材；可借用「每一步有可執行的最小修改」與「解答揭曉前先自己改」 |
| [D3 getting started](https://d3js.org/getting-started)；[D3 官方首頁](https://d3js.org/) | D3／可重用互動／zoom／brush | 官方將 scale、shape、layout 與 pan／zoom／brush／drag 分成可組合能力，並提供 area、bar、donut、histogram、line starter templates | 深：官方文件與 starter template 說明 | D3 只是繪圖／資料處理工具，不提供教學敘事；官方 vanilla HTML 範例推薦 CDN 或本地 bundle，與本專案不載入外部依賴衝突。只借用資料→SVG→事件的分層，必要時原生重寫 |
| [Curvenote `article`](https://github.com/curvenote/article) | 可重用 explorable component／reactive document | 以 web components 表示 reactive variables、方程式、圖表與 layout；文字中的 dynamic／display 元件可直接綁定變數 | 深：官方 README 與元件用法 | 預設要 `@curvenote/article`、CSS、runtime 或 npm；雖可下載 release，但需實際打包才能判斷 offline。可借用「作者以語意標籤描述互動」及把變數／顯示分開 |
| [Concord Consortium Lab Interactives](https://lab.concord.org/) | 科學模型／可組合元件／探究 | JSON 定義的 sharable／embeddable／authorable components，把模型包在 buttons、checkboxes、sliders、graphs 等 inquiry UI 中；同一模型可問「改參數後會怎樣」 | 深：官方 Lab 頁面與範例描述 | 需要模型 runtime、嵌入資產與教學作者環境；不直接符合單檔，但對「references 中有模型／資料時如何包成探究控制項」很有參考價值 |
| [Towards a Survey of Interactive Visualization for Education](https://diglib.eg.org/server/api/core/bitstreams/b47f72ba-d3ae-492f-9aac-fc5c9871c725/content) | 互動教學研究／分類 | 以教育視覺化研究為對象整理分類，適合把案例依「教什麼、誰操作、何時回饋、如何評量」而非依網站外觀分類 | 淺至中：讀論文摘要與分類說明 | 是研究 survey，不是可直接套用的 UI；分類年份較早，需與新工具、無障礙與 AI 生成教材分開核對。可作為本專案的 references 索引起點 |
| [Dynamic／interactive visualisation 的 active integration 研究](https://doi.org/10.1016/j.learninstruc.2004.06.006)、[interactive 與 non-interactive pictures 研究](https://doi.org/10.1016/j.learninstruc.2009.02.008)、[Interactivity Enriching Features 研究](https://doi.org/10.1016/j.compedu.2014.11.018)、[visual explanations 研究](https://link.springer.com/article/10.1186/s41235-016-0031-6) | 互動教學研究／成效與邊界 | 研究共同提醒：互動不是自動有效；需引導學習者整合符號與圖、限制可探索變數、要求解釋或預測，並檢查不可見元件、功能、順序與因果是否都被表達 | 深：讀摘要與可取得的完整文章段落 | 研究情境、年齡、題材與評量各不相同，不能直接推成「本專案 HTML 一定有效」。可用來支撐 prompt 中的 constrained exploration、predict-then-reveal、逐步揭曉與 explanation check，而非用來替代瀏覽器驗收 |

## 按互動型態整理

這批新增候選最容易移植的不是外觀，而是以下幾種「狀態映射」：

- **剖面／分層**：`ASM Visualizer`、`nand2web` 將一個系統拆成由下而上的層；AWS 可用「位元 → CIDR → 路由／子網」或網路可用「應用 → HTTP → TCP → IP → link」呈現。
- **步進／狀態樹**：`LearnGitBranching`、`OS Simulator`、`Svelte tutorial` 讓一次操作只造成一個可追蹤的轉移；適合把命令、封包或計算結果對到固定步驟。
- **zoom／morph／多視角**：`The Universe To Scale`、`Gapminder`、`DAGitty` 不是單純放大圖片，而是切換尺度、時間、圖層或解讀方式；每次切換都要保留讀者的定位與圖例。
- **因果／模型檢查**：`DAGitty`、`Concord Lab`、Chrome Music Lab 的聲音實驗都把參數和結果連在一起；讀者改變條件後，畫面應指出哪個中間狀態先改變。
- **文字驅動圖形**：`Scrollama`、`scrollytell`、The Pudding starter 將每個文字 step 對應到一個 render callback；手機版需提供順序閱讀和明確控制，不能只靠捲動觸發。
- **作者語意層**：Curvenote 將 reactive variable 與顯示元件寫成可檢查的結構；已有的 `explorable-skills`／ViviDoc 詳查另見總報告；這比在 prompt 裡只說「做漂亮互動」更容易驗證。

## 追加結論

1. 工程知識的好案例通常把「命令、模型、狀態、結果」放在同一個可復原循環裡；Git、SQL、OS、編譯器案例都比純概念目錄更接近本專案的實際任務導向。
2. 資料故事的核心不是動畫，而是固定資料和來源後，讓讀者只改變一個切片、時間或尺度，並持續保留座標、圖例與選取狀態。
3. scrollytelling、Svelte、D3 與可重用元件都很適合未來 Astro／網站版本，但它們大多有 build／runtime；目前單檔版本應先把 callback、狀態與圖層方法用原生 HTML／SVG／Canvas 實作。
4. 研究證據支持「受約束的操作、預測、解釋、跨表徵核對」比無目的自由玩更值得投入；它沒有支持「互動越多越好」。
5. 最值得後續人工深讀的新增三條路徑是：`nand2web` 的系統分層、`LearnGitBranching` 的操作—狀態樹、以及 Curvenote／Concord Lab 的模型與顯示元件分工。它們提供的是可移植的製作方法，不代表現在應安裝。

## 本輪搜尋與驗證記錄

本輪依序查找：

- 工程／系統：`interactive Git visualization`、`SQL interactive lessons`、`OS simulator visualizer`、`assembly visualizer`、`NAND to web interactive`。
- 資料／故事：`Gapminder official tools`、`Our World in Data Grapher docs`、`interactive data story official`。
- 互動模式：`causal diagram interactive DAGitty`、`zoom scale explainer official`、`scrollytelling official examples`、`Svelte D3 starter template`、`reusable explorable web components`。
- 音訊：`Chrome Music Lab spectrogram official`、`wavesurfer.js official waveform`。
- 研究：`interactive visualization learning taxonomy`、`active integration dynamic interactive visualizations`、`interactivity enriching features learning`、`creating visual explanations learning`。

本輪以官方頁、官方 README、官方文件和原始論文為主；只讀取網頁與文件，未在瀏覽器逐一操作上述案例，也未安裝任何依賴。獎項、stars 或作者自述若日後放入決策表，仍應與學習成效研究分欄。
