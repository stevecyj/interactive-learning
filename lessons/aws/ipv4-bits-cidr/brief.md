# IPv4／CIDR 互動教學需求

## 來源與狀態

既有成品由使用者先在 DOT 製作。本次僅整理目錄並搬移 HTML；以下內容依成品整理，不代表已取得原始需求。

## 我的需求

- 主題：IPv4 位元、CIDR 前綴、網路位址與 AWS 子網路地址判斷。
- 我目前懂到：待補；原始學習程度尚未提供。
- 我卡住的地方：待補；原始卡點尚未提供。
- 學完後想能做到：依既有成品推定，能判斷一個 IPv4 地址是否位於指定 CIDR 範圍，並依一般 AWS IPv4 子網路的保留規則判斷是否能分配給 EC2。
- 參考資料：見 [references/README.md](references/README.md)；原始教學內容尚未提供。

## 既有教學範圍

由 bit 的 0／1、8 bits 的數值、IPv4 的 32 bits，逐步介紹 /24 與 /16、網路位址計算、前綴比對、CIDR 遮罩連續性，最後以 3 題練習結合 AWS 地址保留規則。

交付成品：[index.html](index.html)。共用教學方法見 [interactive-tutorial.md](../../../prompts/interactive-tutorial.md)。

## 檢查紀錄

### 2026-10-04：目錄整理

- 本次範圍：搬移既有 HTML，補上需求與來源索引。
- 已驗證：搬移前後 HTML 的 SHA-256 相同；本地 Markdown 連結皆有對應檔案；HTML 沒有需隨檔搬移的外部本地資源。
- 未驗證：教學內容正確性、數值與邊界情況、瀏覽器互動、手機版面、鍵盤操作，以及參考網址的目前內容。

### 2026-10-04：Impeccable 樣式試作

- 需求背景：使用者補充，這份內容是為了理解 AWS 雲端，從曾經不懂的二進位、十進位與 IP 分配開始整理；呈現形式結合互動、簡報與教學。
- 本次範圍：保留原始 [index.html](index.html)，另外製作 [index-impeccable.html](index-impeccable.html)。只替換內嵌 CSS；教學文字、HTML 結構、JavaScript 與計算規則不變。
- 視覺方向：暖紙色閱讀底、墨黑頁首、襯線標題、黃色章節／操作重點、等寬數值和較少圓角。綠／橘保留原本的固定／可變位元語意，與教材文字相符；可變位元另用虛線邊框。
- 方法來源：依 [Impeccable v4.5.0 官方 Skill](https://github.com/pbakaus/impeccable/blob/main/.agents/skills/impeccable/SKILL.md) 的 Read／Operate、[new-work](https://github.com/pbakaus/impeccable/blob/main/.agents/skills/impeccable/reference/new-work.md)、[colorize](https://github.com/pbakaus/impeccable/blob/main/.agents/skills/impeccable/reference/colorize.md)、typeset、layout 與 craft-floor 指引手動製作。沿用不安裝工具的限制，未安裝或執行 Impeccable launcher／CLI，也沒有設定全站設計規則。
- 實際瀏覽器預覽：[impeccable-preview.jpg](impeccable-preview.jpg)。這是首章截圖，不是教材需要載入的資源。

已驗證：

- 原始 HTML 的 SHA-256 仍為 `cc89d4f54b6297f5d6220bad1520f3b4cb3db9932040bd6689b348baffb0437d`；新舊檔移除 style 區塊後完全相同，JavaScript 逐字一致。
- 在 Chrome 透過僅限本機、只讀取兩份教材的預覽伺服器操作。桌面與 390px／320px 窄版逐章檢查十個章節，沒有頁面橫向溢出或可見內容超出容器；1024px 另檢查較密集的遮罩頁。
- 上方／下方導覽、章節切換、首章停用上一頁、末章從頭再看，以及回到前頁保留已操作狀態。
- 單 bit 的 0／1、8 個位元逐一累加到 255、10／255／歸零預設、/24 與 /16 可變位元；固定前綴不能操作，地址總數分別為 256 與 65,536。
- 遮罩結果展開／收起、/16 與 /24 的三台機器分組、自由探索的 /16／/24／/32；空值、超出 255、負值、組數不足／過多會提示；0.0.0.0 與 255.255.255.255 可正常計算。
- 遮罩滑桿用 Home／方向鍵核對全部 33 個位置（/0～/32），二進位與十進位一致；預設按鈕、增加／減少 1 bit、端點停用狀態及無效 255.255.191.0 的對照顯示。
- 三題均操作未作答、答錯、答對與重新選擇；每題解析有四組、64 格二進位對照，第二題有四個不相同位元格（上下兩列各兩格）。
- 鍵盤 Enter／Space 可操作按鈕、位元、題目與輸入；滑桿方向鍵保持自身用途。深色頁首的焦點框使用黃色，與背景對比足夠。手機另操作可變位元與第二題解析。
- 逐章檢查已呈現文字的 computed foreground／不透明背景配對，沒有低於適用 4.5:1／3:1 門檻的項目；另檢查並加深位元邊框。這是有限範圍檢查，不是完整 WCAG 合規結論。
- 新檔沒有外部 script、stylesheet、圖片、CSS url／import 或網路請求程式；離線所需內容全在單檔。瀏覽器未記錄教材 JavaScript 錯誤。
- 當日核對 [Amazon VPC 官方規則](https://docs.aws.amazon.com/vpc/latest/userguide/subnet-sizing.html)：一般 AWS IPv4 子網路保留前四個與最後一個地址，原有題目中的 .3 判斷相符。本次沒有改寫教材或全面重新審核全部 RFC 內容。

未驗證：

- 瀏覽器工具不允許 `file:` 網址，因此實際操作使用本機 HTTP 預覽；未透過該工具直接開啟檔案或切斷網路驗收。離線能力的證據為單檔資源與原有無網路依賴的程式結構。
- Safari／Firefox、實機手機、讀屏、系統字體差異、200% 縮放、色覺模擬，以及切換系統減少動態偏好；CSS 已保留 reduced-motion 規則。
- 受眾是否真的更覺得方便、好玩或好奇；這是可供比較的樣式試作，尚未進行受眾測試或選定網站正式配色。
