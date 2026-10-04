# 互動式學習

用可離線開啟的單一 HTML，讓讀者透過操作理解原理，並練習用在實際情境。

## 目錄

```text
interactive-learning/
├── README.md
├── AGENTS.md                         # AI Agent 共用規則
├── CLAUDE.md                         # Claude Code 的規則入口
├── prompts/
│   └── interactive-tutorial.md       # 共用教學提示詞
├── research/
│   ├── skills/                       # Skill、案例、影片與製作方法調查
│   └── visual-design/                # 樣式、配色、受眾感受與視覺身份調查
└── lessons/
    └── aws/
        └── ipv4-bits-cidr/
            ├── brief.md             # Input：這份教學的需求
            ├── index.html           # Output：互動教學成品
            └── references/
                └── README.md        # Source：來源與參考資料
```

`lessons/<主題>/<教學名稱>/` 是每份教學的家。AWS 是其中一個主題；其他主題需要時再新增。資料夾採小寫英文，以連字號分隔。

## 製作與修改

1. 建立教學資料夾，在 `brief.md` 填寫主題、目前程度、卡點與學習目標；未知資訊標記為待補。
2. 有參考資料時建立 `references/`。網址與出處記在其中的 `README.md`；文字、圖片、逐字稿等檔案也放在這裡。
3. 將 [共用提示詞](prompts/interactive-tutorial.md) 與該教學的 `brief.md`、參考資料交給 AI Agent，製作或修改 `index.html`。
4. 檢查內容、數值、邊界情況及互動，在 `brief.md` 的檢查紀錄寫下已驗證與未驗證項目。

共用提示詞放教學方法；`brief.md` 放這份教學的個別需求。直接維護 `index.html`，需要版本紀錄時使用 Git。

需要沿用某份教學的風格時，在 `brief.md` 加上「樣式參考」及檔案路徑，或在當次要求中指定。例如：「請依共用提示詞製作這份教學，樣式參考 `lessons/aws/ipv4-bits-cidr/index.html`；沿用配色、留白、卡片與導覽風格，教學圖像與互動依新主題設計。」

## 開啟現有教學

用瀏覽器直接開啟 [IPv4／CIDR 教學](lessons/aws/ipv4-bits-cidr/index.html)，不需安裝套件或啟動伺服器。成品內的參考連結需要網路才能查看。

未來採用 Astro 時，再新增 `site/` 管理網站導覽與呈現，沿用 `lessons/` 的成品。

## 調查資料

[research/skills/](research/skills/README.md) 保存互動教學方法、Skills、作品、影片與簡報技巧的調查，供後續評估；其中的工具尚未安裝。先讀 [2026-10-04 調查總報告](research/skills/2026-10-04-survey.md)。

[research/visual-design/](research/visual-design/README.md) 保存樣式、配色、受眾感受、視覺參考與跨主題一致性的調查。先讀 [視覺設計調查總報告](research/visual-design/2026-10-04-survey.md)。目前只收集與評估，未修改教材樣式或建立 Skill。
