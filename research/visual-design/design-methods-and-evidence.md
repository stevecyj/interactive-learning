# 互動教學的視覺設計、配色與受眾感受：方法與證據

調查日期：2026-10-04（Asia/Taipei）。這份文件只做研究記錄，不建立 Skill、不安裝套件、不修改既有教材或共用提示詞。研究問題是：如何讓同一個互動學習網站維持一致的身份，又能讓 AWS／IP／Java 等主題有清楚但不俗套的差異；如何把「方便、好玩、引起好奇心」轉成可檢查的視覺決策。

## 先給結論

最可靠的方向不是先找一組「代表好玩」的顏色，而是建立兩層設計語言：

1. **網站層**固定閱讀與互動的共同規則：文字階層、留白尺度、圓角／邊框、互動狀態、動畫節奏、焦點樣式、圖表語法和離線限制。
2. **主題層**只替換少量語意化 accent：例如網路／雲端一組、Java 一組。主題 accent 可改變氣氛和辨識度，但不能取代 success、error、focus 等功能色，也不能讓每份教材變成完全不同的網站。

設計系統的共同做法是把「使用意圖」和「顏色數值」分開。Carbon 稱為 role-based token，Spectrum 優先 semantic decisions，Material 將 tonal palette 映射到 color roles，Radix 為不同用途安排階梯。這些方法都比在 HTML 中到處散落 hex 值更適合日後換主題。

「目前的綠色可能穩定、護眼」是對現有畫面的感受推測，不能當成已證實的色彩心理結論。原始研究比較支持以下較窄的說法：色相、明度／亮度、飽和度及其交互作用會影響情緒評分或生理反應；不同文化有部分共通也有差異；具體介面情境、背景、文字、動態和任務不能由一個色相單獨推導。

因此，後續若要比較配色本身，應固定 token 意義、內容、版面與互動，再受控地改 hue／chroma／tone 或 OKLCH 的 hue／chroma／lightness，逐一檢查最終對比並比較感受。相同明度參數不保證相同對比或情緒；初期若要探索整體身份，則可以比較多種字體與構圖方向，另行解讀。

## 研究範圍與三輪搜尋

### 第一輪：官方設計系統與可延伸的 token 模型

查閱 Material Web／Material Color Utilities、IBM Carbon、Adobe Spectrum、Radix Colors／Themes、USWDS、Atlassian Design 及 DTCG 2025.10。重點是角色、主題、階梯、狀態、明度和跨產品一致性，而非照搬任何品牌的外觀。

### 第二輪：色彩感受與文化差異的第一手研究

查閱 Valdez & Mehrabian 的情緒模型研究、Wilms & Oberfeld 的控制變因實驗、Adams & Osgood 的 23 文化資料，以及涵蓋多國的色彩—情緒和色彩—氣味研究。這輪用來限定可以說到哪裡，特別避免把流行的「紅色等於某情緒」當作規則。

### 第三輪：配色生成、可及性、品牌邊界與非色彩設計

查閱 Adobe Leonardo、Material HCT、W3C WCAG、AWS／Oracle 官方品牌規範，以及 Atlassian 的 typography、spacing、motion 指南。這輪把「好看的候選」收斂成可生成、可檢查、可在不同主題重用的流程。

## 第一手來源與可借用方法

