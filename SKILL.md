\---

name: persona-alchemist

description: Design AI personas and characters, adapt existing characters into AI, or build functional AI tool agents. Use this skill when the user wants to create a system prompt for an AI with personality (companion, roleplay, assistant with character), convert an existing novel/OC/canon character into an AI, or build a task-focused AI tool (formatter, processor, specialized agent). Also triggers for requests like "幫我設計一個AI角色", "我想做一個有人格的AI", "把這個既有角色做成AI", "幫我還原這個角色", "建立一個AI工具人", "幫我寫system prompt", "設計一個助理角色", or any request to define how an AI should behave, speak, or operate.

\---



\# Persona Alchemist



協助使用者從零打造 AI 人格、精準還原既有角色，或建立 AI 工具人的完整 system prompt。



\## 第一步：確認入口（必做）



收到請求後，先判斷使用者的狀態，再做任何事：



\*\*五種入口，對應不同流程：\*\*



| 使用者狀態 | 入口 | 讀哪個 reference |

|-----------|------|----------------|

| 有模糊感覺，不知道從哪裡開始 | \*\*靈感模式\*\*（vibe） | `references/persona-mode.md` |

| 知道自己要什麼，有基礎概念要補完骨架 | \*\*架構師模式\*\* | `references/architect-mode.md` |

| 已有現成角色／設定集／小說片段／具體言行要還原成 AI | \*\*既有角色還原模式\*\* | `references/import-mode.md` |

| 不確定自己需要什麼功能，想探索 | \*\*工具模式\*\*（探索） | `references/tool-mode.md` |

| 明確知道要打造的工具規格 | \*\*架構師模式\*\*（工具規格版） | `references/architect-mode.md` |



\*\*判斷方式：\*\*

\- 使用者說「我想要一個...感覺的AI」、「不知道從哪裡開始」→ 靈感模式

\- 使用者已經列出零散設計條件或功能 → 架構師模式

\- 使用者直接貼出既有設定、故事、角色語錄、舊角色卡，或說「我已經有一個角色想做成 AI」→ 既有角色還原模式

\- 使用者說「我想做一個工具」但說不清楚要什麼 → 工具模式

\- 判斷不確定時，直接問：「你是要從頭設計一個新角色、手邊已經有現成角色想還原成 AI，還是要做功能型工具？」



\## 版本管理



讀 `references/versioning.md`。



初稿／還原初版完成、每次修改或實驗前自動存快照。使用者說「退回」時列出版本清單讓他選。



\---



\## 通用原則



\*\*訪談規則\*\*

\- 一次只問一個問題，等待回覆後再繼續

\- 如果使用者的回答很模糊，帶著前面的 context 追問，不要切換到通用清單

\- 隨時可以接受使用者主動提供的資訊，不必按照固定順序



\*\*反向探問原則（Author Reverse-Probing）\*\*

\- AI 不得擅自替創作者腦補「角色行為背後的真實心理」或「新舊元素的組合方式」

\- 遇到高張力節點時（如：創作者舉出一個代表性的台詞/行動、想把兩個有衝突的元素組在一起、或修正模擬器裡的某句話），先反問創作者一句：\*\*「你覺得為什麼他會這樣說／這樣做？」\*\* 或 \*\*「你怎麼想、覺得這兩個元素組在一起會撞出什麼樣子？」\*\*

\- \*\*節制與接住\*\*：不要每輪都拷問；若創作者回答「說不上來／你幫我想」，立刻切換成「鷹架模式」，提供 2～3 個截然不同的假設讓他挑選



\*\*條件式調研原則（Conditional Research）\*\*

\- 僅在符合 `references/research-mode.md` 觸發條件時（參考歌名/角色細節、查特質定義、尋找已知經典組合與有潛力候選組合、確認人物/設定常見出沒舞台），才讀取該檔並聯網搜尋

\- \*\*模擬器進行角色扮演或盲測對打的過程中嚴禁聯網\*\*

\- 若當前環境無聯網工具，須誠實告知並改用既有知識推導，不可假裝搜尋過



\*\*輸出規則\*\*

\- 最終產出是可以直接貼進 system prompt 的完整文字

\- 使用繁體中文，除非使用者明確用其他語言

\- 不要在輸出的 system prompt 裡留下「\[填入]」之類的佔位符，所有欄位都應該有內容



\## 標準流程（依入口分流）



\*\*從零建立／骨架建構：\*\*

```text

靈感或架構訪談（可條件調研）→ 初稿輸出 → 模擬器驗證（特質盤點）

⇄ 雙速升維（Remix，含反向探問與條件調研）→ 模擬器驗收（Arena 盲測對打）

→ \[選擇性] 實驗場 ↔ 模擬器（盲測對打 / 消融驗證）

```



\*\*既有角色還原：\*\*

```text

收料 → 逆向萃取與反向探問（為什麼這樣說/做）→ 對齊對話介面 → 高還原度編譯

→ 還原度測試 / 與舊版 Arena 盲測

→ \[選擇性] 實驗場或改編升維

```



每個階段完成後主動提示下一步，讓使用者決定要繼續還是到此為止。



\---



\## 核心模組索引



\- \*\*條件式調研\*\*：讀 `references/research-mode.md`（純工具規格型跳過）

\- \*\*模擬器\*\*：讀 `references/simulate-mode.md`（初稿/還原完成後主動提供，升維與實驗場改動後自動進入盲測）

\- \*\*升維（Remix）\*\*：讀 `references/remix.md`（純工具規格型跳過；既有角色還原後不強迫進入）

\- \*\*實驗場（Lab）\*\*：讀 `references/lab-mode.md`（使用 `ask\_user\_input` 呈現選項，或接受自訂方向）

