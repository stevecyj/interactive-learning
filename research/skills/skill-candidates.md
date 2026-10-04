# 互動式學習 HTML／Agent Skill 調查

調查日期：2026-10-04（Asia/Taipei）

這份調查針對目前專案的目標：以 `brief.md` 描述學習者、卡點與實際任務，以 `references/` 提供來源，最後產出可離線開啟的單一 HTML；頁面要循序教學、讓讀者改變條件後立即看到圖形／數值／結論連動，並在最後完成三題先作答再揭曉、逐步圖解的情境練習。

## 讀法與限制

- 這是只讀 survey；沒有安裝任何 Skill、npm 套件、瀏覽器或遠端腳本。
- 主要讀取 GitHub repo 的 `README.md`、實際 `SKILL.md`、官方文件與公開示例頁。只看到榜單或轉載摘要的項目沒有列為主要候選。
- 沒有執行 `npx skills find`：該命令本身會透過 `npx` 下載／執行 CLI，與本次「先不要安裝」的限制不一致。改用 GitHub 原始 repo、官方 README、GitHub API snapshot 與 `skills.sh` 僅作交叉發現。
- 星數是整個 repo 的星數，不是某個 Skill 的品質評分。Anthropic 的 repo 包含許多 Skill，不能把 repo 星數直接視為 `frontend-design` 或 `web-artifacts-builder` 的單項評價。
- GitHub repo 星數以 [github-snapshot-2026-10-04.json](./github-snapshot-2026-10-04.json) 為準，主要候選於 2026-10-04 11:36 UTC 查詢，補查項目各有獨立時間戳。星數會變動，後續投入前應重新查詢。
- 本次沒有逐一下載或操作候選的 live HTML；下面的「效果」是根據 repo 提供的示例、Skill 規則與 QA 流程評估，不能當成對每個示例的瀏覽器驗收。

## 搜尋紀錄

### 第一輪：泛搜

查詢方向：`interactive explainer agent skill`、`visual explanation HTML skill`、`Claude Code frontend design/web artifacts`、`interactive article/data storytelling`。先找出官方 Anthropic Skills、`visual-explainer`、`frontend-slides`、`html-anything`、OpenGenerativeUI，以及 Idyll、Tangle 等可作方法參考的專案。

第一輪的結論是：前端設計 Skill 很多，但真正同時處理「教學編排、可操作互動、單檔 HTML、來源核對、瀏覽器 QA」的項目很少；因此第二輪改為逐一追查教學型 Skill 的實際檔案。

### 第二輪：依第一輪結果補查

查詢方向：`ds-vibe/html-explainer`、`rlfordon/teaching-explainer`、`joshuadavidthomas/agent-skills/html-artifacts`，並回讀 Anthropic 的兩個 Skill、`nicobailon/visual-explainer` 與 `zarazhangrui/frontend-slides` 的實際 `SKILL.md` 和 README。這一輪確認了三個最貼近本專案的能力群：

1. `teaching-explainer`：教學互動與學習科學。
2. `html-explainer`／`html-artifacts`：單檔輸出、互動問題設計與實際 QA。
3. `visual-explainer`／`frontend-slides`：圖解語言、版面、動態簡報與跨 Agent 可攜性。

### 第三輪：針對缺口補查

為了避免只找到「排版漂亮」的 Skill，再查 `explorable explanations`、`interactive article`、`source-grounded lesson`、`retrieval practice interactive HTML`。新增的有效參考是 Idyll、Tangle／Bret Victor 的 reactive document 原則，以及 `iAmAdheil/skills` 的教學參考書工作流；它們沒有改變主推薦，但補足了「狀態如何綁定文字、圖形與模型」以及「來源／學習記錄如何累積」的觀點。

## 主要候選（10 個）

適配度分數是本次依教學、互動、來源、離線與驗收需求作出的主觀排序，不是實測評分，也不是社群評價。

### 1. `rlfordon/teaching-explainer`／`teaching-explainer`

