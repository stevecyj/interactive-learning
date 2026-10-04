# 互動學習的視覺參考案例與原作者影片

調查日期：2026-10-04（Asia/Taipei）。

這份文件是「視覺化互動學習」的 survey 補充，集中回答三個問題：

1. 一個網站如何維持共同身份，同時讓 AWS／IP／Java 等分類有可辨識差異？
2. 「方便、好玩、引起好奇心」可以從哪些畫面、互動和動態決策觀察，而不是只把它寫成形容詞？
3. 哪些案例值得借鏡其設計策略，哪些只能當作品集、獎項或人氣訊號？

這裡只做資料收集，沒有安裝 Skill、套件或遠端框架，也沒有修改既有 HTML。色票、感受和效果不直接複製或宣稱適用於本專案；後文的建議是待驗證的設計假說。

## 證據標記與閱讀深度

- **A（作者／官方明示）**：來源的作者、產品或官方設計文件直接說明的目的、規則或方法。
- **R（研究／訪談）**：研究論文、研究報告或作者公開的使用者訪談；仍要看其樣本與限制。
- **P（人氣／獎項訊號）**：官方頁面公布的使用量、評論、獎項或平台評分。這能幫忙決定先研究什麼，不能證明學習成效或色彩造成某種感受。
- **V（本次視覺推論）**：我從頁面、截圖或設計文件觀察到的特徵；不是受眾研究，也不是作者對所有讀者的保證。

閱讀深度在每列最後標明：

- **全文／核心頁已讀**：讀過方法、設計原則或主要文章，而不是只看搜尋摘要。
- **頁面／互動已讀**：讀取官方介紹或可見互動結構，但沒有針對每個頁面做完整使用者測試。
- **獎項頁 metadata**：核對官方獎項頁的年份、分數、技術或描述；沒有把作品當成已驗證的教學效果。
- **影片 metadata／逐字稿**：只核對官方連結、標題、日期和描述，或另外讀官方逐字稿；影片本身未觀看時不從標題推論內容。

## 先給可移植的結論

值得先帶回本專案的不是某一組綠、藍或橘色，而是以下分層方式：

1. **固定網站層**：文字階層、留白、元件形狀、控制方式、focus、動畫節奏、來源區和鍵盤行為。Duolingo 的 redesign、Khan Academy 的 token 模型、USWDS／Carbon 的語意化 token 都指向同一件事：一致性來自規則，不是每頁使用相同 hex 值。
2. **分類層只換少量 accent**：AWS／IP 可以共享一個「network」分類語境，Java 可以是另一個 anchor；分類色只用於章節標記、圖解焦點和互動元件，不能取代 `success`、`warning`、`error`、`focus` 或固定／變動／推導等教學語意。
3. **每一課再有一個故事焦點**：Red Blob、Ciechanowski、PhET 和 Python Tutor 都讓顏色、線條、位置或動態服務目前要看的變數。不要把整頁染成高飽和色；將 accent 留給「正在改變或要比較的東西」。
4. **感受要拆成可觀察條件**：「方便」較接近可預測的路徑、清楚層級、足夠對比和立即回饋；「好玩」較接近可試錯、可重設、操作會產生結果；「好奇」較接近先提出預測、局部揭露和可回看差異。這些是設計假說，需用任務測試和受眾比較驗證。
5. **固定色彩之外還要固定視覺語法**：形狀、標籤、線型、位置和 motion 應讓讀者在灰階、色覺差異、手機和 reduced motion 下仍能理解。W3C 指出顏色不能是資訊或操作的唯一線索；普通文字對比至少 4.5:1、大字至少 3:1，非文字控制和圖形通常要檢查 3:1。

## 三輪搜尋記錄

### 第一輪：從視覺化學習與品牌系統廣搜

以 `interactive learning visual design`, `explorable explanations`, `visual essays`, `education design system color`, `site:brilliant.org`, `site:duolingo.com`, `site:pudding.cool`, `site:distill.pub` 等組合查找官方案例。先收集互動學習、科普、資料新聞和品牌設計系統，再把獎項網站當發現入口。這輪確立 Brilliant、Duolingo、PhET、The Pudding、Distill、Nicky Case、Red Blob Games 等主線。

### 第二輪：沿作者、設計原則和互動模型追查

從第一輪的原作者、官方 resources、design system 和研究頁面延伸：Khan Academy Wonder Blocks、Python Tutor、Codecademy、R2D3、Seeing Theory、Our World in Data、Ciechanowski、USWDS、Carbon、ColorBrewer。這輪重點轉為「內容如何變成可操作狀態」「網站層與故事層如何分工」「可及性和狀態色怎麼不被主題色破壞」。

### 第三輪：補獎項、影片和可及性缺口

再查 Awwwards、CSS Design Awards 的教育／互動作品頁、PhET 官方影片、Nicky Case Stanford talk、The Pudding resources 以及 W3C WCAG。獎項頁只當策展和視覺人氣訊號；影片只記錄能從官方頁或 metadata 核對的事項，沒有觀看的影片不把標題當成內容證據。

## 互動學習與科普案例

