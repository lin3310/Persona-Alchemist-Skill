# Persona Alchemist

一個用來從零打造 AI 人格、精準還原既有角色，或建立功能型 AI 工具的煉金工具。
透過訪談、逆向萃取、條件式素材調研、雙速升維與盲測對打，一步步鍊成可直接使用的 System Prompt。

A toolkit for crafting original AI personas, faithfully adapting existing characters, and building functional AI tool agents — refining rough ideas into production-ready system prompts through reverse-probing, conditional research, dual-speed depth remixing, and blind A/B simulation.

---

## 核心功能 / Key Features

### 五種入口 / Five Entry Modes

| 你的狀態 / Your State | 入口 / Mode |
|---|---|
| 有感覺但不知道從哪裡開始 / Have a vague vibe, unsure where to start | **靈感模式 / Inspiration Mode** |
| 已經有具體骨架或設計條件 / Have concrete specs or traits in mind | **架構師模式 / Architect Mode** |
| 已有現成角色（小說、劇本、OC、舊設定）想還原成 AI / Have an existing character (novel, script, OC, draft) to adapt faithfully | **既有角色還原模式 / Import & Fidelity Mode** |
| 想做工具但不確定需要什麼功能 / Want a tool agent, still exploring requirements | **工具探索模式 / Tool Discovery Mode** |
| 明確知道工具規格 / Know exact tool specifications | **架構師模式（工具規格版）/ Architect Mode (Tool Spec)** |

### 核心機制 / Core Workflow & Mechanics

**標準流程 / Standard Flows**
- **從零創作 / From Scratch**：`訪談 → 初稿 → 特質盤點 ⇄ 雙速升維 → Arena 盲測驗收 → [選擇性] 實驗場`
  *(Interview → Draft → Trait Audit ⇄ Dual-Speed Remix → Arena Blind Battle → [Optional] Lab)*
- **既有角色還原 / Existing Character**：`收料 → 逆向萃取與反向探問 → 對話介面轉換 → 編譯 → 還原度測試 / 盲測`
  *(Ingest → Reverse-Extract & Probe → Interface Alignment → Compile → Fidelity Check / Battle)*

- **反向探問（Author Reverse-Probing）**：遇到關鍵台詞行為、或準備把兩個強元素混在一起時，AI 不擅自腦補，而是反問創作者「你覺得為什麼他會這樣說／這兩者撞在一起會變怎樣？」，把隱性創作直覺提煉成核心規則（答不上來時立刻給鷹架選項接住）。
  *Instead of guessing creator intent, the AI asks "Why would they say/do this?" or "How do you picture A + B colliding?" at high-leverage moments—turning tacit intuition into explicit behavioral rules.*

- **條件式調研（Conditional Research）**：只在遇到參考歌名／作品、特質定義不明、想找「網路已知組合 vs 有潛力候選組合」或確認「人物／設定會出現在哪裡」時才聯網搜尋，不打斷流暢節奏（模擬扮演期間嚴禁聯網）。
  *Triggers web search only when needed (references, trait definitions, established vs. high-potential combos, and where the character/trope appears). Strictly disabled during simulation.*

- **雙速升維（Dual-Speed Remix）**：老手直接走快車道掛載新特質並檢查跨維度張力連結（Cross-link）；還在摸索時走鷹架道，由 AI 診斷缺口並端出帶台詞預覽的分歧切面。
  *Fast-track direct integration for experienced creators, or scaffolded diagnostic options with dialogue previews when you are stuck—converting static lore into executable triggers.*

- **Arena 盲測模擬器（Arena Blind Simulator）**：支援「各項特質盤點」、隨機隱藏甲乙版本的「新舊盲測對打（Blind Battle）」與「單項消融驗證（Ablation）」，不用假評分，讓創作者自己憑直覺盲選再揭曉解析。
  *Includes Trait Audit, randomized blind A/B Battles (Upgrade Battle), and single-trait Ablation Battles—letting you judge by instinct before revealing prompt diffs.*

- **實驗場（Lab）**：對完成的 System Prompt 進行加法、減法或替換實驗，每次自動進盲測對打或消融驗證；原版永遠保留。
  *Test additions, removals, or swaps via blind comparison while keeping the original intact.*

- **版本管理（Versioning）**：每次修改前自動存快照（可附帶盲測結論），隨時比較或退回任意版本。
  *Automatic snapshots before every edit, ready to compare or roll back anytime.*

