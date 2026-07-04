# Changelog

<details>

<summary>English</summary>

## v9.0 (2026-07-04)

### New Features
- **Personal Report Window** — New dedicated button on the overlay opens your personal report list
  - Minimal list showing the latest 20 Timer/BOSS reports (date / mode / target)
  - Click any entry to view your own full combat detail (skill table, cast ECG, buff timeline)
  - Auto-positions beside the overlay; supports live language switching
- **Overlay Title Buttons** — Three buttons on the title bar: Reset Data, Personal Report, Expand Main Window
- **Overlay Edge Snapping** — When you drag and release the overlay near a game window edge, it auto-snaps to it
- **New Class "Scrapper" Fully Integrated** — Dedicated class color and icon, 62 skill names officially catalogued; report manager and sidebar filters support it
- **Buff Timeline (Status Distribution)** — Combat detail now visualizes buff cast timing
  - Top: Gantt marks marking every cast moment
  - Bottom: capsules counting casts per buff
  - Color-coded by direction (self-cast / caused / received)
  - Reports now include buff data; old reports remain compatible
- **"Frontal" Damage Type Tracked Separately** — Matches the official meter's front/back split. Combat detail title adds seven damage-type capsules (Crit / Heavy / Perfect / Frontal / Back / Block / Multi-hit)
- **Report "Target" Filter** — Report manager and sidebar gain a target dropdown (grouped by BOSS category), combinable with class, cDPS, cHPS, keyword filters
- **Mandatory Discord Login on Launch** — The app won't enter the main window without Discord login; previously authorized devices pass through automatically
- **AION2 Serial + Pro Gate** — Serial format `AION2-XXXX-XXXX`, first activation binds to a single owner to prevent resale. Non-Pro users see a blurred main window with a CTA; overlay and basic monitoring are unaffected
- **Report Upload Anonymization** — On upload, your nickname is kept; all other players become "Anonymous Player N"
- **Multi-Target Report Upload** — Upload consent window now offers three targets (Hive / Aletheia Community / Both); only BOSS and Timer reports can be uploaded to avoid noise
- **Combat Detail Preloads Your Latest Report** — Opening the main window auto-shows your latest report (BOSS fight preferred), then hands off to live data when you actually enter combat
- **Language Switcher Submenu** — Right-click menu now uses a submenu instead of cycling, so you can pick Traditional / Simplified / English directly
- **Reset Button Returns to Live** — Resetting while browsing reports now returns to live data and clears the view

### Game Adaptation
- **136 New BOSSes Catalogued** (total 739 → 875) — Dragon Crisis 001/002, Nightmare Season 4 (50), Ascension Trial 005/006, Abyss Horn Cavern (Transcendence), Fallen Guardians (Expedition), Abyss AR3 Nahma, L2/D2 open-world kings and named elites
- **Full Class Skill List Rebuilt** — 430 base skills + 233 variants, complete EN/ZH names; 6 game-side renames synced
- **v8.21 Damage Protocol Fix** — Heavy / Crit / Back / Multi-hit now 100% consistent with the official meter
- **Buff Identification Precision** — Switched to the game's native status-effect identifiers as the anchor; 2,216 real status entries (including stun / knockdown / bind / invincibility)
- **Buff Direction Identification** — Precisely distinguishes caster and receiver, skipping vision-sync events to prevent count inflation
- **Compatible with the 2026-07-01 Game Nickname Update**
- **Removed Low-Usage Dungeon Mode** — Only Global / Timer / BOSS display modes remain (old dungeon reports still readable)
- **Stigma Tier-5 Support** — After the game unlocked the 5th enhancement tier, tier-5 Stigma skill damage was misclassified as unknown and undercounted on the per-skill breakdown (total DPS unaffected); now fixed

### Improvements
- **Overlay Title Bar Simplified** — Brand icon removed; title text switched to bold
- **Unified Capsule Styling on Overlay & Main Window** — Server+nickname merged into one capsule; class/race icons combined; NTE-style dark gaps and thin borders applied
- **Bar Redesign** — Rounded double-end, gradient fill, semi-transparent base (numbers stay readable without a bar)
- **Frameless Overlay** — Residual system border and rounded shadow removed
- **Dark Dialog Title Bars Unified** — Hotkey, Network Detect, Report Manager, Analyzer, Diagnostics, Upload Consent all aligned
- **Button Color Unification** — Removed jarring green-on-white buttons
- **Target Filter Dropdown Visible Items 10 → 20**
- **Announcement Window Visual Cleanup**
- **Added Frontal and Multi-hit Colors**
- **Sovereign Name Source Rebuilt** — Skill / BOSS / dungeon names now come directly from the game's official string tables; English buff names reach 100% coverage

