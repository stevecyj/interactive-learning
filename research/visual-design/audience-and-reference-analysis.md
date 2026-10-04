# 從受眾感受與參考作品，走到可重用的視覺規則

調查日期：2026-10-04（Asia/Taipei）。這份記錄補上「如何問、如何分析、如何避免只換一個色相」；沒有製作新樣式、候選 HTML 或 Skill。

## 判斷應分成四件事

1. **想傳達什麼**：網站作者希望方便、好玩、引起好奇。這是設計目標。
2. **參考作品怎麼做**：它用什麼配色角色、字體、留白、圖形、動態與操作形成身份。這是可觀察特徵。
3. **我們預期什麼**：保留部分特徵、換掉其他特徵後，可能仍有相近感受。這是設計假說。
4. **讀者實際感受到什麼**：需要讀者的選詞、說明與任務表現。這是尚未蒐集的證據。

不能把第 1 或第 3 項寫成第 4 項。官方品牌文件說的是品牌自己的意圖；得獎、GitHub stars、影片 views 說的是不同形式的關注度。

## 少量、但能決定方向的訪談項目

以下是日後製作時的記錄框架，**不是本輪向使用者提問，也不是已完成的受眾研究**。

| 要記錄的資訊 | 最少可問什麼 | 對設計的影響 |
|---|---|---|
| 人與任務 | 主要給誰看？他來快速找答案，還是願意探索幾分鐘？ | 說明密度、控制數量、章節長度、結果是否先給 |
| 感受優先序 | 在方便、好玩、好奇之間，哪一個優先？ | 避免同時最大化熱鬧動態、快速掃讀和懸念 |
| 不想出現的感受 | 哪種畫面會讓你覺得幼稚、花俏、像企業報表或太冷？ | 設定尺度，不把「好玩」自動翻成卡通、彩虹或動畫 |
| 具體參考 | 指出一個喜歡的片段：喜歡的是顏色、字體、構圖、圖解還是操作？ | 能拆出機制，減少整頁照抄 |
| 維持一致的範圍 | AWS/IP 共用身份；Java 只換 accent，還是圖解語法也不同？ | 決定哪些是網站固定值、哪些是分類變項 |

不要先問一大串設計偏好。已有答案可以從 brief、既有 HTML 和當次要求推定，標記推定即可。此專案目前已知的目標詞是「方便、好玩、引起好奇」，受眾輪廓與其優先序仍未定。

## 將參考作品拆開，再重新組合

