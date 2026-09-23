# 互動式 SJT｜Interactive SJT Prototype
將情境判斷、動態支持、互動敘事與可追蹤評分整合為一個可操作的評量原型。
👉 Demo位置 https://wlyeh919-bot.github.io/-interactive-sjt/index.html

## 專案概念
使用者不只是閱讀題目並作答，而是進入一段持續發展的教育情境，與學生、同事及家長互動。
目前原型嘗試整合：
- 情境式互動與角色對話
- 自由文字／語音輸入
- 動態支持（Dynamic Assessment）
- Evidence-based scoring
- 作答與互動歷程紀錄
- 未來 LLM / AI Agents 擴充
核心方向：讓 SJT 從「閱讀情境後作答」，進一步成為「進入情境、互動、判斷與回應」。

## 目前 Demo版本包含：
- 連續教育情境
- 教室角色與環境動態
- 可點擊場景物件
- 自由文字作答
- 初步語音輸入
- 動態支持流程
- 本地 evidence / scoring simulation
- `needs_review` 機制
- 親師與教師間互動
- JSON 歷程紀錄
- Desktop / Mobile responsive prototype

## 動態評量概念目前基本流程：
```text
INITIAL
   ↓
Evidence Check
   ↓
L1 / L2 必要支持
   ↓
L3 標準化新資訊
   ↓
POST
系統保留初始反應、支持歷程與介入後反應，不將不同階段的表現簡化為單一總分。

## 技術現況_純前端研究原型：
Interactive Scene
      ↓
Local Evidence Engine
      ↓
Dynamic Assessment Flow
      ↓
Versioned Scoring Simulation
      ↓
Audit / JSON Log
角色、場景與動畫目前主要以 SVG、JavaScript 與 CSS 製作。
尚未正式串接大型語言模型（LLM）與 AI Agents，因此自然語言理解、角色回應與評分目前仍以本地暫定規則模擬。
後續將逐步由 keyword matching 轉向 structured evidence extraction。

## AI 預定角色：
- 理解自由文字回應
- 辨識專業判斷證據
- 選擇適當的動態支持
- 產生較自然的角色回應
- 維持角色與情境狀態
正式評分仍應由可追蹤、可版本化、可重新計算的 scoring mechanism 控制。

## 目前階段：
- 概念驗證
- 互動流程測試
- 動態評量設計測試
-  UI / UX 試玩
-  Evidence 與 scoring rule 開發
- 歷程資料結構驗證
目前的評分與判讀結果均屬研發階段，尚不能視為正式評量結果。

## 下一步：
- 提升角色與場景動畫品質
- 優化 Desktop / Mobile UX
- 強化 Evidence Extraction
- 發展 Adaptive Mediation
- 串接 LLM / AI Agents

