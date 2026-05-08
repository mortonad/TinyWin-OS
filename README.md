# 🚀 TinyWin OS — AI 小贏作業系統

> **QSLR (Quick Success, Little Recovery)**
> 快速拿到一個小勝利，快速從小挫敗復原。

一套可攜式的 AI 行為導航技能框架，基於認知行為療法 (CBT) 與創業者思維設計。
將每一份 `SKILL.md` 貼入任何 AI 的 System Prompt，即可啟用對應的行為干預能力。

---

## 📁 目錄結構

```
TinyWin-OS/
└── skills/
    ├── README.md                     # 本文件
    ├── SYSTEM_PROMPT.md              # 主控路由器（Persona + 狀態偵測 + 技能調度）
    │
    ├── nightly-reset/SKILL.md        # SKILL-01 睡前掃雷
    ├── pivot-action/SKILL.md         # SKILL-02 壓力降級
    ├── ugly-draft/SKILL.md           # SKILL-03 醜陋初稿
    ├── ghost-racing/SKILL.md         # SKILL-04 影子賽車
    ├── loss-cutter/SKILL.md          # SKILL-05 停損刀斧手
    ├── mind-dumping/SKILL.md         # SKILL-06 思緒傾印
    └── breadcrumb-pause/SKILL.md     # SKILL-07 進度防腐
```

---

## 🧩 技能一覽

### 啟動防禦模組 (Initiation Defense)

| 技能 | 用途 | 觸發信號 |
|---|---|---|
| **SKILL-01 睡前掃雷** | 睡前掃描隔日行事曆，預先清除啟動摩擦力 | 明天要、還沒準備、隔天行程 |
| **SKILL-02 壓力降級** | 將龐大任務降級為 5 分鐘無威脅版本 | 焦慮、好多事、做不動 |

### 認知優化模組 (Cognitive Optimization)

| 技能 | 用途 | 觸發信號 |
|---|---|---|
| **SKILL-03 醜陋初稿** | 強迫產出 60 分垃圾，利用糾錯本能打破完美主義 | 不夠好、還差一點、一直修 |
| **SKILL-04 影子賽車** | 屏蔽同儕比較，只對比「過去的自己」 | 別人都、他好強、我不如 |
| **SKILL-05 停損刀斧手** | 計算沉沒成本，簽發正式放棄許可證 | 做了好久、放不下、可惜 |

### RAM 外包模組 (Memory Outsourcing)

| 技能 | 用途 | 觸發信號 |
|---|---|---|
| **SKILL-06 思緒傾印** | 接收混亂輸入，自動分類與結構化 | 好亂、腦袋爆炸、資訊過載 |
| **SKILL-07 進度防腐** | 工作中斷時快速封裝脈絡，確保無縫重啟 | 被打斷、等等再說、先去忙 |

---

## 🔄 線上 ↔ 線下雙軌設計

本框架的核心特色：每一個技能都同時提供**數位版**與**實體版**的行動指令。

```
┌──────────────┐         ┌──────────────┐
│  🖥️ 線上模式  │ ◄─────► │  📋 線下模式  │
│  AI 直接操作  │         │  實體行動卡片  │
│  雲端自動存檔  │         │  便利貼 / 紙筆 │
└──────────────┘         └──────────────┘
        │                         │
        ▼                         ▼
   語音辨識 (Whisper)        拍照 OCR 回傳
   API 串接行事曆            手寫筆記數位化
   JSON 結構化存檔           口述進度回報
```

**轉換場景範例**：
- 🌙 **線上→線下**：AI 產出睡前環境佈置清單 → 使用者列印貼在書桌上
- 🌅 **線下→線上**：隔天早上完成清單打勾 → 拍照回傳 → AI 寫入 Victory Log

---

## 🚀 快速開始

### 方法一：貼入任意 AI 對話

1. 複製 `SYSTEM_PROMPT.md` 的全部內容
2. 貼入 ChatGPT / Claude / Gemini 的 System Prompt 或對話開頭
3. 開始對話，AI 會自動偵測你的狀態並調度對應技能

### 方法二：載入單一技能

如果你只需要特定功能，直接貼入對應的 `SKILL.md`：

```
# 範例：只啟用「壓力降級」
將 skills/pivot-action/SKILL.md 的內容貼入對話中
```

### 方法三：整合至 AI Agent 開發框架

每份 SKILL.md 都包含標準化的 YAML Frontmatter：

```yaml
---
name: pivot-action
skill-id: SKILL-02
module: initiation-defense
description: "壓力降級：將任務降級為 5 分鐘版本..."
trigger-signals: ["焦慮", "龐大", "好多事"]
allowed-tools: Read, Write
---
```

可直接被 Cursor Skills、LangChain Agents、AutoGPT 等框架解析與調度。

---

## 📐 SKILL.md 規格標準

每份技能規格遵循統一結構：

| 區塊 | 用途 |
|---|---|
| **YAML Frontmatter** | 機器可讀的元數據（名稱、觸發信號、工具權限） |
| **Operating Mode** | 硬性規則與禁令，防止 AI 偏離技能意圖 |
| **心理學依據** | 說明該技能背後的認知科學原理 |
| **執行流程** | Step-by-step 的介入邏輯 |
| **[ONLINE] / [OFFLINE]** | 線上數位版與線下實體版的雙軌指令 |
| **線上↔線下轉換指引** | 兩種模式之間的銜接方法 |
| **輸出格式** | AI 回應的標準化模板 |
| **Boundary Reminders** | 技能的適用邊界與失敗降級策略 |

---

## 📄 授權與歸屬

- **專案名稱**：TinyWin OS（小贏作業系統）
- **開發者**：Morton (FlowGPS)
- **版本**：v2.0
- **方法論**：QSLR (Quick Success, Little Recovery)
- **適用對象**：有拖延傾向、高敏感特質、多重潛能的行動者
