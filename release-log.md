# Changelog

<details>

<summary>English</summary>

## v8.20 (2026-06-10)

### New Features
- **Video Search Upgrade** — Added Bilibili and Niconico search alongside YouTube. Three platform buttons in equal-width layout. Bilibili results open directly within the search window
- **Unified Right-Click Menu** — Overlay, main window, and system tray share a single context menu. New quick access to Report Manager, Network Diagnostics, and Language Switch
- **Report Manager Upgrade** — Added batch upload, refresh, and open folder buttons. Checkbox count updates in real-time. Window no longer blocks the main window
- **Difficulty Column in Report Manager** — Shows BOSS difficulty tier (Nightmare Lv.10, Transcendence Grade 3, Exploration...), sortable
- **Analyzer Baseline Redesign** — Four-level collapsible tree (Category → Dungeon → Difficulty → BOSS). Same BOSS across different languages automatically merged

### Game Update (06-10)
- **Ascension Trial — 4 dungeons, 30 BOSSes fully catalogued** — Nightmare Altar, Tyrant's Lair, Sanctum of Loathing, Trail Vault, each with 6 difficulty tiers
- **Musphe Sanctuary Normal/Hard split** — Iscariel and Kaldrix Normal difficulty correctly identified after 06-10 game update
- **NPC Database expanded to 6,447 entries** — Unified architecture with multilingual support. BOSS and dungeon names follow language switching

### Improvements
- **BOSS Difficulty Classification** — 722 BOSSes tagged with dungeon difficulty across 17 categories. Directly benefits Analyzer baseline and Report Manager
- **SVG Control Icons** — Window control buttons (minimize, maximize, close, etc.) now use SVG vector icons, crisp at any size
- **Button Press Feedback** — All buttons now have scale animation on press for clearer interaction feedback
- **Rank Bar Class Colors Restored** — Rank panel and overlay bars restored from unified cyan to per-class colors. Self row all green for instant recognition
- **Main Window Rank Text Simplified** — Metallic text effect removed from main window rank panel, replaced with clean shadow text. Overlay retains metallic rendering
- **Overlay Title Buttons** — Converted to native widgets with press animation feedback

### Bug Fixes
- **Sniffer Stability** — Fixed duplicate damage calculation that could occur after reconnect or reset
- **Report Export Stability** — Fixed brief stutter during rapid report output
- **Dialog Memory** — Fixed dialog windows not releasing resources properly when reopened
- **Nickname Detection** — Fixed auto-detection occasionally producing garbled nicknames
- **Analyzer Baseline** — Fixed baseline selection not working
- **SkillMAP Short Fights** — Fixed SkillMAP silently closing on very short fights with no skill rotation data
- **Bilibili Search Navigation** — Fixed Bilibili search results opening in external browser instead of within the search window
- **Hotkey Dialog** — Fixed button text truncation in English interface

</details>

---

<details>

<summary>繁體中文</summary>

# Changelog

## v8.20 (2026-06-10)

### 新功能
- **影片搜尋升級** — YouTube 外新增 B站和 Niconico 搜尋，三個平台按鈕等寬排列。B站搜尋結果直接在搜尋視窗內開啟
- **右鍵選單統一** — 浮窗、主視窗、系統匣三處共用右鍵選單，新增戰報管理、網路診斷、語言切換入口
- **戰報管理視窗升級** — 新增批次上傳、重新整理、開啟資料夾按鈕。勾選即時更新計數、視窗不再鎖定主視窗
- **戰報管理新增難度欄** — 顯示 BOSS 的難度分級（惡夢 Lv.10、超越 Grade 3、探險…），可排序
- **分析工具基準線重設計** — 四層收合結構（分類 → 副本 → 難度 → BOSS），不同語系的同一 BOSS 自動合併

### 遊戲適配（06-10 更新）
- **覺醒戰 4 副本 30 BOSS 完整收錄** — 惡夢祭壇、暴君藏身處、憎惡聖所、軌跡保管所，各 6 個難度等級
- **Musphe 聖域普通/困難切分** — 06-10 遊戲更新後的副本難度拆分，伊斯卡利爾/凱德利斯的普通難度正確識別
- **NPC 資料庫 6,447 筆** — 統一架構，BOSS 名稱/副本名稱跟隨語系切換