| 案例與官方來源 | 可觀察的視覺／互動策略 | 證據、感受與可借方向 | 成本與 a11y 注意事項 | 閱讀深度 |
|---|---|---|---|---|
| [Brilliant About](https://brilliant.org/about/)、[Features](https://brilliant.org/help/features/)、[K–5 trust and methodology](https://brilliant.org/practice/guides/trust-and-methodology/) | 把概念拆成短步驟；視覺元件可拖曳、點選或輸入；先讓學習者作答，再逐步補程序；回饋、聲音和觸覺是互動的一部分。官方方法頁還描述原生控制、鍵盤／輔助技術、focus、狀態播報、文字／符號備援、touch/desktop 和 reduced motion。 | 「互動、適應、好玩」是產品自己的定位（A）；官方 educators 頁稱 10m+ learners、100k+ 5-star app reviews，是自述的 P，不是獨立驗證。可借的是「一個核心問題＋可操作表示＋立即而可解釋的回饋」，不是模仿其品牌色。 | 中至高：每個互動題目要有狀態和錯誤回饋。優先使用原生 controls，固定和變動資訊用文字／符號同步呈現；動態不能是唯一答案。 | About、Features、方法頁核心段落已讀；未逐題做完整可及性測試。 |
| [Duolingo core tabs redesign](https://blog.duolingo.com/core-tabs-redesign/)、[Imagery](https://design.duolingo.com/identity/imagery)、[Typography](https://design.duolingo.com/identity/typography)、[Shape language](https://blog.duolingo.com/shape-language-duolingos-art-style/) | 官方 redesign 明列四種方向：鮮明實色 header、柔和漸層、模組卡片、扁平留白；用原型比較一致性／目的、簡潔／清楚，最後建立標題、字級和 spacing 階層。illustration、圓形／柔和形狀、Duo 角色與字體是比「整頁綠色」更穩定的身份。 | 「讓學習感覺好」與「好玩」是品牌和設計團隊的 A；文章報告較高 engagement 但仍屬內部自述。外部不能從其形象推論所有人會覺得好玩。可借「共同 shell＋可控的分類／內容 accent」，以及先做幾個方向再比較。 | 中：要建立 typography、spacing、shape 和 illustration 規則。高飽和 accent 應保留給標記和互動；焦點、文字和狀態不能只靠 Feather green。 | redesign、imagery、typography 和 shape 文章已讀；logo 頁在本次只核對官方搜尋結果，未把商標色作為 palette 建議。 |
| [Khan Academy Wonder Blocks color system](https://blog.khanacademy.org/how-we-rebuilt-khan-academys-color-system-from-the-ground-up/)、[Windows high contrast](https://blog.khanacademy.org/making-websites-work-with-windows-high-contrast-mode/) | 用 `Domain → Layer → Context → Intensity` 組成語意 token：Core／Learning／Component、background／border／foreground／shadow、base／instructive／success／warning／critical 等，再用 subtle／default／strong 控制強度。生成器可由 primary anchor 產生色階並匯出 JSON／CSV；另說明 Windows high contrast 下 CSS background 可能消失，重要視覺要用語意 img/SVG 或 outline。 | 顏色不是「這課叫 AWS 所以整頁某色」，而是「這個表面／狀態／強度要做什麼」。這是官方設計系統方法（A），可作本專案全站和分類分層的最直接參考。感受沒有在此被宣稱，V 只指出其結構可讓介面較可預測。 | 中至高：初期要整理 token，但日後換分類色和 dark mode 成本較低。必須保留文字、線條、outline 和 SVG 語意，不能只用背景色。 | 兩篇官方文章核心內容已讀；未執行 Wonder Blocks 生成器。 |
| [PhET About and design principles](https://phet.colorado.edu/en/about)、[Teaching with PhET](https://phet.colorado.edu/nn/teaching-resources/teaching-with-phet)、[research](https://phet.colorado.edu/zh_TW/research) | 以模擬、視覺 mental model、多重表示、現實連結、有限控制和立即回饋讓不可見機制變得可見；官方說明「科學探究、interactivity、make the invisible visible、multiple representations」等原則。控制數量有意限制，讓因果關係較容易被探索。 | 官方列出 Open Education Award 2019、TPG accessibility 2018、APS 2018 等獎項（P），研究頁與訪談論文報告超過 200 次訪談（R/A）；研究限制仍需看個別模擬和教學情境。可借「一個操作同時更新圖、數值和文字」，以及把互動當模型而非裝飾。 | 高：物理／科學模型、錯誤狀態和多重表示需內容專家審查。把 input label、文字狀態、替代圖解和鍵盤路徑設計在模型內；動畫要能暫停或以文字／靜態圖理解。 | About、teaching、research 和 design principles 核心頁已讀；未對特定模擬做完整 screen reader／手機驗證。 |
| [Python Tutor](https://pythontutor.com/)、[visualize](https://pythontutor.com/visualize.html?source=post_page-----1f46e887f351----------------------) | 程式碼、執行步驟、變數／物件／指標、stack frame 和資料結構同時呈現；前進／後退會對應到同一執行狀態。每一步有穩定的物件身份，讓讀者比較「這一步前後哪裡改變」。 | 官方首頁自述 25m+ users、500m+ visualizations、180+ countries、10k+ schools（P，存取日 2026-10-04；不是外部 audit）。可借 stepper＋狀態對照，尤其適合 CIDR 位元或 Java 執行流程；這些使用量不代表學習效果。 | 中：執行引擎和狀態畫面需較多工程，靜態教材可先用少量狀態。每個物件需有文字／標籤與 keyboard path，不能只靠節點顏色。 | 首頁和可視化頁已讀；未量測現有工具在本專案手機和輔助技術的表現。 |
| [Codecademy](https://www.codecademy.com/) | 「Learn by doing」的產品模式：左側步驟與說明、中間編輯器、右側輸出／檢查；輸入改變後立即看到執行結果和 AI／練習回饋。畫面將內容、操作和結果固定在同一個工作區。 | 這些是官方產品主張（A），「millions」是首頁自述人氣訊號（P）。可借「原本寫法／執行結果／錯誤提示同屏比較」；對本專案可轉為 CIDR 輸入、展開二進位、計算結果三欄，而不是照搬 code editor。 | 中：需處理錯誤狀態、輸入限制和手機窄版。輸出要有文字摘要，焦點／錯誤不能只用紅邊或紅色。 | 官方首頁和產品描述已讀；未登入體驗付費課程，未把 AI feedback 視為已驗證效果。 |
| [Red Blob Games](https://www.redblobgames.com/)、[making circle drawing](https://www.redblobgames.com/making-of/circle-drawing/) | 由一個簡單圖示／演算法開始，讓 slider 或 pointer 改變 source-of-truth 變數；圖、公式、輸入和結果並排。making-of 直接談 HTML＋SVG、mobile pointer capture、負空間、拆分 diagram，以及只用紅色標示目前的 radius、避免紅色變成裝飾。 | 作者說自己以 reading／watching／doing 學習，也把站點做成可玩的演算法解釋（A）。「清楚、好玩」是 V／作者語境，不是受眾研究。可借「accent 服務當前關係」和「先拆一個變數，再逐步加入複雜度」。 | 中：SVG／canvas 和 direct manipulation 可自己控制；需加入 keyboard 等價操作、數值輸入、文字解釋和 reset。pointer interaction 不應是唯一路徑。 | 首頁、making-of 全文核心段落已讀；未對全部遊戲逐項驗證。 |
| [Explorable Explanations hub](https://explorabl.es/)、[Nicky Case](https://ncase.me/)、[How I Make an Explorable Explanation](https://blog.ncase.me/how-i-make-an-explorable-explanation/)、[design patterns](https://blog.ncase.me/explorable-explanations-4-more-design-patterns/) | 把學習內容做成 sandbox：拖動節點、改變參數、重試、看系統反應；文章討論 puzzle-it-out、可探索的視覺模型和「先玩再說」。首頁明確定位為 learning through play 的 hub。 | 「play」是作者與 hub 的自我定位（A）；2018 文章提及 100+ Explorables 是作者頁面的歷史 P/A。可借「先給可逆操作和因果回饋，再補術語」，但不可直接把遊戲化等同於學會。 | 中至高：狀態模型和重設容易做，完整鍵盤／讀屏替代較難。每個節點、箭頭和結果都需要文字或表格路徑；motion 要可停。 | hub、作者頁和兩篇方法文章已讀；未逐個 explorable 做 a11y audit。 |
| [R2D3: A Visual Introduction to Machine Learning](https://www.r2d3.us/)、[part 1](https://www.r2d3.us/visual-intro-to-machine-learning-part-1/)、[part 2](https://www.r2d3.us/visual-intro-to-machine-learning-part-2/) | 以決策樹、偏差／變異和逐步故事把抽象統計概念分成選擇與結果；閱讀順序和圖像重複語法讓讀者知道自己在故事哪一層。頁面以互動設計表達 statistical thinking。 | 官方作品定位是作者／團隊主張（A）；2015 年創作年份可由教育資料索引交叉核對，但不當作學習成效研究。V：稀疏畫面、單一焦點、逐段選擇有助降低初始負擔。可借其「每段只問一個視覺問題」。 | 高：scrollytelling、模型圖和手機排版需要內容與動畫 QA。需提供章節導覽、靜態摘要、鍵盤／scroll 替代和 reduced motion。 | 官方首頁和文章描述已讀；未完整逐章完成操作測試，尤其未驗證輔助技術。 |
| [Seeing Theory](https://seeing-theory.brown.edu/)、[Brown Conduit article](https://cs.brown.edu/about/conduit/conduit_v27.pdf)、[official guide](https://seeing-theory.brown.edu/doc/seeing-theory.pdf) | 五個單元各有三個視覺化，每個單元在上一個視覺化上疊加；同一套畫布、控制和圖形反覆出現，像教材而不是一堆獨立 demo。 | Brown 文章記錄 2017 年推文後 72 小時數萬 views，後來超過 1.5m page views、來自全美與近乎每個國家，並用於兩門 Brown 統計課（P/A，歷史快照）；也記錄學生／教育者回饋，但不是 RCT。可借「重複視覺語法＋小單元前進」。 | 中至高：重複 component 和圖形可延伸到本專案；需補文字／表格説明、按鈕 label、焦點和非顏色標記。 | Brown PDF、官方 guide 和網站介紹已讀；互動細節部分頁面閱讀，未做全站 a11y QA。 |
| [The Pudding About](https://pudding.cool/about/)、[resources](https://pudding.cool/resources/)、[process](https://pudding.cool/process/pivot-continue-down/) | 視覺 essay 把研究、資料、文字、版面和程式綁成一個故事；官方 process 說明先問 data story question、收集／分析、storyboard、code，並容許大量 idea 被 pivot 或放下。通常以共同的排版／敘事 shell 配合每篇的 topic accent。 | 官方 About 公布多個作品獎項：2026 Excellence in Visual Storytelling（Sizing Chaos）、2025 Best in Show/Silver、2024 Best in Show/Gold、2023 Information is Beautiful Gold（On Upward Mobility）、2021 World Press Photo Interactive of the Year、2020 Golden Kitty、2019 Website of the Year 等（P/A，年份按頁面）。獎項是視覺／敘事策展訊號，不代表互動學習效果。可借「共同 typography／spacing，故事層自訂 accent」與 storyboard。 | 高：官方 resources 提到 HTML/CSS/JS、D3、Svelte、Scrollama 和製作流程；每篇可用數週至數月的團隊成本。需做 source、caption、keyboard、static summary、reduced-motion 和 mobile fallback。 | About、resources、process 核心頁已讀；作品本身未逐篇完成操作和可及性檢查。 |
| [Our World in Data: redesigning interactive data visualizations](https://ourworldindata.org/redesigning-our-interactive-data-visualizations) | 同一資料提供 chart／map／table 多種 view；控制項靠近內容，來源、下載、分享和 fullscreen 被放到可找到的位置；table 使用對齊和 contrast，source overlay 保留資料脈絡。 | 官方文章是產品團隊對 2023 redesign 的說明（A）；Grapher 是開源、可嵌入且 CC BY（A）。可借「網站 shell 固定，圖表局部換語意色」以及把來源和資料限制視為介面的一部分。 | 中至高：資料圖表、來源和 embed 的狀態多；不能用單一色相區分十幾條序列，需標籤、線型、表格和 pattern 備援。 | redesign 文章與相關官方頁已讀；未以本專案資料做 chart/table 操作測試。 |
| [Distill: Communicating with Interactive Articles](https://distill.pub/2020/communicating-with-interactive-articles/)、[Guide](https://distill.pub/guide/) | 系統整理 prediction/reveal、details-on-demand、simulation、多重表示和減輕認知負擔；同時提醒動畫不自動等於更好，互動有成本，需考慮 accessibility、mobile、archive。 | 2020 文章為作者／編輯群的設計 synthesis（A），不是單一配色或 RCT。可作本專案的教學判準：每個互動要回答一個認知問題，且能說明操作後看哪裡。 | 中：預測／揭示和多重表示可用原生 HTML/SVG；成本主要在狀態、解釋和替代路徑。固定／變動／結果要同時由標籤、位置或形狀表示。 | 文章和 Guide 核心內容已讀；未執行 Guide 依賴的外部 script，因本專案交付需離線。 |
| [Ciechanowski: Gears](https://ciechanow.ski/gears/)、[Internal Combustion Engine](https://ciechanow.ski/internal-combustion-engine/) | 從簡單元件開始，逐步加入 crank、齒輪、剖面和方程式；可拖曳 3D／剖面、調 slider、畫 trace；全域 pause 讓讀者停止動畫，把模型與畫面對照。 | 作者的頁面本身是工程解釋（A）；V：motion、cutaway 和負空間讓不可見結構變成可比較的狀態。可借「概觀→剖面→局部元件→公式」和「動畫可暫停」。不能只因畫面漂亮就宣稱更易學。 | 高：3D/WebGL、動畫和模型要大量內容與效能 QA；為低動態和讀屏提供靜態剖面、文字／數值表和 pause。 | 兩篇文章的主要互動和模型段落已讀；未對每個動態元件做完整手機／screen reader QA。 |

## 本輪新增：實際畫面指紋

以下不是只讀正文後的形容詞。我在 2026-10-04 用自己的研究瀏覽器分頁實際開啟官方頁面，查看首屏、官方文章中的作品截圖或指定互動區段；Khan、Duolingo、Brilliant、The Pudding、Red Blob Games、Seeing Theory 都至少有一個畫面是直接看過的。沒有把螢幕上的顏色抽成 hex，也沒有把未載入的作品當成看過。每項都把「畫面上看見的事實」「作者／官方說法」「我的感受假說」分開。

### Khan Academy／Wonder Blocks：中性畫布＋多色但有語意的系統

- **實際看到的畫面**：Khan 官方色彩文章的首屏是白色 masthead、黑色文字和很寬的主內容欄；主圖放在淺藍灰色矩形中，以圓餅切片和周圍的圓、三角形、五邊形等幾何形狀展示多種藍、綠、黃、橘、粉、紫。往下的 primitives 圖是按 hue 排列、由深到淺的整齊色塊矩陣；實際介面截圖則以淺色／白色畫布、細邊框、小圓角控制和少量紫色／多色小 icon 組成，文字保持深色。
- **設計指南／官方圖可核對的事**：文章明寫新 palette 先用三個 divergent interface directions 和窄而不同的 core hue 做 contrast 測試，再以 HSL lightness 0–100 建 primitives；實際 schema 是 `Domain → Layer → Context → Intensity`，而不是「一個產品一個顏色」。這是 A 和畫面截圖的交叉證據。
- **視覺指紋**：大面積中性或低彩度底；多色存在，但通常作色階、元件或圖形，不把整張背景染成高彩度；幾何形狀偏簡單、圓角克制、層級靠明度／大小／留白。整體像可擴充的學習產品系統，而不是一張 moodboard（最後一句是 V）。
- **感受假說 → 可替換元素**：保留「有系統但不冷漠」的感覺假說，需保留中性 canvas、固定 intensity scale、清楚的前景／背景 pair 和少量幾何 accent；可以替換 core hue、圖形角色、主題 anchor 和 illustration，但不要替換狀態色的用途、對比規則或元件間距。這是 V，不是受眾測試。
- **可移植到本專案**：AWS／IP／Java 可以各自換 `topic.accent`，但共用 `site.canvas`、`surface`、`text`、`focus`、`state-*`，正好對應 Wonder Blocks 的 semantic abstraction。這比在每份 `index.html` 散落一批 hex 更能維持全站辨識度。
- **查閱深度**：官方文章的 palette 圖、contrast 圖、semantic swatch 圖和 light/dark dashboard 圖以螢幕查看；文章核心文字已讀；未執行其 generator，也未把截圖當成本專案的 contrast pass。

### Duolingo：白底大留白＋角色插畫＋每個 tab 的局部強色

- **實際看到的畫面**：官方 redesign 文章頁本身是白色背景，頂部有綠色 blog mark、淡灰 uppercase 導覽和圓角搜尋框；標題用粗圓感的綠色字。文中的 app screenshots 都是白色手機畫面、圓角外框和固定的底部 icon navigation。`Punchy` 方案在 tab 頂部放大面積的粉紅、深藍或橘色實色 header；`Soft` 改用很淡的粉／藍漸層；`Modular` 把內容切成圓角卡片；`Flat` 大幅留白、幾乎不靠容器邊框。進度條和小 icon 才使用更飽和的粉、黃、藍。
- **設計文章可核對的事**：官方文字說明四個方向是把 consistency、simplicity、purpose、clarity 拉到可比較的極端，並在手機 prototype 上測試；後續保留 tiered heading、固定 title position、少量 type styles 和按用途留白。這是作者／團隊的 A，螢幕是畫面證據。
- **視覺指紋**：中性白底承擔主要面積；一個 tab 的身份通常由一塊 header 色、角色／物件插畫和固定底部導覽構成；圓角、粗線條角色、短標籤和 progress bar 讓畫面有遊戲介面味，但文字層級仍是簡潔的。高彩度不是平均撒滿頁面，而是集中在 tab header、進度和 icon。
- **感受假說 → 可替換元素**：保留「活潑、親近、願意探索」的感覺假說，需保留白底、圓角 shape、角色或抽象 illustration、一個局部高彩度焦點和穩定 navigation；可替換 tab anchor hue、角色風格、header 是實色或柔和漸層，但不應同時改變 type hierarchy、button meaning 和狀態色。感覺是 V；「delightful／easy and enjoyable」是 Duolingo 自己的 A，不是外部受眾研究。
- **可移植到本專案**：每個教學可有一個 `topic` 或 lesson accent，放在章節標誌／主圖／互動焦點；全站仍共用白／中性 canvas、字體、圓角、spacing 和按鈕行為。這樣可避免 AWS、IP、Java 各自成為完全不同的網站。
- **查閱深度**：官方 redesign 頁首屏、early explorations、Punchy、Soft 和 Flat 的截圖已以螢幕查看；本文沒有把官方 app screenshot 當成手機 QA，也沒有讀取實際 app。

### Brilliant：柔和漸層英雄區＋黑色大字＋少量高彩度行動色

- **實際看到的畫面**：Brilliant About 首屏是白色頂部導覽，右上是白底 outlined `Sign in` 和綠色實心 `Sign up`。主視覺是一大片非常淡的奶油黃、淡藍、淡紫和淡粉漸層，中央放兩行超大的黑色粗 sans heading，下方是一個灰紫、半透明的大圓弧／球體，帶少量白色點狀細節。往下的區段回到接近白色，使用較大的黑色 serif section heading、黑色文字和帶黑衣、青綠頭髮、珊瑚紅小物的 editorial illustration；Math／Coding 是一個淺灰圓角 segmented control。
- **官方意圖與畫面分開**：About 文字把產品稱為 interactive、adaptive、fun，並說視覺和可操作表示是方法；這是 A。上述漸層、黑字、圓弧、插畫、控制形狀是直接畫面觀察，不能把它們反推成學習成效。
- **視覺指紋**：大面積低彩度 pastel canvas＋少量黑色大字形成強對比；hero 的幾何體偏抽象、透明和柔和，下面再用一兩個飽和插畫細節給性格。留白很多，內容欄寬不擁擠；文字和 CTA 的黑／綠角色比各區塊換色更穩定。
- **感受假說 → 可替換元素**：保留「樂觀、輕盈、具能力感」的感覺假說，需保留 soft canvas、很清楚的黑色 typography、足夠留白和一個高辨識 CTA／illustration accent；可以換漸層方向、hero 幾何物件、插畫角色和 CTA hue，但不要讓低對比 pastel 承擔正文或錯誤訊息。這是 V；不能把品牌文案的 `purpose and joy` 當受眾測量。
- **可移植到本專案**：若未來想脫離目前平均綠色，可先把網站身份放在 typography、canvas、圓角／幾何圖形和一個 CTA role，而把 AWS／IP／Java accent 限制在圖解焦點。只換色、不換留白和 type hierarchy，才知道感受改變是否真的來自 palette。
- **查閱深度**：官方 About 首屏、`Our learners` illustration 和 Math／Coding segmented control 已以螢幕查看；未登入課程或逐題檢查其互動元件。

### The Pudding：黑色編輯室 shell，故事頁再換成紙色與單一 accent

- **實際看到的畫面**：官方 About 頁使用接近黑色的整頁 canvas；The Pudding logo 和 `ABOUT／SUBSCRIBE／MORE` 是白色手繪／貼紙感字形，主標題是大號白色 sans，介紹文字是大號米白 serif，混用 italic，段落下方用細灰分隔線。團隊照片在黑底上排列，色彩集中於照片而非 UI。實際查看 `On Upward Mobility` 故事首屏時，畫面改成很淡的暖白／紙色，中央上方是黑色 The Pudding wordmark，地圖只用非常細的粉紅／莓色線，沒有滿版照片或高彩度塊面。
- **官方／作品資料可核對的事**：About 明示「visuals inform and entertain」和自 2017 年做 visual essays；作品頁的畫面則直接顯示共同 logo／文字 shell 如何和故事局部圖形色分開。這裡的「編輯、好奇、認真又不嚴肅」是 V，不是 Pudding 讀者研究。
- **視覺指紋**：全站身份靠黑／白、手寫 logo、serif＋sans 對比、窄而長的 editorial measure 和少量分隔線；單篇故事可使用紙色、地圖線、照片或資料色，但不必把全站 shell 改掉。開場留白大，資料圖形出現時才提高密度。
- **感受假說 → 可替換元素**：保留「作者有觀點、值得慢慢探索」的感覺假說，需保留一個很清楚的 logo／wordmark、強烈 type contrast、低彩度大面積背景和一個故事 accent；可換 accent hue、紙色／深色比例、插畫／地圖語法與 section rhythm，但要維持來源／caption／正文的 editorial hierarchy。這是 V；`inform and entertain` 是作者明示的 A。
- **可移植到本專案**：可把網站首頁和每課的 `site shell` 分開：首頁／導覽固定一套 identity，lesson 圖解只換局部 accent；對 AWS／IP 共用 network family、Java 另用 accent，但不重造 logo、字級和來源區。
- **查閱深度**：About 首屏、獎項表和 `On Upward Mobility` 的實際首屏已以螢幕查看；未逐篇比較所有 Pudding story，也未把作品的資料色當作可及性通過證明。

### Red Blob Games：技術文件版式＋一條醒目概念色

- **實際看到的畫面**：`Making of: Circle drawing` 是白色中央閱讀欄，頂端有深紅色蜂巢／六角紋理 banner，白色 sans title 與 nav 疊在上面；正文是黑色 serif，超連結是紅色底線，右側有密集但清楚的 Table of Contents。圖解被放在文字之間，以白／灰網格、很淡的 slate 色方格、黃色或白色拖曳 handle、少量紅色文字／半透明標記組成，四周留有可見空白。這些是實際頁面首屏和圖解區段的畫面觀察。
- **官方 making-of 可核對的事**：作者說先做 shapes，再做 interaction 和 colors；`negative space` 段落明確解釋把網格邊線放到背景色，避免搶焦；頁面也說紅色會依「主要概念」加入或移除，radius 是焦點時才加回紅色。這是作者的 A，遠比「紅色讓人興奮」可靠。
- **視覺指紋**：像可讀的工程筆記，而不是全螢幕 app：白底、serif reading、固定目錄、深紅 header 作身份、SVG 圖解使用灰／米色底，再用一個黃／紅／白 handle 表示目前變數。密度集中在 diagram，段落周圍保持可呼吸的留白。
- **感受假說 → 可替換元素**：保留「親手拆解、精準但可以玩」的感覺假說，需保留 document shell、單一概念 highlight、diagram 與文字並排、可見的數值／handle；可以換 header texture、accent hue、grid shape 和字體 pairing，但不要讓裝飾色多到遮住主要變數，也不要把 diagram 背景改成全高彩度。
- **可移植到本專案**：CIDR／subnet 很適合借這個比例：網站層保留文件式閱讀，當前 bit／mask／network／host 用一個 accent、線型和文字 label 一起標；不同 topic 可換 banner／accent，但不換概念聚焦規則。
- **查閱深度**：官方 making-of 首屏、`Diagram`、`negative space`、`Detail: appearance`、`Summary` 和其內嵌 SVG demo 已以螢幕查看；未完整操作每一個 drag step，也未把頁面現有 contrast 當作本專案 pass。

### Seeing Theory：深色粒子封面 → 淺色分欄工作區

- **實際看到的畫面**：官方首頁是深靛紫／炭黑 canvas，整面散落大小不一的藍、青、橘、黃、紅、粉圓點；中央是白色 `Seeing Theory` sans heading 和白色圓角 `Start` button，頂部 nav 也是白色。進入 Basic Probability 後，chapter overview 改成很淡的天空藍背景，右側三個白色卡片各有灰藍圓形 icon；在 Expectation 互動區，左半是淺藍文字欄、公式、骰子和按鈕，右半是白色圖表 canvas，黑色座標軸與細藍色水平線，底部用藍色 bars 表示可調機率。
- **官方意圖與觀察分開**：首頁把自己稱為 `A visual introduction to probability and statistics`，About 說目標是用 interactive visualizations 讓 statistics 更 accessible（A）；「粒子封面有好奇、進入課程後變得有秩序」是 V。
- **視覺指紋**：封面用滿版深色和多色圓點製造活動感，課程內頁則降低彩度、提高空間和可讀性；圓形 icon、白卡、兩欄比例和簡單座標軸反覆出現，建立跨章節的學習語法。色彩從「環境背景」轉成「圖表／控制」時，面積和功能也跟著改變。
- **感受假說 → 可替換元素**：保留「先引起好奇，再進入清楚的工作台」的感覺假說，需保留 dark cover／light workspace 的節奏、圓形／卡片重複語法和圖表白底；可以換粒子 hue、chapter accent、icon illustration 和分欄比例，但不要用封面粒子色直接表示 success／error 或資料值，且要重新檢查淡色文字與圖形對比。這是 V，沒有把 Brown 的 views 當感受證明。
- **可移植到本專案**：可以讓互動教學開場用一個較有性格的 hero／topic canvas，進入推導時回到高可讀的中性 workspace；對 AWS／IP 可共享深色 network cover，Java 只換粒子／accent，不改正文、圖表和鍵盤路徑。
- **查閱深度**：官方首頁、Basic Probability chapter overview 和 Expectation 互動段落已以螢幕查看；未測量其淡色文字 contrast，也未做完整 keyboard／screen reader audit。

### 這些指紋不是 palette 複製表

上面六個案例的共同點是「面積、用途、形狀、字體和節奏」的組合：Khan 用語意與強度階梯，Duolingo 用白底和局部強色，Brilliant 用柔和 canvas 加大字，Pudding 用黑／白 editorial shell，Red Blob 用文件式版面加單一焦點，Seeing Theory 用 dark cover 到 light workspace 的場景切換。相同的感覺策略可以換 hue、illustration、texture 或 topic accent；若同時改掉文字對比、spacing、控制狀態和資料語意，就已經不是「同感覺、不同 palette」的受控比較。

本輪觀察仍有三個邊界：

- 螢幕截圖能支持「畫面上有什麼」，不能支持「所有人因此覺得什麼」；感受詞都標作 V 或作者 A。
- 官方 design guide 能支持角色、token 和選色流程，不能替本專案的離線 HTML 做 acceptance test。
- CSSDA Simulator 的官方作品 URL 目前顯示 Tilda `Domain has been assigned`；Awwwards 的 Oat the Goat detail 頁有 award metadata 和 palette／技術欄，但本輪未成功載入原作品。因此兩者沒有被列進上面六個「實際畫面指紋」，避免把獎項頁或失效 domain 當成作品畫面。

## 作品集、獎項和互動視覺參考

這一組適合回答「什麼樣的 visual language 會被策展人或設計社群注意」，不適合回答「讀者因此學得更好」。Awwwards／CSS Design Awards 的分數是平台評分，應記作 P，而不是使用者研究。

| 作品與官方獎項頁 | 確切訊號（年份／分數／技術） | 可觀察特徵與可借策略 | 感受證據、成本、a11y | 閱讀深度 |
|---|---|---|---|---|
| [Oat the Goat — Awwwards](https://www.awwwards.com/sites/oat-the-goat)；[CSSDA 2018 winners](https://www.cssdesignawards.com/blog/website-of-the-year-2018-winners/311/) | Awwwards SOTD 2018-06-13；頁面列 overall 7.88、design 7.77、usability 7.66、creativity 8.20、content 8.33、accessibility 7.67，技術含 WebGL／GSAP／Three。CSSDA 2018 WOTY 文章列入 Top 10、8.95 並獲 Best Animated Site。 | 三色主調（頁面列 `#2779a7`、`#49c5b6`、`#ECD06F`）、動畫故事書、清楚的角色和場景轉換；可借「少量高辨識 accent＋敘事節點」，不要照抄三個色碼。 | playful／curious 是 V（動態故事書和明亮三色的視覺推論），不是教育效果。WebGL/GSAP 成本高；所有關鍵訊息需提供文字、pause、低動態和非 WebGL 路徑。 | 官方獎項頁 metadata 已讀；未完整遊玩或做 a11y audit。 |
| [Simulator — CSS Design Awards](https://www.cssdesignawards.com/sites/simulator/46890/) | Special Kudos 2025-01-17；頁面列 public UI 7.82、UX 7.67、innovation 7.80，judge final 7.76，judge votes 20/20；描述為 KODE UAE 給 IT career aspirants 的 animated、fullscreen、one-page educational project。 | 全螢幕一頁、動畫和明確的職涯情境讓主題變得像可進入的空間；可借「一課一個完整舞台」和「開場先給視覺任務」，但需壓低裝飾以維持教學焦點。 | 「有效」只能說平台評分和作者描述（P/A）；不推論好玩或學會。全螢幕與動畫成本中至高；需要窄版、keyboard、skip、reduced-motion 和文字摘要。 | 官方獎項頁 metadata 已讀；未進行完整操作。 |
| [MedClass — CSS Design Awards](https://www.cssdesignawards.com/sites/medclass/42744/) | Special Kudos 2023-01-20；頁面列 public UI 6.57、UX 6.83、innovation 6.50，judge final 7.83；描述為給考慮醫學的高中生使用的免費教育平台，強調 animated、colorful、responsive。 | 可作「教育平台用有色 illustration／情境卡片」的對照案例；分數比 Simulator 不高，正好提醒色彩鮮豔本身不能當品質證明。 | colorful／friendly 是作品描述和 V，不是讀者研究。需保留文字層級、對比和替代文字；CSSDA 分數不回答 a11y 或學習轉用。 | 官方獎項頁 metadata 已讀；未進行完整操作。 |
| [Expedition Wild Worlds — Awwwards](https://www.awwwards.com/sites/expedition-wild-worlds) | Awwwards Honorable Mention 2018-02-15；頁面描述為 360 live-action WebVR expedition、Culture & Education，並列技術／評分欄。 | 以沉浸式環境把內容變成探索路徑；可借「先給地點／任務再讓讀者選方向」的敘事結構，不必引入 VR。 | curiosity 是 V；WebVR 成本和裝置依賴高，a11y 風險更高。若借用只保留 2D fallback、鍵盤／文字路徑和靜態地圖。 | 官方獎項頁 metadata 已讀；未進行 VR 操作。 |
| [My Little Storybook — Awwwards](https://www.awwwards.com/sites/my-little-storybook) | SOTD 2021-11-24；頁面列 overall 7.77、技術含 WebGL／GSAP／Lottie／C4D／Blender；搜尋結果與官方頁列 two-color palette（`#2779a7`、`#fff`）與 immersive children story。 | 以低數量色彩、插畫／3D 角色和轉場建立故事身份；可借「固定中性＋單一分類 anchor」，而不是用很多色碼競爭注意力。 | playful 是 V；WebGL/3D 成本高，動態和字體需靜態／低動態備援。分數只是 Awwwards 策展訊號。 | 官方獎項頁和搜尋 metadata 已讀；未完整操作，色票只作來源頁的記錄。 |

### 獎項到底在排什麼：官方評分機制與限制

- **Awwwards** 的官方 [Evaluation System](https://www.awwwards.com/about-evaluation/) 明列四項固定權重：Design 40%、Usability 30%、Creativity 20%、Content 10%。通過審核後，每個 nominee 至少送給 18 位 jury；離平均最遠的 3 個 jury 分數會被自動剔除；投票流程通常 5 天，若 jury 分數高且至少 10 位 PRO users 支持，可以提前成為 SOTD。官方也寫明 HM 是 jury 6.5 以上，SOTD 是當天 jury 分數最高者，SOTD 再交 developer jury、分數高於 7 才給 Developer Award；Site of the Month 是每月最高分的 8 個網站再審。這是**獎項／策展排名機制**，不是全網教育網站的客觀排名，也不是學習效果或受眾感受的研究。
- **CSS Design Awards（CSSDA）** 的官方 [Simulator detail page](https://www.cssdesignawards.com/sites/simulator/46890/) 內嵌 FAQ 說明兩套系統：WOTD 由 judges 決定，通常平均分數要超過 8（門檻會依提交作品品質變動）；非 WOTD 作品分數超過 6 可得 Special Kudos。Public Awards 分 UI Design、UX Design、Innovation，由 public votes 和 judge score 合併；要在一個或多個類別有 20 votes，且 judges 總平均超過 6。FAQ 對 UI 的解釋偏 aesthetics/effects、UX 偏功能、Innovation 偏新的開發／設計想法。Simulator 頁面本身列 public UI 7.82、UX 7.67、Innovation 7.80（各 20/20V）和 final judge 7.76，這是可核對的作品頁訊號。
- 因此，本報告把 Awwwards SOTD、CSSDA Special Kudos／Public Awards 當成「有人依該平台規則挑出並評分」的 P；它們可幫忙找值得看的藝術方向，不能證明「這套配色讓讀者好奇」或「這個教育互動有效」。平台的提交者、評審和作品類型本來就有選擇偏差；獎項頁也不一定呈現當前作品在所有裝置的真實體驗。

## 針對全站與分類配色的官方方法

這些不是「教育作品」，但能把前述案例的直覺落成可維護的規則。

| 來源 | 可移植規則 | 對本專案的用法與限制 |
|---|---|---|
| [USWDS color overview](https://designsystem.digital.gov/design-tokens/color/overview/)、[system tokens](https://designsystem.digital.gov/design-tokens/color/system-tokens/) | 用 lightness grade 和 system／theme／state token 建立 palette；文件建議先處理 black/white、hierarchy 和可用性，再用 moodboard 思考情緒，並提醒色彩感受受個人／文化影響。 | `site.*` 固定 canvas/surface/text/border/focus，`topic.*` 只改 anchor/container；先過 contrast 再討論「好玩」。USWDS 的比例和 grade 是方法提示，不是本專案必採數字。 |
| [IBM Carbon color](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview) | 以 role token 管理 hover、active、selected、focus、disabled；focus 用 2px border 並要求可辨識 contrast；文字／圖形有不同門檻。 | 可固定互動狀態，避免 AWS／IP／Java 的分類色把 `success`、`warning`、`error` 搞混。Carbon 的企業密度和色票不要直接搬入教材。 |
| [W3C WCAG 2.2 contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)、[non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html)、[designing](https://www.w3.org/WAI/tips/designing/) | 普通文字 4.5:1、大字 3:1；非文字 controls／圖形通常 3:1；不要用色彩作唯一辨識；先定 palette，再查連結、icon、按鈕、地圖、互動圖解和 responsive。 | 每一份教學的固定／變動、成功／錯誤、選中／未選中都要搭配文字、形狀、線型、位置或標籤。這是硬性可及性檢查，不是 mood 建議。 |
| [ColorBrewer 2.0](https://colorbrewer2.org/?open_in_browser=true) | 互動選 sequential、diverging、qualitative scheme，並檢查 colorblind／print／photocopy safe；可輸出 CSS/JS。 | 適合資料圖表的序列色、差異色和分類色，不是完整網站品牌 palette。若 CIDR 需要表示數值層級，可先用它理解資料色的任務，再嵌入本網站 semantic roles。 |
| [Adobe Spectrum introduction](https://spectrum.adobe.com/getting-started/introduction) | 設計系統把 color、spacing、type、motion 等設計決策寫成可學習的 token／component 規則。 | 支持將「風格參考」寫成可重複的 token 和元件契約，日後由 AI 產出不同主題時仍維持相同可用性；不代表要導入 Spectrum。 |

## 官方／原作者影片與演講

以下先記錄 4–8 個值得後續觀看的入口。這一輪**沒有完整觀看這些影片**；除 Nicky Case 項目另讀官方逐字稿外，其餘只核對官方 resource 頁、影片連結和可見 metadata。不要依影片標題推論未讀內容。

| 官方入口 | 日期／可核對訊號 | 本輪狀態 | 為何值得後續看、可對照什麼 |
|---|---|---|---|
| [Nicky Case — How To Explain Things Real Good（Stanford talk）](https://ncase.me/StanfordTalk/)、[官方 transcript](https://ncase.me/StanfordTalk/transcript.html) | 官方頁列 talk、slides 和 YouTube；逐字稿自述約 15–18 分鐘，談多年測試／迭代的解釋方法。 | **影片未觀看；官方逐字稿已讀。** | 可觀察作者如何把互動、比喻、預測和故事順序連在一起；後續應把影片畫面與逐字稿中的方法逐項對照。 |
| [Nicky Case — Learning & Games: A Confession](https://ncase.me/learning/) | 官方頁列約 30 分鐘 talk 加 1 小時 Q&A，並提供延伸閱讀。 | **影片未觀看；官方頁 metadata 已讀。** | 值得看它如何把「遊戲」和學習設計分開討論；不能只因標題就宣稱其主張。 |
| [PhET — A Brief Introduction to PhET](https://www.youtube.com/watch?v=gKI-9Ksvgg4) | PhET Simulations 官方 YouTube；發布 2013-01-13；搜尋時 metadata 顯示約 31,928 views、144 likes（2026-10-04 snapshot）。描述說明為介紹 PhET 關鍵特色。 | **只讀官方 YouTube metadata，未觀看。** | 後續可核對模型、控制、visual representation 和教學使用的具體示範；views／likes 是人氣訊號，不能當教學成效。 |
| [Carl Wieman — Why I founded PhET, the goal and unique features](https://www.youtube.com/watch?v=4p3wCu8oLOE) | PhET Simulations 官方 YouTube；發布 2025-03-26；搜尋時 metadata 顯示約 3,260 views、60 likes（snapshot）。 | **只讀官方 YouTube metadata，未觀看。** | 可與 PhET About／研究頁對照「作者宣稱的設計目標」和實際 demo 是否一致。 |
| [The Pudding — Shaping Ideas into Data Stories](https://www.youtube.com/watch?v=J3Awc4HxDK0) | The Pudding 官方 resources 列為 Data Stories Speaker Series，2020-10；官方頁連到此 YouTube URL。 | **只核對官方 resources 與連結，未觀看。** | 後續可看研究問題、storyboard、視覺焦點和資料故事如何取捨；適合對照本專案 brief 到 HTML 的流程。 |
| [The Pudding — Animating Data Visualization in Svelte](https://www.youtube.com/watch?t=2003s&v=pJcbZr5VlV4) | The Pudding 官方 resources 列為 Svelte Summit，2022-09，連到 YouTube。 | **只核對官方 resources 與連結，未觀看。** | 值得看動畫如何服務資料變化、狀態和效能，而不是只做轉場；使用 Svelte 的演講不能直接推導本專案應採套件。 |
| [The Pudding — Develop Your Data-Driven Storytelling Chops with Four Simple Principles](https://www.youtube.com/watch?v=yQp3Y7nf6Hc) | The Pudding 官方 resources 列為 Google Cloud Next，2018-07，連到 YouTube。 | **只核對官方 resources 與連結，未觀看。** | 可研究其敘事原則與資料圖表的選擇；後續須實際觀看並記錄講者說的四項原則，不能從標題擴寫。 |
| [The Pudding — Living Coding a Story from Start to Finish](https://www.youtube.com/watch?list=PLsuhXm2zs07JuSfrNentA3DxAbaFO7ay2&v=lvgzS0fWtJU) | The Pudding resources 列出 Living Coding playlist，官方頁顯示約 50 episodes。 | **只核對官方 playlist metadata，未觀看。** | 適合觀察從想法、資料、layout、transition 到 QA 的取捨；成本較高，後續可只選一集深入。 |

## 給本專案的視覺決策框架

### 建議的三層 token，而不是每課各自選色

```text
site.color.canvas
site.color.surface
site.color.surface-raised
site.color.text
site.color.text-muted
site.color.border
site.color.focus
site.color.interactive
site.color.interactive-on
site.color.state-success
site.color.state-warning
site.color.state-error
site.color.state-info

topic.network.accent
topic.network.accent-on
topic.network.accent-container
topic.network.accent-muted

topic.java.accent
topic.java.accent-on
topic.java.accent-container
topic.java.accent-muted

lesson.diagram-fixed
lesson.diagram-variable
lesson.diagram-derived
lesson.diagram-highlight
```

規則是：

- `site.*` 固定整個網站的閱讀、focus、狀態和元件行為。
- `topic.*` 讓分類有辨識度，但只影響 title marker、章節識別、局部圖解和互動焦點。
- `lesson.*` 由每個教學依原理定義，必須同時用標籤、位置、線型、形狀或數值說明；不可只用顏色。
- `state-*` 不隨 AWS／IP／Java 任意換成另一套意義。成功、錯誤、警告、focus 是使用者需要預測的功能狀態。
- 每個候選 palette 先通過 WCAG，再比較氣氛；若 accent 不能同時滿足文字對比，改用中性 container 和較深／淺的 token，不犧牲可讀性。

### 「同樣感覺、不同 palette」的可驗證流程

1. 把「方便、好玩、好奇」各寫成兩三個可觀察條件，例如「方便＝下一步位置穩定」「好玩＝改值立即看到因果」「好奇＝先預測再揭示」。這些標成假說。
2. 固定同一份 CIDR 內容、文字、layout、字體、spacing、圓角、預設值和 motion，只替換 semantic accent，避免一次改太多變因。
3. 做三組方向不同的候選：例如低彩度冷色、深色中性加明亮 accent、暖色小面積 highlight。名稱用角色或參數描述，不先命名「快樂色」「護眼色」。
4. 先檢查普通／大字、control／圖形對比、灰階、色覺差異、keyboard focus、窄螢幕、reduced motion、離線開啟和 print／截圖可讀性。
5. 用同一任務讓人比較 A/B/C：能否找到操作、預測結果、說明看哪裡、把規則套到新案例；再問第一印象和方便／好玩／好奇。主觀感受只能和任務表現並列，不能代替它。
6. 將最後選擇記成 token、對比結果、測試對象、日期和未解決問題，讓後續 AI agent 依規則延伸，而不是每次重新猜一組平均的綠色。

### 案例到本專案的優先清單

若後續只投入有限 token／時間，建議先深入以下順序：

1. **Khan Academy Wonder Blocks＋USWDS／W3C**：先把全站、分類、狀態和可及性分層，避免每課各自決定顏色。
2. **Duolingo redesign**：參考「同一品牌做多個視覺方向原型」和 typography／shape／spacing 的共同身份；不要先複製 Feather green。
3. **Brilliant＋PhET**：研究「問題、可操作模型、立即回饋」如何共同形成好玩的感覺；兩者都提醒內容狀態比裝飾色重要。
4. **Red Blob＋Ciechanowski**：研究單一變數、direct manipulation、pause、cutaway 和圖／公式同步，最貼近 AWS subnet／CIDR 的計算理解。
5. **Nicky Case＋Distill**：研究 prediction、sandbox、reveal 和替代路徑；先定每個互動回答的認知問題。
6. **The Pudding＋OWID**：研究共同網站 shell、資料來源、storyboard、chart/map/table 和每個故事的局部 accent；把來源與限制放進介面。
7. **Awwwards／CSSDA**：只作 moodboard 和視覺發現入口。可借構圖、層次和節奏，不把獎項分數當教育效果或可及性證明。

## 成本與學習適配

| 做法 | 大致成本 | 適合先做嗎 | 必須補的學習／a11y 路徑 |
|---|---:|---|---|
| Semantic CSS tokens＋三組 accent 候選 | 低至中 | 適合 | 對比、灰階、色覺、focus、分類色和 state 色分離；保留單檔離線能力 |
| SVG／HTML 的可拖曳數值與同步圖解 | 中 | 適合 | keyboard input、數值輸入、reset、文字摘要、圖和表互換 |
| Prediction → reveal → explanation | 中 | 適合 | 未互動前也能讀到問題；reveal 後逐點標出看哪裡與為何成立 |
| Scrollytelling／多階段頁面 | 中至高 | 有明確故事才做 | skip／章節導覽、靜態順序、reduced motion、手機 scroll 不遺失焦點 |
| Canvas／WebGL／3D／VR | 高 | 目前不應先做 | DOM／SVG／文字 fallback、pause、鍵盤、低效能裝置、screen reader 的平行表示 |
| 受眾 A/B/C 視覺比較 | 中 | 在有兩三個候選後做 | 測任務、預測、轉用和自評；樣本與日期要記錄，不能把單次偏好當普遍規則 |

「方便」要優先投資在 typography、spacing、預測性和狀態説明；「好玩」要優先投資在可逆試錯和即時因果回饋；「好奇」要優先投資在預測、局部揭示和可比較的前後狀態。這三者都能用低至中等成本的 HTML／SVG 做出，不必先導入 WebGL 或完整設計框架。

## 尚未驗證與限制

- 本文件沒有對現有 `lessons/aws/ipv4-bits-cidr/index.html` 做完整的 contrast、keyboard、手機、screen reader、reduced-motion 或色覺模擬 acceptance test。
- 除 Oat the Goat 官方獎項頁列出的色票外，沒有做全站色彩抽取，也沒有把任何來源 palette 當成本專案候選。
- Awwwards／CSSDA 分數、Brilliant／Python Tutor／Seeing Theory 的使用量和評論都是時間點、官方或平台頁面的訊號，沒有外部 audit，也不能證明教育效果。
- 本輪影片沒有完整觀看；Nicky Case Stanford talk 只讀官方逐字稿，其餘只讀官方 resources／YouTube metadata。後續若要引用演講觀點，仍需看影片或完整 transcript。
- 「綠色穩定、護眼」「明亮色好玩」「3D 讓人好奇」在本文只會標成 V、作者聲稱或平台描述，沒有冒充受眾研究。色彩情緒受 hue、明度、飽和度、背景、文化和任務影響，不能從色相單獨推導。
- Distill、PhET、Nicky Case、Pudding、Ciechanowski 等案例的互動可能依賴外部 script、WebGL 或網路；本專案交付仍以單一 HTML、離線、手機、鍵盤和可及性為硬限制。

## 直接來源清單（本輪保留）

教育／互動：

- [Brilliant About](https://brilliant.org/about/)
- [Brilliant Features](https://brilliant.org/help/features/)
- [Brilliant Trust and Methodology](https://brilliant.org/practice/guides/trust-and-methodology/)
- [Duolingo core tabs redesign](https://blog.duolingo.com/core-tabs-redesign/)
- [Duolingo imagery](https://design.duolingo.com/identity/imagery)
- [Duolingo typography](https://design.duolingo.com/identity/typography)
- [Khan Academy Wonder Blocks](https://blog.khanacademy.org/how-we-rebuilt-khan-academys-color-system-from-the-ground-up/)
- [PhET About](https://phet.colorado.edu/en/about)
- [PhET research](https://phet.colorado.edu/zh_TW/research)
- [Python Tutor](https://pythontutor.com/)
- [Codecademy](https://www.codecademy.com/)
- [Red Blob Games](https://www.redblobgames.com/)
- [Explorable Explanations](https://explorabl.es/)
- [R2D3](https://www.r2d3.us/)
- [Seeing Theory](https://seeing-theory.brown.edu/)
- [The Pudding About](https://pudding.cool/about/)
- [The Pudding resources](https://pudding.cool/resources/)
- [Our World in Data redesign](https://ourworldindata.org/redesigning-our-interactive-data-visualizations)
- [Distill interactive articles](https://distill.pub/2020/communicating-with-interactive-articles/)
- [Ciechanowski Gears](https://ciechanow.ski/gears/)

視覺策展／獎項：

- [Awwwards: Oat the Goat](https://www.awwwards.com/sites/oat-the-goat)
- [Awwwards: Expedition Wild Worlds](https://www.awwwards.com/sites/expedition-wild-worlds)
- [Awwwards: My Little Storybook](https://www.awwwards.com/sites/my-little-storybook)
- [CSSDA: Simulator](https://www.cssdesignawards.com/sites/simulator/46890/)
- [CSSDA: MedClass](https://www.cssdesignawards.com/sites/medclass/42744/)
- [CSSDA 2018 winners](https://www.cssdesignawards.com/blog/website-of-the-year-2018-winners/311/)

可及性／配色 guardrail：

- [USWDS color overview](https://designsystem.digital.gov/design-tokens/color/overview/)
- [IBM Carbon color](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview)
- [W3C contrast minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)
- [W3C non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html)
- [W3C designing for accessibility](https://www.w3.org/WAI/tips/designing/)
- [ColorBrewer 2.0](https://colorbrewer2.org/?open_in_browser=true)
- [Adobe Spectrum introduction](https://spectrum.adobe.com/getting-started/introduction)