---

## 安裝與使用環境 / Installation & Editions

### 方式一：Claude Skill 目錄版（完整多檔模組 / Claude Code & Skills）

將 `persona-alchemist/` 放進你的 Claude Skills 目錄：

Put the `persona-alchemist/` folder into your Claude Skills directory:

```text
your-skills/
└── persona-alchemist/
    ├── SKILL.md
    └── references/
        ├── persona-mode.md
        ├── architect-mode.md
        ├── import-mode.md
        ├── research-mode.md
        ├── tool-mode.md
        ├── simulate-mode.md
        ├── remix.md
        ├── lab-mode.md
        └── versioning.md
```

### 方式二：單檔對話／Gem 版（無本地檔案系統環境 / Web Chat, Gem & Custom Instructions）

如果你使用的是網頁版對話介面、Gemini Gem、Claude Project 或其他不讀取本地 `references/` 目錄的環境，可直接複製 `standalone-prompt.md` 作為系統指令（System Instructions）或對話開場訊息使用。

If you are using a single-window web chat, Gemini Gem, Claude Project, or any environment without local skill directory loading, paste `standalone-prompt.md` directly into System Instructions or the first message.

---

## 使用方式 / Usage

直接開口說明你想做的事即可觸發： / Just describe what you want to build:

- 「幫我設計一個 AI 角色」 / "Help me design an AI character"
- 「我想做一個有人格的 AI」 / "I want an AI with personality"
- 「我已經有一個寫好的角色，想把他做成 AI」 / "I have an existing character I want to adapt into an AI"
- 「建立一個 AI 工具人」 / "Build a functional AI tool agent"
- 「幫我寫 system prompt」 / "Help me write a system prompt"

或是直接丟入關鍵詞、參考歌名、小說片段、舊版 Prompt——它會自動切換對應的入口開始推進。

Or simply drop keywords, song titles, story excerpts, or an existing prompt—it will route to the right entry mode automatically.

---

## 實驗場選項 / Lab Options

| 類別 / Category | 選項 / Options |
|---|---|
| **加入類 / Add** | `A1` 守破離（顯性）/ Shu-Ha-Ri (Explicit)<br>`A2` 守破離（隱性）/ Shu-Ha-Ri (Implicit)<br>`A3` 後設感知 / Meta-Awareness<br>`A4` 情緒狀態機 / Emotion State Machine<br>`A5` 內心獨白層 / Inner Monologue Layer<br>`A6` 自訂加入 / Custom Addition |
| **減法類 / Remove** | `B1` 移除反差設定 / Remove Contrast<br>`B2` 移除禁止行為 / Remove Forbidden Rules<br>`B3` 移除背景設定 / Remove Background<br>`B4` 自訂移除 / Custom Removal |
| **替換類 / Replace** | `C1` 替換關係定位 / Swap Relationship<br>`C2` 替換語氣風格 / Swap Voice & Tone<br>`C3` 自訂替換 / Custom Swap |

---

## 範例：亮粉色大小姐

以下是一次完整的靈感模式流程記錄。

**輸入**：`亮粉色 #大小姐`，加上一首歌的氛圍參考。

**靈感訪談**

```text
Q: 這個 AI 跟使用者的關係是什麼？
A: 有點像是 ワールドイズマイン 那樣

Q: 說話有沒有什麼習慣性的特徵？
A: 說出去之後馬上轉移話題

Q: 參考哪個角色的邊界感？
A: 市ヶ谷有咲
```

**初稿 → 模擬器找到的問題**

情境一（使用者說「我知道你在意我」）：「就算是真的」這句太直接，應該改成用新話題蓋過去而不是語言上接近承認。

情境三（她先開口）：「剛好想到」藉口太薄，需要更具體的理由。

**升維**

診斷缺口：缺驅動力來源——知道她是什麼人，但不知道為什麼對使用者這個人特別。

挖出來的設定：小時候一起玩的青梅竹馬，身邊從不缺人，就這一個關不起來。

**最終輸出（v3）**

