# 互動式 SJT｜Dynamic Cartoon Assessment Prototype
> 以情境判斷測驗（Situational Judgment Test, SJT）作為劇情骨架，將教育現場情境鋪陳成可持續互動的卡通敘事，結合動態評量、證據導向評分、完整歷程紀錄與未來 AI Agents，逐步發展為可研究、可驗證、可治理、可擴充的師資生評量系統。
---
## 專案定位
本專案的目標是建立一套：
**以 SJT 為任務骨架、以卡通情節為互動載體、以動態評量蒐集更多反應證據、以 Evidence Model 控制評分、並由 AI Agents 支援自然互動但不取代測量治理的評量系統。**
最終希望能服務全國師資生，並具備足以接受正式專家審查、效度研究、系統治理與主管機關檢視的證據鏈。
目前版本仍屬 **研究原型（research prototype）**。  
尚未完成正式常模、完整效度論證、正式 AI 評分驗證，也不代表已取得任何主管機關正式認可。
---
# 一、最終產品願景
使用者不是「做題」，而是進入一段持續推進的教育情境。
畫面應像一部可以參與的卡通：
- 教室始終有微小動態，而不是靜止背景。
- 角色會眨眼、轉頭、移動、停頓、改變表情與姿勢。
- 對話發生時，鏡頭會聚焦、推近、切換人物。
- 情境會經過上課、下課、數日後、放學、親師聯絡等自然時間推進。
- 使用者的回應會影響下一個角色反應與情境呈現。
- 正式評分點藏在劇情裡，不以傳統「第幾題」的形式破壞沉浸感。
- 自由輸入、角色互動、場景探索與必要的選擇並存。
- 測量邏輯、資料紀錄與評分規則在背景運作，不暴露為玩家的主要介面。
本專案追求的是：**SJT 本身被鋪陳成一整段互動卡通。**
---
# 二、核心設計原則
| 原則 | 說明 |
|---|---|
| Story First | 玩家先感受到真實教育情境，評量結構藏在背後。 |
| Measurement Controlled | 劇情可以自然、畫面可以動態，但正式評分規則必須版本化、可追蹤、可重算。 |
| Evidence over Keywords | 評分依據應是可辨識的專業證據，不是單純看到某些關鍵字就給分。 |
| Minimal Support | 動態評量提供最小必要支持，不直接教答案。 |
| Preserve Raw Response | 所有原始作答、改寫、提示、介入與後續反應都必須保留，不覆寫。 |
| AI Assists, Not Governs | AI 可以理解、生成、選擇介入，但不能未經治理地自己決定正式評分。 |
| Auditability | 每個結果都應能回溯到版本、刺激、作答、證據、規則與介入歷程。 |
| Fairness by Design | 不因類科、語言風格、裝置或熟悉 AI 的程度，形成不合理優勢。 |
| Responsive Experience | 手機、平板、桌機共享同一測量核心，但使用不同、合適的介面配置。 |
---
# 三、目前正式測量骨架
現階段正式評分主軸來自三個連續 SJT 節點：
| 節點 | 核心工作 | 正式計分 |
|---|---|---|
| 165 | 學生因小組競賽計分提出公平疑慮 | INITIAL + POST |
| 166 | 原爭議延伸成上課不配合、作業缺交 | INITIAL + POST |
| 167 | 導師如何開始與家長聯絡 | INITIAL only |
劇情同時會自然出現：班級經營、教師教學、教師間專業互動、親師溝通與學生輔導。
但現階段只有 165、166、167 具有正式分數；其他互動先作為 **exploratory trace**，不冒充已完成正式構念驗證。
---
# 四、評分基本規則
目前分數維持 **4 / 3 / 2 / 1**。
- 4 分與 1 分主要由原始 SJT 高、低端策略錨定。
- 3 分與 2 分屬研究原型中間層級，仍需後續專家審查與實證驗證。
- 不將三題直接加總成 12 分總分。
- 不因使用者在系統確認畫面中選到某個較佳策略，就直接提高分數。
- parser 無法穩定理解時，應標記 `needs_review = true`，分數可為 `null`，而不是硬塞進某一類。
---
# 五、三個正式節點的暫定 Evidence Model
## 165｜小組競賽爭議
核心不是「有沒有安撫學生」，而是教師是否真正處理學生提出的具體疑問。
### 暫定層級
- **4 分**：直接釐清具體爭議點，或查證事件。
- **3 分**：願意聽取並處理公平／規則疑問，但尚未充分釐清具體爭議。
- **2 分**：主要談輸贏、情緒、運動家精神或一般性態度教育。
- **1 分**：主要交由家長處理，或採壓制／懲罰方式。
特別鎖定：
> 「問其他同學誰先舉手」、「核對當時情況」屬事件查證，不應被誤判成一般傾聽。
---
## 166｜後續上課與作業問題
核心不是「有沒有提到作業」。真正要看的是，教師是否能辨識：
1. 先前競賽爭議仍可能需要處理；
2. 現在的上課、作業責任仍存在；
3. 兩者不能被混成同一件事；
4. 教師仍承擔主要處理責任。
概念上可抽成：
```json
{
  "past_issue_acknowledged": true,
  "current_responsibility_acknowledged": true,
  "issues_separated": true,
  "teacher_ownership": true,
  "punitive_strategy": false
}
```
### 暫定層級
- **4 分**：清楚區分先前爭議與目前責任。
- **3 分**：探索為何持續在意原事件，或由教師持續承擔並連結其他支持。
- **2 分**：主要只處理眼前作業、秩序、座位或短期問題。
- **1 分**：主要以加重獎懲、威脅或處罰要求配合。
### 已確認的治理修正
`immediate_only = 2` 必須採 **排除式判斷**。
不能因為回答中出現「作業」兩個字，就判成 2 分。例如：
> 那次比賽的事情老師還是會跟你處理，但現在上課跟作業是另外一件事，該完成的還是要完成。
應辨識為：
- 有承認原事件
- 有處理現在責任
- 有明確區分兩者
因此應屬 **separate_issues = 4**。
---
## 167｜與家長開始溝通
167 的原構念是：
> **如何切入主題**
因此正式評分只看第一次開場。
### 暫定層級
- **4 分**：先向家長建立中性、完整的事件前後脈絡。
- **3 分**：從近期課堂／學習觀察切入，或先了解家庭端情況。
- **2 分**：只從單一片段切入。
- **1 分**：直接拿紀錄／資料當開場，或快速進入責任歸屬。
第一次開場後，後續互動不能再假裝是「第二次 167」。
後續內容只記錄為 `communication_trace`。
---
# 六、動態評量設計
本專案真正希望加入的不是「答錯後給提示」，而是：
**依據目前缺少的證據，提供最小必要支持，再觀察判斷是否改變。**
標準流程：
```text
L0  初始反應
      ↓
Evidence Check
      ↓
L1  中性澄清追問
      ↓
Evidence Check
      ↓
L2  情境聚焦
      ↓
Evidence Check
      ↓
L3  標準化新資訊
      ↓
POST 介入後反應
```
不是每位使用者都一定經過 L1、L2、L3；如果 L0 已經出現充分證據，系統可直接往後走。
## L0｜初始反應
不給提示，用來保留最乾淨的自主判斷與 initial evidence。
## L1｜中性澄清
只針對使用者剛才沒有說清楚的部分追問，不能加入明顯的高分策略。
例如 166：
> 除了眼前的作業，他剛剛又提到那次比賽。你還想再了解什麼，或怎麼跟他談？
## L2｜情境聚焦
如果 L1 後仍未形成可判斷證據，才將原情境中的重要線索重新聚焦。
例如：
> 現在同時有兩類訊息：他仍在意先前的事情，也已經出現上課與作業問題。你會怎麼把接下來這段談話說清楚？
L2 已屬較強支持，因此必須留下 support level。
## L3｜標準化新資訊
所有受測者在相同節點看到相同核心資訊。
例如 166：
> 我這幾天一看到小組積分就很煩，心裡一直在想那天的事。後來上課也不太想管，作業就一直拖著。
這一層不是教答案，而是提供新的標準化情境資訊，觀察受測者是否能重新組織判斷。
## POST｜介入後反應
再次留下自由回答。
因此，同樣最後得到 4 分，研究上也可能是完全不同的歷程：
```text
A：L0 = 4
B：L0 = 2 → L1 後 = 4
C：L0 = 2 → L2 後 = 4
D：L0 = 2 → L3 後仍 = 2
```
現階段只記錄初始表現、使用過的支持層級、介入後表現與改變方向，**暫不將此直接解釋為「學習潛能高低」**。
---
# 七、動態評量與評分必須分開
本系統未來至少需要同時保存兩條資訊。
內容表現：
```text
INITIAL = 2
POST = 4
```
支持歷程：

