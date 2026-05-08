# 📖 TinyWin OS — 線上 AI 平台使用指南

> 本文件說明如何將 TinyWin OS 的技能規格載入各大 AI 平台，讓任何一個 AI 都能變成你的「行動特助」。

---

## 🎯 核心觀念：三種載入方式

```
┌─────────────────────────────────────────────────────┐
│                 TinyWin OS 載入方式                   │
├──────────┬──────────────┬───────────────────────────┤
│ 方式 A    │ 方式 B        │ 方式 C                    │
│ 全系統載入 │ 單一技能載入    │ 口頭啟動（零配置）         │
│          │              │                           │
│ 貼入      │ 只貼需要的     │ 直接描述你的狀態            │
│ SYSTEM_  │ SKILL.md     │ AI 會依據對話             │
│ PROMPT   │              │ 自行推理對應行為            │
│ .md      │              │                           │
├──────────┼──────────────┼───────────────────────────┤
│ 最完整    │ 最輕量        │ 最快速                    │
│ 有路由邏輯 │ 針對性強      │ 但精確度最低               │
└──────────┴──────────────┴───────────────────────────┘
```

---

## 🤖 各平台操作教學

### 1. ChatGPT（OpenAI）

#### 方式 A：使用 Custom Instructions（推薦）

1. 點擊左下角頭像 → **Customize ChatGPT**
2. 在 **「How would you like ChatGPT to respond?」** 欄位中
3. 貼入 `SYSTEM_PROMPT.md` 的全部內容
4. 儲存

> ✅ 設定一次，之後每次對話都會自動生效。ChatGPT 會自動偵測你的情緒狀態並啟動對應技能。

#### 方式 B：使用 GPTs（進階）

1. 前往 https://chatgpt.com/gpts/editor
2. **Name**：`TinyWin OS`
3. **Instructions**：貼入 `SYSTEM_PROMPT.md`
4. **Knowledge**：上傳所有 7 份 `SKILL.md` 檔案
5. 發布為私人 GPT

> ✅ 這是最完整的用法。GPT 會擁有完整的技能庫，並能根據你的對話動態載入對應技能。

#### 方式 C：單次對話

在新對話的第一句話直接貼入：

```
請扮演我的行動特助，使用以下規格運作：
[貼入 SYSTEM_PROMPT.md 內容]
```

---

### 2. Claude（Anthropic）

#### 方式 A：使用 Projects（推薦）

1. 在 https://claude.ai 左側欄點擊 **Projects**
2. 建立新 Project，命名為 `TinyWin OS`
3. 在 **Project Instructions** 中貼入 `SYSTEM_PROMPT.md`
4. 在 **Project Knowledge** 上傳所有 `SKILL.md` 檔案
5. 在此 Project 內開始對話

> ✅ Claude Projects 支援大量知識文件，非常適合載入完整的 TinyWin OS 技能庫。

#### 方式 B：單次對話

在對話開頭貼入：

```
<system>
[貼入 SYSTEM_PROMPT.md 內容]
</system>

我現在的狀態是：[描述你的狀況]
```

#### 方式 C：搭配 Claude Desktop + MCP

如果你使用 Claude Desktop 搭配本地 MCP Server：

1. 將 `skills/` 資料夾放在 MCP 可存取的路徑下
2. Claude 可直接透過 `Read` 工具讀取對應的 `SKILL.md`
3. 實現真正的「按需載入」——只在需要時才讀取對應技能

---

### 3. Google Gemini

#### 方式 A：使用 Gems（推薦）

1. 前往 https://gemini.google.com
2. 點擊左側 **Gems** → **新增 Gem**
3. **名稱**：`TinyWin OS 行動特助`
4. **Instructions**：貼入 `SYSTEM_PROMPT.md`
5. 儲存

> ✅ Gem 會記住你的設定，之後點擊該 Gem 就能直接與行動特助對話。

#### 方式 B：Gemini API（開發者）

```python
import requests

system_prompt = open("SYSTEM_PROMPT.md").read()

payload = {
    "system_instruction": {"parts": [{"text": system_prompt}]},
    "contents": [{"parts": [{"text": "我今天好多事要做，完全不知道從哪開始"}]}]
}

# Gemini 會根據 SYSTEM_PROMPT 自動啟動 SKILL-02 壓力降級
```

---

