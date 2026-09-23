# 互動式 SJT｜Interactive SJT Prototype
- 將情境判斷、動態支持、互動敘事與可追蹤評分整合為一個可操作的評量原型
- Demo：https://wlyeh919-bot.github.io/-interactive-sjt/index.html

## 研發與測量治理原則
- 本專案目前可採快速原型與 Vibe Coding，加速介面、動畫與互動設計
- 待進入正式研究或高風險評量應用，測量核心與正式系統須進入可版本化、可測試、可審查、可追溯的開發流程：
  - 程式碼納入 Git 版本控制，保留版本與變更紀錄
  - API 金鑰與敏感資訊不得置於公開前端，應以環境變數及後端機制管理
  - 使用支援版本控制與可重現環境的正式開發流程
  - 系統逐步拆分為互動呈現層、評量流程層與測量核心層
  - Evidence coding、rubric 與 scoring rule 的正式變更須經人工審查，不由 AI 自行決定
  - 建立人工裁決的已知答案測試集（golden / regression test set），每次更新後重新驗證
  - Development / Staging / Production 環境分離，未驗證版本不得直接進入正式環境
  - 正式資料、模型、prompt、Evidence Model 與 scoring rule 均須留下版本與 audit trail，並具備回溯與 rollback 能力

## 專案概念
- 使用者不只是閱讀題目並作答，而是進入一段持續發展的教育情境，與學生、同事及家長互動
- 目前原型嘗試整合：
  - 情境式互動與角色對話
  - 自由文字／語音輸入
  - 動態支持（Dynamic Assessment）
  - Evidence-based scoring
  - 作答與互動歷程紀錄
  - 未來 LLM / AI Agents 擴充
- 核心方向：讓 SJT 從「閱讀情境後作答」，進一步成為「進入情境、互動、判斷與回應」

## 目前 Demo 版本包含
- 連續教育情境
- 教室角色與環境動態
- 可點擊場景物件
- 自由文字作答
- 初步語音輸入
- 動態支持流程
- 本地 Evidence / Scoring Simulation
- `needs_review` 機制
- 親師與教師間互動
- JSON 歷程紀錄
- Desktop / Mobile Responsive Prototype

## 動態評量概念
- 目前基本流程：  
  **INITIAL → Evidence Check → L1 / L2 必要支持 → L3 標準化新資訊 → POST**
- 系統保留初始反應、支持歷程與介入後反應，不將不同階段的表現簡化為單一總分

## 技術現況｜純前端研究原型
- 技術流程：  
  **Interactive Scene → Local Evidence Engine → Dynamic Assessment Flow → Versioned Scoring Simulation → Audit / JSON Log**
- 角色、場景與動畫目前主要以 SVG、JavaScript 與 CSS 製作
- 尚未正式串接大型語言模型（LLM）與 AI Agents
- 目前自然語言理解、角色回應與評分仍以本地暫定規則模擬
- 後續將逐步由 Keyword Matching 轉向 Structured Evidence Extraction

## AI 預定角色
- 理解自由文字回應
- 辨識專業判斷證據
- 選擇適當的動態支持
- 產生較自然的角色回應
- 維持角色與情境狀態
- AI 協助 Interpretation 與 Interaction，正式評分仍由可追蹤、可版本化、可重新計算的 Scoring Mechanism 控制

## 目前階段
- 概念驗證
- 互動流程測試
- 動態評量設計測試
- UI / UX 試玩
- Evidence 與 Scoring Rule 開發
- 歷程資料結構驗證
- 目前評分與判讀結果均屬研發階段，尚不能視為正式評量結果

## 下一步
- 提升角色與場景動畫品質
- 優化 Desktop / Mobile UX
- 強化 Evidence Extraction
- 發展 Adaptive Mediation
- 建立正式 Regression Test Set
- 模組化 Assessment / Measurement Core
- 串接 LLM / AI Agents
- 建立 Staging / Production 部署流程
- 進行專家審查與實證驗證