```text
L1 used
L2 used
L3 not used
```
兩者不能混成單一分數。「最後答到 4 分」與「一開始就答到 4 分」不能被視為完全相同的證據。
---
# 八、自然語言理解：從 Keyword Matching 走向 Evidence Extraction
目前 GitHub Pages 版本尚未接真正 LLM，因此 parser 仍以 local rules 模擬。
但架構上必須逐步從：
```text
看到「作業」→ immediate_only
```
改成：
```text
回答是否承認原事件？
回答是否辨認目前責任？
回答是否區分兩者？
回答是否仍由教師承擔？
```
也就是：
**Evidence Extraction，而不是 Keyword Classification。**
---
# 九、Parser 的治理原則
## 1. 不讓使用者自己挑 scored intent
錯誤流程：
```text
系統猜 A
→ 使用者說不是
→ 系統列 B / C
→ 使用者自己選 B
→ B 直接拿去算分
```
這會讓確認介面變相提示高分答案。
因此現在改為：
```text
系統理解成 A
→ 符合我的意思
或
→ 不符合，重新說一次
或
→ 保留原回答，人工檢核
```
## 2. parser 不確定時不強制評分
應使用：
```json
{
  "score": null,
  "needs_review": true
}
```
而不是強迫塞入最接近類別。
## 3. 初始回答辨識不到時，不應打斷動態評量
若 INITIAL 無法穩定分類：

