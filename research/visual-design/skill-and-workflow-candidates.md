# 互動教材的視覺方向、配色與受眾感受：Skill／工作流候選

調查日期：2026-10-04（Asia/Taipei）

這份文件是調查記錄。**沒有安裝、執行或新增任何 Skill，也沒有修改既有 HTML、prompt 或 AGENTS.md。** 連結以原作者 repository、官方文件或原始研究為主；星數是 GitHub repository 層級的單次快照，不是品質證明。

## 先給判斷

目前最值得後續投入的不是找一個「自動選出好看配色」的工具，而是把幾種互補的方法接起來：

1. 用產品／受眾／任務 brief 先說清楚「讀者要完成什麼、希望留下什麼感受」。
2. 從值得參考的網站量測現有視覺系統，記錄觀察值和推測值；不要憑印象抄一組色票。
3. 用 semantic token 把網站共同規則和主題 accent 分開，讓 AWS／IP 可以共用一種語言，Java 仍有自己的識別色。
4. 探索整體方向時可以比較不同字體、構圖與配色；要研究配色本身時，固定內容、版面和互動，只替換色彩角色。控制變項有助比較，但不保證換 hue／chroma 後仍有同樣感覺或對比。
5. 用實際 render、可及性檢查和小型受眾測試收斂；「好玩、好奇、方便」先當作待驗證假說。

若只選一條後續路線，我會先研究 **Impeccable 的 brief／DESIGN.md 方法 + brand-book 或 Dembrandt 的量測 + Material／Radix 類 semantic roles + Digital.gov／GOV.UK 的測試方法**。UI/UX Pro Max、Taste、Anthropic theme-factory 很適合產生方向或候選，但內建資料庫／預設主題較容易把「不想要的平均感」重新帶回來。

## 研究方式與證據標記

### 三輪搜尋

- **第一輪：廣搜。** 以 GitHub、官方 Skills repo、`theme factory`、`design audit`、`extract design system`、`brand tokens`、`avoid AI design`、`visual design direction` 等關鍵字，找出可用的 Agent Skill、作者工作流和非 Skill 方法。
- **第二輪：縮窄。** 逐一讀候選的 README、`SKILL.md`、reference、腳本說明或原始碼，確認它實際會問什麼、產出什麼，以及是否真的能處理 palette／受眾／一致性；不以榜單摘要代替原文。
- **第三輪：交叉查核。** 補查官方設計系統、token 標準、使用者研究和視覺偏好測試，將「作者宣稱的 anti-slop／好看」與可以檢查的規則分開。

### 標記

- **已讀**：本次讀過連結指向的 README／SKILL／reference 或官方方法頁。
- **未操作**：沒有安裝、沒有執行、沒有拿本專案的 HTML 實測。
- **作者宣稱**：作者自己對效果、反 AI 平均風格或覆蓋範圍的描述；不等於本專案已驗證。
- **官方方法**：不是 Agent Skill，因此沒有 GitHub stars；可借用原則和測試方法，但不代表能直接產生 HTML。
- **星數**：GitHub repository stars，2026-10-04 查詢；會變動，且一個 repository 可能包含多個 Skill。

## 第一梯隊：直接解決「方向、配色、網站一致性」

### 1. Impeccable（pbakaus）