### 4. Cursor / Windsurf / AI IDE

#### 方式：放入 Rules 或 Skills 目錄

1. 將整個 `skills/` 資料夾放在專案根目錄下
2. 在 IDE 的 AI 設定中指定規則檔案路徑：
   - **Cursor**：`.cursor/rules/` 或直接在 Settings → Rules 中引用
   - **Windsurf**：`.windsurfrules` 中引用
3. AI 在開發過程中會自動根據你的訊息觸發對應技能

> ✅ 特別適合在寫程式寫到卡關時，AI 自動偵測你的拖延/焦慮狀態並介入。

---

### 5. 其他平台速查表

| 平台 | 載入位置 | 備註 |
|---|---|---|
| **Poe** | 建立 Bot → System Prompt | 可公開分享給其他人使用 |
| **Coze** | 建立 Bot → Persona & Prompt | 支援 Plugin，可串接行事曆 |
| **Dify** | Application → System Prompt | 支援 Workflow，可實作完整路由 |
| **HuggingChat** | System Prompt（對話開頭） | 開源模型，隱私性高 |
| **Perplexity** | 不適用 | 搜尋導向，不適合角色扮演 |

---

## 📋 實際使用範例

### 範例 1：壓力降級（任何平台都適用）

**你說：**
```
我今天有報告要寫、信要回、還要準備明天的會議，完全不知道從哪開始。
```

**AI 回應（已載入 TinyWin OS）：**
```
## [當前診斷]
啟動癱瘓：3 項任務同時壓迫，前額葉離線中

## [導航指令]
啟動 SKILL-02 壓力降級，限時 5 分鐘

## [微小動作]
1. 打開報告的 Word 檔案，寫出 3 個小標題
2. 設定手機計時器 5 分鐘
3. 5 分鐘後回來告訴我「完成了」或「卡住了」

## [模式標記]
🖥️ 線上版

## [存檔狀態]
⏳ 等待你完成後存檔
```

### 範例 2：口頭啟動（零配置版）

即使你沒有貼入任何 SYSTEM_PROMPT，也可以直接對任何 AI 說：

```
請用 TinyWin OS 的「壓力降級」技能幫我處理：
我的報告寫不出來，已經拖了三天。
請把任務降級成 5 分鐘版本，不要超過 3 個步驟。
```

> 💡 大部分 AI 都能理解這種結構化的指令，即使沒有完整的 SYSTEM_PROMPT。

---

## ⚡ 進階技巧

### 技巧 1：技能串接

在對話中手動串接技能：

```
我剛完成了壓力降級的 5 分鐘任務，但現在覺得寫得不夠好，一直想修改。
```

→ AI 會自動從 SKILL-02 切換到 SKILL-03（醜陋初稿）

### 技巧 2：模式切換

告訴 AI 你要切換模式：

```
我要出門了，請幫我把剛才的分析結果轉成線下版的便利貼格式。
```

→ AI 會將數位結果轉換為可列印/手抄的實體行動卡片

### 技巧 3：每日儀式

建議的每日使用流程：

```
🌅 早上：「讀檔」→ 恢復昨天的進度（SKILL-07）
🌞 工作中：遇到卡關 → AI 自動偵測並啟動對應技能
🌙 睡前：「掃雷」→ 準備明天的環境（SKILL-01）
```

---

## ❓ 常見問題

### Q：哪個平台效果最好？

**Claude Projects** 和 **ChatGPT GPTs** 的效果最完整，因為它們支援上傳多份知識文件，能實現完整的技能路由。單次對話的效果取決於你貼入的內容量。

### Q：免費版能用嗎？

可以。所有平台的免費版都支援「方式 C：單次對話」。只要把 SYSTEM_PROMPT 或單一 SKILL.md 貼入對話開頭即可。

### Q：我可以修改技能內容嗎？

當然。每份 SKILL.md 都是獨立的 Markdown 文件，你可以根據自己的需求調整觸發信號、行動指令、輸出格式等。修改後重新載入即可。

### Q：可以跟別人分享嗎？

可以。將 `skills/` 資料夾分享給任何人，對方只需按照本指南載入即可使用。如果你想公開分享，推薦上傳至 GitHub 並建立 ChatGPT GPT 或 Poe Bot 供他人直接使用。

---

*TinyWin OS v2.0 | 開發者：Morton (FlowGPS)*