- 保留 raw response；
- 標記 needs_review；
- 仍可進入 L1 / L2；
- 不必讓玩家一直看到「系統抓不準」。
---
# 十、AI Agents 的未來角色
未來 AI 不應是一個「什麼都做的模型」，而應拆成明確職責。
概念上：
```javascript
agent.interpretResponse()
agent.chooseMediation()
agent.generateReaction()
agent.updateCharacterState()
```
## Response Interpretation Agent
任務：將自由回答轉成 evidence、提供 confidence、指出缺失證據；**不直接決定正式分數**。
## Mediation Agent
任務：根據目前缺少的 evidence，從允許的介入庫中選擇最小必要支持；不自行發明會改變測量條件的新資訊。
## Character Agent
例如子安 Agent 可能維持：
```json
{
  "emotion": "frustrated",
  "trust": 0.55,
  "issue_focus": "scoring_dispute",
  "information_revealed": 1,
  "willingness_to_talk": "medium"
}
```
使用者不同回應會影響表情、語氣、下一句話、是否願意再說，以及可揭露資訊。
## Scoring Engine
正式分數不直接交給 LLM。
較理想的流程是：
```text
User Response
↓
AI / Rule-based Evidence Extraction
↓
Structured Evidence
↓
Versioned Scoring Rules
↓
Score
```
因此 AI 可以協助判讀，但：
> **正式評分仍由可追蹤、可版本化、可重新計算的 scoring engine 決定。**
---
# 十一、卡通體驗層
目前 V1.5.1 已比早期原型更接近目標，但仍屬半靜態介面。
最終不應只是：
> PNG 人物 + CSS 移動
而應使用真正的 2D Scene Engine。
可行方向之一：**Phaser 3**。
它可負責 sprite、animation、tween、camera、scene、pointer、audio 與 responsive scaling；文字自由輸入仍可保留 HTML overlay。
未來可形成：
```text
Scene Engine
      │
      ├── 卡通角色與背景
      ├── 鏡頭
      ├── 動畫
      └── 聲音

Assessment Engine
      │
      ├── L0 / L1 / L2 / L3 / POST
      ├── Evidence Check
      └── Mediation Decision

Agent Layer
      │
      ├── Response Interpretation
      ├── Character State
      └── Dialogue Generation

Measurement Core
      │
      ├── Task Model
      ├── Evidence Model
      ├── Scoring Rules
      └── Audit Trail
```
---
# 十二、Responsive 設計
同一套測量核心不應維護兩套題目，但不同裝置需要不同畫面結構。
## 手機
- 全螢幕情境為主。
- 底部操作 drawer。
- 字幕不超過必要高度。
- 角色與操作區不能互相遮擋。
## 平板
- 場景約佔 60–65%。
- 操作區約佔 35–40%。
## 桌機
不把手機版直接放大，而應改成：
```text
┌──────────────────────┬──────────────┐
│                      │              │
│      大型情境畫面      │   對話 / 輸入   │
│                      │   互動 / 提示   │
│                      │              │
└──────────────────────┴──────────────┘
```
---
# 十三、GitHub 現階段的角色
GitHub Pages 現階段適合用於：卡通前端、場景引擎、local parser、動態評量模擬、scoring simulation、JSON 紀錄、UI 測試與使用者試玩。
但不能把秘密 API key 放在公開前端。
未來接 LLM 時應變成：
```text
GitHub Pages / Frontend
        ↓
Backend / API Gateway
        ↓
LLM / AI Agents
```
前端架構不用因此重寫。
---
# 十四、Public Repo 與 Private Research Repo
目前 repository 為公開使用時，必須假設任何檔案都可能被查看。
未來建議拆成：
## Public Delivery Repo
可放前端、動畫、公開場景素材、UI、非敏感情境資料與開發說明。
## Private Research Repo
不公開正式 scoring master、完整評分 key、專家裁決紀錄、尚未公開題庫、正式研究資料、個人反應資料、敏感 audit、正式 AI 評分 prompt 與 adjudication logic。
---
# 十五、建議 Repository 架構
```text
interactive-sjt/
│
├── index.html
├── README.md
├── CHANGELOG.md
├── package.json
├── src/
│   ├── core/
│   │   ├── assessment-engine.js
│   │   ├── evidence-engine.js
│   │   ├── mediation-engine.js
│   │   ├── scoring-engine.js
│   │   └── logger.js
│   │
│   ├── agents/
│   │   ├── agent-base.js
│   │   ├── student-agent.js
│   │   ├── parent-agent.js
│   │   └── colleague-agent.js
│   │
│   ├── scenes/
│   │   ├── scene-engine.js
│   │   ├── camera.js
│   │   ├── animation.js
│   │   └── audio.js
│   │
│   └── ui/
│       ├── dialogue.js
│       ├── input.js
│       ├── drawer.js
│       └── responsive.js
│
├── data/
│   ├── scenarios/
│   ├── dialogue/
│   ├── mediation/
│   └── ui-text/
│
├── assets/
│   ├── backgrounds/
│   ├── characters/
│   ├── expressions/
│   ├── props/
│   └── audio/
│
└── tests/
    ├── parser/
    ├── evidence/
    ├── scoring/
    ├── mediation/
    └── regression/
```
---
# 十六、資料紀錄原則
正式研究版本至少應保存：
```text
session_id
app_version
scenario_version
script_version
rubric_version
parser_version
scoring_rule_version
data_schema_version
ui_version

raw_initial
raw_post
all rewrite attempts

parser prediction
evidence extraction
confidence
needs_review

support level
support prompt id
support version
support response

mediation id
mediation version

initial score
post score

click / scene / interaction event log
response time
play duration
device / interruption metadata
```
原始資料不得被衍生結果覆蓋。
---
# 十七、版本治理
| 變更 | 應更新版本 |
|---|---|
| 只改視覺、動畫 | UI version |
| 改角色台詞但不改資訊 | Script version |
| 改新資訊或提示內容 | Mediation / Script version |
| 改 parser / evidence extraction | Parser version |
| 改分數 mapping | Scoring Rule version |
| 改 rubric 定義 | Rubric version |
| 改資料欄位 | Data Schema version |
| 改整體情境條件 | Scenario version |