### 改善
- **BOSS 難度分級** — 722 個 BOSS 標記副本難度（17 種分類），分析工具基準線與戰報管理直接受益
- **控制圖標升級** — 視窗控制按鈕（最小化/最大化/關閉等）改用 SVG 向量圖標，任意尺寸清晰銳利
- **按鈕觸覺回饋** — 全程式按鈕按下時帶有縮放動畫，操作感更明確
- **量條顏色改回職業色** — 排名面板與浮窗量條從統一青色改回職業色，本人行全部綠色一眼可辨
- **主視窗排名面板金屬字移除** — 金屬色效果移除，改為清晰的陰影文字（浮窗仍保留金屬字渲染）
- **浮窗標題鈕操作感** — 按鈕改為原生元件，帶有按壓回饋動畫

### 修正
- **嗅探穩定性** — 修正重新連線或重設後傷害重複計算的問題
- **戰報寫入穩定性** — 修正戰報輸出時偶爾短暫卡頓的問題
- **對話框記憶體** — 修正重複開啟對話框時資源未正確釋放的問題
- **暱稱偵測** — 修正自動偵測偶爾產生亂碼暱稱的問題
- **Analyzer 基準線** — 修正基準線選擇功能無效的問題
- **SkillMAP 短戰鬥** — 修正極短戰鬥（無技能序列）時 SkillMAP 無預警關閉的問題
- **B站搜尋跳轉** — 修正 B站搜尋結果點擊後跳到外部瀏覽器的問題
- **快捷鍵設定** — 修正英文介面下按鈕文字截斷的問題

</details>

---

<details>

<summary>简体中文</summary>

# Changelog

## v8.20 (2026-06-10)

### 新功能
- **影片搜索升级** — YouTube 外新增 B站和 Niconico 搜索，三个平台按钮等宽排列。B站搜索结果直接在搜索窗口内开启
- **右键菜单统一** — 浮窗、主窗口、系统托盘三处共用右键菜单，新增战报管理、网络诊断、语言切换入口
- **战报管理窗口升级** — 新增批量上传、刷新、打开文件夹按钮。勾选即时更新计数、窗口不再锁定主窗口
- **战报管理新增难度栏** — 显示 BOSS 的难度分级（噩梦 Lv.10、超越 Grade 3、探险…），可排序
- **分析工具基准线重设计** — 四层折叠结构（分类 → 副本 → 难度 → BOSS），不同语言的同一 BOSS 自动合并

### 游戏适配（06-10 更新）
- **觉醒战 4 副本 30 BOSS 完整收录** — 噩梦祭坛、暴君藏身处、憎恶圣所、轨迹保管所，各 6 个难度等级
- **Musphe 圣域普通/困难切分** — 06-10 游戏更新后的副本难度拆分，伊斯卡利尔/凯德利斯的普通难度正确识别
- **NPC 数据库 6,447 条** — 统一架构，BOSS 名称/副本名称跟随语言切换

### 改善
- **BOSS 难度分级** — 722 个 BOSS 标记副本难度（17 种分类），分析工具基准线与战报管理直接受益
- **控制图标升级** — 窗口控制按钮（最小化/最大化/关闭等）改用 SVG 矢量图标，任意尺寸清晰锐利
- **按钮触觉反馈** — 全程序按钮按下时带有缩放动画，操作感更明确
- **量条颜色改回职业色** — 排名面板与浮窗量条从统一青色改回职业色，本人行全部绿色一眼可辨
- **主窗口排名面板金属字移除** — 金属色效果移除，改为清晰的阴影文字（浮窗仍保留金属字渲染）
- **浮窗标题按钮操作感** — 按钮改为原生组件，带有按压反馈动画

### 修正
- **嗅探稳定性** — 修正重新连接或重置后伤害重复计算的问题
- **战报写入稳定性** — 修正战报输出时偶尔短暂卡顿的问题
- **对话框内存** — 修正重复打开对话框时资源未正确释放的问题
- **昵称检测** — 修正自动检测偶尔产生乱码昵称的问题
- **Analyzer 基准线** — 修正基准线选择功能无效的问题
- **SkillMAP 短战斗** — 修正极短战斗（无技能序列）时 SkillMAP 无预警关闭的问题
- **B站搜索跳转** — 修正 B站搜索结果点击后跳到外部浏览器的问题
- **快捷键设置** — 修正英文界面下按钮文字截断的问题

</details>