- Repo：[rlfordon/teaching-explainer](https://github.com/rlfordon/teaching-explainer)（6 stars；repo-level）。
- Skill：[teaching-explainer/SKILL.md](https://github.com/rlfordon/teaching-explainer/blob/main/teaching-explainer/SKILL.md)；README：[README.md](https://github.com/rlfordon/teaching-explainer/blob/main/README.md)。
- 真實能力：先做 grounding、學習者程度、組織方式與教學模式的 scoping；再建立概念依賴順序。每個關鍵概念至少放一個 constructive interaction，例如 predict-then-reveal、self-explain、classify 或 predictive step-through；整頁至少兩個分散的 retrieval check，而且必須有「為什麼」回饋與 retry。內建 `predict-reveal`、`retrieval-mc`、`self-explain`、`classify`、`step-through` 元件，並要求鍵盤、ARIA live region、focus、reduced motion 與 WCAG 2.2 AA QA。
- 依賴：成品是內嵌 CSS／JavaScript 的單一離線 HTML；製作／測試 repo 需要 npm、Playwright、Chromium、axe-core。它還有自己的 component kit 與 review overlay，不能只複製一個 `SKILL.md` 就取得全部能力。
- 輸出形態：單一 self-contained lesson HTML，可放 GitHub Pages 或 LMS；互動只在瀏覽器自我檢查，不把資料送出。
- Claude Code／Codex 可攜性：Skill 使用 Agent Skills 形式，Codex 可以讀取其規則；README 主要描述 Claude Code，但成品格式與一般檔案操作沒有 Claude 專屬 runtime。完整 kit／測試流程仍要自行移植或手動遵循。
- 對本專案適配度：**5/5，最適合作為教學流程來源**。它直接覆蓋「先理解再練習、答錯後解釋、鍵盤與手機」這些需求。
- 缺口：Phase 0 強制要求六軸訪談，和本專案「除非關鍵資訊不足，不必逐項詢問」不同；強制兩個 retrieval check 也不一定適合每個短主題。它沒有 `brief.md`／`references/` 的專案慣例，需要把現有檔案結構接上。

### 2. `ds-vibe/html-explainer`／`html-explainer`

- Repo：[ds-vibe/html-explainer](https://github.com/ds-vibe/html-explainer)（15 stars；repo-level）。
- Skill：[SKILL.md](https://github.com/ds-vibe/html-explainer/blob/main/SKILL.md)；README：[README.md](https://github.com/ds-vibe/html-explainer/blob/main/README.md)；[live examples gallery](https://ds-vibe.github.io/html-explainer/)。
- 真實能力：以「一個 mental model、逐步增加複雜度、可操作 micro-demo」組織教學；先研究與釐清 brief，再決定 scrolling page 或 slide deck。README 提供 Doppler effect、fractional reserve banking、Gutenberg printing press、EU AI Act 等可直接閱讀的單檔示例。品質迴圈會用 headless browser 截 desktop、mobile、interactive states，回看後再修改；quiz 要顯示文字版正誤、正解標記、why feedback 與 retry，不能只用綠／紅色。
- 依賴：成品可用 inline CSS／vanilla JS；品質迴圈需要 Node、Playwright、Chromium。README 明確說首次執行可能自動安裝約 100–200 MB 的 Chromium，這不符合目前「先不要安裝」的 survey 限制，但只影響製作工具，不是最終 HTML 的離線使用。
- 輸出形態：單一 HTML，或單檔 slide deck；附帶可選的 Review & edit overlay。頁面形狀可依內容選 scrolling、deck 或 hybrid。
- Claude Code／Codex 可攜性：主要為 Claude Code，但規則是 Markdown，Codex 可參考；品質迴圈強依賴 Claude Code 的瀏覽器操作流程，需自行改成 Codex 的瀏覽器工具或手動驗收。
- 對本專案適配度：**5/5，最接近目前的動態簡報與視覺教學目標**。尤其適合把「原本寫法／展開結構／圖形／練習」組成一條閱讀路徑。
- 缺口：七項必問會造成前置互動；視覺品質規則很多，可能讓短教材變重。它的模式偏「內容先寫成一頁完整 explainer」，而本專案希望沿用 `brief.md` 與 references 並固定三題練習，需要自行加上專案契約。

### 3. `joshuadavidthomas/agent-skills`／`html-artifacts`

- Repo：[joshuadavidthomas/agent-skills](https://github.com/joshuadavidthomas/agent-skills)（54 stars；repo-level，多個 Skill）。
- Skill：[html-artifacts/SKILL.md](https://github.com/joshuadavidthomas/agent-skills/blob/main/html-artifacts/SKILL.md)；README：[agent-skills/README.md](https://github.com/joshuadavidthomas/agent-skills/blob/main/README.md)；另有 [quality-and-validation.md](https://github.com/joshuadavidthomas/agent-skills/blob/main/html-artifacts/references/quality-and-validation.md)。
- 真實能力：把輸出分成 document、explorable document、presentation；要求先讀來源、建立 evidence ledger，分開 observed／inferred／proposed，記錄未知資訊。每個控制項都要符合「讀者問題 → 操作 → 立即可見答案」；因果關係用 controlled parameter paired with immediate output。明確要求真正離線單檔、inline CSS／JS／SVG／資料、無 CDN／remote fonts／fetch／server；QA 覆蓋 320–390px、鍵盤、focus、非色彩線索、reduced motion、console／network errors、數值和來源核對。
- 依賴：預設建議 plain semantic HTML、inline SVG、少量 vanilla JS；可選 component contract 與 Python inliner。最終成品不需要框架或網路。
- 輸出形態：本地單檔 HTML；explorable document 很適合「預設狀態完整，互動深入理解」的形式。
- Claude Code／Codex 可攜性：README 遵循 Agent Skills specification，也支援 Claude Code、OpenCode 與 skills.sh；Codex 可以直接讀 Markdown 規則。瀏覽器 QA 仍取決於執行環境是否有瀏覽器工具。
- 對本專案適配度：**5/5，最適合作為離線與驗收契約**。它幾乎直接回答本專案「互動不能只是翻頁」和「單一 HTML」的要求。
- 缺口：不是教學專用 Skill，沒有固定的前置概念分析、retrieval practice 或三題解題流程；需要把現有 prompt 的教學規則疊在它的 artifact／QA 規則上。repo 星數也不能代表 `html-artifacts` 這個單一 Skill 的採用度。

### 4. `clockless-org/html-anything`／`html-anything`

- Repo：[clockless-org/html-anything](https://github.com/clockless-org/html-anything)（152 stars）。
- Skill：[SKILL.md](https://github.com/clockless-org/html-anything/blob/main/SKILL.md)；README：[README.md](https://github.com/clockless-org/html-anything/blob/main/README.md)；[live demo gallery](https://clockless-org.github.io/html-anything/examples/)。
- 真實能力：把 idea、brief、檔案、資料夾、URL 或匯出資料轉成 HTML；以 use case、source、style 三層路由，對「teach me／tutorial」選 `teaching` 的 Lesson Lab 形狀。README 宣稱有 60 個 source prompts、17 個 style systems、11 個 demos，並要求讀取 reference HTML、第一 viewport、token、component vocabulary、interaction model 與 motion grammar，保留樣式參考的結構契約而非只換顏色。
- 依賴：可產出單檔，但 README 也允許 `assets/`、生成圖片與 local media；設計規則的預設外部字體呼叫需要特別關掉，才能符合本專案的完全離線條件。製作流程使用檔案／瀏覽器，沒有固定 React runtime。
- 輸出形態：預設 `output.html`，必要時加 `assets/`；明確要求 single-file 時才把 CSS、JS、資料和資產盡量內嵌。教學 style 有 visual stage、step rail、try-it controls、concept cards、check-yourself、recap 等版型。
- Claude Code／Codex 可攜性：README 明確列出 Claude Code、Codex、Cursor、OpenCode 等使用方式，這是目前候選中最清楚的跨 Agent 路徑之一。
- 對本專案適配度：**4.5/5，最適合作為 references／樣式參考的輸入路由**。特別值得借用它對「參考 HTML 是結構契約」的定義。
- 缺口：它是廣泛的 HTML artifact router，不是嚴格的學習科學流程；自動 style routing 可能繞過本專案對 `brief.md` 的固定要求。必須明確覆寫「單檔、無外部字體／CDN／fetch、以 `lessons/.../index.html` 為輸出、依 references 核對」等限制。

### 5. `nicobailon/visual-explainer`／`visual-explainer`

- Repo：[nicobailon/visual-explainer](https://github.com/nicobailon/visual-explainer)（10,239 stars；repo-level）。
- Skill：[plugins/visual-explainer/SKILL.md](https://github.com/nicobailon/visual-explainer/blob/main/plugins/visual-explainer/SKILL.md)；README：[README.md](https://github.com/nicobailon/visual-explainer/blob/main/README.md)。
- 真實能力：以 figures 作為頁面骨架；每個 figure 只表達一個 claim，先畫機制再寫名稱，箭頭用動詞標示。對流程用 stepper／scene player，對 live parameter 用 live figure，對案例用 small multiples，對架構／資料流用手繪 inline SVG。要求第一視窗就放主答案、狀態不能只靠顏色、數字旁邊放圖、動畫只表達 change／flow，並支援 reduced motion。README 提供 self-contained HTML、dark/light theme、hand-drawn diagrams 與 browser output。
- 依賴：正常 Skill 使用無 build step、只需瀏覽器；README 允許字型／libraries CDN，MCP／PPTX 等加值工具需 Node 套件。若採用本專案，必須刪除 CDN，改用 system fonts 和 inline SVG／vanilla JS。
- 輸出形態：一個完整 HTML；預設輸出到 `~/.agent/diagrams/` 或使用者指定路徑。Markdown companion 只有使用者要求 source brief 時才產生。
- Claude Code／Codex 可攜性：README 明確列出 Claude Code、Codex CLI、OpenCode、Cursor、Antigravity 等路徑，跨 Agent 支援很好。
- 對本專案適配度：**4/5，最適合作為圖像語言與圖解規則來源**。CIDR／bit／mask 這類「同一狀態多個表示同步變化」的教材很適合借用它的 figure、stepper 和 live figure 觀念。
- 缺口：核心仍是 visual explanation，不是完整教學編排；沒有固定的 prerequisite map、三題情境題、作答後逐步解答或 source ledger。原始規則容許 CDN，和本專案的離線要求直接衝突。

### 6. `zarazhangrui/frontend-slides`／`frontend-slides`

- Repo：[zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides)（30,118 stars）。
- Skill：[SKILL.md](https://github.com/zarazhangrui/frontend-slides/blob/main/SKILL.md)；README：[README.md](https://github.com/zarazhangrui/frontend-slides/blob/main/README.md)。
- 真實能力：零依賴、單一 HTML、inline CSS／JS；先產生三個視覺 preview，讓使用者用實際畫面選風格；有固定導覽、箭頭／Space／swipe、進度顯示、URL hash、focus 移動、reduced motion 與 inline text editing。README 明確說 Codex、Kimi Code、OpenCode 等也可讀取同一份 Skill。
- 依賴：最終 HTML 不需要 npm／build tools；PPTX、PDF、Vercel 部分才需要 Python、Playwright、Node 或 Vercel。
- 輸出形態：固定 1920×1080、16:9 stage 的 HTML presentation。
- Claude Code／Codex 可攜性：**很高**，README 直接說其他 coding agent 讀 `SKILL.md` 即可使用。
- 對本專案適配度：**3.5/5，適合借用導覽、進度、風格探索**。
- 缺口：固定 16:9 stage 且手機不重排內容，和本專案要求真正適合手機、可讀的教學頁衝突；它偏簡報與視覺風格，沒有來源 grounding、概念前置、數值模型同步或教學型回饋。應借用導覽機制，不能當核心教學 Skill。

### 7. `anthropics/skills`／`frontend-design`

- Repo：[anthropics/skills](https://github.com/anthropics/skills)（179,585 stars；整個多 Skill repo）。
- Skill：[skills/frontend-design/SKILL.md](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md)；repo README：[README.md](https://github.com/anthropics/skills/blob/main/README.md)。
- 真實能力：要求設計由主題、受眾與主要工作推導，先做短 design plan，再檢查是否只是通用 AI 預設；明確要求有意識的 palette／type／layout，少用裝飾性動態，支援 mobile、visible keyboard focus、reduced motion 和 screenshot critique。它對「不要把每個頁面做成相同 SaaS 卡片」的提醒很實用。
- 依賴：沒有固定 runtime 或 build pipeline；它是設計判斷規則，不會替專案產出 component kit 或 QA script。
- 輸出形態：沒有固定輸出，取決於呼叫它的前端任務。
- Claude Code／Codex 可攜性：Markdown 規則可由 Codex 讀取；官方 repo 主要圍繞 Claude Skills 系統。
- 對本專案適配度：**3/5，適合作為視覺 review 規則**，不是教學生成器。
- 缺口：不處理 brief／references grounding、互動模型、練習題、離線包裝或瀏覽器驗收；不能因 repo 星數很高就把它當成完整方案。

### 8. `anthropics/skills`／`web-artifacts-builder`

- Repo：[anthropics/skills](https://github.com/anthropics/skills)（179,585 stars；整個多 Skill repo）。
- Skill：[skills/web-artifacts-builder/SKILL.md](https://github.com/anthropics/skills/blob/main/skills/web-artifacts-builder/SKILL.md)；repo README：[README.md](https://github.com/anthropics/skills/blob/main/README.md)。
- 真實能力：為複雜、多元件的 Claude HTML artifact 建立 React 18 + TypeScript + Vite + Tailwind + shadcn/ui 專案，再用 Parcel 和 html-inline 打包成單一 `bundle.html`。適合有 routing、state management、複雜表單或大量 shadcn 元件的 artifact；也有避免 generic AI UI 的設計規則。
- 依賴：Node 18+、React、TypeScript、Vite、Tailwind、shadcn、40+ Radix 元件；`bundle-artifact.sh` 會安裝 Parcel、resolver、html-inline 等 bundling dependencies。最終檔案可以內嵌，但製作流程不符合目前「單檔、無外部套件」的簡潔預設。
- 輸出形態：多檔 React 專案加最後的 self-contained `bundle.html`。
- Claude Code／Codex 可攜性：官方 Skill 偏 Claude.ai artifact，但腳本是一般 shell；Codex 可手動遵循，沒有同等保證。對只想維護 `lessons/.../index.html` 的專案，移植成本高。
- 對本專案適配度：**2.5/5，目前不建議作預設**；未來教材變成真正的多頁應用或複雜互動工具時再考慮。
- 缺口：沒有教學編排、來源核對、三題解答或手機／鍵盤 QA 契約；authoring 依賴很多，增加 token、安裝和 bundling 失敗面。

### 9. `iAmAdheil/skills`／`teach-me`

- Repo：[iAmAdheil/skills](https://github.com/iAmAdheil/skills)（0 stars；repo page 沒有 README，只有 2 commits）。
- Skill：[teach-me/SKILL.md](https://github.com/iAmAdheil/skills/blob/master/teach-me/SKILL.md)。
- 真實能力：先提供短回答，再詢問是否建立文件；建立文件後依照來源和程度生成七段文章：Hook、Key Components、Concrete Example、Visual Model、Deeper、Cross-links & Sources、Recall／Check。Skill 要求官方 primary sources、概念 map／animated SVG、interactive recall、Bloom calibration、Mayer 原則，並把原始 Q&A 存成 `source.md`，再產生 `index.html` 和索引。這是「教學資料累積成參考書」的完整工作流。
- 依賴：Skill 參照 `references/`、`templates/`、scripts 和外部查詢工具；公開的第三方 Skill catalog 標示 requests、BeautifulSoup、pandas 等依賴，但因 repo 沒有 README，不把該依賴視為已由 repo README 確認。它也以 `.claude/teaching/` 或 user scope 的資料庫為中心，和本專案的 `lessons/<topic>/<lesson>/` 不同。
- 輸出形態：Q&A source markdown、七段文章、SVG 視覺、`index.html` 以及索引；不是單一「讀 brief／references 後寫指定路徑的 index.html」契約。
- Claude Code／Codex 可攜性：frontmatter 和 Markdown 可讀，但 workflow 寫得很 Claude／`.claude` 導向；Codex 需要自行改路徑與工具名稱。
- 對本專案適配度：**3.5/5，值得借用來源分層、程度校準與七段教學骨架**。
- 缺口：0 stars、repo 很小，沒有可由 README 驗證的品質／瀏覽器 QA 證據；它會先問是否建立 doc，和本專案想直接依 `brief.md` 產出不完全一致。不能只因規則寫得完整就視為已證明效果好。

### 10. `jamesrochabrun/skills`／`math-teacher`

- Repo：[jamesrochabrun/skills](https://github.com/jamesrochabrun/skills)（214 stars；多個 Skill）。
- Skill：[skills/math-teacher/SKILL.md](https://github.com/jamesrochabrun/skills/blob/main/skills/math-teacher/SKILL.md)；repo README：[README／Skills index](https://github.com/jamesrochabrun/skills#skills-plugin--marketplace)。
- 真實能力：針對數學產生 interactive playground；包含圖形／動畫／SVG／canvas、sliders、即時回饋、進階程度、題目挑戰、提示和 gamification。Skill 的標準 playground 結構是 header／score、visual area、controls、real-time explanation、points／achievements；宣稱 mobile、keyboard／ARIA、單檔無外部依賴。它有分數、拋物線係數滑桿、導數切線等具體互動例子。
- 依賴：設計上是 pure HTML／CSS／JS；repo 另附 `generate_playground.sh`、`generate_game.sh`、`generate_quiz.sh`，Skill 文字甚至含有作者本機絕對路徑，移植時不能照抄。沒有 source grounding 或通用內容來源流程。
- 輸出形態：獨立 HTML playground／game／quiz；偏互動練習，不是來源驅動的教學文章。
- Claude Code／Codex 可攜性：一般 HTML／JS 可移植；生成 scripts 的路徑與 Bash 指令需要重寫，Codex 不能假設那些檔案存在。
- 對本專案適配度：**2.5/5，僅作為「即時控制＋數學圖形」的局部參考**。CIDR／位元計算可借用 slider、同步圖形與 challenge 的想法。
- 缺口：只適用數學，強調 gamification，可能造成學習干擾；用 color-coded explanation 但本專案要求不能只靠顏色；沒有 references／引文／證據 ledger，也沒有本專案的「三題逐步圖解」規則。

## `references` 轉成互動頁面的映射能力

本專案真正要評估的不是「能不能產生漂亮 HTML」，而是能否把來源材料轉成一條可檢查的映射：

```text
來源 references／brief
  → 核心概念與前置依賴
  → 可操作的 state／輸入
  → 定義、推導、情境規則
  → 圖形／文字／數值的同步 render
  → 立即回饋、解釋與重試
```

下面把十個主要候選放回這條鏈上。這裡的「有」表示 Skill 明確要求或提供相應流程；「弱」表示可以由 Agent 自行補，但 Skill 沒有形成可依循的契約；「無」表示它主要負責美化、導覽或 runtime。

| 候選 | 來源 → 概念 | 概念 → state／輸入 | 規則 → render | render → 回饋 | 判斷 |
|---|---|---|---|---|---|
| `teaching-explainer` | **有**：primary source、學習者程度、concept dependency | **中強**：constructive interaction 元件，但 state schema 由每頁決定 | **中**：教學骨架清楚，定義／推導／情境規則要由作者標出 | **強**：why feedback、retry、live region | 最完整的教學流程，需接上本專案檔案結構 |
| `html-explainer` | **有**：source grounding、mental model、單一 centerpiece | **中強**：micro-demo、slider／toggle／quiz，但沒有固定資料 schema | **中**：要求事實、引用、邏輯順序；規則分類需自行設計 | **強**：micro-demo、quiz verdict、why、retry | 很接近目標，適合做生成流程參考 |
| `html-artifacts` | **強**：evidence ledger、observed／inferred／proposed | **強**：controlled parameter paired with immediate output | **中強**：按 governing question 選 representation，要求來源與未知可追溯 | **強**：每個 control 必須回答問題；但沒有教學型答題 kit | 最好的 artifact／離線／QA 契約，不是完整教學法 |
| `html-anything` | **強**：idea／file／folder／URL／brief → source/use case/style | **中**：style 會決定 interaction model，但 state 不是通用 schema | **弱中**：來源 prompt 與 style prompt 可承載規則，沒有固定定義／推導分類 | **中**：teaching style 有 try-it／check-yourself，但回饋依 style | 適合 references 與樣式路由，需鎖定 offline 和教學規則 |
| `visual-explainer` | **中強**：一個 source claim 對一個 figure | **中**：live figure、stepper、scene player 可承載狀態 | **強於圖形**：機制、箭頭動詞、數字旁圖；教學規則分類弱 | **中**：圖形隨 state 變，但沒有 quiz／retry 契約 | 最適合作為圖解層，不是完整 lesson generator |
| `frontend-slides` | **弱**：brief → 三個視覺 style preview | **弱**：主要是 slide index、hash、edit state | **無／弱**：內容規則不在 Skill 內 | **中**：導覽、focus、swipe；沒有概念 feedback | 主要是簡報排版與導覽，不能解決 source→learning mapping |
| `frontend-design` | **中**：brief／subject → palette、type、layout plan | **無**：不規定教學 state 或 input | **無**：沒有來源規則或計算模型 | **弱**：只要求視覺 review、focus、reduced motion | 純設計 review；不要誤當互動教學 Skill |
| `web-artifacts-builder` | **弱**：把產品需求轉成 React artifact | **強於工程**：React state、routing、components | **弱**：可把規則寫進程式，但 Skill 沒有教學分類 | **弱中**：元件能互動，沒有教學回饋契約 | 複雜 app builder；對本專案是過重的實作底座 |
| `iAmAdheil/teach-me` | **強**：official sources → Q&A `source.md` → 7-section article | **中強**：Bloom calibration、visual type、recall；具體 state 仍由生成頁實作 | **中強**：七段骨架和 visual type catalog，適合映射定義／例子／edge cases | **中強**：interactive recall、quiz、step reveal；QA 證據不足 | source→lesson 思路很完整，但 repo 小且工具／路徑耦合 |
| `math-teacher` | **弱**：user prompt → math playground，通常不是讀 references | **強**：slider／input → graph／canvas／score | **中**：公式與 challenge 可編碼，沒有 source ledger 或規則分類 | **強**：即時圖形、提示、try-again、challenge | 可借用同步互動；不適合作為通用來源驅動流程 |

因此，真正能支援「`references` → 動態視覺」的候選是 `teaching-explainer`、`html-explainer`、`html-artifacts`、`iAmAdheil/teach-me`；`html-anything` 負責 source／style 路由；`visual-explainer` 和 `math-teacher` 負責局部圖形與 state pattern。`frontend-design` 和 `frontend-slides` 主要是美化／導覽，不能單獨達成教學目標；`web-artifacts-builder` 是工程底座，也不會自動把來源轉成可學習的模型。

## 另外檢視但不列入主要 Skill shortlist 的工作流

### `kambleakash0/agent-skills`／`teach-me`

- Repo：[kambleakash0/agent-skills](https://github.com/kambleakash0/agent-skills)（9 stars；repo-level）。
- Skill：[skills/teach-me/SKILL.md](https://github.com/kambleakash0/agent-skills/blob/main/skills/teach-me/SKILL.md)；README：[README](https://github.com/kambleakash0/agent-skills)。
- 它把學習視為長期 workspace：`MISSION.md`、`GLOSSARY.md`、`RESOURCES.md`、`learning-records/`、`lessons/`、`cheatsheets/`。每課只教一件事，先讓學習者做互動題或真實任務，立即回饋，所有事實要引到 `RESOURCES.md`。
- 這對本專案的 `brief.md` 與 `references/` 很有啟發，但它不是視覺化 HTML 生成器；沒有單檔、圖形同步、手機／鍵盤 QA 的實作契約。適合借用「任務目標、學習記錄、來源清單」而不是整份安裝。

## 非 Skill，但值得作為互動原理參考

### Idyll：宣告式 interactive article

- Repo：[idyll-lang/idyll](https://github.com/idyll-lang/idyll)（2,041 stars；repo-level）。
- 文件：[Idyll overview](https://idyll-lang.org/docs)。
- Idyll 用接近 Markdown 的語法寫 interactive essays／explorable explanations；變數可綁定元件、按鈕與 input，變數更新時圖表和其他元件同步重繪，並能接 D3／P5。這正好對應「改一個條件，原本寫法、圖形、數值和結論一起變」。
- 它是 Node／React／npm 的 authoring framework，不符合目前單一離線 HTML 的預設；最值得借的是「單一狀態模型驅動多個表示」而不是直接引入工具。

### Tangle 與 Bret Victor 的 reactive document

- Repo：[worrydream/Tangle](https://github.com/worrydream/Tangle)（1,800 stars；repo-level）。
- 原理文章：[Explorable Explanations](https://worrydream.com/ExplorableExplanations/)。
- Bret Victor 的核心不是把讀者丟進 sandbox，而是把模型、文字和圖形嵌在解釋裡：讀者改變假設後，後文與圖形立即重算；靜態說明仍完整，互動讓讀者驗證和追問。文章也強調每個互動要有作者引導，不能只叫讀者「自己探索」。
- Tangle repo 很舊，沒有現代手機、無障礙、ES module 或本專案 QA 的保證；應作為 interaction pattern 的思想來源，不應直接當成依賴。

### CopilotKit／OpenGenerativeUI：互動元件決策與視覺回應層

- Repo：[CopilotKit/OpenGenerativeUI](https://github.com/CopilotKit/OpenGenerativeUI)（1,584 stars）。
- Skill：[master-playbook/SKILL.md](https://github.com/CopilotKit/OpenGenerativeUI/blob/main/apps/agent/skills/master-playbook/SKILL.md)；README：[README.md](https://github.com/CopilotKit/OpenGenerativeUI/blob/main/README.md)。
- 它提供「問題類型 → SVG／stepper／chart／interactive widget」的 decision tree，以及 Hook → Visual → Narration 三層結構；互動 widget 要有可調參數與即時輸出。這些規則可拿來完善 prompt 的表示選擇。
- 但它是自架 generative UI 應用：Next.js、Python／LangGraph、Anthropic 或 OpenAI API、MCP、sandbox iframe；文件還使用 esm.sh import map。它不是離線單檔教材生成器，應只取方法，不列為本專案的執行基礎。

## 綜合判斷

目前沒有一個候選完整涵蓋本專案的所有條件。最實用的組合是「借規則，不急著安裝」：

1. **教學編排**：以 `teaching-explainer` 的 concept dependency、constructive interaction、why feedback、retry 為主；用 `html-explainer` 的 mental model、micro-demo、progressive complexity 和三層深度補強。
2. **離線與 QA**：以 `html-artifacts` 的 explorable document、evidence ledger、單檔 offline、控制項問題／答案契約和 320px／keyboard／network 檢查為硬規則。
3. **圖解語言**：借 `visual-explainer` 的 one claim per figure、draw the mechanism、live figure、small multiples、非色彩狀態與 reduced-motion。
4. **樣式參考**：借 `html-anything` 對 reference HTML 的「第一視窗、元件詞彙、互動模型、motion grammar」要求；`frontend-design` 只用來做主題化視覺 review。
5. **導覽**：若要做動態簡報，借 `frontend-slides` 的 progress、鍵盤、hash／focus 機制，但保留本專案真正的手機 reflow，不採用它的固定 16:9 stage。

若只選三個後續深入閱讀，優先順序是：

1. [`rlfordon/teaching-explainer`](https://github.com/rlfordon/teaching-explainer)：最完整回答「怎麼教」。
2. [`joshuadavidthomas/agent-skills/html-artifacts`](https://github.com/joshuadavidthomas/agent-skills/tree/main/html-artifacts)：最完整回答「怎麼做成真正離線且可驗收的 HTML」。
3. [`ds-vibe/html-explainer`](https://github.com/ds-vibe/html-explainer)：最接近「有視覺品質的循序互動教學」，而且有多個 live examples 可對照。

接著再看 [`clockless-org/html-anything`](https://github.com/clockless-org/html-anything) 的 source／style routing，以及 [`nicobailon/visual-explainer`](https://github.com/nicobailon/visual-explainer) 的 figure 規則。`frontend-slides`、`frontend-design` 和 `math-teacher` 適合抽取局部做法；`web-artifacts-builder`、Idyll、OpenGenerativeUI 暫時不適合成為本專案的預設技術路線。

## 可直接轉成現有 prompt 的共同工作流

這不是安裝指示，而是從候選中整理出的本專案候選規格：

1. **讀取並建 evidence ledger**：先讀 `brief.md`、`references/README.md`、來源檔與樣式參考；標記哪些是來源明載、哪些是推導、哪些是本次教學安排，記下來源日期與未知處。
2. **找出一個 governing question**：學完後要能理解、比較、驗證或做哪個真實判斷；把卡點拆成最少的前置概念與依賴順序。
3. **選一個主表示**：流程用 stepper、因果用控制項＋即時輸出、狀態用 state diagram、比較用 aligned small multiples、空間關係用 SVG／topology。每幅圖只回答一個問題。
4. **先給完整靜態解釋，再加探索**：互動是深入理解，不應成為讀者取得主結論的唯一方式。
5. **維持單一狀態來源**：每個控制項只改一個明確變數；同一份 state／計算結果更新圖形、數值、原文對照、結論與解題標記。畫面上明確標「改了什麼、保持什麼不變、為何結果改變」。
6. **練習採 predict → reveal → explain → retry**：三題由單一判斷到綜合判斷；作答前不揭曉；作答後依序標出條件、圖中關鍵位置、適用定義／推導／情境規則、成立或不成立的原因。
7. **交付前實測**：開啟真正的最終 HTML，檢查 console、外部請求、桌面與 320–390px、鍵盤 focus、窄螢幕、reduced motion、無效與邊界輸入、三題未作答／答對／答錯／重試。未操作的項目不能宣稱已驗證。

這個組合比直接選一個高星前端 Skill 更貼近本專案：高星通常證明 repo 有人看過，不能證明它會把 `references` 可靠地轉成教學、也不能證明它符合單檔離線和三題逐步解答。
