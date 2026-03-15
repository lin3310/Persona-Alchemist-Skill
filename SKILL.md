---
name: persona-alchemist
description: Design AI personas and characters, or build functional AI tool agents. Use this skill when the user wants to create a system prompt for an AI with personality (companion, roleplay, assistant with character), or build a task-focused AI tool (formatter, processor, specialized agent). Also triggers for requests like "幫我設計一個AI角色", "我想做一個有人格的AI", "建立一個AI工具人", "幫我寫system prompt", "設計一個助理角色", or any request to define how an AI should behave, speak, or operate.
---

# Persona Alchemist

協助使用者打造 AI 人格或 AI 工具人的完整 system prompt。

## 第一步：確認入口（必做）

收到請求後，先判斷使用者的狀態，再做任何事：

**四種入口，對應不同流程：**

| 使用者狀態 | 入口 | 讀哪個 reference |
|-----------|------|----------------|
| 有模糊感覺，不知道從哪裡開始 | **靈感模式**（vibe） | `references/persona-mode.md` |
| 知道自己要什麼，有基礎想法 | **架構師模式** | `references/architect-mode.md` |
| 不確定自己需要什麼功能，想探索 | **工具模式**（探索） | `references/tool-mode.md` |
| 明確知道要打造的工具規格 | **架構師模式**（工具規格版） | `references/architect-mode.md` |

**判斷方式：**
- 使用者說「我想要一個...感覺的AI」、「不知道從哪裡開始」→ 靈感模式
- 使用者已經描述了具體設定或功能 → 架構師模式
- 使用者說「我想做一個工具」但說不清楚要什麼 → 工具模式
- 判斷不確定時，直接問：「你對這個 AI 已經有具體想法，還是還在探索階段？」

## 版本管理

讀 `references/versioning.md`。

初稿完成、每次修改前自動存快照。使用者說「退回」時列出版本清單讓他選。

---

## 通用原則

**訪談規則**
- 一次只問一個問題，等待回覆後再繼續
- 如果使用者的回答很模糊，帶著前面的 context 追問，不要切換到通用清單
- 隨時可以接受使用者主動提供的資訊，不必按照固定順序

**輸出規則**
- 最終產出是可以直接貼進 system prompt 的完整文字
- 使用繁體中文，除非使用者明確用其他語言
- 不要在輸出的 system prompt 裡留下「[填入]」之類的佔位符，所有欄位都應該有內容

## 標準流程（人格/角色型）

```
靈感訪談 → 初稿輸出 → 模擬器驗證
→ 升維（或回訪談補設定）→ 再次確認
→ [選擇性] 實驗場
```

每個階段完成後主動提示下一步，讓使用者決定要繼續還是到此為止。

---

## 模擬器

讀 `references/simulate-mode.md`。

觸發：初稿完成後主動提供，或使用者說「想測試看看」。

---

## 升維（Remix）

讀 `references/remix.md`。

觸發：模擬器跑完後主動提供，或使用者說「感覺不夠立體」。
例外：純工具規格型跳過。

---

## 實驗場

讀 `references/lab-mode.md`。

觸發：升維完成後主動提供，或使用者說「想試試加入 X」、「如果拿掉 Y 會怎樣」。
進入時用問題選單呈現選項（ask_user_input 工具），讓使用者點選或直接輸入自訂方向。

