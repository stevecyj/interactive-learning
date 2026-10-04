# 互動式教學與視覺化案例調查

調查日期：2026-10-04  
調查目的：為本專案的「`brief` + `references` → 單檔、可離線使用的互動式教學」找可移植的設計方法、案例與未來可評估的 Skill。  
調查狀態：三輪搜尋；未安裝任何 Skill、套件或依賴，也沒有修改既有教材、提示詞或 `AGENTS.md`。

## 先給結論

本專案最值得保留的核心方向，是把靜態資料或公式拆成一條可觀察的鏈：

> **輸入／條件 → 中間狀態或運算步驟 → 視覺表徵 → 數值與文字結果 → 邊界／判斷**

這個方向不依賴教材主題。AWS CIDR 可以把「前綴長度、主機位元、位址範圍、保留規則」串起來；網路協定可以把「封包欄位、編碼、狀態轉移、回應」串起來；演算法可以把「資料結構、每一步的選擇、複雜度」串起來。線性代數或機率案例若有好效果，應借用的是這種映射方法，不是把數學主題本身列為本專案教材方向。

目前最值得先研究的組合如下：

1. **教學敘事**：借用 [Nicky Case 的 explorable explanation 方法](https://blog.ncase.me/how-i-make-an-explorable-explanation/)：先由一個可感知的問題開始，逐步建立抽象，再以沙盒讓讀者提出自己的「如果……會怎樣？」。
2. **同步的圖解與步進**：借用 [Red Blob Games 的 A* 互動說明](https://www.redblobgames.com/pathfinding/a-star/introduction.html) 以及 [Python Tutor](https://pythontutor.com/) 的「目前步驟、來源、狀態、結果一起變」。這最接近目前 AWS Subnet 初稿想做的事情。
3. **多重表徵與即時回饋**：借用 [PhET 的設計原則](https://phet.colorado.edu/en/research/design-principles)，同一個變化同時在圖形、數字、文字或量測工具中顯示，並限制控制項讓因果關係容易看出來。
4. **單檔交付與互動契約**：先評估 [explain-this](https://github.com/analyticalmonk/explain-this)、[html-explainer](https://github.com/ds-vibe/html-explainer)、[teaching-explainer](https://github.com/rlfordon/teaching-explainer) 與 [html-artifacts](https://github.com/joshuadavidthomas/agent-skills/tree/main/html-artifacts)。它們的目標與「自包含 HTML、研究後才產出、互動要回答讀者問題」相近，但目前只做資料閱讀，沒有安裝或採用任何一個。
5. **可攜的實作先例**： [GILP 論文](https://arxiv.org/abs/2210.15655) 展示以互動 HTML 讓學習者不必安裝工具；[Apex](https://github.com/pen-pal/apex) 則展示工程與網路主題如何把模型、測試不變量與畫面分開。兩者都能提供架構靈感，但不能直接當成本專案的離線依賴。

沒有一個案例同時證明「一定能學會」、適合所有主題、又能直接輸出單檔離線 HTML。因此後續應分開評估：

- **學習成效證據**：PhET 的研究與訪談、Python Tutor 的研究論文等。
- **作者方法與呈現品質**：Red Blob、Nicky Case、Distill、Google PAIR 等。
- **工具人氣或維護訊號**：GitHub stars、獎項、使用者數。這些是聲譽或採用度訊號，不是學習成效證據。
- **本專案工程相容性**：是否能在不載入 CDN、不需伺服器、不需讀取外部檔案的情況下交付單一 HTML。

## 閱讀與實際驗證範圍

- 已閱讀各案例的官方網站、官方 README、作者文章或論文；報告中的外部連結都指向原作者、官方專案、論文或官方影片頁。
- 在可用瀏覽器中實際操作 [Red Blob A*](https://www.redblobgames.com/pathfinding/a-star/introduction.html)：點擊一次步進後，步數、圖解與程式／狀態顯示同步改變，確認互動不是單純換頁。
- 在可用瀏覽器中開啟 [Seeing Theory](https://seeing-theory.brown.edu/)，點擊 `Chance Events` 章節，確認頁面可載入並能進入互動章節；沒有逐項操作所有控制項。
- 其他案例是閱讀其官方內容或程式碼結構，沒有聲稱已驗證每個互動、每個瀏覽器或離線下載結果。
- 影片部分只核對原作者頁面與影片 URL 的身份／描述，沒有把未觀看的影片內容當成已驗證結論；詳見「作者影片與演講」。
- GitHub stars 是 2026-10-04 的查詢快照，整理在 [`github-snapshot-2026-10-04.json`](./github-snapshot-2026-10-04.json)。star 數會變動，而且不能代表學習效果。

## 可移植的設計方法

以下是從案例中抽出的、與主題無關的設計單位。它們比複製某個網站的外觀更適合放進共用提示詞或日後的檢查表。

| 設計單位 | 讀者應看到什麼 | 套到 AWS / 工程主題的例子 |
|---|---|---|
| **狀態模型** | 哪些是固定資料，哪些是讀者能改的條件；固定與變動要有文字或符號標記，不能只靠顏色 | 固定 IPv4 32 位元；可變的是 CIDR 前綴；`/24` 改成 `/26` 後，主機位元和範圍立即改變 |
| **表示映射** | 原始寫法、展開結構、每一部分代表什麼，並排對照 | `10.0.2.0/24` 同時顯示十進位、二進位的網路／主機切分、範圍與位址數 |
| **單一變因** | 每次只改一個條件，標出「改了什麼、保持什麼、結果變哪裡」 | 只拖動前綴長度；保留 VPC 基底不變；觀察子網範圍、可分配數與 AWS 保留五個位址的變化 |
| **過程步驟** | 中間狀態不是黑盒：每一步能回看，下一步回答一個核心問題 | 從「總位元數」到「主機位元」再到「2^h」及「第一個／最後一個位址」 |
| **多重表徵** | 同一個結果在圖、數字、文字中同步出現；讀者可用其中一種表徵核對另一種 | 位元格、範圍條、數值卡、文字判斷同時更新 |
| **預測與揭曉** | 先讓讀者預測或選擇，再用高亮和逐步圖解說明為什麼 | 先問「`/28` 有幾個可用位址？」；揭曉時標出網路位址、廣播位址與 AWS 保留位址 |
| **邊界與反例** | 顯示規則何時成立、何時變成例外，避免把特定情境規則誤認成定義 | `/31`、`/32` 或 AWS 不同資源的保留規則要標成情境規則，不和一般 IPv4 算式混成同一條定義 |
| **開放沙盒** | 教學完成後仍能讓讀者換條件、提出自己的問題，而不是只按下一頁 | 讓讀者輸入 CIDR、選擇子網需求，再觀察能否切分與剩餘空間 |

建議未來的 HTML 內部也維持這個分離：一份狀態、一個純計算函式、數個依狀態渲染圖／值／步驟的函式，以及把控制項連到狀態的事件處理。這是本專案的實作建議，不是任何一個外部案例要求的唯一架構。

## 第一輪：廣泛搜尋 explorable explanations 與互動文章

第一輪查詢集中在 explorable explanations、視覺化教學、互動文章、作者方法與可反應文件。查詢詞包括：`Explorable Explanations`、`Nicky Case`、`Seeing Theory`、`Red Blob Games`、`Distill interactive`、`Google PAIR explorable`、`3Blue1Brown interactive lessons`、`Josh Comeau interactive`、`Observable notebooks`、`Tangle.js`、`Idyll`、`PhET research` 等。

### 案例與可借用模式

| 案例 | 觀察到的互動方法 | 可移植到本專案的部分 | 離線單檔限制與證據狀態 |
|---|---|---|---|
| [Explorable Explanations](https://explorable-explanations.com/en/) | 以「觸摸、移動、看見」理解 AI 與資料視覺化；適合作為案例索引與形式分類 | 把互動視為推理的一部分，而不是在文字旁放裝飾圖 | 這是作品入口，不是單一建置工具；閱讀官方頁面，未逐一操作所有作品 |
| [Nicky Case：How I Make an Explorable Explanation](https://blog.ncase.me/how-i-make-an-explorable-explanation/) | 從動機問題開始，逐步從具體走向抽象，最後留一個可自由探索的 sandbox | 直接對應「先補前置概念、一步一問、最後接實際任務」；也適合規劃 brief 的學習路徑 | 方法文章，不規定技術堆疊；已閱讀。其作品聲譽可由 [GitHub 的 trust（6,301 stars）](https://github.com/ncase/trust) 與 [loopy（1,746 stars）](https://github.com/ncase/loopy) 作為採用度訊號，但不是成效證據 |
| [Nicky Case：Loopy](https://ncase.me/loopy/) | 拖曳節點、連線、播放因果／系統模型，鼓勵「what if」與 remix | 工程主題可把元件、狀態、封包或服務當節點；用箭頭顯示因果，不只顯示結果 | 原作品是網站，需要檢查資產與腳本是否能內嵌；已閱讀頁面，未宣稱完成離線打包 |
| [Red Blob Games：A* introduction](https://www.redblobgames.com/pathfinding/a-star/introduction.html) | 起點／終點、步進按鈕、動畫、演算法比較、圖與程式同步 | 最適合移植「按一步就看見一個中間狀態」；CIDR 可把每個位元切分視為步驟，網路可把封包狀態視為步驟 | 已在瀏覽器點擊步進並觀察狀態改變。作者也說明 [離線保存互動 HTML 的限制](https://simblob.blogspot.com/2022/)，所以不能直接假設另存網頁就能保留互動 |
| [Red Blob Games：making of little things](https://www.redblobgames.com/making-of/little-things/) | 著重配色控制、狀態機、可連結章節、雙欄文字／圖、列印與程式碼並排 | 可把目前綠色風格保留為既有教材的局部語言，同時把互動狀態、圖例、固定／變動標記制度化 | 這是作者方法頁，不是框架；已閱讀相關頁面與作者文章，未複製其 CSS |
| [Seeing Theory](https://seeing-theory.brown.edu/) | 把機率與統計概念拆成卡片／章節，將抽象分布、抽樣與機率結果轉成可操作圖 | 適合參考「先定義圖上元素，再讓參數改變圖形與數值」；不把數學題材本身列為本專案方向 | 官方 README 列出 Webby、SXSW 等獎項，GitHub 頁面 2,191 stars；這是聲譽訊號。已開啟並點擊一章，未做完整互動測試；專案自 2019 後維護狀態有限 |
| [Distill](https://distill.pub/about/) | 互動圖解、可檢查的模型、讓讀者輸入例子並查看內部 activation／狀態 | 「看見中間運算」與「模型可被檢查」很適合套到協定、資料結構與 AWS 計算；可將每個步驟設為可觀察 state | Distill 2016–2021 發表、目前 indefinite hiatus；適合作為設計先例，不適合作為現成平台依賴 |
| [Google PAIR Explorables](https://pair.withgoogle.com/explorables/) | 以高度互動與圖像方式解釋 ML 概念，將概念拆成可操作的短篇 | 可參考短單元、滑桿與可見的模型內部表示；一個 HTML 只處理一個核心問題 | 通常是完整網站與前端資產；閱讀 Google／PAIR 官方頁面，未檢查其離線包裝 |
| [3Blue1Brown](https://www.3blue1brown.com/about/) | 以動畫、幾何與多媒體建立直覺；網站也有文字／互動課程，並公開 Manim 生態 | 借用「先建立可見直覺，再補符號」與動畫節奏；不把影片取代互動操作 | 多數內容是影片或網站，不能直接滿足單檔離線條件；閱讀官方 about 頁，未觀看特定影片 |
| [Josh Comeau：Whimsy](https://whimsy.joshwcomeau.com/) | 互動文章、短影片、練習與小遊戲；要求讀者實際修改 CSS／JS，而不是只看解說 | 適合做短小的「改一個條件、立即看到結果」微實驗；可把練習嵌在主教材後 | 文章仍屬網站內容，需自行內嵌；作者頁中的推薦語是 testimonial，不能當學習成效研究 |
| [Observable notebooks](https://observablehq.github.io/documentation/notebooks/) 與 [Inputs](https://observablehq.github.io/documentation/inputs/overview) | Markdown、程式、輸出與 slider／button／table 以 reactive cells 連接 | 可借用「一個輸入驅動多個輸出」與把計算拆成可閱讀的 cell；對提示詞的狀態模型很有幫助 | 預設依賴 notebook runtime／平台或建置流程；不符合本專案不載入外部依賴的交付條件 |
| [Tangle](https://github.com/worrydream/Tangle) | 讓讀者直接在文件中調整數字，相關文字和結果即時更新；GitHub 快照 1,800 stars | 可借用「文字中的數字也是控制項」與反應式計算；例如拖動 `/24` 時同一段說明同步變成 `/26` | 原始專案是 2011 年 JavaScript library，需內嵌或自行重寫；stars 是人氣，不代表現代瀏覽器或教學成效 |
| [Idyll](https://github.com/idyll-lang/idyll) 與 [UIST 論文](https://idl.cs.washington.edu/files/2018-Idyll-UIST.pdf) | 以可讀標記描述互動文章；支援 reactive variables、sticky visualization、文字／滾動觸發 | 可借用「內容結構和視覺元件分離」與「每個段落只驅動有限狀態」；可轉寫成單檔原生 DOM | 預設需要 Node／React／建置；GitHub 快照 2,041 stars、88 forks，是工具採用度訊號，不是本專案現在應安裝的依賴 |
| [PhET design principles](https://phet.colorado.edu/en/research/design-principles) 與 [research](https://phet.colorado.edu/en/research) | 科學探究、讓不可見的東西可見、視覺模型、多重表徵、即時因果回饋、用限制控制項提供隱性引導 | 這是最可直接變成本專案檢查表的一組原則：圖、數字、文字互相驗證；只暴露有教學價值的控制項；結果立刻回饋 | PhET 模擬器本身不是本專案的單檔模板，但官方有多輪 think-aloud 訪談與研究；這是本調查中較強的學習設計／成效證據之一。另見 [訪談研究 PDF](https://phet.colorado.edu/publications/PhET_Interviews_I.pdf) |

### 第一輪得到的判斷

- 「互動」最有價值的部分是**讓讀者看到自己改變的條件如何穿過中間運算，最後改變結果**。單純按下一頁、播放裝飾動畫或換一張圖不符合這個標準。
- Red Blob、Nicky Case、PhET 三者互補：前者提供步進狀態，第二者提供敘事弧線，第三者提供多重表徵與研究導向的限制控制。
- Observable、Tangle、Idyll 適合作為反應式文件的概念來源，但其 runtime／建置方式與「單檔離線」衝突；後續應只吸收資料流與版面方法。
- Seeing Theory、3Blue1Brown、Distill 的數學或 ML 題材不是本專案學習目標；可移植的是「把抽象關係畫成可操作的狀態」這個方法。

## 第二輪：演算法、執行流程、作者工具與 Skill

第二輪沿著第一輪的互動模式再查：演算法／程式逐步執行、互動文章框架、可攜 HTML、AI agent Skill、視覺化工具，以及原作者演講。查詢詞包括：`Python Tutor`、`Algorithm Visualizer`、`VisuAlgo`、`GILP interactive HTML`、`p5.js`、`The Pudding`、`explain-this skill`、`html-explainer skill`、`teaching-explainer`、`Bret Victor Inventing on Principle`、`Nicky Case How To Explain Things Real Good` 等。

### 執行流程與教材案例

| 案例 | 觀察到的互動方法 | 對本專案的移植價值 | 限制、聲譽與驗證 |
|---|---|---|---|
| [Python Tutor](https://pythontutor.com/) 與 [UIST 研究論文](https://pg.ucsd.edu/publications/Python-Tutor-scalable-sustainable-research-software_UIST-2021.pdf) | 一行一行執行，並列顯示程式、變數、物件、指標、stack frame；支援多種語言 | 對網路／AWS 教學可把「設定／請求／回應／狀態」做成可逐步檢查的狀態表；每步標出目前行動與新增／改變的值 | 官方宣稱超過 2,500 萬使用者、5 億次 visualization；這是採用度。其 [unsupported features](https://github.com/pythontutor-dev/pythontutor/blob/master/unsupported-features.md) 也明示小型片段、伺服器執行與行動版限制；不適合直接嵌入離線 HTML |
| [Algorithm Visualizer](https://github.com/algorithm-visualizer/algorithm-visualizer) | 從程式或教學文章操作演算法動畫，將程式執行和圖解連結 | 可借用「程式／規則／資料狀態／畫面」四區同步；適合未來做路由、排序、CIDR 切分等演算法化題目 | GitHub 快照 48,881 stars（repo-level），人氣很高；官方架構是 React 與執行／編譯服務，需要網站 runtime，不能視為離線依賴 |
| [VisuAlgo](https://visualgo.net/en) 與 [Training](https://visualgo.net/training) | 多個資料結構／演算法模組、step／play、使用者輸入、e-lecture、線上測驗 | 可借用「先看一個小例子，再讓讀者輸入自己的例子，最後做判斷題」的編排；與本專案 3 題練習很接近 | 官方說明由 NUS 的 Steven Halim 發起；這是作者／產品資訊，不是獨立學習成效證據。網站 runtime 與模組資產不符合單檔要求 |
| [GILP 論文](https://arxiv.org/abs/2210.15655) | 把線性規劃的代數步驟、幾何位置、限制與目標函數同步呈現；可產生學生直接開啟的互動 HTML | **不推薦線性規劃作為本專案學習主題**，但很值得借用「靜態式子 → 圖形狀態 → 每次迭代 → 結果」的映射，以及輸出可攜 HTML 的先例 | 論文報告約 100 人課程的正向回饋，這是單一課程經驗，不是普遍成效。作者工具仍用 Python／Plotly 等依賴；學習者端不必安裝是其直接價值 |
| [p5.js examples／tutorials](https://p5js.org/tutorials/) | 以簡短程式建立畫布、動畫與互動，適合初學者與教學者 | 若未來需要複雜 canvas 動畫，可參考其最小互動單元；目前單檔則應以原生 SVG／Canvas 重寫必要部分 | 需要 library 才能直接使用；官方案例是學習資源，不是離線單檔交付方案 |
| [The Pudding resources](https://pudding.cool/resources/) 與 [about](https://pudding.cool/about/) | 以資料、故事、設計與前端程式組成 visual essay；長頁／scrollytelling 把敘事和畫面串起來 | 可借用「每一段文字都推動一個視覺狀態」與先做資料／故事／程式分工；應縮小成簡潔 stepper，避免只剩滾動特效 | 多數作品使用 D3、Svelte 或外部資料；官方 about 的獎項是創作聲譽，不是教學成效；本輪閱讀官方頁面，未逐一操作作品 |

### AI agent Skill 候選（僅調查，沒有安裝）

以下星數來自 GitHub 頁面或本次 [GitHub API 快照](./github-snapshot-2026-10-04.json)。Skill 的 repo star 是專案人氣，不能直接證明產出教材的品質；而且不同 repo 的星數不一定只對應該單一 Skill。

| Skill／專案 | README 或 Skill 明示的方向 | 與本專案的契合度 | 主要疑慮與建議 |
|---|---|---|---|
| [explain-this](https://github.com/analyticalmonk/explain-this) | Distill-style interactive explainer；輸出單一自包含 `index.html`，sticky 雙欄、Canvas 圖；含來源／研究 intake、codebase explaining、fact-checking 三類 Skill。實際模板仍載入 Google Fonts，需覆寫才能完全無網路請求 | **高**：同時覆蓋研究、視覺化、單檔與事實檢查；README 頁面當時 20 stars | 規模與實際維護度仍小；star 不高不能據此否定，但應先人工讀完整 Skill、拿目前 CIDR brief 做小型 dry run，再決定是否安裝 |
| [html-explainer](https://github.com/ds-vibe/html-explainer) | 單頁或投影片式 HTML；流程含 research → learning architecture → design → render／實看 → revise；要求桌機、手機、互動截圖檢查 | **高**：補足目前提示詞中「要實際看畫面」的 QA 環節；README 頁面約 15 stars | 完整 QA 需要 Playwright／Chromium，會增加依賴；先只借流程，不安裝。Star 低且 repo 新，不能視為成熟標準 |
| [teaching-explainer](https://github.com/rlfordon/teaching-explainer) | 針對 accessible、single-page、offline HTML；列出 `predict-reveal`、retrieval MC、self-explain、classify、step-through；提到 Mayer／ICAP、WCAG 2.2 AA 與 Playwright／axe 測試 | **最高的教學流程契合度**：涵蓋先作答、逐步揭曉、鍵盤與可及性；三題的數量另由本專案規範；GitHub 快照 6 stars、1 fork | repo 很新且人氣低；README 的 evidence-based 宣稱需要逐項核對來源與實作，不能把 Skill 自己的宣稱當研究證據。建議列為第一個人工審閱候選，不立即安裝 |
| [html-artifacts](https://github.com/joshuadavidthomas/agent-skills/tree/main/html-artifacts) | self-contained local HTML；內嵌 CSS／JS／SVG／資料；互動必須回答「讀者問題 → 動作 → 立即可見答案」；explorable document 適合因果機制、參數取捨、耦合表徵 | **高**：可直接強化目前「條件 → 結果聯動」與離線限制的提示語 | repo 快照 54 stars、7 forks；它是通用 HTML artifact Skill，不是完整教學法。建議抽出交付與互動契約，與 `teaching-explainer` 的教學檢查合併評估 |
| [ibook-skills](https://github.com/dmccreary/ibook-skills) | 以 learning graph／DAG、Bloom、概念與 MicroSim 組織智慧教材；新舊文件的 Skill 分類曾改動，應以目前 repo 與實際 SKILL.md 為準 | 可借用「前置概念圖」與長期課程分類，解決未來多主題時 brief／references 的索引問題 | GitHub 快照 105 stars、17 forks；常用 MkDocs、Python、npm 與多個視覺套件，與目前單檔最小交付衝突。適合後期教材庫成熟後再看，不適合現在直接導入 |
| [visual-explainer](https://github.com/nicobailon/visual-explainer) | 通用 AI agent 的視覺解釋 Skill／工具集合 | 可作為稍後比較的高人氣候選，先看其輸出契約是否真的涵蓋 offline、互動因果鏈與教育評量 | GitHub 快照 repo 約 10.2k stars，但 repo 人氣不能替代內容審查；本輪只記錄候選與人氣，沒有把它列入本專案的推薦 Skill |
| [claude-visual-explainer](https://github.com/schmosbyy/claude-visual-explainer) | 單檔 zero-dependency HTML，提供 heatmap、probability bars、stepper、flow diagram 等 widget | 可借用元件清單與「每個 widget 自己容錯」的概念 | GitHub 0 stars、未見明確 license；低維護／可持續性風險高，只列為 widget 參考，不建議投入安裝評估 |

### 第二輪得到的判斷

- **Skill 應拆成兩層**：一層負責研究、學習結構、事實核對與評量；另一層負責單檔 HTML、內嵌資產、瀏覽器 QA。`teaching-explainer`、`explain-this`、`html-artifacts` 的責任邊界比「找一個萬用 Skill」更清楚。
- Python Tutor／Algorithm Visualizer／VisuAlgo 的共同可移植單位是「來源／規則與狀態圖同步」，不是它們的 server 或 framework。
- GILP 特別值得保留作為「公式或靜態資料如何變成圖形與運算過程」的參考；報告只推薦其設計方法，不推薦其數學主題。
- 高 star 工具通常代表更大的平台或社群，反而更可能違反單檔離線約束；人氣應用來排序閱讀，不應直接決定採用。

## 作者影片與演講

本輪只核對原作者或原作者維護頁面的 URL 與描述，沒有逐部觀看；以下內容只適合建立待觀看清單，不可當成已完成的內容摘要。

| 作者／作品 | 原作者來源 | 本輪狀態 | 可以期待的研究方向 |
|---|---|---|---|
| Bret Victor — *Inventing on Principle* | [Vimeo 影片](https://vimeo.com/906418692)、[作者 CV](https://worrydream.com/cv/) | **只讀 URL／作者 CV，未觀看**；CV 將其列為公開演講並記錄很高的觀看量 | 觀察作者如何把「工具應讓人的想法可直接表達」轉成可操作介面；觀看後再判斷哪些能移植到條件／過程／結果鏈 |
| Nicky Case — *How To Explain Things Real Good* | [作者 Patreon 貼文](https://www.patreon.com/ncase/posts/how-to-explain-68466234)、[YouTube](https://youtu.be/b-M2U3Jl1Cg) | **只讀作者頁與影片連結，未觀看**；方法文章本身已閱讀 | 對照其影片與文字方法：動機、分段、比喻、沙盒、開放問題；可補強共用提示詞的教學敘事 |
| 3Blue1Brown — visual／written／interactive lessons | [官方 About](https://www.3blue1brown.com/about/) | **讀官方文字頁，未選定或觀看特定影片** | 觀察動畫如何先建立直覺，再讓符號與圖形對應；只移植視覺敘事節奏，不把影片當單檔互動實作 |

其他原作者影片的驗證程度見 [總報告](2026-10-04-survey.md)。後續新增影片也應維持同樣標記：**已觀看**、**只讀文字／metadata**、或**尚未驗證**，不要用影片標題推論教學效果。

## 第三輪：沿作者與方法往工程、網路、分散式系統延伸

第三輪不是再列一批一般視覺化網站，而是沿前兩輪的「狀態、步驟、因果、可攜」四個方向，查找工程網路、分散式系統、互動科學作者與程式執行視覺化。查詢詞包括：`interactive distributed systems networking visualization`、`MinuteLabs`、`Python Tutor official`、`CS Visualizer`、`Apex networking distributed systems` 等。

| 案例 | 新增或重複 | 觀察到的模式 | 對本專案的判斷 |
|---|---|---|---|
| [MinuteLabs](https://minutelabs.io/about/) | 新增 | 由 MinutePhysics／MinuteEarth 延伸，把短影片式科學解說改成可以玩的互動 app；官方列出概念、程式與設計的作者分工 | 可借用「一個小問題、一個可玩的模型」與作者分工思維；它偏探索與遊戲，不足以單獨規範前置概念、評量與離線交付 |
| [Apex](https://github.com/pen-pal/apex) | 新增 | README 列出網路、密碼學、分散式系統、資料庫、硬體、OS 等約 497 個 hands-on visualization；以每個主題的 pure model、測試不變量與 React view 分離，引用 RFC／論文／PCAP | **工程主題的高價值參考**：可把「規則正確性」放在純模型與測試，把畫面當表徵層。GitHub 快照僅 16 stars、0 forks，屬新且小的專案，不能把人氣或維護度當學習成效；需要 npm／React／Vite build，不能直接採用 |
| [Encore：Queueing](https://encore.dev/blog/queueing) 與 [Retries](https://encore.dev/blog/retries) | 新增；已做小範圍實測 | 以工程情境把排隊、重試與系統行為做成可操作的互動文章；可觀察條件改變如何影響吞吐、延遲或失敗結果 | 很接近本專案要做的工程 explainers，適合研究「真實任務 → 模型 → 可見結果」。另有 [作者的 Bluesky 說明](https://bsky.app/profile/samwho.dev/post/3mav64hwmb22b) 與 [Podcast 討論](https://frontendfirst.fm/episodes/blog-post-club-queueing-an-interactive-study-of-queueing-strategies)；後者是同業討論／認可訊號，不是學習成效研究。小範圍瀏覽器實測記錄見總報告，這裡保留案例指向 |
| [Distributed Systems Visualizer](https://github.com/sandeepkv93/distributed-systems-visualizer) | 新增 | 以 step controls 與理論文章示範 CAP、Lamport／vector clocks、snapshot、eventual consistency、CRDT、Paxos／Raft／PBFT 等 | 可借用「網路延遲、分割、訊息遺失等條件要能被切換」的情境設計；GitHub 0 stars、需 Next.js／Bazel，暫列觀察，不列入首批投入 |
| [CS Visualizer](https://cs-visualizer.com/) | 新增 | 提供 flowchart、資料結構、遞迴、演算法、Big O、OS、automata 等 step／play／reset 互動，並支援多種執行環境 | 適合作為功能清單：step、reset、執行中的資料、結構圖；官方產品需要 runtime／擴充功能，未找到足夠的獨立教學成效證據，不能當採用標準 |
| [Python Tutor](https://pythontutor.com/) | **重複確認** | 第三輪重新從「程式執行視覺化」查到同一案例；補充確認它的 server-side 執行、小型片段定位與手機限制 | 沒有改變第二輪判斷：借用同步狀態與逐步揭露，不能把服務本身放入離線 HTML |
| [Nicky Case／Red Blob／PhET 方法](https://blog.ncase.me/how-i-make-an-explorable-explanation/) | **重複確認** | 工程案例仍需要同一套問題導向、步進狀態、多重表徵與限制控制項 | 第三輪沒有推翻第一輪結論，反而顯示工程主題更需要把不可見的封包／狀態／不變量具體化 |

### 第三輪得到的判斷

- 工程與網路主題不一定要做成大型模擬器。對本專案而言，一個**小而完整的狀態模型**通常比一個涵蓋所有協定的大平台更適合單檔教材。
- Apex 的「純模型 → 測試不變量 → 視圖」很適合轉化成教材檢查：每個互動至少要有可驗證的規則、圖形狀態與結果文字；這也能降低 AI 產生看似合理但算錯的圖。
- 分散式系統案例提示未來 brief 應明確寫出「訊息延遲／遺失／節點故障是可變條件」，並把每一步的觀察窗口固定下來；否則動畫容易變成無法回推的黑盒。
- 第三輪新增的案例改變了**主題候選範圍**，沒有改變**本專案的首選方法**：先做小型、可驗證、單檔的條件—過程—結果教材。

## 依本專案限制的排序

| 優先 | 來源 | 建議投入方式 | 原因 |
|---|---|---|---|
| A | Red Blob、Nicky Case、PhET | 直接拆解互動與教學方法，寫進後續 brief／prompt 的檢查欄位 | 分別覆蓋步進、敘事、因果回饋與多重表徵；不需要安裝 |
| A | `teaching-explainer`、`html-artifacts`、`explain-this` | 先讀完整 Skill 與範例，使用目前 CIDR brief 做 dry run；通過後才考慮安裝 | 最接近「單檔、離線、互動、教學評量」的需求，但成熟度與依賴仍需審查 |
| B | GILP、Python Tutor、VisuAlgo、Apex | 只抽取特定互動模式：公式映射、逐步執行、輸入／測驗、模型／測試分離 | 能補足 AWS、網路、演算法、工程主題；不能直接引入其 runtime |
| B | Distill、Google PAIR、Tangle、Idyll、Observable | 當作資訊架構與反應式文件的參考 | 方法有價值，但平台、框架或歷史維護狀態與本專案交付條件有落差 |
| C | MinuteLabs、The Pudding、3Blue1Brown、Josh Comeau | 研究敘事、動畫節奏、短微實驗與視覺風格 | 呈現品質高，但不能直接證明其適合完整教學或離線單檔 |
| C | Distributed Systems Visualizer、CS Visualizer、低 star Skill | 只在未來真的做該主題時再定向閱讀 | 可借用功能想法，但人氣、維護或成效證據不足 |

## 後續在本專案內可落地的檢查表

每次由 `brief` 與 `references` 產生 HTML 時，可以要求產出者逐項回答：

1. 讀者在本步要回答哪一個問題？若拿掉互動，是否仍能看出答案如何得出？
2. 哪些資料／條件固定？哪些是讀者可變？是否有文字、符號或標籤明確說明？
3. 原始寫法如何拆成圖上的元素？每一個元素代表什麼？
4. 改變一個條件後，哪個中間運算先變、哪個結果後變？畫面是否同步顯示這條鏈？
5. 公式是定義、推導結果，還是 AWS／服務／協定的特定規則？是否在首次出現時標出？
6. 是否有最小例子、混淆對照例子與至少一個邊界情況？
7. 三題練習是否先收答案，再以高亮、箭頭、數值或步驟指出「看哪裡、比對什麼、為什麼」？
8. 在關閉網路、直接開啟檔案、窄螢幕、鍵盤操作與 reduced motion 下，核心內容是否仍可用？
9. 是否用實際瀏覽器操作記錄通過、未測與已知問題，而不是只檢查原始碼？

這份檢查表是依案例歸納的本專案建議；它不是任何單一案例或 Skill 的官方標準。

## 三輪搜尋記錄

### 第一輪

`Explorable Explanations`、`Nicky Case`、`Seeing Theory`、`Red Blob Games`、`Distill interactive`、`Google PAIR explorable`、`3Blue1Brown interactive lessons`、`Josh Comeau interactive`、`Observable notebooks`、`Tangle.js`、`Idyll`、`PhET research`。

### 第二輪

`Python Tutor`、`Algorithm Visualizer`、`VisuAlgo`、`GILP interactive HTML`、`p5.js tutorials`、`The Pudding resources`、`explain-this skill`、`html-explainer skill`、`teaching-explainer`、`html-artifacts`、`Bret Victor Inventing on Principle`、`Nicky Case How To Explain Things Real Good`、`3Blue1Brown visual explanation`。

### 第三輪

`interactive distributed systems networking visualization`、`MinuteLabs interactive explainer`、`Python Tutor official code visualization`、`Apex networking distributed systems`、`CS Visualizer`、`distributed systems visualizer`。第三輪沿已找到的作者、獎項與方法頁外擴；新增工程／分散式系統案例，並重查 Python Tutor、Nicky Case、Red Blob、PhET。重查沒有改變首選，只增加了工程主題的移植例子與限制。

## 不列入首批推薦的來源

本輪也看過一些一般性的 AI／HTML／投影片 Skill 與搜尋結果，但沒有足夠的教學專門性、來源品質或離線相容性，因此不把它們湊成推薦清單。原因包括：只產生漂亮頁面而沒有條件—過程—結果鏈、依賴瀏覽器自動化／遠端 runtime、沒有明確 license／維護訊號，或只有 repo star 而缺少可檢查的內容與例子。後續若專案改成框架網站、需要批量教材、或真的開始做分散式系統，再針對該條件重查會比現在安裝一堆工具更有效。