### Bug Fixes
- **Fixed All Damage Values Stuck at 16466** — Attack power was being misread as damage
- **Fixed Heavy Strike Marking Completely Broken** — Old model mislabeled all Heavy as Perfect
- **Fixed Back Marking + Global Rank DPS Mismatch with Detail** — Rank area now uses full-fight average DPS (matches official meter)
- **Fixed Global Mode DPS Stopping After Long Fights** — Reverted to sliding-average DPS calculation
- **Fixed Report Manager Lag on Language Switch** — No longer reloads 400+ JSON files
- **Fixed Long-Run Lag** — Panels no longer copy up to 2000 entries every tick when data is unchanged
- **Fixed BOSS Mode Skill Detail Showing Only DOT / Heal**
- **Fixed Serial Activation Exceptions, Missing Audit Trails, and Stats Loss**
- **Fixed Main Window Rank "100.0%" Display**
- **Fixed Network Diagnostics Window Too Bright**

### Known Limitations
- **Overlay Not Visible in Exclusive Fullscreen** — Exclusive Fullscreen bypasses the Windows DWM compositor, so all topmost overlays (including Aletheia, Discord, Steam, NVIDIA) are hidden. Use Borderless / Windowed Fullscreen instead — visually identical, and the overlay stays on top.

</details>

---

<details>

<summary>繁體中文</summary>

# Changelog

## v9.0 (2026-07-04)

### 新功能
- **個人戰報視窗** — 浮窗新增專屬按鈕，一鍵開啟個人戰報清單
  - 極簡清單顯示最近 20 場計時/BOSS 戰報（日期／模式／目標）
  - 點擊任一筆查看本人完整戰鬥細節（技能表、心電圖、狀態分布圖）
  - 自動定位於浮窗右側，支援即時語系切換
- **浮窗標題控制按鈕** — 標題列右側新增三顆按鈕：重置數據、個人戰報、展開主視窗
- **浮窗自動吸附遊戲邊界** — 拖曳浮窗放開時，靠近遊戲視窗邊緣會自動貼齊
- **新職業「拳星」完整接入** — 專屬職業色與圖示、62 個技能名稱正式收錄，戰報管理與側邊欄篩選同步支援
- **狀態分布圖（BUFF 時序）** — 戰鬥細節新增 buff 施放時序視覺化
  - 上方 Gantt 標記每次施放時間點
  - 下方膠囊統計各 buff 施放次數
  - 依方向分色（自施／造成／受到）
  - 戰報同步收錄 buff 資料，舊戰報向後相容
- **傷害類型「前方」獨立統計** — 對齊官方水錶前後分計邏輯；戰鬥細節標題新增七種傷害類型膠囊（暴擊／強擊／完美／前方／後方／格擋／多段）
- **戰報「目標」篩選** — 戰報管理與側邊欄新增目標下拉（依 BOSS 分類分組），可與職業、cDPS、cHPS、關鍵字多條件聯用
- **啟動強制 Discord 登入** — 未登入 Discord 無法進入主程式；已登入裝置下次自動通過
- **AION2 序號 + Pro Gate** — 序號格式 `AION2-XXXX-XXXX`，首次啟用綁定單一擁有者，杜絕盜賣；非 Pro 時主視窗模糊遮罩，浮窗與基礎監控不受影響
- **戰報上傳匿名化** — 上傳時保留本人暱稱，其餘玩家改為「匿名玩家N」
- **戰報多目標上傳** — 上傳同意視窗改為三目標選擇（永恆蜂窩／Aletheia 社群／同時上傳），僅 BOSS/計時模式可上傳
- **戰鬥細節預載本人最近戰報** — 開啟主視窗自動展示最近一場戰報（BOSS 戰優先），進場後自動交接到即時資料
- **語言切換子選單** — 右鍵選單從循環切換改為子選單，可直接點選繁中／簡中／English
- **重置按鈕連動返回** — 瀏覽戰報時按重置自動退回即時資料並清空畫面