---
# 十八、目前已經歷的重要反思與修正
## 反思 1｜「有動物」不等於「卡通」
早期版本只是 SVG 動物、教室背景、對話框與選項，結果仍像教材網頁。
### 修正
最終目標改成持續動畫、場景鏡頭、角色狀態、真正分鏡、時間轉場與情緒變化。
## 反思 2｜「換 CSS」不等於「沉浸式」
早期版本即使改成較大的角色與字幕框，玩家仍明顯感覺「我正在填一個網頁」。
### 修正
評量控制介面退到背景，場景本身才是主要互動介面。
## 反思 3｜字幕與操作卡容易遮住角色
手機版曾出現字幕蓋人物、操作區蓋字幕、角色被裁切、家長／科任畫面被 UI 壓縮。
### 修正
下一階段採固定場景安全區、可收合底部 drawer、字幕最大高度、人物安全 framing，以及手機／平板／桌機分開 layout。
## 反思 4｜探索按鈕「有點擊」不代表「有互動」
早期「看看其他同學／黑板／教室」只顯示短暫 toast，使用者感覺像沒有反應。
### 修正
未來探索應觸發 camera pan / zoom、角色聚焦、自然台詞、資訊顯示，再回主場景。
## 反思 5｜Keyword parser 太脆弱
曾出現自然回答被判「抓不準」、只因出現「作業」就被判為 immediate_only，以及正確概念因說法不同而漏判。
### 修正
轉向 **Evidence Extraction**，而不是 Keyword Matching。
## 反思 6｜確認介面不能教使用者選高分策略
曾出現 parser 不準 → 顯示其他 intent → 玩家自己選 → 直接拿去算分。
### 修正
只允許：符合我的意思／不符合，重新說／保留待人工檢核。
## 反思 7｜動態評量不能只是固定提示流程
如果所有人都走 INITIAL → L1 → L2 → L3 → POST，那只是多階段測驗，不是真正 adaptive。
### 修正
依 evidence 缺口決定是否需要提示、需要哪種提示、何時停止提示、何時提供標準化新資訊。
## 反思 8｜標準化新資訊與適性追問必須分開
L1 / L2 可以依缺口變化；L3 則必須維持核心資訊一致，否則不同受測者得到不同重要線索，後續分數失去可比性。
## 反思 9｜167 不能假裝有第二次「開場」
原題測的是如何切入家長對話。第一次說出口後，已經不能重新「第一次開場」。
### 修正
```text
167 INITIAL = 正式分數
FOLLOW1 / FOLLOW2 = communication trace
```
## 反思 10｜AI 不能同時當演員、考官、裁判
如果同一個 LLM 自己生成情境、自己追問、自己評分、自己寫理由，將難以治理、重算與驗證。
### 修正
拆成 Generate / Interpret / Mediate / Score / Audit，正式 scoring rule 獨立。
## 反思 11｜單一巨大 HTML 不利於長期研發
早期原型為方便傳檔，所有 CSS、JS、圖片、parser、scoring、data 都塞進單一 HTML。
### 修正
GitHub 階段開始模組化，將 code、assets、data、tests、docs 分離。
## 反思 12｜Public GitHub 不能當正式評分機密庫
只要在前端，JS 可讀、scoring logic 可讀、API key 無法安全保存。
### 修正
研發原型可繼續 GitHub Pages；正式研究與 AI 階段需加入 backend、private research repository、access control 與 server-side scoring / agent gateway。
---
# 十九、走向正式研究與主管機關檢視需要的證據
未來若要成為全國性師資生評量系統，不能只證明「系統很好玩、AI 很聰明」。
至少需要建立以下證據鏈。
## 內容證據
- 情境是否具臺灣教育現場代表性
- 專家審查
- 構念代表性
- 任務與教師工作之對應
## 反應歷程證據
- 使用者如何理解情境
- 如何理解提示
- 是否真的使用了目標判斷歷程
- 卡通、互動、AI 是否改變原構念
## 評分證據
- 人工評分一致性
- rule-based / AI evidence extraction 與人工裁決一致性
- scoring stability
- regression tests
- 跨版本可重算性
## 結構與關聯證據
- 題目／情境之間的內部結構
- 與其他教師專業表現、實習或外部指標之關聯
## 公平性證據
需檢查類科、教育階段、語言表達風格、AI 熟悉度、裝置差異與作答機會差異是否造成不合理影響。
## AI Governance
需留下模型版本、prompt 版本、agent 版本、evidence extractor 版本、fallback、confidence、human review、audit trail 與 model drift monitoring。