[Samantha Warren 的 Style Tiles](https://alistapart.com/article/style-tiles-and-how-they-work/) 用字體、色彩與介面元素討論方向，讓抽象形容詞可以對照具體視覺；[Dan Mall 的 Element Collages](https://v3.danmall.com/articles/rif-element-collages/) 則容許先記錄局部設計構想，再與頁面架構整合。它們是設計溝通方法，沒有保證某組配色必然造成某種情緒。

Style Tiles 原作者的 [Style Guides Podcast 逐字稿](https://styleguides.io/podcast/samantha-warren/) 提供一個有用的例子：先理解客戶對「多面向、當代」的聯想，再從具體穿搭參考取出色彩，附上選擇理由討論。重點是讓設計選擇能追溯到語境。**本輪讀的是搜尋工具取得的原站逐字稿，沒有聽音訊；另以直接 HTTPS 連線補查時，發現憑證 hostname 不符，未繞過驗證。** 這個舊入口的可用性需後續重查，不把它當作目前穩定可用的工具。

本專案可以沿用下面的分析表；這是本次綜合整理，不是原作者的固定模板。

| 分析欄位 | 記什麼 | 如何保留相近感覺、做出不同身份 |
|---|---|---|
| 使用情境 | 首頁廣告、閱讀文章、操作圖解、答題回饋，要分開看 | 避免把 landing page 的巨型標題套到計算步驟 |
| 色彩角色 | 背景、文字、操作、分類、資料、狀態各自用什麼 | 保留角色分工，不保留每個色碼 |
| 色彩關係 | 明暗差、彩度、暖冷對比、accent 面積、是否只在關鍵處出現 | 保留層級與聚焦方式，改 hue／chroma 後重新驗對比 |
| 字體 | 標題與正文對比、字重、等寬數值、繁中效果 | 保留層級，採離線可用的字體策略 |
| 空間與形狀 | 密度、閱讀寬度、邊框、線條、圓角、是否所有內容都裝卡片 | 改變一兩個有理由的特徵，避免整套模板原封不動 |
| 圖形語法 | 哪種線、箭頭、標籤表示固定／變動／結果 | 對應概念，保持跨課可預測；顏色有非色彩備援 |
| 動態 | 何時動、什麼狀態改變、能否停止、是否增加等待 | 保留因果回饋，捨去對理解沒有作用的動態 |
| 證據 | 官方設計意圖、看到的畫面、獎項、實測反應各自標明 | 不把分析者的感受說成所有讀者的感受 |

**示意推論，尚未選定設計**：若喜歡某參考的「俐落但可探索」，可以保留中性閱讀底、清楚的操作層級、單一動態焦點與可重設探索；分類用不同 accent 家族，圖形採自己的標記。是否仍俐落、是否更有辨識度，要在相同內容上比較，而不是靠命名「新潮色」判定。

### 兩種比較，不要混為一談

- **探索視覺方向**：可同時改字體、形狀、配色、密度，幫助選一種整體身份；結果只能說整體方向受到偏好。
- **研究色彩的影響**：保持內容、操作、字體、layout、motion、預設值一致，只替換配色角色；才能較有理由將差異歸到配色。

前者適合初期比較 Style Tiles／片段；後者適合已有共同介面後比較 AWS/IP 與 Java 的 accent。這是對本專案的研究設計建議，尚未做 A/B/C 測試。

### 非 Skill 的現成做法：Mailchimp Brand Kit

[Mailchimp 官方 Brand Kit 文件](https://mailchimp.com/help/use-brand-kit-creative-assistant/) 把 logo、字體、顏色、品牌個性和按鈕樣式放在一起：個性選項與滑桿會連到 mood board 範例，色彩還記錄能否作背景及其文字配對，套用後用同一模板預覽。這是值得借的「描述感覺 → 看具體差異 → 保存共同規則」產品流程；**它的自動品牌判讀與生成品質是產品宣稱，本輪沒有登入或操作，也不建議為教材採用其行銷平台。**

[2018 年原設計負責人的改版說明](https://mailchimp.com/resources/new-brand-announcement-2018/) 記錄另一個相關問題：產品、網站、行銷與支援各自發展後，身份逐漸分散；改版同時整理字體、色彩、圖像與共同身份，仍希望保留原有個性。這是品牌意圖與歷史案例，沒有證明讀者感受。對本專案可借的是「跨觸點一致＋留有個性」，不只是換品牌色。

### 補充：直接談視覺方向與色彩的原作者影片

以下是補查得到的觀看入口，**沒有觀看影片或讀完整字幕**。只記官方搜尋結果的標題／作者、可見 description 與 chapters；Google 項目另讀官方研究文章。直接擷取部分 YouTube 觀看頁失敗，不以第三方轉錄補成已觀看的內容。

| 官方影片 | 可核對的訊號與深度 | 後續值得看什麼 |
|---|---|---|
| [Google Design — Introducing: Material 3 Expressive](https://www.youtube.com/watch?v=n17dnMChX14)、[官方研究說明](https://design.google/library/expressive-material-design-google-research) | 官方影片 metadata 已查；研究文章核心方法／限制已讀。影片描述將色彩、形狀、字體、動態與元件一起討論 | 看「有個性、好玩」如何由多個設計元素共同形成。研究是特定介面與 Google 自述，不能直接推成教材的效果保證 |
| [Kevin Powell — Build smarter color systems with relative colors](https://www.youtube.com/watch?v=vGfTyHPWZLE) | 官方 metadata：2026-01-07；約 20,140 views／1,400 likes（本輪搜尋快照，可能是索引值）；章節列 relative colors 與 OKLCH | 值得補技術層：分類 accent 如何從共同色彩關係產生。未核對示範程式、瀏覽器相容性或對比，不把影片當已驗證方案 |
| [Juxtopposed — world's shortest UI/UX design course](https://www.youtube.com/watch?v=wIuVvCuiJhU)、[Realtime Colors 作者文件](https://www.realtimecolors.com/docs/about-realtime-colors) | 官方搜尋結果核對影片標題與作者；作者文件已讀，工具有局部操作紀錄。未取得完整官方字幕 | 值得觀察作者如何講網站元素與整體預覽。影片具體主張尚待觀看；本輪實際工具發現以後文紀錄為準 |

播放量、likes 和頻道關注度只表示關注，不是效果評分。這三項補上視覺／配色方向；教學敘事與互動演講另見 [案例與影片](reference-sites-and-videos.md#官方原作者影片與演講)。

## 怎麼測量「看起來有某種感覺」

[NN/g 對 Microsoft Desirability Toolkit 的視覺測試改編](https://www.nngroup.com/articles/microsoft-desirability-toolkit/) 建議用精簡、混合正面／負面／中性詞的選詞方式，比只問「喜不喜歡」多一層可比較資訊；也要追問選詞理由。靜態截圖可用於第一印象，**不能測出實際操作是否方便、探索是否好玩、概念是否學會**。該文章是 NN/g 的方法說明，不是 Microsoft 原始研究全文。

未來可用自己整理的繁中詞彙，例如清楚、親切、活潑、好奇、熟悉、平淡、擁擠、幼稚、冷淡、難辨認，先自由回答再選詞，避免只放期望中的正面詞。這是訪談輔助，**不是經驗證的繁中量表，也不要把它稱為 UEQ**。少量質性測試記錄原話與人數，不用精密百分比包裝成普遍規則。

[UEQ 官方手冊](https://www.ueq-online.org/Material/Handbook.pdf) 區分整體吸引力、清楚易懂、效率、可控制／可預期、激勵感和新穎性。本專案可以借這些區別避免把「好看」等同「方便」。將方便對應到清楚／效率、好玩對應到激勵感、好奇對應到新穎性，是**我們的概念對照**，不是原量表的等義翻譯。UEQ-S 的 8 題只有較粗的實用／享樂維度，不能當成完整 UEQ 的六個量表；自訂題目也不能沿用其基準分數。本輪讀過手冊的量表說明與方法段落，沒有施測。

可以分別記錄三種結果：

| 結果 | 適合的問題／任務 | 不足以證明什麼 |
|---|---|---|
| 第一印象 | 這畫面讓你想到哪些詞？哪個位置造成這個印象？ | 實際可用性與學習效果 |
| 操作感受 | 更改 prefix、讀出結果、回到原值；哪裡找不到或不確定？ | 是否真的理解 CIDR 原理 |
| 理解與轉用 | 給不同 IP／prefix，請解釋判斷並指出圖上依據 | 是否適合所有受眾，或所有題材 |

[NN/g 的 aesthetic-usability effect 說明](https://www.nngroup.com/articles/aesthetic-usability-effect/) 也提醒，外觀可能影響人對可用性的評價。因此好看與完成任務都要看，不能只以「感覺更容易」當通過。

AI 可以協助找出假說、整理差異，不能冒充受眾訪談。[Salim & Mueller 的 2026 預印本](https://arxiv.org/abs/2607.02455) 比較 persona 提示在不同模型的色彩指定與圖表選擇，結果依模型／任務而異；它只適合提供探索線索，不能取代真人參與者。**本輪只核對摘要與版本，未完整審查方法或重現實驗。**

## 「AI 平均樣式」這個說法的證據

使用者看到兩份相近的綠色內容，是值得記錄的觀察；目前未提供該影片 URL、模型／prompt／版本或其他樣本，不能確定共同原因。

- [HTTP Archive 2025 Generative AI 章節的 AI colors 分析](https://almanac.httparchive.org/en/2025/generative-ai#ai-colors) 查 CSS 變數中的紫／indigo 等特定色碼。Tailwind 頁面的比例沒有明顯暴增，整體網頁比例上升可能反映框架普及；作者也列出漏掉 hardcoded 色碼等限制。**不能據此宣稱 AI 網頁普遍偏綠，也不能以顏色辨認某個作品是否 AI 生成。** 本輪讀過這節的查詢方法、結果與限制。
- [Shin et al. 的 2026 design homogenization 預印本](https://arxiv.org/html/2603.13036v1) 以學術／灰色文獻與平台 walkthrough 討論樣式趨同，提出反思與語境錨定方法。這不是綠色頻率調查，也沒有為本專案提供經驗證的解法。本輪讀過核心方法、設計建議與限制。

對本專案的合理應對是：保存受眾、內容、參考機制與選擇理由，要求有具體差異的視覺方向；評估字體、構圖、密度與圖解語法，不只把綠色換成紫色。這是我們的設計判斷，不是上述研究驗證過的保證。

旁支追查了 2021 CHI 的 *Investigating the Homogenization of Web Design*，但舊作者 PDF URL 已轉址、另一份校方 PDF 本輪抓取失敗；未把搜尋摘要當成已讀論文，也未以它支撐具體結果。

## 配色工具：哪些解決角色，哪些只是發想

| 工具／原始來源 | 可借的方法 | 本輪查閱與操作 | 限制與投入順序 |
|---|---|---|---|
| [Realtime Colors](https://www.realtimecolors.com/)、[作者文件](https://www.realtimecolors.com/docs/about-realtime-colors) | 將 text/background/primary/secondary/accent 套進同一網站預覽；看色票如何實際使用 | 官方文件已讀；**實際用鍵盤改 Primary hue，預覽 CTA 同步變色** | 適合快速比較角色。預覽不是教學頁；對比提示與虛構 testimonials 都不能當品質驗證。優先 |
| [Huemint About](https://huemint.com/about/)、[網站單 accent 預覽](https://huemint.com/website-1/) | 用背景／前景／accent 的關係產生方案，可鎖色並調生成多樣性 | 原作者方法頁已讀；**實際按 Generate，色碼與同一版面同步更新** | 使用 CIE Delta-E 描述色彩差異，**不是 WCAG luminance contrast**；機率高也不代表有身份或符合受眾。值得發想 |
| [Adobe Leonardo](https://github.com/adobe/leonardo) | 用 target contrast ratios 建色階 | 官方 README／方法由同輪研究讀取；未執行 | 適合正式生成與對比流程；暫不安裝。優先研究方法 |
| [OKLCH Picker](https://oklch.com/)、[Evil Martians 方法說明](https://evilmartians.com/chronicles/oklch-in-css-why-quit-rgb-hsl) | 分開 lightness/chroma/hue，觀察色域後做有控制的色階變化 | 作者工具與核心方法／gamut 段已讀；未操作生成完整 palette | 比 HSL 更適合討論感知變化；**相同 L 或旋轉 hue 不保證 WCAG 通過**，仍驗最終色值／色域。優先 |
| [Happy Hues](https://www.happyhues.co/) | 策展 palette 與網頁各部件使用情境並列 | 官方頁結構已讀；未實際切換全部範例 | 適合學色彩用途；流行色票與一般色彩心理文字不能證明情緒因果。補充 |
| [Khroma](https://www.khroma.co/) | 以個人選色偏好生成，預覽 typography／gradient／palette，提供色值與配對 rating | 官方產品說明已讀；未挑選、訓練或匯出 | 學的是使用者偏好，不是目標受眾感受；也不是跨頁 semantic system。補充 |
| [Lyft coloralgorithm](https://github.com/lyft/coloralgorithm)、[ColorBox 現站](https://colorbox.io/) | 沿 hue/saturation/brightness 曲線產生多階色彩；研究可重複生成流程 | Lyft README 與現站介面已讀；未執行 | **現站署名 Kevyn，不能把它全部當成舊 Lyft 實作**。現站列 OKLCH／多種 export，未操作核實；歷史演算法和現版本分別看。補充 |
| [ColorBrewer](https://colorbrewer2.org/) | 區分類別色、序列色和以中點為界的差異色 | 官方工具方法由案例文件整理；未用本專案資料測試 | 主要是資料圖表，不是品牌方案；色彩角色有明確資料任務時很有用 |

### 實際瀏覽器操作紀錄

- **Realtime Colors**：預設 Primary `#2f27ce`。在 picker 用鍵盤將 hue 243 改為 0，textbox 顯示 `#ce2727`；同一 Get Started CTA computed background 由 `rgb(47,39,206)` 變為 `rgb(206,39,39)`，文字仍 `rgb(251,251,254)`。這確認一項角色變更會套到預覽。較早以 HEX textbox fill＋Enter 的嘗試未提交 palette，沒有將那次當成功。
- **Huemint**：開單 accent 網站模板，畫面／heading 色碼為 `#4b3b56 / #e4ebe4 / #bb8f67`；按 Generate 後變為 `#153147 / #f2dc95 / #ba5440`。截圖確認同一排版的背景、文字與重點色同步改變。這是隨機生成觀察，**不是為專案選定的色票，也不代表對比已通過**。
- 兩者都沒有登入、上傳專案、儲存帳戶設定、匯出成品或安裝。未驗完整手機、讀屏、鍵盤路徑或每個 palette。

## 現有 HTML 的樣式基線

本輪讀取 [IPv4 教材](../../lessons/aws/ipv4-bits-cidr/index.html) 的 CSS，原始值和計算細節保存於 [current-style-observations.json](current-style-observations.json)。檔案 SHA-256：`cc89d4f54b6297f5d6220bad1520f3b4cb3db9932040bd6689b348baffb0437d`。

| 目前角色 | 實際 CSS | 觀察 |
|---|---|---|
| 閱讀底／正文 | `--bg #f3f2ed`／`--ink #18352f` | 暖中性底與深色正文 |
| 主要綠色 | `--green #17664f`／`--pale #dceae2` | 章節提示、進度、主要操作、選中位元、固定前綴共用 |
| 可變部分 | `--orange #a44916`／`--peach #fff0df` | 主機位元、對照、部分提示；不全是品牌 accent |
| focus／錯誤 | `#216ed1`／多種紅色 literal | 已存在獨立功能色；不能只改 root 八個值就說完成所有主題狀態 |
| 字體／版面 | system-ui；數值等寬；白底圓角邊框 panel；小幅轉場 | 辨識度與閱讀感也來自這些參數，不只綠色 |

只計算了六組**不透明、純色的 CSS 色值配對**，沒有量測實際渲染：正文／頁底 11.79:1，輔助文字／頁底 4.98:1，綠文字／淺綠底 5.54:1，橘文字／淺橘底 5.30:1，白文字／綠底及綠文字／白底均 6.89:1。這些配對符合普通文字 4.5:1 的門檻；**不等於整份 HTML 通過 WCAG**。計算以未四捨五入的數值判定，顯示才取兩位。[W3C Contrast Minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)

日後換 theme 最重要的技術觀察是 `--green` 目前同時承擔多種角色。可以分開網站／分類身份、操作狀態與教學語意，再映射回顏色；不能用一個新 accent 無差別取代所有綠色。**本輪只記錄這個改造方向，沒有修改 CSS。**

## Astro 與單檔離線的交界

[Astro 官方樣式文件](https://docs.astro.build/en/guides/styling/) 支援 global/scoped CSS 與 CSS variables，適合日後網站共用規則。但如果現有 HTML 以 iframe 嵌入，裡面是另一份 document，外層變數不會自然變成教材的樣式；這由 [iframe 文件邊界](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/iframe) 和 [CSS variables 的元素繼承](https://www.w3.org/TR/css-variables-1/) 可推得。

目前可先記錄兩個未決方案：獨立 HTML 的共同規則在產出時寫入每檔，維持單檔離線；或之後整合 Astro 元件，於網站建置共用規則，再另產生離線檔。**共享規則不必等於執行時連外下載 CSS**。本輪不決定架構、不建立 token pipeline。

## 後續值得深讀的順序

1. Style Tiles／Element Collages：把「感覺」變成可以看、可以討論的差異。
2. NN/g desirability＋UEQ：分清第一印象、操作品質與探索感。
3. 同輪的 Khan／Duolingo 案例與 Impeccable：讀現有身份、保存規則、再比較不同方向。
4. Realtime Colors／Huemint／OKLCH／Leonardo：分別用於角色預覽、多樣化發想、受控變色、對比生成；不讓一個工具代替全部判斷。

原作者資料、官方介面與方法已標閱讀深度；未提供的影片、未進行的受眾研究、未操作的工具，都不視為已驗證。