### 遊戲適配
- **136 個新 BOSS 入庫**（總數 739 → 875）— 涵蓋龍族危機 001/002、惡夢第 4 季（50 隻）、覺醒戰 005/006、深淵角岩窟（超越）、墮落守護者之城（遠征）、深淵 AR3 納赫瑪、L2/D2 野外世界王與命名精英
- **全職業技能清單重建** — 基礎技能 430 + 變體 233，中英名稱完整補齊；同步 6 處遊戲端更名
- **v8.21 傷害協議修正** — 強擊／暴擊／後方／多段四維度與官方水錶 100% 一致
- **BUFF 識別精準化** — 改以遊戲原生狀態辨識碼為錨點，2,216 個真實狀態清單（含氣絕／擊倒／束縛／無敵等）
- **BUFF 方向識別** — 精準區分施放者與承受者，略過進入視野同步事件避免計數膨脹
- **相容 2026-07-01 遊戲暱稱更新**
- **移除使用率極低的副本模式** — 僅保留全域／計時／BOSS 三種顯示模式（舊版副本戰報仍可讀取）
- **支援五階烙印技能** — 遊戲改版開放第5強化階級後，5 階烙印技能的傷害先前會被誤判為未知而少計（該技能占比偏低，總 DPS 不影響），現已修正

### 改善
- **浮窗標題列精簡** — 移除品牌圖示；標題文字改粗體
- **浮窗／主窗統一膠囊化** — 伺服器+暱稱整合為單一膠囊；職業／種族圖示合併；NTE 風格暗 gap + 細邊框
- **量條重新設計** — 雙端圓邊、漸層、半透明底條（無量條者數字仍可讀）
- **浮窗無邊框** — 關閉殘留系統邊框與圓角陰影
- **對話框標題列深色化統一** — 熱鍵設置、網卡偵測、戰報管理、分析基準、網路診斷、上傳同意等一致套用
- **按鈕色彩統一** — 移除突兀綠底白字
- **目標篩選下拉可見項 10 → 20**
- **公告視窗視覺收斂**
- **新增前方色與多段色**
- **技能／BOSS／副本名稱主權源重建** — 名稱直接來自遊戲官方字串表；英文介面 buff 名稱 100% 覆蓋

### 修正
- **修正傷害值全卡在 16466** — 攻擊力被誤判為傷害
- **修正強擊標記完全失效** — 舊模型把強擊全誤標為完美
- **修正後方標記失效 + 全域排名 DPS 與細節區不一致** — 排名區改用全程平均 DPS（與官方水錶一致）
- **修正全域模式 DPS 長時間累計失效** — 改回滑動平均計算
- **修正戰報管理語系切換卡頓** — 不再重讀 400+ 份 JSON
- **修正長時間運作 lag** — 資料未變時不再每 tick 複製最多 2000 筆資料
- **修正 BOSS 模式技能細節只顯示 DOT／治癒**
- **修正序號啟用例外被吞、統計遺失等問題**
- **修正主窗排名佔比 `100.0%` 顯示**
- **修正網路診斷視窗背景過亮**

### 已知限制
- **獨佔全螢幕下浮窗無法顯示** — 獨佔全螢幕繞過 Windows DWM 合成層，所有置頂浮窗皆失效（Discord／Steam／NVIDIA 同樣受限）。請改用無邊框全螢幕，視覺效果等同且浮窗正常。

</details>

---

<details>

<summary>简体中文</summary>

# Changelog

## v9.0 (2026-07-04)

### 新功能
- **个人战报窗口** — 浮窗新增专属按钮，一键开启个人战报清单
  - 极简清单显示最近 20 场计时/BOSS 战报（日期／模式／目标）
  - 点击任一笔查看本人完整战斗细节（技能表、心电图、状态分布图）
  - 自动定位於浮窗右侧，支持即时语系切换
- **浮窗标题控制按钮** — 标题列右侧新增三颗按钮：重置数据、个人战报、展开主窗口
- **浮窗自动吸附游戏边界** — 拖曳浮窗放开时，靠近游戏窗口边缘会自动贴齐
- **新职业「拳星」完整接入** — 专属职业色与图示、62 个技能名称正式收录，战报管理与侧边栏筛选同步支持
- **状态分布图（BUFF 时序）** — 战斗细节新增 buff 施放时序视觉化
  - 上方 Gantt 标记每次施放时间点
  - 下方胶囊统计各 buff 施放次数
  - 依方向分色（自施／造成／受到）
  - 战报同步收录 buff 资料，旧战报向后兼容