| 來源 | 直接觀察到的方法 | 對本專案的用處與限制 |
|---|---|---|
| [Material Web：Color](https://github.com/material-components/material-web/blob/main/docs/theming/color.md) | 以 `primary`、`on-primary`、`container`、`surface`、`outline` 等 role token 組成 scheme；配對的 `on-*` token 用於內容對比 | 可用作網站 token 命名和 foreground/background 配對。Material 的整套元件和 HCT 演算法不必導入單檔 HTML |
| [Material Color Utilities：Dynamic Color Scheme](https://github.com/material-foundation/material-color-utilities/blob/main/concepts/dynamic_color_scheme.md) | HCT 將顏色拆成 Hue、Chroma、Tone；由 source color 產生 tonal palettes，再把 tone 指派給 roles；可把 accessibility 視為 hard constraint、偏好視為 soft constraint | 很適合做「同感覺不同色相」的受控候選。它是 Google Material 的方法，不是情緒保證；HCT library 本身本次未安裝 |
| [IBM Carbon：Color](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview) | Token 表示 role，theme 決定 value；以中性灰建立 layering model；另外定義 hover、active、selected、focus、disabled | 可直接借「網站層中性背景＋少量主題 accent＋狀態色」和狀態命名。Carbon 的企業 UI 密度與本專案教學頁不必完全照搬 |
| [Adobe Spectrum：Design tokens](https://spectrum.adobe.com/foundations/design-data/design-tokens) | token 是可重用的設計決定，可描述 color、spacing、typography、motion；強調 semantic、systematic、learnable，並區分 global、alias、component-specific | 支持把主題身份、閱讀節奏、動畫等都放進一致的 token 語言，而不只建立色票。Spectrum 的完整產品系統比本專案需求大 |
| [Adobe Spectrum：Color fundamentals](https://spectrum.adobe.com/page/color-fundamentals/) | 以視覺感知、inclusive design、accessibility 為色彩基礎；以色階／contrast target 來定義 token，而非只命名一個色相 | 可用來提醒「同一色相不同明度不是同一種可用性」。頁面是 Spectrum 的設計指引，不是本專案受眾測試 |
| [Radix Colors](https://www.radix-ui.com/colors)／[Radix Themes：Color](https://www.radix-ui.com/themes/docs/theme/color) | 12 階 scale 按背景、互動元件、邊框、solid、accessible text 分工，另有 alpha、dark、functional variants；`accentColor` 是主互動色，gray 可帶色調 | 適合做原生 CSS 的輕量 role map；可以讓 AWS/IP 共用骨架，只換 accent scale。Radix 的實作保證不能代替本專案自己的離線、手機和教學 QA |
| [USWDS：Using color](https://designsystem.digital.gov/design-tokens/color/overview/)／[Theme tokens](https://designsystem.digital.gov/design-tokens/color/theme-tokens/) | 分開 system、theme、state tokens；theme 用 role-based `base`、`primary`、`secondary`、`accent` 家族；文件提到 60/30/10 作比例思考 | 可借 token 三層和 state 與 brand 分離。60/30/10 是 USWDS 的設計提示，不是普遍定律，也不能直接證明「不平庸」 |
| [Atlassian Design：Color](https://atlassian.design/foundations/color) | 飽和色用於意義、highlight、相似 UI 關聯；中性色承擔大多數背景、文字和形狀；以 color tokens 而非直接選數值 | 支持用大面積中性底和小面積 accent，讓互動焦點有辨識度。文件描述 Atlassian 自己的產品語言，不代表所有教材都應採其色票 |
| [Design Tokens Community Group：Format 2025.10](https://www.designtokens.org/tr/2025.10/format/) | 2025-10-28 發布的 Final Community Group Report；token 至少有 name/value，可有 type、description、alias/reference、group，並供設計、轉換、文件工具共享資料 | 這個版本被標為 stable、intended for implementation，但仍不是 W3C Standard 或 W3C Recommendation。可作未來保存 `site`／`topic`／`state` 的資料格式參考；目前不需要為本專案直接導入 |
| [Adobe Leonardo](https://github.com/adobe/leonardo)／[contrast-colors README](https://github.com/adobe/leonardo/blob/main/packages/contrast-colors/README.md) | 從 target contrast ratio 反向生成 color scale；可調 lightness、contrast、saturation，並支援多種插值色彩空間；把 contrast 放到選色流程前面 | 很適合產生同一 role 結構的多個 palette，再檢查 WCAG；目前只閱讀原始碼／文件，沒有安裝或執行 |
| [W3C WCAG 2.2：Contrast Minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html) | 普通文字至少 4.5:1，大字至少 3:1；對比是 relative luminance 的比值，不能把色相漂亮當成可讀性；不應四捨五入跨過門檻 | 是交付前的硬性檢查。內容文字、按鈕、鍵盤 focus、圖表和圖解需分別檢查，不能只看整體 screenshot |
| [W3C WCAG 2.2：Use of Color](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html)／[Non-text Contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html) | 顏色不能是辨識資訊或操作的唯一方式；非文字 UI component 和圖形要有足夠對比，並用文字、形狀、紋理、位置或標籤補足 | 對互動教材尤其重要：固定／變動、正確／錯誤、保留／可用 IP 不能只靠綠紅色。這也對應目前 prompt 要求的非顏色標記 |
| [Atlassian Design：Typography](https://atlassian.design/foundations/typography) | typography 影響 communication、brand 和 emotion；以字體、大小、line-height、heading 層級和 spacing token 建立 hierarchy；使用 rem 方便調整 | 支持「方便」應先處理可讀性、層級、字距和 responsive，而不是只換色。Atlassian 的字體不必直接使用 |
| [Atlassian Design：Spacing](https://atlassian.design/foundations/spacing) | 以有限 spacing scale 和 8px base unit 維持跨 app 一致；spacing 同時支援 responsive 和 density | 可把現有 HTML 的留白轉成網站層 token，讓不同主題仍像同一網站。8px 是該系統選擇，不是必須採用的數字 |
| [Atlassian Design：Motion](https://atlassian.design/foundations/motion) | motion 用來說明改變、引導注意和表達品牌；以 duration、easing、property 及 semantic token 定義；要求 reduced-motion 和單一 focal point | 支持「好玩／好奇」不能只靠鮮豔色：有意義的 reveal、focus、因果轉場也會影響感受。其 50–150ms／150–400ms 是參考，不是所有教材的硬值 |
| [AWS Trademark Guidelines](https://aws.amazon.com/trademark-guidelines/)／[AWS Partner Creative Guide](https://pages.awscloud.com/rs/112-TZM-766/images/AWS%20Partner%20Creative%20and%20Messaging%20Guide_January_2022_v1.pdf) | AWS 文件展示其 logo、色彩層級和清晰度規則；同時把整體網站 look and feel 視為品牌的一部分 | AWS 的色票與視覺語境可作雲端／工程內容的參考案例，但本網站仍應建立自己的 identity；本研究只採其視覺身份資訊，不把它當配色效果證據 |
| [Oracle Java Branding and Licensing Guidelines](https://www.oracle.com/a/ocom/docs/java-licensing-logo-guidelines-1908204.pdf) | Java 指南列出 Java Blue／Java Orange、背景、留白和可辨識性例子 | 可作 Java 分類視覺語境的參考案例；最終是否採用相近或不同的 accent，應由本網站的 role token、受眾感受假說和對比檢查決定，不把官方色票直接定為本網站色票 |

## 色彩感受的實證邊界

### 可以引用的結果

| 研究 | 實驗／資料 | 對本專案的可用結論 |
|---|---|---|
| [Valdez & Mehrabian, 1994, *Effects of color on emotions*](https://doi.org/10.1037/0096-3445.123.4.394) | **閱讀深度：資料庫摘要。** 摘要描述以 Munsell 色彩和 Pleasure–Arousal–Dominance 模型測試 hue、saturation、brightness，並報告 saturation／brightness 的迴歸結果 | 可作早期結果的索引，提醒選色至少記錄明度／亮度和飽和度；因未讀完整論文，不能在本文件推論其完整樣本、流程或限制。它不是網站介面或學習成效研究 |
| [Wilms & Oberfeld, 2018, *Color and emotion: effects of hue, saturation, and brightness*](https://www.staff.uni-mainz.de/oberfeld/downloads/Wilms-Oberfeld2018_Article_ColorAndEmotionEffectsOfHueSat.pdf) | **閱讀深度：完整 PDF 的方法、結果、討論與限制。** 研究獨立操弄 hue、saturation、brightness，配合情緒自評及 skin conductance／heart rate；作者指出三個維度及交互作用都重要 | 最直接支持「同樣是藍或綠，亮度／飽和度改變後感受可能不同」。研究使用大面積自發光色塊；作者也明說不能直接推廣到小色塊、不同背景、衣服或室內空間 |
| [Adams & Osgood, 1973, *A Cross-Cultural Study of the Affective Meanings of Color*](https://doi.org/10.1177/002202217300400201) | **閱讀深度：出版者摘要與 metadata；全文受限。** 摘要描述 Osgood 23 個文化的 semantic differential color data，並提醒樣本不代表整個國家 | 可保留作跨文化研究的歷史索引，但不應把它變成「綠色在所有人眼中都穩定」的規則；完整研究設計和樣本限制需另讀全文 |
| [Jonauskaite et al., *A machine learning approach to quantify the specificity of colour–emotion associations and their cultural differences*](https://royalsocietypublishing.org/doi/10.1098/rsos.190741) | **閱讀深度：出版者摘要、搜尋可讀的論文摘錄與結果摘要；未完整重現方法。** 摘要描述中國、德國、希臘、英國的 711 名參與者，以及 colour／country classification 的方法與結果 | 可作「既有共通也有 country-specific patterns」的研究線索，支持未來問目標受眾；目前不把部分方法細節或效應大小當成完整核對結果 |
| [Kawai et al., *The good, the bad, and the red: implicit color-valence associations across cultures*](https://link.springer.com/article/10.1007/s00426-022-01697-5) | **閱讀深度：出版者摘要與方法摘錄；未完整重現兩個實驗。** 研究比較西方與中國／澳門參與者在紅—綠、紅—白情境的 implicit valence interaction，指出不同群組的效應強度可能不同 | 「顏色在不同文化有不同意義」可成為待測假說，但這仍不等於網站 mood 的直接測量；使用前應回到完整論文和目標受眾測試 |
| **旁支：[Levitan et al., *Cross-Cultural Color-Odor Associations*](https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0101651)** | **閱讀深度：PLOS publisher 的摘要、引言與結果摘錄。** 122 名、6 個文化群組，為 14 種氣味選 congruent／incongruent 色彩；群組內有一致選擇，群組間 pattern 有差異 | 只用來限制「聯想可能受經驗與文化影響」的推論；這是 color–odor 而非 UI 或網站 mood 研究，不列為主要配色證據 |

### 對目前綠色觀察的精確說法

- **程式觀察**：現有 `lessons/aws/ipv4-bits-cidr/index.html` 的主要互動／章節／固定前綴共用綠色變數。
- **使用者主觀感受**：穩定、簡單、常見；這不是測得的讀者反應。
- **尚未證實的假說**：綠色是否讓本網站受眾感到方便、護眼、穩定或好玩。這需要受眾比較或問卷，不應只由色相推導。
- **研究支持的較窄結論**：明度／亮度、飽和度、色相、背景與文化語境共同影響色彩感受；「綠色」不是足夠精確的設計規格。

## 把「方便、好玩、引起好奇心」轉成可檢查決策

下面是待驗證的設計假說，不是研究已證實的心理因果。每個詞都要對應畫面、操作和測試指標，否則只是 moodboard 文案。

| 受眾想感受到 | 可先試的視覺決策 | 互動／內容決策 | 檢查方式 |
|---|---|---|---|
| 方便 | 高可讀性中性底、固定內容寬度、清楚 heading、穩定按鈕位置、足夠 line-height、可預測的 focus 和返回路徑 | 每次只引入一個新變數；改值後直接看到中間步驟和結果；避免無意義的等待 | 受試者能否在限定時間找到操作、說出下一步要看哪裡、用鍵盤完成同任務；WCAG 對比與手機檢查 |
| 好玩 | 少量高 chroma accent、可即時回饋的 hover／press／drag、可重設的沙盒、局部節奏變化；避免整頁高飽和 | 允許試錯，讓操作產生可見後果；用數值、圖形、文字一起回應，而不是用裝飾動畫代替結果 | 使用者是否主動嘗試第二種輸入、是否重做或探索邊界；完成任務時間和自評只能作輔助，不把互動次數當學會 |
| 引起好奇心 | 一個清楚的視覺焦點、局部先藏後揭、對比或留白暗示尚未解釋的關係；預告結果但不先公布原因 | 先問「如果只改這一位會怎樣？」再 reveal；讓讀者可回到原狀態比較 | 使用者是否提出預測、能否在 reveal 前說出可能結果、能否把規則套到新案例；檢查 reveal 是否有解釋而非純粹驚奇 |

色彩只是上述決策的一個參數。字體和留白影響掃讀與認知負荷，幾何與圖層影響結構理解，motion 影響注意力和「改變如何發生」的可見性；Atlassian 的 typography、spacing、motion 指南和 W3C 的可及性文件都直接把這些列為獨立的設計問題。

## 建議的網站層／主題層 token 結構

這是後續實作前的資料模型構想，不是現在要寫進 AGENTS.md 或 Skill。

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
site.color.diagram-fixed
site.color.diagram-variable
site.color.diagram-derived
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
```

規則如下：

1. `site.*` 固定網站身份和閱讀行為；同一網站的 AWS、IP、Java 都沿用。
2. `topic.*` 只影響 title marker、互動控制、章節識別和少量圖解 highlight；不重定義 error、success、focus。
3. `diagram-fixed`、`diagram-variable`、`diagram-derived` 是教學語意，不可只用顏色辨識，還要搭配線型、標籤、紋理、位置或形狀。
4. 每個文字／背景／圖形 pair 在候選 palette 中先通過 WCAG，再談 mood；不同主題若 accent 對比能力不同，應調整 tone 或使用 neutral container，而不是降低文字可讀性。
5. 先維持同一字體、spacing、shape、motion 和 component geometry，再比較三組 accent palette。這樣才能知道受眾反應是來自色彩，還是整體版面變化。

「AWS/IP 一組、Java 一組」可作資訊架構。AWS／Java 官方色票可以是分析視覺語境的參考案例，但本網站應由自己的 identity、受眾感受假說和 contrast rules 決定，不必直接複製任何品牌的整體 look and feel。這份研究只提出網站設計判斷；後續可建立自己的 `topic.network` 與 `topic.java`，並記錄它們是本網站的分類色。

## 同感覺、不同 palette 的研究流程

1. **先定義受眾與任務**：寫清楚訪客是要快速理解、探索、複習還是解決工作問題；同一個「好玩」對新手和熟手可能是不同體驗。
2. **建立 mood brief**：選 3–5 個詞，例如「方便、好玩、好奇、可信」，每個詞寫一條可看到的行為或畫面條件；把主觀詞標為假說。
3. **固定非色彩變因**：同一份 CIDR 內容、同一文字、同一 layout、字體、spacing、圓角、motion、互動和預設值，先不要同時換十件事。
4. **以 role token 生成候選**：以 HCT 或 OKLCH 控制 hue／chroma／tone（或 lightness），維持相同 semantic role 和對比門檻。可參考 Material HCT、Radix scale、Adobe Leonardo，但本專案目前不需要安裝它們。
5. **做至少三組待測候選**：例如低彩度深青＋暖色 highlight、偏藍紫的冷色方案、偏黃綠但低亮度的自然方案。這些只是後續比較的方向，不是本次選定的預設色系；名稱描述角色和參數，不要先把「快樂色」「護眼色」當作事實。
6. **先檢查可讀性與操作**：普通文字 4.5:1、大字 3:1；識別操作元件／狀態或理解內容所需的圖形部分，與相鄰色至少 3:1（不是要求所有裝飾邊框都達 3:1）。keyboard focus、dark/light、手機窄版、reduced motion、非色彩標記和離線載入也要依實際介面驗。[WCAG Non-text Contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html)
7. **再做受眾比較**：讓相同受眾在相同內容上看 A/B/C；詢問第一印象、可信度、好奇、方便、好玩，並觀察是否能完成任務、預測、解釋和轉用到新案例。主觀評分不能取代內容正確性。
8. **保留決策紀錄**：記錄候選的 token、source color、色彩空間、contrast 結果、受眾與日期；若只靠口頭說「比較有感覺」，下次無法重現。

## 成本與驗證邊界

| 層級 | 成本 | 可回答的問題 | 目前狀態 |
|---|---:|---|---|
| Token／contrast 靜態檢查 | 低 | 顏色是否能重用、文字與圖形是否可讀 | 可先用原生 CSS／手算或現有工具；本次未對現有 HTML 做完整 audit |
| 三個 palette 的同內容 prototype | 中 | 同樣的互動與版面換色後，整體是否仍一致、哪組較易掃讀 | 尚未製作 |
| 鍵盤／手機／reduced-motion／灰階檢查 | 中 | 互動和資訊是否仍可理解 | 現有研究只整理規則，尚未對本專案逐項驗證 |
| 小型受眾 A/B/C 比較 | 中 | 「方便／好玩／好奇」是否在目標受眾身上成立 | 尚未招募或測試；結果只能代表測試對象 |
| 跨文化或多語受眾研究 | 高 | 色彩聯想是否因語言／文化改變 | 原始研究可作風險提醒，不能直接預測本網站受眾 |
| 建立自動 palette／token pipeline | 中至高 | 多主題、多檔案長期產出是否節省時間 | 暫不值得先安裝；先以一份網站 token JSON／CSS prototype 驗證重複需求 |

星數、搜尋排名、權威品牌和漂亮的 showcase 只適合決定先讀什麼，不能證明某套色彩會讓人覺得好玩、好奇或學得更好。品牌官方文件能說明它自己的規則；色彩情緒研究能說明在特定刺激和受試者下觀察到的結果；兩者都不能直接替本網站受眾做決定。

## 本次未驗證事項

- 沒有安裝或執行 Material Color Utilities、Adobe Leonardo、Radix 或任何候選 Skill。本輪另有 Realtime Colors／Huemint 的局部瀏覽器操作，見 [實際操作紀錄](audience-and-reference-analysis.md#實際瀏覽器操作紀錄)，不等於上述工具已驗收。
- 沒有用現有 IPv4 教材做完整 contrast、色覺模擬、手機、鍵盤、screen reader 或 reduced-motion acceptance test。
- 沒有實際訪談或問卷，因此「方便、好玩、引起好奇心」仍是使用者提出的目標詞和本次整理的待驗證假說。
- 沒有建立 AWS／IP／Java 的最終色票，也沒有決定網站應採 light、dark 或雙主題。
- 本次讀取的原始研究多測量顏色刺激、語意聯想或情緒維度，並非本專案的互動教學學習成效；後續實驗需要同時測視覺感受、任務完成和概念轉用。

## 來源查閱紀錄

本文件的連結均指向官方設計系統、規格、品牌文件或原始研究頁面。Material 3 主頁部分內容需 JavaScript，因此使用 Material Web repository 和 Material Color Utilities 的官方原始文件補足；DTCG 已改用 2025.10 正式 Final Community Group Report，並保留它「stable、intended for implementation、但不是 W3C Standard」的狀態說明。研究閱讀深度為：官方設計系統核心色彩／token／motion 頁面已讀；色彩研究逐項標出摘要、摘錄或完整 PDF 的閱讀程度；未安裝套件、未執行遠端範例、未將任何來源視為已通過本專案 QA。
