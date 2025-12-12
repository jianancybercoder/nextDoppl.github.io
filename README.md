# ✨ Doppl-Next VTON Engine

> **次世代 AI 虛擬試穿引擎 (Next-Gen Virtual Try-On Engine)**  
> Powered by Google Gemini 3 Pro & Phantom Haptics Technology

![Status](https://img.shields.io/badge/Status-Online-green)
![Model](https://img.shields.io/badge/AI-Gemini_3_Pro-blue)
![Tech](https://img.shields.io/badge/Tech-React_19_+_Tailwind-38bdf8)

## 📖 專案簡介 (Introduction)

**Doppl-Next** 是一款利用最先進生成式 AI 技術打造的虛擬試穿 (VTON) 應用程式。不同於傳統的 2D 圖像疊加技術，Doppl-Next 利用 **Google Gemini 3** 的多模態能力，深入理解布料物理特性、光影環境與人體姿態，合成出具備 **8K 級攝影真實感** 的試穿效果。

此外，本專案首創 **「幻影觸感 (Phantom Haptics)」** 技術，不僅生成視覺圖像，還能透過 AI 推論布料的觸覺數據（如透氣度、重量感、彈性），並以動態圖表可視化呈現。

---

## 🌟 核心亮點 (Core Highlights)

### 1. 🧠 Gemini 3 驅動的物理模擬
採用 Google 最新 Gemini 2.5/3.0 模型，透過 Prompt Engineering 模擬真實物理法則：
- **重力垂墜模擬**：精確呈現布料在身體上的堆積與下垂感。
- **光場適配**：自動調整服裝光影，使其與使用者原圖環境光完美融合。
- **層次遮擋**：智慧識別長髮、手部與配件，確保試穿層次正確 (Occlusion Handling)。

### 2. 🖐️ 幻影觸感技術 (Phantom Haptics)
Doppl-Next 不僅讓你看見，還讓你「感覺」到衣服：
- **AI 觸感推論**：模型分析服裝材質，輸出 5 維度物理數據。
- **數據視覺化**：透過雷達圖 (Radar Chart) 與進度條展示：
  - ✨ **舒適度 (Comfort)**
  - 🌬️ **透氣度 (Breathability)**
  - 🪶 **重量感 (Weight/Heaviness)**
  - 🧶 **柔軟度 (Softness/Touch)**
  - ⚡ **彈性係數 (Elasticity)**

### 3. 🌗 暖色調護眼介面 (Warm/Eye Comfort UI)
專為長時間操作設計的 UI/UX：
- **Paper / Coffee 色系**：亮色模式採用米白與深咖啡色，如閱讀紙質書般舒適。
- **Obsidian / Warm Text**：暗色模式屏棄冷冽的純黑，改用帶有溫度的黑曜石色與微黃文字，降低藍光刺激。

---

## 🚀 主要功能 (Features)

*   **雙重圖片上傳**：支援拖曳上傳「使用者照片」與「服裝照片」。
*   **多模型切換**：
    *   `Flash 2.5 (Standard)`: 速度快，適合一般預覽。
    *   `Flash 2.0 (Experimental)`: 實驗性功能測試。
    *   `Pro 3 (High Res)`: 最高品質，支援細節微調 (需相應 API 權限)。
*   **自然語言微調 (Refinement)**：可輸入文字指令（例如：「把袖子捲起來」、「讓衣服更緊身一點」）來控制生成結果。
*   **四階段生成視覺化**：即時顯示 AI 處理狀態（語意分析 -> 物理翹曲 -> 光場合成 -> 觸感渲染）。
*   **高解析度下載**：一鍵下載合成後的試穿結果。

---

## 🛠️ 技術堆疊 (Tech Stack)

*   **Frontend Framework**: React 19
*   **Styling**: Tailwind CSS (with Custom Theme Configuration)
*   **AI SDK**: Google GenAI SDK (`@google/genai`)
*   **Icons**: Lucide React
*   **Build Tool**: Vite / ESBuild (Implicit in current setup)

---

## 📖 使用指南 (Usage Guide)

### 1. 取得 API Key
由於本專案使用 Google Gemini API，您需要前往 [Google AI Studio](https://aistudio.google.com/app/apikey) 申請一組 API Key。
> **注意**：建議使用付費或綁定專案的 Key 以使用 Pro 等級模型，避免 Rate Limit (429) 或權限錯誤 (403)。

### 2. 啟動應用
開啟網頁後，於上方輸入框貼上您的 API Key。

### 3. 上傳圖片
- **左側卡片**：上傳您的全身或半身照 (建議背景單純)。
- **右側卡片**：上傳想試穿的衣服照片 (平拍或模特圖皆可)。

### 4. (選填) 輸入指令
在文字框中輸入額外需求，例如：「請將上衣紮進褲子裡」。

### 5. 開始生成
點擊 **「啟動 VTON 引擎」**。系統將經歷四個模擬階段，約 5-15 秒後產出結果。

### 6. 查看數據與下載
生成後，下方將顯示試穿圖與「幻影觸感」雷達圖分析。點擊圖片上的下載按鈕即可保存。

---

## 🎨 色彩系統 (Color Palette)

本專案採用自定義的 Tailwind 色票：

| Mode | Background | Text | Primary Accent |
| :--- | :--- | :--- | :--- |
| **Light** | `Paper (#FAF9F6)` | `Coffee (#4A3B32)` | `Indigo (#6366f1)` |
| **Dark** | `Obsidian (#191716)` | `Warm Text (#F3E9D2)` | `Indigo (#6366f1)` |

---

## ⚠️ 常見問題排除 (Troubleshooting)

*   **錯誤 403 (Permission Denied)**:
    *   API Key 無效或專案未啟用 Generative AI API。
    *   您選擇了 `Pro` 模型但帳號無權限，請切換回 `Flash` 模型嘗試。
*   **錯誤 400 (Bad Request)**:
    *   上傳的圖片檔案過大或格式不支援。
*   **生成圖片有人臉扭曲**:
    *   請確保上傳的使用者照片臉部清晰。
    *   可在提示詞中加入 "Ensure the face remains unchanged" (系統預設已加入)。

---

Created with ❤️ by the Doppl-Next Team.
