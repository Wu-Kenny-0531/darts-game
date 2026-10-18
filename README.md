# darts-game
# 🎯 《501飛鏢遊戲》 (501 Darts Arcade Deluxe v1.3)

![Version](https://img.shields.io/badge/Version-v1.3%20Deluxe-f5c542?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Desktop%20%7C%20Mobile%20Web-38bdf8?style=flat-square)
![Dependency](https://img.shields.io/badge/Dependencies-Zero%20\(Single%20HTML\)-2a9d8f?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-94a3b8?style=flat-square)

一款主打**「爽感娛樂、真實規則與戰術導引」**的瀏覽器飛鏢遊戲。全專案封裝於單一 `index.html` 檔案中，透過原生 SVG、Canvas、Web Audio API 與 Web Speech API 打造，**零外部圖檔、零外部音檔、不依賴任何 CDN 或後端伺服器**，支援離線遊玩與一鍵 GitHub Pages 部署。

🔗 **線上試玩 (Live Demo)**：`https://wu-kenny-0531.github.io/darts-game/`

---

## ✨ 核心特色

* **🎯 標準 501 Double Out 競技規則**：
  * 完整實作單倍、雙倍、三倍環與內外牛眼（25 / 50 分）幾何座標判定。
  * 嚴格遵循 **Double Out（雙倍結標）** 與 **Bust（爆分）** 規則（剩餘分數 `< 0`、`= 1`、或降至 `0` 但最後一鏢非雙倍/內牛眼時判定 Bust，自動回復至該回合起始分數）。
* **🕹️ 雙操作模式 × 三段物理難度檔位**：
  * **模式 A（Crosshair Breathing 準星點擊）**：支援李薩如（Lissajous）8 字手部自然擺動與呼吸縮圈（Sweet Spot 綠圈時機判定）。
  * **模式 B（Swipe Throw 向上滑動投擲）**：依向上拖曳距離、滑動速度（`speed/650` 基準映射）與水平偏移計算落點，支援黃金虛線軌跡預覽與手勢過短防呆取消。
  * **三段難度一鍵切換**：提供 `🟢 休閒/驗收 (100% 精準)`、`🟡 標準娛樂 (微幅呼吸縮圈)`、`🔴 職業擬真 (結標心跳加速手抖 + 盲狙滑動)` 三種體感。
* **🤖 5 階段 AI 對手 (DartBot) & 👥 本機雙人對戰**：
  * 內建 **Lv.1 新手學徒 (3DA ~42)** 至 **Lv.5 世界冠軍傳奇 (3DA ~108)** 共 5 個等級的 AI 對手，具備自動結標路線規劃與削分留雙倍戰術智慧。
  * 支援 **P1 vs P2 本機雙人熱座模式（Pass & Play）**，輪流投擲並自動切換計分板。
* **💡 智能霓虹結標提示 & 路線引擎**：
  * 當剩餘分數 `≤ 170` 且在當前剩餘鏢數內可合法結標時，靶面自動以**金色霓虹呼吸框**標示第一鏢建議目標，並提供首選與替代路線（例如：`170: T20 → T20 → Bull 50`）。
* **🔥 街機稱號徽章、Web Speech 裁判唱分 & BGM 合成器**：
  * 單回合觸發 **TON 80 (180)**、**HAT TRICK (三牛眼)**、**THREE IN A BED**、**WHITE HORSE**、**HIGH TON**、**LOW TON** 時彈出專屬街機徽章與粒子爆發特效。
  * 內建英語裁判語音播報（*"Game on!"*, *"One Hundred and Eighty!"*, *"Game shot, and the match!"*）與 3 種純 Web Audio 即時合成的背景音樂曲風（`Pub Lounge` / `Neon Arcade` / `Finals Arena`）。
* **↩ 完整 Undo 撤銷系統與模式隔離統計**：
  * 支援單步連續 Undo，完整還原分數、落點、Bust/勝利狀態、計時器與統計數據（對戰模式下按 Undo 會自動退回 AI 剛投完的飛鏢至玩家上一鏢）。
  * **501 標準**、**練習模式**與 **結標挑戰（40 ~ 170 指定分數）** 紀錄完全獨立保存於 `localStorage`。

---

## 🎮 操作與玩法指南

### 1. 頂部快捷列
* **難度切換按鈕**：點擊可隨時在 `🟢 休閒/驗收`、`🟡 標準娛樂`、`🔴 職業擬真` 之間循環切換。
* **🎵 BGM / 🗣️ 語音**：一鍵開關背景音樂與英語裁判唱分。
* **⏸ 暫停 / ☰ 主選單**：暫停計時或切換遊戲模式。

### 2. 兩種投擲方式（可於對局中隨時切換）
| 操作模式 | 操作方式 | 瞄準技巧 |
| :--- | :--- | :--- |
| **模式 A：準星點擊**<br>(`Crosshair`) | 移動滑鼠或手指瞄準靶面，點擊即投出飛鏢。 | 在 `標準` 或 `職業` 難度下，觀察準星外圍虛線圈縮成**「綠色實線小圈」**的瞬間點擊，落點最精準！ |
| **模式 B：滑動投擲**<br>(`Swipe Throw`) | 在靶面下方按住滑鼠或單指，**向上滑動並放開**。 | 滑動距離越長、速度越快，飛鏢落點越高；左右偏移決定水平落點。若向上滑動過短（`< 14px`）放開會自動取消手勢，不消耗飛鏢。 |

---

## 📊 規格與參數一覽

### 三段難度物理參數
| 參數維度 | 🟢 休閒 / 驗收 (`CASUAL`) | 🟡 標準娛樂 (`STANDARD`) | 🔴 職業擬真 (`PRO`) |
| :--- | :--- | :--- | :--- |
| **準星 8 字擺動振幅** | `0 px`（純視覺呼吸，不改座標） | `8.5 px` | `13.5 px` |
| **呼吸縮圈半徑範圍** | 固定無散射 | `2.0 ~ 13.0 px` | `2.8 ~ 19.5 px` |
| **Swipe 軌跡預覽長度** | `100%` + 顯示終點紅心 | `65%` 導引線（無終點紅心） | `40%` 短導引線（盲狙手感） |
| **Swipe 出手高斯標準差** | `0 px` | `5.0 px` | `8.2 px`（長按逾 1.8 秒加疲勞抖動） |
| **結標區 (`≤ 50分`) 心跳倍率** | `1.0x` | `1.2x` | `1.5x`（準星變紅且晃動顯著加快） |

### 街機稱號徽章 (Arcade Awards) 觸發條件
* 🔥 **TON 80**：單回合三鏢總分達 `180` 分（`T20 × 3`）。
* 🎩 **HAT TRICK**：單回合三鏢全中內牛眼（50）或外牛眼（25）。
* 🎯 **THREE IN A BED**：單回合三鏢命中同一個三倍區（例如 `T19 × 3`）。
* 🐎 **WHITE HORSE**：單回合三鏢分別命中三個不同的三倍區（例如 `T20 + T19 + T18`）。
* ⚡ **HIGH TON**：單回合三鏢總分介於 `151 ~ 179` 分。
* ✨ **LOW TON**：單回合三鏢總分介於 `100 ~ 150` 分。

---

## 🚀 快速部署教學 (GitHub Pages)

本專案為純靜態單一檔案架構，無須建置工具（No Build Step），部署步驟如下：

1. 在 GitHub 建立一個新的 Repository（例如命名為 `501-darts-game`）。
2. 將遊戲程式碼儲存為 `index.html`，連同本 `README.md` 上傳至專案根目錄（`main` 分支）。
3. 進入該 Repository 的 **Settings** ➔ 左側選單點擊 **Pages**。
4. 在 **Build and deployment** 區塊：
   * **Source** 選擇 `Deploy from a branch`。
   * **Branch** 選擇 `main`（或 `master`），資料夾選擇 `/ (root)`，點擊 **Save**。
5. 等待約 1 分鐘後，即可透過 `https://<你的帳號>.github.io/501-darts-game/` 在桌面或手機瀏覽器開啟遊玩！

---

## 🛠️ 技術棧與儲存結構

* **前端介面與排版**：HTML5、CSS3 Grid / Flexbox 響應式設計（桌面雙欄並排、手機單手觸控適配）。
* **向量靶面與動畫**：SVG `<path>` 幾何扇形繪製、CSS Keyframes 霓虹呼吸與震動、HTML5 `<canvas>` 粒子系統。
* **原生音效與語音**：
  * `AudioContext` 振盪器（OscillatorNode）與增益控制（GainNode）即時合成撞擊音、號角與三種背景音樂。
  * `window.speechSynthesis` 原生英語語音唱分。
* **本機資料持久化 (`localStorage`)**：
  * `darts501_v12_settings`：保存難度、操作模式、靈敏度、BGM 與語音設定。
  * `darts501_v12_active_game`：即時保存未完成對局，支援重新整理頁面後無縫恢復。
  * `darts501_v12_stats_501` / `practice` / `challenge`：三大模式獨立統計數據與防重複結算 `settledMatchIds` 機制。