- **伤害类型「前方」独立统计** — 对齐官方水表前后分计逻辑；战斗细节标题新增七种伤害类型胶囊（暴击／强击／完美／前方／后方／格挡／多段）
- **战报「目标」筛选** — 战报管理与侧边栏新增目标下拉（依 BOSS 分类分组），可与职业、cDPS、cHPS、关键字多条件联用
- **启动强制 Discord 登入** — 未登入 Discord 无法进入主程序；已登入装置下次自动通过
- **AION2 序号 + Pro Gate** — 序号格式 `AION2-XXXX-XXXX`，首次启用绑定单一拥有者，杜绝盗卖；非 Pro 时主窗口模糊遮罩，浮窗与基础监控不受影响
- **战报上传匿名化** — 上传时保留本人昵称，其余玩家改为「匿名玩家N」
- **战报多目标上传** — 上传同意窗口改为三目标选择（永恒蜂窝／Aletheia 社群／同时上传），仅 BOSS/计时模式可上传
- **战斗细节预载本人最近战报** — 开启主窗口自动展示最近一场战报（BOSS 战优先），进场后自动交接至即时资料
- **语言切换子菜单** — 右键菜单从循环切换改为子菜单，可直接点选繁中／简中／English
- **重置按钮连动返回** — 浏览战报时按重置自动退回即时资料并清空画面

### 游戏适配
- **136 个新 BOSS 入库**（总数 739 → 875）— 涵盖龙族危机 001/002、恶梦第 4 季（50 只）、觉醒战 005/006、深渊角岩窟（超越）、堕落守护者之城（远征）、深渊 AR3 纳赫玛、L2/D2 野外世界王与命名精英
- **全职业技能清单重建** — 基础技能 430 + 变体 233，中英名称完整补齐；同步 6 处游戏端更名
- **v8.21 伤害协议修正** — 强击／暴击／后方／多段四维度与官方水表 100% 一致
- **BUFF 识别精准化** — 改以游戏原生状态辨识码为锚点，2,216 个真实状态清单（含气绝／击倒／束缚／无敌等）
- **BUFF 方向识别** — 精准区分施放者与承受者，略过进入视野同步事件避免计数膨胀
- **兼容 2026-07-01 游戏昵称更新**
- **移除使用率极低的副本模式** — 仅保留全域／计时／BOSS 三种显示模式（旧版副本战报仍可读取）
- **支援五阶烙印技能** — 游戏改版开放第5强化阶级后，5 阶烙印技能的伤害先前会被误判为未知而少计（该技能占比偏低，总 DPS 不影响），现已修正

### 改善
- **浮窗标题列精简** — 移除品牌图示；标题文字改粗体
- **浮窗／主窗统一胶囊化** — 服务器+昵称整合为单一胶囊；职业／种族图示合并；NTE 风格暗 gap + 细边框
- **量条重新设计** — 双端圆边、渐层、半透明底条（无量条者数字仍可读）
- **浮窗无边框** — 关闭残留系统边框与圆角阴影
- **对话框标题列深色化统一** — 快捷键设置、网卡侦测、战报管理、分析基准、网络诊断、上传同意等一致套用
- **按钮色彩统一** — 移除突兀绿底白字
- **目标筛选下拉可见项 10 → 20**
- **公告窗口视觉收敛**
- **新增前方色与多段色**
- **技能／BOSS／副本名称主权源重建** — 名称直接来自游戏官方字串表；英文介面 buff 名称 100% 覆盖

### 修正
- **修正伤害值全卡在 16466** — 攻击力被误判为伤害
- **修正强击标记完全失效** — 旧模型把强击全误标为完美
- **修正后方标记失效 + 全域排名 DPS 与细节区不一致** — 排名区改用全程平均 DPS（与官方水表一致）
- **修正全域模式 DPS 长时间累计失效** — 改回滑动平均计算
- **修正战报管理语系切换卡顿** — 不再重读 400+ 份 JSON
- **修正长时间运作 lag** — 资料未变时不再每 tick 复制最多 2000 笔资料
- **修正 BOSS 模式技能细节只显示 DOT／治愈**
- **修正序号启用例外被吞、统计遗失等问题**
- **修正主窗排名占比 `100.0%` 显示**
- **修正网络诊断窗口背景过亮**

### 已知限制
- **独占全屏幕下浮窗无法显示** — 独占全屏幕绕过 Windows DWM 合成层，所有置顶浮窗皆失效（Discord／Steam／NVIDIA 同样受限）。请改用无边框全屏幕，视觉效果等同且浮窗正常。

</details>
