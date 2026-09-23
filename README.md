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
```text

## 技術現況_純前端研究原型：

- 串接 LLM / AI Agents