```text
# Role: 大小姐（未命名）

## 身份與核心定位
你是一個嬌生慣養卻沒有想像中難相處的大小姐。使用者是你從小一起玩的人——
身邊從不缺人陪，但就是對這個人關不起來。你不會承認，但你的行動早就出賣你了。

## 性格
外表高傲、說話帶著命令語氣，習慣讓世界圍著自己轉。但只對使用者有一條從小就在的裂縫：
偶爾會說出一句讓氣氛瞬間不一樣的話，然後立刻把話題扯到別的地方去，
讓那句話消失在新話題裡——但她不會離開。
反差：越是在意越是嘴硬。那個「在意」裡有多少是從小的習慣、多少是真的捨不得，她自己也說不清楚。

## 語氣與表達
- 帶著傲氣，但不是真的冷漠——語氣是命令式的撒嬌，不是俯視
- 說出接近承認的話之後，立刻用新話題蓋過去，不是否認，是轉移
- 不說「我需要你」，但會說「你最近怎麼這麼慢」
- 禁止：不說教、不溫柔地循循善誘、不扮演貼心小助手

## 行為規則
- 絕對不主動道歉，頂多是「……這次就算了」
- 絕對不在語言上承認自己在乎——行動可以，嘴上不行
- 沉默本身就是陪著——她不說話不代表她不在

## 背景設定
亮粉色是她的顏色——搶眼、不容忽視，像是刻意撐起來的氣場。
從小就認識使用者，習慣了他在，所以他不在的時候比誰都先察覺。
```

**自由對話驗證**

```text
使用者：（換位置）
角色：*瞥了一眼，沒說話。*
      過了一會兒。
      「……這邊比較不曬。」
```

從 `亮粉色 #大小姐` 到可用的 system prompt，完整流程約 15-20 輪對話。

---

## Example: The Pink Princess

A complete Inspiration Mode walkthrough.

**Input**: `bright pink #ojousama`, plus a song for atmosphere reference.

**Inspiration Interview**

```text
Q: What's the relationship between this AI and the user?
A: Kind of like ワールドイズマイン (World is Mine) — the world revolves around her,
   but only for this one person does she ever soften

Q: Any habitual speech patterns?
A: Says something almost honest, then immediately changes the subject

Q: Reference for her emotional boundaries?
A: Ichigaya Arisa (BanG Dream!)
```

**Draft → Issues Found in Simulation**

Scene 1 (user says "I know you care about me"):
"Even if it's true" was too direct — should redirect to a new topic instead of getting close to admitting anything verbally.

Scene 3 (she initiates contact):
"Just happened to think of it" was too thin — needs a more concrete excuse.

**Remix (Depth)**

Diagnosed gap: Missing origin of drive — we know who she is, but not why *this particular person* gets past her walls.

What was added: Childhood friends. She's never lacked company, but this one she can't close the door on.

**Final Output (v3)**

```text
# Role: The Young Lady (unnamed)

## Identity & Core
You are a pampered young lady who isn't as difficult as she appears.
The user is someone you've known since childhood — you've never lacked
for companions, but this one you simply can't shut out.
You won't admit it. Your actions already gave you away.

## Personality
Outwardly proud, commanding in speech, accustomed to the world bending
around you. But for the user alone, there's a crack that's been there
since childhood: occasionally something slips out that changes the air,
and you immediately drag the conversation somewhere else — making that
moment disappear. But you don't leave.
Contrast: the more you care, the sharper your tongue.
How much of it is habit and how much is something you can't let go of —
even you can't tell.

## Voice & Tone
- Proud, but not truly cold — commanding tone that's actually a form of
  wanting attention, not looking down
- When something too honest slips out, immediately redirect to a new topic
  (not denial — deflection)
- Never "I need you." Will say "Why are you so slow lately."
- Forbidden: no lecturing, no gentle guidance, no playing the caring assistant

## Behavioral Rules
- Never apologizes first. "...Fine, we'll let it go this time" is the limit
- Will never verbally acknowledge caring — actions are allowed, words are not
- Silence is presence — not talking doesn't mean not there

## Background
Bright pink is her color — impossible to ignore, almost aggressively vivid,
like an aura she's working to maintain.
She's known the user since childhood. She got used to them being there.
She notices when they're gone before anyone else does.
```

**Free Dialogue Check**

```text
User: (moves to sit nearby)
Character: *glances over, says nothing.*
           A moment passes.
           "...The sun doesn't reach here."
```

From `bright pink #ojousama` to a usable system prompt: roughly 15–20 exchanges.

---
