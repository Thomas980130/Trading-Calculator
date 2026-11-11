# 交易風控計算機 | Trading Risk Control Calculator

[🇹🇼 繁體中文](#-繁體中文) | [🇺🇸 English](#-english)

---

## 🇹🇼 繁體中文

一個專為加密貨幣合約交易、外匯與期權投資者設計的 **前端微型 Web App**。透過嚴格的風控邏輯，幫助交易員在進場前精確計算出「在固定虧損風險下，所需要投入的保證金與合約數量」，從而落實紀律交易，杜絕情緒化爆倉。

### 🎯 核心亮點
* **以損定倉**：輸入單筆交易預計承擔的爆倉/割肉金額（USDT），自動推算安全倉位。
* **嚴格防錯機制**：自動校驗多空方向（做多時止損必在下方、做空時止損必在上方），防止盲目輸入導致的反向開倉。
* **行動端極致優化**：採用靈活的 RWD 佈局、iOS 防自動縮放設計、呼叫數位鍵盤（`inputmode="decimal"`），適合手機桌面捷徑與 PWA 級別體驗。
* **專業交易介面**：極簡深色主題（Dark Mode），搭配交易所標準的紅綠視覺識別。

### 🚀 功能與操作說明
1. **輸入參數**
   * **單筆想賠多少 (USDT)**：此單若觸及止損，您心裡預期且能承受的最大虧損金額。
   * **【進場】開倉價格**：預計建立部位的市價或限價。
   * **【收錢】止盈價格 (TP)**：預期獲利平倉的目標價。
   * **【割肉】止損價格 (SL)**：技術面破位、必須嚴格認賠的出場價。
   * **【工具】槓桿倍數 (x)**：交易所開立的槓桿倍率（用以換算實際所需保證金，不影響合約數量）。
2. **計算結果**
   * **你需要下單的保證金**：在該槓桿倍數下，你實際要在交易所輸入的「投入本金」。
   * **交易方向**：根據 TP/SL 的相對位置，自動判定並著色顯示 `做多 (Long)` 或 `做空 (Short)`。
   * **合約數量**：實際需要買入/賣出的資產總總量（名目價值單位）。
   * **此單盈虧比**：這筆交易的「風險報酬比」，幫助評估此單是否值得出手（建議大於 1:1.5）。

### 📐 計算公式
$$\text{價格距離 (Price Distance)} = | \text{開倉價格} - \text{止損價格} |$$
$$\text{合約數量 (Contract Size)} = \frac{\text{單筆想賠金額}}{\text{價格距離}}$$
$$\text{名目價值 (Notional Value)} = \text{合約數量} \times \text{開倉價格}$$
$$\text{所需保證金 (Margin Required)} = \frac{\text{名目價值}}{\text{槓桿倍數}}$$

### 🛠️ 技術棧與架構
本專案採用 **零依賴 (Zero-dependency)** 靜態架構，無須編譯，隨開隨用：
* **HTML5**：語意化標籤及行動端 Meta 設定。
* **CSS3**：CSS Variables（變數管理主題色）、Flexbox 響應式佈局。
* **Vanilla JavaScript (ES6+)**：原生 DOM 操作與強型別數值驗證邏輯。

### 📦 安裝與部署
1. **本地執行**：下載 `index.html`，連同 `icon.png` 放入同一個資料夾，雙擊即可在瀏覽器開啟。
2. **託管部署**：可直接上傳至 [GitHub Pages](https://github.com)、Vercel 或 Netlify，一鍵生成線上網址。
3. **手機捷徑**：在手機瀏覽器開啟網頁後，點選「加入主畫面」，即可當作獨立 App 快速喚醒。

### 📝 免責聲明
本工具僅供交易策略與風險控管數據計算參考。市場有風險，投資需謹慎。作者不對因使用本計算機輸入錯誤、代碼延遲或市場滑點所造成的任何實質交易虧損承擔任何法律責任。

---

## 🇺🇸 English

A lightweight, multi-device optimized **front-end micro Web App** tailored for crypto perpetual futures, forex, and margin traders. By enforcing strict risk management rules, it helps traders accurately determine the exact "Margin Required" and "Contract Size" before entering a trade, eliminating emotional trading and catastrophic liquidations.

### 🎯 Core Features
* **Risk-Based Position Sizing**: Input the exact amount (in USDT) you are willing to lose on a single trade, and the calculator automatically computes the safe position size.
* **Anti-Error Guardrail**: Automatically validates trade direction (e.g., Stop Loss must be below Entry for Longs, and above Entry for Shorts) to prevent disastrous, wrong-way order placements.
* **Mobile-First UX**: Responsive Web Design (RWD) optimized for smartphone screens, features iOS auto-zoom prevention, and triggers the numeric keypad (`inputmode="decimal"`) for seamless on-the-go calculation.
* **Exchange-Grade UI**: A clean, premium Dark Mode interface utilizing industry-standard red and green visual cues for instant situational awareness.

### 🚀 How to Use
1. **Input Parameters**
   * **Risk Amount (USDT)**: The maximum financial loss you are willing and prepared to accept if the trade hits your Stop Loss.
   * **Entry Price**: The market or limit price at which you intend to open your position.
   * **Take Profit Price (TP)**: Your target price to exit the trade in profit.
   * **Stop Loss Price (SL)**: Your strict invalidation price to cut losses when the market moves against you.
   * **Leverage (x)**: The leverage multiplier utilized on your exchange (affects required margin only; does not alter contract size or risk).
2. **Output Results**
   * **Margin Required**: The actual capital/collateral you need to enter into the order box on your exchange.
   * **Trade Direction**: Automatically identifies and color-codes the setup as either `Long` (Green) or `Short` (Red).
   * **Contract Size**: The exact amount of asset units (notional quantity) you need to buy or sell.
   * **Risk-to-Reward Ratio (R:R)**: The efficiency metric of your trade setup to evaluate if the trade is statistically viable (recommended > 1:1.5).

### 📐 Formulas & Core Logic
$$\text{Price Distance} = | \text{Entry Price} - \text{Stop Loss Price} |$$
$$\text{Contract Size} = \frac{\text{Risk Amount}}{\text{Price Distance}}$$
$$\text{Notional Value} = \text{Contract Size} \times \text{Entry Price}$$
$$\text{Margin Required} = \frac{\text{Notional Value}}{\text{Leverage}}$$

### 🛠️ Tech Stack & Architecture
Built with a **zero-dependency**, pure static front-end architecture. No compilation or build steps needed:
* **HTML5**: Semantic elements and high-performance mobile viewport configuration.
* **CSS3**: Modern CSS Variables for clean theme management and Flexbox layout for responsiveness.
* **Vanilla JavaScript (ES6+)**: High-speed, lightweight DOM manipulation with strict numerical validation guardrails.

### 📦 Deployment & Installation
1. **Local Run**: Download `index.html`, keep `icon.png` in the same directory, and double-click to open it in any browser.
2. **Cloud Hosting**: Deploy with zero configuration to [GitHub Pages](https://github.com), Vercel, or Netlify.
3. **Mobile Web App (PWA Experience)**: Open the URL on your mobile browser and select "Add to Home Screen" to use it like a native utility app.

### 📝 Disclaimer
This tool is provided for educational and risk-modeling purposes only. Financial markets involve substantial risk of loss. The author assumes no legal or financial liability for any real trading losses incurred due to input errors, execution slippage, or script latency.