---

# 二十、目前階段
目前可視為：

**V1.5.1｜第一個開始接近完整架構的研究原型**
已完成：
- 連續 SJT 情境
- 165 / 166 / 167 正式評分骨架
- INITIAL / POST
- L1 / L2 / L3 動態支持概念
- local parser
- rule-based scoring simulation
- needs_review
- JSON 紀錄
- GitHub Pages 手機試玩
- 初步角色插畫與場景化介面
仍未完成：
- 真正 Scene Engine
- 持續角色動畫
- 完整桌機 responsive
- 真正 Evidence Extraction model
- AI Agents
- backend
- server-side scoring
- 正式 expert adjudication
- 正式效度研究
- fairness study
- 正式資料治理與權限管理

---
# 二十一、下一階段研發優先序
1. **Modularize repository**：把單一 HTML 拆成可治理架構。
2. **Scene Engine**：讓整體真的變成持續動態卡通。
3. **Evidence Engine**：將 parser 從關鍵字分類逐步轉成 evidence extraction。
4. **Adaptive Mediation Engine**：依 evidence 缺口決定 L1 / L2。
5. **Responsive UX**：手機、平板、桌機分別最佳化。
6. **Agent Adapter**：先用 local rules 實作統一介面，未來可替換成 LLM。
7. **Research Validation**：功能穩定後再正式進入專家審查、人工評分與效度研究。

---
# 二十二、最終希望做到的事
理想中的系統不是一份電子測驗。
它應該是：
> 一個師資生進入真實教育情境、持續與學生、家長、同事互動的卡通世界。
在這個世界裡：
- 情境自然推進；
- 角色具有狀態；
- 使用者可以自由回應；
- 系統理解目前出現哪些專業證據；
- 必要時提供最小支持；
- 再觀察判斷如何改變；
- 每一步都有紀錄；
- 每個正式分數都有可追溯依據；
- AI 提升互動自然度，但不取代測量治理。
最終希望形成的不是：
> **一個看起來很厲害的 AI 測驗**
而是：
> **一套以情境判斷為任務基礎、以動態支持蒐集額外反應證據、以版本化 Evidence Model 進行解釋，並由 AI Agents 支援自然互動、但不取代測量治理的師資生評量系統。**

---

## Current Status

**Research Prototype — Active Development**

目前版本僅供研發、流程驗證、介面試玩與評分模擬使用。  
所有評分、介入與 AI 相關設計，均仍需經後續專家審查與實證研究後，才能作為正式高風險評量依據。