來源：[repository](https://github.com/pbakaus/impeccable)／[SKILL.md](https://github.com/pbakaus/impeccable/blob/main/.agents/skills/impeccable/SKILL.md)／[init](https://raw.githubusercontent.com/pbakaus/impeccable/main/.agents/skills/impeccable/reference/init.md)／[document](https://raw.githubusercontent.com/pbakaus/impeccable/main/.agents/skills/impeccable/reference/document.md)／[colorize](https://raw.githubusercontent.com/pbakaus/impeccable/main/.agents/skills/impeccable/reference/colorize.md)／[new-work](https://raw.githubusercontent.com/pbakaus/impeccable/main/.agents/skills/impeccable/reference/new-work.md)。

- **快照**：75,837 stars、4,537 forks；Apache-2.0。官方 `SKILL.md` metadata 讀到 v4.5.0；這是 repository 快照，不是本專案驗證。
- **實際能力**：`init` 把 primary user、情境、任務、定位、限制、證據寫入 `PRODUCT.md`；`document` 從現有 code 和 computed style 形成 `DESIGN.md`；`extract` 抽出重複的 token／component；`colorize` 會從角色、語意、對比、使用情境和情緒溫度安排顏色；`bolder` 只在既有設計世界內加強。
- **對受眾感受的處理**：`init` 明確不先問 mood、顏色或字體，先問產品真實情境；`document` 之後才用 Creative North Star、mood／anti-reference、顏色描述、component philosophy 問視覺語言。`critique` 會把語氣問題連到具體發現，而不是只問「喜不喜歡」。這很適合把「方便、好玩、好奇」變成可討論的設計假說。
- **參考轉換與一致性**：`document`、`extract`、`DESIGN.md` 和 `.impeccable/design.json` 能保留網站層 token、元件規則、動態和敘事；可從參考或既有畫面抽出結構，再用 `colorize` 重新選 hue／chroma／tone，而不是直接沿用參考值。`new-work` 要求說明受眾熟悉的視覺世界，適合做「同感覺、不同 palette」。
- **Claude／Codex**：官方列出 Claude Code、Codex CLI、Cursor、Gemini CLI、GitHub Copilot 等適配；本次只讀文件，未在 Codex 或 Claude 執行。
- **成本與限制**：命令需要其 launcher／瀏覽器迭代，初次可能下載自包含 binary；本次不安裝。它很強但偏向完整前端專案，對單檔離線教材仍需把 `DESIGN.md` 的角色和決策翻成原生 CSS token。`colorize` 的作者規則是工作流，不是受眾情緒因果證明。
- **評估**：**最值得先深入**。它最接近「先理解受眾與既有真實，再決定視覺世界」，也最能避免把「換一個綠色」誤當成設計方向。

### 2. UI/UX Pro Max

來源：[repository／README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)／[主 Skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill/blob/main/.claude/skills/ui-ux-pro-max/SKILL.md)／[brand Skill](https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/brand/SKILL.md)／[palette reference](https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/brand/references/color-palette-management.md)／[design system](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill/blob/main/.claude/skills/design-system/SKILL.md)。

- **快照**：132,915 stars、14,081 forks；MIT。
- **實際能力**：README／Skill 聲稱涵蓋 79 styles（50 active）、192 product palettes／reasoning profiles、74 font pairings、119 UX guidelines、chart、motion 和多種技術 stack；先由產品類型和需求產生 design system，再做 accessibility、interaction、hierarchy、typography、color 等檢查。Brand Skill 會處理 brand voice、visual identity、palette、token 和一致性；palette reference 提到從圖片抽色、映射到品牌色、WCAG 檢查。
- **對受眾感受的處理**：從產品類型和需求推導 mood／style，能把「可信、活潑、技術感」變成樣式候選；沒有實際訪談、視覺偏好測試或學習成效測試，不能把資料庫推薦當受眾證據。
- **參考轉換與一致性**：有 palette／brand context 和 semantic token 層，可維持一個產品的共同系統；比較像「根據 brief 選一套既有方案」，而不是分析指定網站再換一個同感覺 palette。
- **Claude／Codex**：Skill 以 `.claude` 結構提供，README 另列 Codex CLI 等使用方式；本次未安裝。Python 部分以標準函式庫搜尋資料，不需第三方套件，但資料量和規則本身很大。
- **成本與限制**：192 組 palette／79 種 style 是強大的起點，也可能把平均化的分類答案帶進來；palette 管理裡的比例和範例色是 heuristic／hardcoded sample，不能證明某色一定帶來某種感覺。偏 React／Tailwind／Motion，不是單檔離線 HTML 的直接產出器。
- **評估**：**可作候選生成與 anti-pattern checklist，不能單獨承擔受眾研究或參考抽取。**

### 3. Taste Skill

來源：[repository](https://github.com/Leonxlnx/taste-skill)／[design-taste-frontend Skill](https://raw.githubusercontent.com/Leonxlnx/taste-skill/main/skills/taste-skill/SKILL.md)。

- **快照**：92,468 stars、6,272 forks；MIT。
- **實際能力**：從 page kind、vibe words、reference signals、audience、brand assets、constraints 形成一行 `Design Read`；用 VARIANCE、MOTION、DENSITY 三個 dial 控制結果，並要求一個 project 維持一套 palette、最多一個 accent，明確避開紫藍漸層、居中的 mesh、三張卡片、玻璃 everywhere、Inter＋slate 等常見 AI 預設。
- **對受眾感受的處理**：會要求或讀取受眾與 vibe，只有方向偏離時才問一個澄清問題；這比沒有 brief 的生成好，但仍是 agent 推斷，沒有實際受眾量測。
- **參考轉換與一致性**：認得 Material、Carbon、Primer、GOV.UK、Radix 等系統並主張一個 project 一套 system；能使用 reference signal，但沒有像 Dembrandt 那樣從 computed style 做可追蹤 extraction，也沒有「保留情緒關係、換 hue」的測試流程。
- **Claude／Codex**：Skill 是 Markdown，可移植；repository 主要示範 React／Tailwind／Motion／Next，另有較偏 Codex 的變體；本次未操作。
- **成本與限制**：硬性禁用清單能降低 AI 平均風格，卻可能造成另一種固定偏好；不適合直接當離線 HTML 產出器，也不能取代 audience test。
- **評估**：**適合作為反平均風格的設計 brief 及 dial 語言，排在 Impeccable 之後。**

### 4. Anthropic `theme-factory`

來源：[官方 `anthropics/skills` repository](https://github.com/anthropics/skills)／[theme-factory/SKILL.md](https://github.com/anthropics/skills/blob/main/skills/theme-factory/SKILL.md)。

- **快照**：repository 179,588 stars、21,236 forks；repository 內含多個 Skill，沒有單獨的 theme-factory stars。
- **實際能力**：提供 10 個預設主題（例如 Ocean Depths、Forest Canopy、Arctic Frost、Tech Innovation），先展示 theme showcase，再讓使用者選擇或建立 custom theme，然後把顏色／字體套用到簡報、文件或其他 artifact。
- **對受眾感受的處理**：讓人先看視覺候選再選，適合快速收斂 mood；沒有問受眾任務、沒有從真實網站抽取，也沒有偏好測試或教學互動語意。
- **參考轉換與一致性**：跨 artifact 套用同一主題的做法可借用到網站；10 組 preset 可能太固定，若要「同樣感覺但不同 palette」應把它當 style tile 起點，不直接採用。
- **Claude／Codex**：Anthropic 官方 Skill 格式，Codex 可讀其 Markdown 方法但不是本專案已驗證的 Codex plugin；本次未安裝。部分工作流需要 theme showcase／字體或文件工具。
- **成本與限制**：preset 是 hardcoded palette，容易平庸或與其他內容撞色；是主題套用器，不是受眾研究或設計系統抽取器。
- **評估**：**可借用「先比較 style tiles、再決定」的互動方式，低於 Impeccable／brand-book。**

### 5. Anthropic `frontend-design`

來源：[官方 repository](https://github.com/anthropics/skills)／[frontend-design/SKILL.md](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md)。

- **快照**：同上，179,588 stars 是整個 `anthropics/skills` repository 的數字。
- **實際能力**：要求先思考 aesthetic、主題、受眾和內容，再做有鮮明方向的 frontend；反對 generic AI defaults，要求 typography、color、composition、motion 與題材建立關係。
- **對受眾感受的處理**：能把 audience／topic 和視覺方向綁在一起，適合初始化教材；沒有獨立的受眾研究、情緒量表或 reference measurement。
- **參考轉換與一致性**：可引導同一網站維持完整 design language，然而不提供 `brand.json`／token extraction；對既有 IPv4 HTML 的延續需另加本專案規則。
- **Claude／Codex**：官方 Anthropic Skill，可作一般 Markdown 工作流參考；本次未在任何 agent 執行。
- **成本與限制**：容易產出漂亮但一次性的頁面；若不加離線、固定／變動語意、鍵盤和可及性約束，不能直接滿足互動教材需求。
- **評估**：**可作 anti-generic 的創意 brief，不應單獨決定 color system。**

### 6. `ordinarynerds/brand-book`

來源：[repository](https://github.com/ordinarynerds/brand-book)／[HTML Skill](https://github.com/ordinarynerds/brand-book/blob/main/brand-book-html/SKILL.md)／[intake](https://github.com/ordinarynerds/brand-book/blob/main/brand-book-html/references/intake.md)／[brand JSON](https://github.com/ordinarynerds/brand-book/blob/main/brand-book-html/references/brand-json.md)／[design system](https://github.com/ordinarynerds/brand-book/blob/main/brand-book-html/references/design-system.md)。

- **快照**：3 stars、0 forks；MIT。星數低，但方法特殊，保留研究。
- **實際能力**：intake 可用 browser 量測 live site，按頻率整理 computed colors、fonts、logo、image 和 voice；也可接 structured brief。它要求把觀察值、推測值和 confidence 分開，最後用單一 `brand.json` 作 source of truth，產生 self-contained brand book、tokens.css／JSON 和 companion skill。
- **對受眾感受的處理**：會問未決問題並附建議；用 physical mood word（如 mineral、bookish、gallery、nocturnal、signage）代替空泛的「現代感」，也提醒避開 tired palette cliché。它沒有正式的受眾偏好研究，但比直接問「想要什麼顏色」更容易形成可討論的方向。
- **參考轉換與一致性**：七個語意角色（background／surface／border／muted／foreground／accent 等）含 hex、OKLCH、名稱、用途和 provenance；非常適合網站層／主題層 token 與跨教材一致性。它建議一個 view 只出現一次主要 accent，比例只是 heuristic。
- **Claude／Codex**：以 agent skill／self-contained HTML 思路撰寫，Markdown 可移植；未宣稱本專案的 Codex／Claude 已適配，本次未操作。
- **成本與限制**：低星、偏品牌書，不是互動教材 builder；量測 live site 需要 browser；要求 sign-off 的工作流比目前單檔 HTML 生成重。抽出的色碼只是參考的觀察，不是本網站方案；需重新映射角色並檢驗。這裡研究的是視覺設計決策，hue 本身不是品牌獨占，也不把這段流程當法務清單。
- **評估**：**最適合作為本專案日後的 `DESIGN.md`／theme provenance 參考，尤其能避免「AI 憑空猜綠色」。**

### 7. `arvindrk/extract-design-system`

來源：[repository](https://github.com/arvindrk/extract-design-system)／[Skill](https://github.com/arvindrk/extract-design-system/blob/main/skills/extract-design-system/SKILL.md)。

- **快照**：232 stars、29 forks；MIT。
- **實際能力**：對公開 URL 用 Playwright render，再輸出 raw／normalized JSON、colors、fonts、spacing、radius、shadows 和 W3C-compatible `tokens.json`／CSS；先問 extraction-only 或 starter files，也明確提醒動態網站可能只取到部分狀態。
- **對受眾感受的處理**：沒有情緒訪談；它的價值在把「這個網站到底用了什麼」從主觀印象變成可檢查的資料，之後仍要由設計流程解讀 atmosphere 和 density。
- **參考轉換與一致性**：最直接支援「參考權威網站的結構但自己換 palette」：先抽 token／量測，再以本網站 role token 重新命名和生成，不能把輸出當成新網站的權威答案。可將多個參考的共同結構整理成網站層，差異留在 topic layer。
- **Claude／Codex**：`SKILL.md` 可作 generic agent workflow；命令實作需要 Node／Playwright，不是本專案可直接嵌進離線 HTML 的 runtime。本次未安裝，沒有對任何網站執行。
- **成本與限制**：通常需要 `npx playwright install chromium` 和 CLI；Canvas／WebGL、登入後頁面、hydration、hover/focus 等可能遺漏。抽出的色碼只是參考的觀察，不是本網站方案；需重新映射角色並檢驗。
- **評估**：**適合做 reference measurement，不能取代視覺方向或受眾驗證。**

### 8. `dembrandt`

來源：[repository／README](https://github.com/dembrandt/dembrandt)／[限制與使用方式](https://github.com/dembrandt/dembrandt/blob/main/docs/usage.md)。

- **快照**：3,598 stars、318 forks；MIT。GitHub API 2026-10-04 讀取成功。
- **實際能力**：用 Playwright 和 computed styles 抽取 semantic colors、palette、CSS variables、typography、spacing、borders、shadows、motion、components、breakpoints、icons、frameworks；可輸出 W3C DTCG、`DESIGN.md`、Tailwind／shadcn、HTML report、screenshots、real DOM WCAG pairs，並以 crawl、多頁、mobile、dark mode、compare 做跨頁和 drift 分析。
- **對受眾感受的處理**：不問 audience emotion；它提供「observed system」，情緒／品牌解讀要由 Impeccable 或人工完成。README 的「benchmarking」「AI agent design system builds」是作者宣稱，尚未在本專案驗證。
- **參考轉換與一致性**：多頁 confidence、token baseline 和 drift gate 很適合分析網站共同規則；抽出的色碼只是參考的觀察，不是本網站方案；取得參考後需重新映射 `site.*`／`topic.*` 角色並檢驗。
- **Claude／Codex**：README 明列 Claude Code、Cursor、Windsurf、MCP-compatible client；Codex 若接 MCP 理論上可用，但本專案未設定或操作。
- **成本與限制**：需要 Node 18+、Chromium；MCP 用法展示 `npx`，本次禁止安裝；dark mode、hover/focus、動態內容、Canvas/WebGL 有限制；自動化分析應只對允許的網站執行。
- **評估**：**若日後要做「分析 3–5 個參考站，再建立自己的 token」，它比一般 palette generator 更值得投資。**

### 9. `sonyabirch/skills` 的 `visual-design-direction`

來源：[repository／Skill](https://github.com/sonyabirch/skills/tree/main/visual-design-direction)／[SKILL.md](https://github.com/sonyabirch/skills/blob/main/visual-design-direction/SKILL.md)。

- **快照**：0 stars、0 forks；Apache-2.0。低星但方法明確，保留。
- **實際能力**：把 art direction 當作可辯護的決策：先列 constraints，再只推導 1–2 個 material questions；逆向檢查既有 system；區分 code-extracted value 和 render-only impression；用 role-based neutral ramp、單一 accent、style tile 和實際 UI 驗證。
- **對受眾感受的處理**：不把 moodboard 或「年輕／現代」當結論；要求把感受翻成可以看到、可以辯護、可以測的視覺規則。這直接適合把「好玩、引起好奇心」寫成候選而非事實。
- **參考轉換與一致性**：很適合先找參考的視覺關係，再自己做 style tile；沒有自動抽色、瀏覽器量測或 token export，要搭配 Dembrandt／extract-design-system。
- **Claude／Codex**：一般 Markdown Skill，未宣稱特定 agent；本次未操作。
- **成本與限制**：低成本、低自動化；品質取決於執行者是否真的拿 render 和內容驗證，而不是只寫一段 art direction prose。
- **評估**：**是值得保留的低星特殊方法，適合作為本專案的設計決策審查框架。**

### 10. `yappologistic/frontend-GOD`

來源：[repository](https://github.com/yappologistic/frontend-GOD)／[frontend design director Skill](https://github.com/yappologistic/frontend-GOD/blob/main/skills/frontend-design-director/SKILL.md)。

- **快照**：5 stars、1 fork。
- **實際能力**：提供 Build／Redesign／Review／Design System 模式；brief 包含 audience／job、content、constraints、emotional target、visual direction、signature motif；使用 semantic token 層，並列出 Codex browser／screenshot QA 的桌面與手機 viewport。
- **對受眾感受的處理**：把 emotional target 變成輸入欄位，這比只說「做得漂亮」可操作；仍未看到實際受眾測試或 reference extraction。
- **參考轉換與一致性**：有 token audit 和 design audit 腳本，適合作為網站共同語言與分類主題的橋樑；palette 仍需自行決策。
- **Claude／Codex**：明顯偏 Codex workflow，對本專案可能比只寫 React 的 Skill 近；本次未安裝或執行。
- **成本與限制**：低星、工具鏈和流程依賴未完整驗證；若搬到單檔 HTML，要保留 brief／token／viewport QA 的方法，不必照搬腳本。
- **評估**：**適合研究如何把 audience/emotion 寫進可重用的 brief，列為 Codex 方向候選。**

## 第二梯隊：反平均、視覺 QA 與局部技術

### 11. `avoid-ai-design`

來源：[repository／SKILL.md](https://github.com/funboy322/avoid-ai-design/blob/main/SKILL.md)。

- **快照**：92 stars、5 forks；MIT。
- **實際能力**：可對 CSS／HTML／React／Tailwind／shadcn 做 detection-only 或 rewrite；render 可用時看實際畫面，否則把 code-only 判讀標為較低 confidence；會找 purple gradient、重複 cards、generic icons、玻璃和模板化 hero 等 AI 平均樣式。
- **對受眾感受的處理**：不訪談、不測 mood；只提醒先確定一個 intentional direction，再移除 generic patterns。
- **參考轉換與一致性**：不能抽參考 palette，沒有 theme token pipeline；可在生成後檢查每份教材是否偏離網站共同規則或落回平均模板。
- **Claude／Codex**：作者宣稱可用於 Codex、Claude、Cursor、Copilot 等；本次未操作。
- **成本與限制**：是 lint／rewrite，不是完整設計方法；禁止清單可能製造另一種公式化外觀；rewrite 前需 review，避免改掉教學資訊結構。
- **評估**：**值得做最後一關 anti-slop check，不值得作為唯一視覺方向 Skill。**

### 12. `EnchStyle/ui-ux-audit-skill`

來源：[repository](https://github.com/EnchStyle/ui-ux-audit-skill)／[audit Skill](https://github.com/EnchStyle/ui-ux-audit-skill/blob/main/ui-ux-audit/SKILL.md)／[visual excellence](https://github.com/EnchStyle/ui-ux-audit-skill/blob/main/ui-ux-audit/references/visual-excellence.md)／[color／states](https://github.com/EnchStyle/ui-ux-audit-skill/blob/main/ui-ux-audit/references/color-states-forms.md)。

- **快照**：5 stars、0 forks；MIT。
- **實際能力**：在 360／768／1280 等 viewport 做 screenshot、flow、keyboard、edge-case 和 16 類檢查；視覺規則包含一個主意念、tinted neutral、單一 accent、category-specific direction、responsive、contrast 和 state。
- **對受眾感受的處理**：用 render quality 和任務完成審查，不問「觀眾覺得什麼」；適合驗證方便、清楚和可操作，不能單獨證明好玩或好奇。
- **參考轉換與一致性**：能檢查是否過度使用 gradient、三卡片等模板，但不抽 reference tokens，也不產生新 palette。
- **Claude／Codex**：一般 Skill；完整流程依賴 Python Playwright／Chromium，本次未安裝。
- **成本與限制**：瀏覽器安裝和截圖成本中等；score 是審查工具的判斷，不是學習成效或審美真理。
- **評估**：**適合作為交付前的實際畫面 QA。**

### 13. Emil Kowalski 的 design engineering Skill

來源：[repository](https://github.com/emilkowalski/skills)／[emil-design-eng/SKILL.md](https://github.com/emilkowalski/skills/blob/main/skills/emil-design-eng/SKILL.md)。

- **快照**：43,077 stars、2,440 forks；MIT。
- **實際能力**：把 design taste 建立在研究優秀作品和 reverse engineering；對動畫先問是否必要、它傳達什麼、duration／easing 是否服務改變；強調 invisible details、accessibility 和 performance。
- **對受眾感受的處理**：能幫助把「好玩／好奇」轉成 purposeful reveal、focus、feedback，不會直接問受眾或選 palette。
- **參考轉換與一致性**：沒有 palette extraction；對跨教材一致性的貢獻是 motion、micro-interaction、focus 和細節品質，且仍需套在共同 token 上。
- **Claude／Codex**：Skill 內容可移植；示例偏 React／Motion，未用本專案單檔 HTML 驗證。
- **成本與限制**：只適合 motion／craft 子問題；若用來「加更多動畫」會背離其原則。
- **評估**：**作為互動教材的動態呈現方法參考，而不是色彩 Skill。**

### 14. `tomwangowa/agent-skills` 的 `ui-design-analyzer`

來源：[repository／Skill](https://github.com/tomwangowa/agent-skills/blob/main/ui-design-analyzer/SKILL.md)。

- **快照**：2 stars、0 forks。
- **實際能力**：對 screenshot 做 score，檢查 usability、color scheme、accessibility、UX 和 platform／brand context；要求提供 audience demographics、brand guidelines 和比較背景。
- **對受眾感受的處理**：會要求 audience context，但輸出是專家式 review，不是實際訪談或 preference test。
- **參考轉換與一致性**：可比較「實作畫面／目標設計」並指出差異，不能抽出 token 或自動生成另組 palette。
- **Claude／Codex**：通用 Markdown Skill；本次未操作。
- **成本與限制**：高度依賴 screenshot 品質和 reviewer 判斷；低星、沒有 browser／DOM 的客觀量測。
- **評估**：**保留作低成本第二意見，不列為主流程。**

### 15. `netresearch/netresearch-branding-skill`

來源：[repository](https://github.com/netresearch/netresearch-branding-skill)。

- **快照**：4 stars、0 forks；未標準化 license（repository metadata 顯示 NOASSERTION）。
- **實際能力**：以真實公司品牌規範示範 colors、typography、web components、WCAG 和使用禁忌如何寫成 agent 可遵循的 branding context。
- **對受眾感受的處理**：它把已決定的品牌規則交給 agent 執行，沒有替新專案研究 audience emotion。
- **參考轉換與一致性**：最有用的是格式：把網站共同規則、可用色、字體、元件和 WCAG 變成單一品牌／設計 context。若抽取其中的色彩，色碼只是參考的觀察，不是本網站方案；需重新映射角色並檢驗。
- **Claude／Codex**：一般 Skill／repository，可閱讀但未宣稱本專案適配；本次未操作。
- **成本與限制**：範例高度 company-specific；repository metadata 的 license 是 `NOASSERTION`，實際品牌內容與依賴未在本次操作中確認。若抽取其中的色彩，色碼只是參考的觀察，不是本網站方案；需重新映射角色並檢驗。
- **評估**：**適合參考 AGENTS／DESIGN context 的寫法，不是 palette 生成器。**

### 16. `cuellarfr/design-skills` 的 UX research／journey mapping

來源：[repository](https://github.com/cuellarfr/design-skills)／[UX research](https://github.com/cuellarfr/design-skills/tree/main/skills/ux-research)／[journey mapping](https://github.com/cuellarfr/design-skills/tree/main/skills/journey-mapping)。

- **快照**：93 stars、7 forks；MIT。
- **實際能力**：把研究分為 generative、descriptive、evaluative、causal；要求觀察任務而非只問喜好；原型測試建議每輪 3–5 人，訪談 5–8 人，並將 Pattern→Insight→Recommendation 分開。Journey map 記錄 goals／thoughts／feelings、emotional curve、moments of truth。
- **對受眾感受的處理**：這是本候選中最直接回答「如何詢問或分析受眾感受」的方法；可問「哪裡覺得迷路／想繼續探索」，並觀察任務，而不是問「你喜歡這個綠色嗎？」。
- **參考轉換與一致性**：不產生 palette，也不抽網站 token；可用來驗證不同 theme 是否影響理解、預測、轉用和完成任務。
- **Claude／Codex**：一般 Skill，未在本專案執行。
- **成本與限制**：需要真實招募和測試，不能用 stars 或 agent 自評替代；3–5 人只適合發現問題，不足以宣稱普遍偏好。
- **評估**：**後續若真的要決定「好玩／好奇／方便」是否成立，這比再找一個 palette generator 重要。**

### 17. `Kappaemme-git/codex-design-audit-skill`

來源：[repository](https://github.com/Kappaemme-git/codex-design-audit-skill)。

- **快照**：47 stars、3 forks。
- **實際能力**：對 URL、local frontend 或 screenshot 做 UX/UI、responsive、visual hierarchy、contrast、console、interaction audit，支援 preset 和 before/after score。
- **對受眾感受的處理**：以專家審查與 score 為主，沒有 audience interview 或 reference extraction。
- **參考轉換與一致性**：可在建立候選 palette 後作差異前後檢查，不能決定何種 visual direction。
- **Claude／Codex**：名稱和工作流偏 Codex；本次未安裝或執行。需先讀完整安裝與權限要求。
- **成本與限制**：audit 分數的可重現性和本專案離線 HTML 適配尚未驗證；只列為候選，不作現階段依賴。
- **評估**：**若未來需要 Codex 內的審查入口，可和 EnchStyle 比較；現階段證據不足。**

## 第三梯隊：非 Skill 的權威方法與設計系統

這些沒有 stars，但它們補上 Skill 最常缺的部分：角色語意、可及性、視覺偏好研究和使用者任務。它們不是安裝候選，而是後續流程的規則／證據來源。

### 18. Material 3 theming／Material Color Utilities

來源：[Material 3 theming codelab](https://developer.android.com/codelabs/m3-design-theming?hl=en)／[dynamic color scheme](https://github.com/material-foundation/material-color-utilities/blob/main/concepts/dynamic_color_scheme.md)／[Material Web color roles](https://github.com/material-components/material-web/blob/main/docs/theming/color.md)。

- **方法**：以 primary、on-primary、container、surface、outline 等 role token 組成 scheme；HCT 把 source color 分成 hue、chroma、tone，再將 tonal palette 映射到 roles；可將 accessibility 當 hard constraint、偏好當 soft constraint。
- **對本專案的用處**：做「相同 role 結構、不同主題 accent」的候選生成；文字、surface、focus、error 和 diagram 語意不會因換色而混淆。
- **受眾感受與限制**：沒有告訴我們哪種色相必然好玩；HCT library 未安裝、未執行。Material 的元件密度和動態配色不必整套搬到單檔 HTML。
- **狀態**：**官方方法，已讀、未操作。**

### 19. IBM Carbon color system

來源：[Carbon designing overview](https://www.carbondesignsystem.com/getting-started/designing/overview)／[color token overview](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview)。

- **方法**：token 表示 role、theme 決定 value；中性灰建立 layer；hover、active、selected、focus、disabled 分開，不以一個 brand hex 解決所有狀態。
- **對本專案的用處**：網站層保留中性背景／文字／邊框／focus，AWS/IP 和 Java 只換 topic accent；可把固定、變動、推導結果用語意 token 和非顏色標記一起表達。
- **限制**：Carbon 服務企業產品；本次只借用 role／state 的分層方法，不把其具體值當成本網站方案；沒有 audience emotion test。
- **狀態**：**官方方法，已讀、未操作。**

### 20. Adobe Spectrum color system

來源：[color system](https://spectrum.adobe.com/page/color-system/)／[color fundamentals](https://spectrum.adobe.com/page/color-fundamentals/)／[design tokens](https://spectrum.adobe.com/foundations/design-data/design-tokens)。

- **方法**：從視覺感知、inclusive design、accessibility 和 contrast target 建立色階；token 分 global、alias、component-specific，讓設計決定可重用。
- **對本專案的用處**：把 emotion、site identity、component state 和教材 diagram 語意分層；日後可讓 CSS／HTML／文件共用同一組 token data。
- **限制**：完整 Spectrum 遠大於單檔教材；其色彩語意是系統方法，不是對本專案受眾的直接結論。
- **狀態**：**官方方法，已讀、未操作。**

### 21. Radix Colors

來源：[理解 12 階 scale](https://www.radix-ui.com/colors/docs/palette-composition/understanding-the-scale)／[composing a palette](https://www.radix-ui.com/colors/docs/palette-composition/composing-a-palette)。

- **方法**：12 階 scale 按背景、互動元件、邊框、solid、accessible text 分工，另有 alpha、dark 和 functional variants；accent 是互動色，gray 可帶 hue。
- **對本專案的用處**：可在原生 CSS 中做輕量 role map，維持相同層級和對比，只換 topic accent；比把 `#xxx` 散落在每個 component 更容易維護。
- **限制**：它提供 palette architecture，不提供 audience mood 或 reference extraction；本次未使用其 CSS／套件。
- **狀態**：**官方 OSS 方法，已讀、未操作。**

### 22. W3C Design Tokens Community Group

來源：[Format module 2025.10](https://www.designtokens.org/tr/2025.10/format/)／[Color module 2025.10](https://www.designtokens.org/tr/2025.10/color/)。

- **方法**：2025.10 Format 和 Color 是 2025-10-28 發布的 Final Community Group Report，標示為 stable、intended for implementation；token 有 name／value，可有 type、description、alias／reference 和 group，color module 讓色彩資料可被設計、轉換和文件工具共享。它們仍是 Community Group Reports，不是 W3C Standard。
- **對本專案的用處**：未來可把 `site.*`、`topic.*`、`state.*` 存成一份 JSON，再產生單檔 HTML 的 CSS；也能保留 source／provenance／contrast 結果。
- **限制**：它們不是 W3C Standard；目前只採資料模型概念，不直接導入規格或第三方 parser。
- **狀態**：**官方 Final Community Group Report，stable／intended for implementation；已讀、未操作。**

### 23. Google Labs `DESIGN.md` format

來源：[repository](https://github.com/google-labs-code/design.md)／[format specification](https://raw.githubusercontent.com/google-labs-code/design.md/main/docs/spec.md)。

- **快照**：28,235 stars、2,285 forks；main；Apache-2.0；repository metadata 快照為 2026-10-04。這是格式 repository，不是 Skill 品質分數。
- **方法**：以 YAML frontmatter 保存 machine-readable design tokens，再用人類可讀文字說明原因、原則和上下文；目標是讓設計決策跨 agent／session 持續，而不只存在某次對話或某個畫面。
- **對本專案的用處**：可和 Impeccable 的 `DESIGN.md`／`PRODUCT.md` 思路並用，記錄 `site.*`／`topic.*` token、受眾假說、參考觀察、設計理由和 contrast 結果，讓未來用 Claude、Codex 或其他 agent 時有可讀的共同上下文。
- **限制**：格式目前是 alpha，linter 只檢查文件裡已定義的 pair，不能代替實際頁面的完整 accessibility／responsive／interaction QA；它也不會自動讓 Codex 或 Claude 載入，需由工作流明確讀取。官方 spec 本次只閱讀，未執行 CLI。
- **評估**：**值得作為本專案日後的跨 agent 設計決策載體，但不是 palette generator、受眾研究工具或瀏覽器驗證器。**

### 24. Digital.gov visual preference testing

來源：[Visual preference testing](https://digital.gov/guides/research-collaboration/testing/visual-preference)。

- **方法**：用多個視覺候選比較偏好和認知，將測試條件、樣本、問題和解讀分開；適合將同一份教材做 A/B/C style tile。
- **對本專案的用處**：同一內容、同一互動、同一 layout，只換 palette／type／shape 的一個變因；問「哪組最容易理解、最可信、最想繼續探索」，再觀察任務結果。
- **限制**：偏好不是學會，也不是可及性或正確性的替代；需要實際受試者，沒有 agent 自動化工具。
- **狀態**：**官方使用者研究方法，已讀、未操作。**

### 25. GOV.UK user research／usability testing

來源：[start by learning user needs](https://www.gov.uk/service-manual/user-research/start-by-learning-user-needs)／[user research overview](https://www.gov.uk/service-manual/user-research)／[qualitative usability testing](https://www.gov.uk/guidance/usability-testing-qualitative-studies)。

- **方法**：從使用者的需要、環境和任務開始；以觀察、訪談和 task-based qualitative testing 發現問題，不把設計者對受眾的猜測當事實。
- **對本專案的用處**：把「好玩／好奇」轉為可觀察行為：受試者是否先預測、是否主動改第二個條件、是否能說明圖形與結果的因果；把「方便」轉為找到按鈕、完成任務、用鍵盤操作等。
- **限制**：不是 palette 生成器；樣本和任務必須依本專案讀者重新設計。
- **狀態**：**官方研究方法，已讀、未操作。**

### 26. Google Material 3 Expressive 研究

來源：[Google Design 的 Expressive Material 研究](https://design.google/library/expressive-material-design-google-research)／[Google first-impression research summary](https://research.google/blog/users-love-simple-and-familiar-designs-why-websites-need-to-make-a-great-first-impression/)。

- **方法**：Google 描述以數十項研究、數百個設計和大量參與者評估 expressive attributes，如 playful、energetic、creative、friendly、modernity、subculture；另引用早期研究指出視覺複雜度和 prototypicality 會影響很快的第一印象。
- **對本專案的用處**：提醒我們把「好玩／好奇」寫成可比較的 adjective pairs 和 scene，而不是靠一個鮮豔 accent；可以先用同一教材做兩三個 style tile，再看受眾對 playful／familiar／novel／credible 的感受和任務完成。
- **限制**：Google 自己的研究摘要和產品情境，不是本專案受眾、不是互動教材學習效果的證明；不能把「Google 說 playful」直接套用。
- **狀態**：**官方研究摘要，已讀、未操作；部分數字和結論是來源自述。**

## 這些候選如何組成一條可執行的路線

### 建議的分工

| 問題 | 首選參考 | 交付物 | 不要交給它的事 |
|---|---|---|---|
| 讀者、任務、限制是什麼？ | Impeccable `init`、GOV.UK、UX research | `PRODUCT.md` 或 brief 欄位；可觀察的受眾假說 | 直接選色 |
| 現有網站／參考站實際用了什麼？ | Dembrandt、extract-design-system、brand-book intake | observed tokens、screenshot、provenance、confidence | 判定受眾一定會喜歡 |
| 如何把情緒變成視覺方向？ | Impeccable `new-work`／`document`、visual-design-direction、Taste | 2–3 個 style tiles、North Star、anti-reference、決策理由 | 用 mood 文字代替 QA |
| 如何保持 AWS／IP／Java 一致又有差異？ | Carbon、Material、Spectrum、Radix、W3C DTCG | `site.*`／`topic.*`／`state.*` token model | 把參考色直接當成 topic token |
| 如何避免 AI 平均樣式？ | Taste、frontend-design、avoid-ai-design | anti-pattern review、明確的 visual POV | 只靠禁用清單產生個性 |
| 如何知道是否真的可用？ | EnchStyle、Tom analyzer、Codex audit | desktop／mobile／keyboard／contrast／edge-case QA | 用分數代替使用者研究 |
| 受眾真的感到方便／好玩／好奇嗎？ | Digital.gov、GOV.UK、cuellarfr UX research | A/B/C preference + task observation + Pattern→Insight→Recommendation | 問一句「你喜不喜歡綠色」就結案 |

### 建議的「同感覺、不同 palette」操作

1. 先寫 audience／job／context／constraints；暫時不要從顏色開始。
2. 選 3–5 個可信參考，量測其 first viewport、computed colors、font、spacing、density、motion，標明 **observed** 和 **inferred**。
3. 從量測結果抽「關係」：對比範圍、accent 劑量、留白、層次、動態節奏。抽出的色碼只是參考的觀察，不是本網站方案；需重新映射角色並檢驗，hue 本身不是品牌獨占。
4. 固定教材內容、layout、元件尺寸、互動和 state；先只換 `topic.accent` 的 hue／chroma／tone。`site.text`、`site.surface`、`state.*`、`focus`、`diagram-fixed/variable/derived` 維持角色不變。
5. 做三組 style tiles，讓受眾比較 calm–energetic、familiar–novel、serious–playful、clinical–warm、dull–curious 等維度，同時讓他們完成一個教材任務。
6. 先檢查 WCAG 對比、非顏色線索、keyboard、手機、reduced motion、灰階和離線載入，再解讀喜好。
7. 將結果保存成 palette／token、來源、日期、測試對象和限制；沒有測試的情緒詞一律標成 hypothesis。

## 建議暫時不投入的類型

- **純 component／CSS／chart library**：能加元件，卻沒有 audience brief、reference extraction 或 anti-average 方法；對本問題不是研究候選。
- **只列 preset palette 的網站或榜單**：可做靈感牆，但沒有 provenance、語意 role、對比和受眾驗證；不列為 Skill 候選。
- **只會產生漂亮 screenshot 的 generator**：若不讀內容、不檢查互動和狀態，不能回答互動教材的教學目的。
- **只用 stars 排名**：stars 只表示 repository 的受歡迎程度，不能證明能產出有效教材、適合離線 HTML，或能避免平均風格。

## 成本與待驗證邊界

| 候選層級 | 預估成本 | 本次狀態 |
|---|---:|---|
| 閱讀 brief／token／anti-pattern 方法 | 低 | 已讀；未寫入 Skill 或 AGENTS |
| 由 1–3 個 URL 抽 token／computed style | 中 | 已確認工具能力；未安裝 Node／Playwright、未執行 |
| 產生 2–3 個相同內容的 style tiles | 中 | 尚未製作 |
| 既有 IPv4 HTML 的 desktop／mobile／keyboard／contrast QA | 中 | 尚未完整驗證 |
| 小型受眾 A/B/C 與 task observation | 中 | 尚未招募或測試 |
| 建立網站層／主題層 token pipeline | 中至高 | 尚未實作；先以一份教材驗證重複需求較合理 |

未執行 `npx` 安裝指令，未下載 Playwright／Chromium、任何 Skill 或 MCP。GitHub API 的 repository metadata 批次查詢成功，未因 rate limit 重試；星數請視為 2026-10-04 快照。Dembrandt 的 README 另一次 API metadata 查詢也成功（3,598 stars）。本文件沒有用瀏覽器實際操作候選工具，也沒有對現有 `index.html` 做 acceptance test。

## 來源與判讀原則

作者 Skill 的「反 AI 平均」「award-winning」「好看」等字樣保留為作者宣稱；本文件只把它們當作流程線索，不當作研究結果。官方設計系統能支持 role token、contrast、狀態和一致性；官方使用者研究能支持任務觀察和測試設計；兩者都不能替這個網站的讀者決定最終 palette。最終決策應留下可重現的 token、參考測量、假說、測試條件和未驗證限制。
