# Changelog

<details>

<summary>English</summary>

## v9.3 (2026-07-17)

### Important Behavior Changes
- **Discord Login Security Upgrade** — Serial activation/release and report uploads are now verified server-side against your Discord login, eliminating identity spoofing. **If you last logged in before 2026-07-06 and haven't re-logged since, you'll be asked to log in to Discord once after updating**; recently logged-in users won't notice anything.
- **Upload Consent Now Required at Startup** — The consent item moved to the startup announcement window, with terms updated to v2.2 fully disclosing what gets uploaded; you cannot enter the main program without consenting (the old "declining doesn't affect normal use" wording has been corrected). Old consent records don't carry over — you'll be asked to read and agree again after updating. Consent can be toggled anytime in the announcement window, effective immediately.
- **Automatic Report Upload for Free Users** — Compliant reports from free users are uploaded anonymously and automatically to the Aletheia community platform; Sponsors have auto-upload off by default, can enable it, and keep manual target selection. Teammates are always anonymous; only an active Sponsor who explicitly enables name display shows their own in-game nickname.
- **Anonymous Team Data Points** — New reports include every teammate with a known class and damage as an anonymous data point for the community mixed leaderboard; class/skill pages remain Sponsor-only. Historical reports didn't save teammate data and can't be backfilled.

### New Features
- **BOSS Mode Summary Row** — In boss fights, the top ranking row now shows a team summary: boss icon + boss name (in red) + team total damage + team DPS, with a full red bar setting it apart from player rows; the title bar slims down to the timer and kill mark. The summary row ignores clicks/hover/right-click.
- **New-Report / New-Version Badge Dots** — The main window, sidebar, right-click menu, system tray, and announcement window show breadcrumb badge dots in sync, cleared only when you reach the corresponding destination; opening personal reports clears the new-report dot.
- **Announcement Version Tabs** — The announcement changelog now switches between versions via capsule tabs, so you can look back at previous versions.
- **Hive Upload Link Dialog** — After a successful upload to BNS Hive, a dialog with a selectable URL pops up (Copy Link / Open in Browser) instead of force-opening your browser; batch uploads merge into one dialog with copy-all.
- **First-Launch Language Detection** — With no saved language preference, the app picks Traditional Chinese / Simplified Chinese / English from your Windows locale; manual selection always wins.
- **Upload Status at a Glance** — Report Manager now shows each report's "Uploaded / Pending / Non-compliant" status and totals directly.

### Game Adaptation
- **Bakron Island "Trial" Difficulty Support** — The expedition Trial difficulty added in the 2026-07-15 game update is fully covered (three bosses: Tiere / Thamon / Vakron), bringing total bosses from 875 to 878; report lists and Report Manager show and sort the "Trial" tag correctly.

### Improvements
- **Right-Click Menu Stays Open** — Checkable options (opacity / size / format / language, etc.) keep the menu open for consecutive adjustments; mutually exclusive options act as radio groups; menu text updates in place when switching language, without flicker.
- **Report Manager Upgrades** — Wider window; a language dropdown in the filter row (two-way synced with the main window); new "All / Uploadable / Not Uploadable" quick filters; batch-upload compliance checks now split by target — community standards apply only to the "Aletheia Community" target, while "BNS Hive" uploads pass through.
- **Manual Uploads Take Priority** — During background backfill, manual uploads always jump the queue; clicking upload on a report already queued shows a clear message.
- **Upload Threshold Adjusted** — Minimum fight duration lowered from 15s to 5s so short-fight reports can upload; completely failed captures (all nicknames empty) are correctly marked not uploadable.
- **Personal Report List Polished** — Uploaded reports correctly show "Uploaded" and disable the button; the list refreshes when you upload from the sidebar / Report Manager; button text follows language switching instantly.
- **Title Bar & Sidebar Detailing** — Wider spacing between overlay title-bar buttons to reduce misclicks; the sidebar arrow no longer shows double tooltips and aligns to the panel top; the "⋮" button moved to the far right and renamed "More Settings"; classic DPS format gains a `/s` suffix.
- **Community Site Language Follows the App** — Opening the community platform from the app now carries your language, so the site matches the app instead of your browser language.

### Fixes
- **Update Handoff Fixed** — When the updater launched by the app applies an update, the main program now exits properly instead of minimizing to the tray; updates also apply cleanly while minimized to the tray; canceling the updater restores the new-version notice.
- **Upward-Expansion Jitter Fixed** — Fixed the overlay jittering up and down each frame when expanded upward near the bottom of the screen in BOSS mode.
- **Overlay Snap Lockout Fixed** — Fixed the overlay getting stuck off-screen (even across restarts) when dragged far past the game window edges; diagonally stuck overlays also snap back to the nearest corner.
- **Black Message Box Fixed** — Fixed message windows (e.g. upload results) rendering with an unreadable all-black background.
- **English Layout Fix** — Buttons in the upload-target dialog no longer truncate in English (the window widens to fit).
- **Badge Dot High-DPI Fix** — Badge dots no longer blur at 150%/200% system scaling.

### Known Limitations
- **One-Time Transition from v9.2** — v9.2 has neither badge dots nor the update handoff (both new in this version): a running v9.2 won't be notified of the new version (restart, or use Check for Updates in the announcement window), and after updating, **the old v9.2 may linger in the system tray — please right-click and exit it manually**. Updates from v9.3 onward won't have this rough edge.
- **Trial Difficulty Pending Field Reports** — Trial data is in place; in-game boss identification and tagging await user reports.
- **Very Large Field Bosses (Dozens On-Screen) — Under Observation** — 5-player dungeons and field bosses verified against the official meter; dozens-on-screen scenarios remain under observation.
- **Overlay Not Visible in Exclusive Fullscreen** — Exclusive Fullscreen bypasses the Windows DWM compositor, hiding all topmost overlays. Use Borderless / Windowed Fullscreen instead.

## v9.2 (2026-07-11)

### Critical Fixes
- **Nickname Display Restored (game-update fix)** — After a game update, character nicknames disappeared in Abyss maps. This is now fixed. **If you were on v9.1, your nicknames are currently broken — please update.**
- **Field / Multiplayer Damage Loss Fully Fixed** — A new transport-layer TCP stream reassembly step now sits between packet capture and parsing: in-order packets pass through instantly, retransmissions are de-duplicated, out-of-order segments are re-ordered, and dropped packets are isolated. This eliminates whole-event damage loss on large compressed packets split across network segments (the root fix for v9.1's "cross-segment loss" known limitation). Verified against the official meter in a 5-player dungeon and a field boss fight.

### Overlay Improvements
- **Upward-Expanding Layout** — When the overlay sits near the bottom of the game screen, it now stacks upward (title bar at the bottom, rank 1 nearest the title bar), keeping the window bottom-anchored as entries change.
- **Your-Row Emphasis** — When you are first identified and when your total damage ticks up, your ranking row plays a brief highlight, micro-shift, and a spark at the end of your bar (display-only; combat stats untouched).
- **Custom Background Fully Rendered** — Your custom overlay background is now drawn as a full backdrop with cover-crop and a readability mask; toggling it via right-click applies instantly and persists.
- **K/s → M/s Rounding** — Values switch to `M/s` before they would round up to `1,000.0K/s`; the three columns now lay out by actual text width.

### Main Window & Reports
- **Report Sidebar Redesign** — A new "Reports" nav button (expand-only; the arrow still collapses); sidebar labels reorganized (Back to Global / Refresh / Report Manager / Community Platform / Personal Analysis / Skill Map); the "Upload" entry is now "Community Platform" (opens the Aletheia community site).
- **Per-Report Upload Buttons** — Every report in the sidebar and the personal-report list gains its own upload button (disabled with a hint for dungeon / legacy reports).

### Announcement & Menu
- **Announcement Window Rebuilt** — The announcement is now rich-text cards (donation / changelog / download), with clear spacing, list indentation, and clickable links; the window is larger and resizable, and the donation address / account text is selectable.
- **Right-Click Menu Cleanup** — "Upload with my nickname" moved directly under the Discord identity item; "Deactivate Serial" removed (serial deactivation still handled by the announcement window); checkbox display and spacing fixed.
- **Activate-Serial Button Highlighted** — When not activated, the "Activate Serial" entry is now a bold amber outlined button instead of a gray text link.

### Known Limitations
- **Very Large Field Bosses (Dozens On-Screen) — Community Testing** — 5-player dungeons and 2-player field bosses are verified against the official meter; the original dozens-on-screen 5% scenario is left to community testing this release.
- **Theme-Style Switcher Temporarily Removed** — Colors/themes can still be adjusted via settings; the live in-app switcher UI is temporarily removed this version and will return as a restart-applied option.
- **Overlay Not Visible in Exclusive Fullscreen** — Exclusive Fullscreen bypasses the Windows DWM compositor, hiding all topmost overlays. Use Borderless Fullscreen instead.

## v9.1 (2026-07-10)

### New Features
- **Built-in Auto-Update (New Launcher: ALETHEIA-DPS.exe)** — The package now bundles a launcher and updater
  - Please launch via `ALETHEIA-DPS.exe` from now on (instead of the main program directly)
  - Future versions check for and apply differential updates automatically — no more full re-downloads
  - If power is lost or the app is force-closed mid-update, it auto-recovers on next launch
  - This version is still a full download; auto-update takes effect from versions after v9.1
- **Manual Update Check** — The announcement window gains a "Check for Updates" button to trigger an update check anytime
- **Your Gear Score Display** — Combat detail now shows a "Gear" field with the player's gear score in real time; reports record it too and show it when reopened
- **Full Report Upload to Community Platform** — Reports uploaded to the Aletheia community platform now include every skill's full metrics (Crit / Heavy / Perfect / Frontal / Back / Block / Multi-hit rates, average and minimum damage) and healing, powering class skill leaderboards and spec/stigma stats
- **Upload-With-Nickname Toggle** — New right-click option (off by default); when on, reports uploaded to the community platform show your nickname, otherwise anonymous
- **Auto-Release of "In Use" Serials** — When a serial is stuck "In Use" and can't activate, it now auto-releases and re-activates (owner only), removing most manual support resets
- **Overlay Title Close Button** — A close button on the right of the overlay title bar hides the overlay directly

### Game Adaptation
- **DOT Skills Named Separately** — Damage-over-time branches like Lingering Flame and Frostbite now show dedicated names (e.g. "Lingering Flame - DOT"), across all enhancement tiers, no longer merged with the base skill
- **Scrapper Damage Undercount Fixed** — Scrapper's damage-over-time (DOT/HOT) was previously dropped as a group due to a skill-identification gap, systematically undercounting Scrapper's total damage; now fixed
- **Heal/Shield Identification Expanded** — The heal/shield skill whitelist grows to 66 entries (adding Ruinous Shield and others); their sustained effects are no longer miscounted as damage
- **Charge Skill Tier Suffix Corrected** — Fixed tier detection for some charge skills so max tier correctly shows the MAX suffix
- **Removed Mislabeled Skills** — Fixed items like "Flame Zone" that were wrongly tagged as special skills

### Improvements
- **Smoother Overlay Snapping** — When you drag and release the overlay to snap to a game edge, it now glides in smoothly instead of jumping
- **Wider Overlay Snap Range** — Snapping now triggers from farther off the game edge
- **Overlay "You" Marker** — A slanted YOU tag on the top-right of your own nickname capsule in the ranking rows, so you spot yourself at a glance
- **Overlay Three-Column Split** — "Total Damage", "Contribution %", and "DPS" split into three separate columns, removing the old value/percentage toggle menu
- **Overlay Title Simplified** — BOSS/Timer mode titles no longer show session total DPS (fight duration kept); hovering title-bar buttons shows trilingual tooltips
- **"Share %" Column in Combat Detail** — The skill table gains a contribution-share column based on that group's total damage
- **Ranking Selection Highlight Upgraded** — The selected row now uses a rounded capsule glow, matching the bar's arc
- **Personal Report Window Widened** — Combat detail displays more spaciously (1200×720)

### Bug Fixes
- **Multiplayer Damage Loss Fixed** — Fixed partial damage loss in multiplayer dungeons caused by large compressed packets being split; multiplayer DPS now realigns with the official meter
- **Top-Gear High Damage Dropped Fixed** — Fixed ultra-high crits (over 2M) from skills like Aimed Shot on top gear being wrongly discarded by an overflow guard (single-hit cap raised to 5M)
- **Timer Mode Report Replay DOT Display Fixed** — When reopening exported Timer-mode reports, DOT skills are no longer merged into the base skill
- **Lifesteal Sword Cross-Class Misattribution Fixed** — The cross-class lifesteal sword no longer causes buff attribution errors
- **Report List Sorting Fixed** — Reports now sort by fight time, no longer reshuffled after upload
- **Combat Detail Skill Sorting Fixed** — Combo groups now sort by group total damage
- **Upload Experience Improved** — Upload progress now shows a clear busy indicator + per-target live status; fixed the progress window occasionally hanging; upload failures now show friendly reasons; default upload target is now the Aletheia community platform
- **Settings Corruption Protection** — Settings (serial / language / hotkeys / overlay) now use a safer write method, so a crash mid-save no longer corrupts settings or wipes your serial

### Known Limitations
- **Rare Cross-Segment Loss on Very Large Packets** — This version fixed multiplayer compressed-packet loss across segments; full reassembly of uncompressed very-large packets across segments is not yet implemented (no real impact observed so far), to be addressed in a later version
- **Overlay Not Visible in Exclusive Fullscreen** — Exclusive Fullscreen bypasses the Windows DWM compositor, hiding all topmost overlays (Discord/Steam/NVIDIA are equally affected). Use Borderless Fullscreen instead — visually identical and the overlay works normally.

</details>

<details>

<summary>繁體中文</summary>

# Changelog

## v9.3 (2026-07-17)

### 重要行為變更
- **Discord 登入安全升級** — 序號啟用／釋放與戰報上傳一律由伺服器驗證 Discord 登入身份，杜絕冒用他人身份。**2026-07-06 之前登入且此後未重新登入的用戶，更新後會被要求重新登入 Discord 一次**；近期登入過的用戶無感。
- **戰報上傳同意改為啟動必要條件** — 同意項移至啟動公告視窗，條款升版 2.2，完整揭露上傳內容；未同意無法進入主程式（舊條款「不同意不影響正常使用」的描述已訂正）。舊版的同意紀錄不沿用，更新後會要求重新閱讀並同意；同意可隨時在公告視窗勾選／取消，即時生效。
- **免費用戶戰報自動上傳** — 免費用戶的合規戰報會匿名自動上傳至 Aletheia 社群平台；Sponsor 預設關閉自動上傳，可自行開啟並保留手動選擇上傳目標。隊友永遠匿名；只有有效 Sponsor 且主動開啟顯名時，上傳者本人才會顯示遊戲暱稱。
- **全隊匿名資料點** — 新戰報會把每位已知職業且有傷害的隊員作為匿名資料點納入社群平台混合榜；職業／技能頁維持 Sponsor 專屬。歷史戰報未保存隊友資料，無法回補。

### 新功能
- **BOSS 模式浮窗彙總行** — BOSS 戰排名首行新增全隊彙總：BOSS 圖標 + BOSS 名稱（紅色）+ 全隊總傷害 + 全隊 DPS，以紅色滿條與玩家列區隔；標題列同步精簡為計時與擊殺標記。彙總行不回應點擊／滑鼠停留／右鍵。
- **新戰報／新版本紅點提示** — 主視窗、側欄、右鍵選單、系統匣與公告視窗同步顯示麵包屑紅點，到達對應位置才清除；開啟個人戰報即清除新戰報紅點。
- **公告版本分頁** — 公告視窗的更新內容以版本膠囊切換，可回看前版內容。
- **蜂窩上傳網址對話框** — 上傳永恆蜂窩成功後彈出可選取網址的對話框（複製連結／開啟網頁），不再強制開瀏覽器；批次多筆合併為單一對話框、一鍵複製全部。
- **首次啟動自動語系** — 沒有既存語言偏好時，依 Windows 語系自動選擇繁中／簡中／英文；手動選擇永遠優先。
- **自動上傳狀態可見化** — 戰報管理可直接查看每份戰報「已上傳／待處理／不合規」與總數，不需進入其他視窗。

### 遊戲適配
- **巴克隆空中島「試煉」難度支援** — 2026-07-15 遊戲更新新增的遠征試煉難度完整收錄（提耶／塔蒙／巴克隆三 BOSS），BOSS 總數 875 → 878；戰報列表與戰報管理正確顯示「試煉」標籤並排序。

### 改善
- **右鍵選單連續操作** — 勾選型選項（透明度／尺寸／格式／語言等）點選後選單保持開啟、可連續調整；互斥選項成組單選；切換語言時選單文字即時更新、不再閃爍。
- **戰報管理升級** — 視窗加寬；篩選列新增語言下拉（與主視窗雙向同步即時翻譯）；新增「全部／可上傳／不可上傳」快速篩選；批次上傳的合規檢查依目標分流——僅「Aletheia 社群」目標套用社群標準，「永恆蜂窩」照傳不誤擋。
- **手動上傳優先** — 背景補傳進行中，手動上傳一律插隊優先送出；戰報已在上傳佇列時再點上傳會明確提示。
- **上傳門檻調整** — 戰鬥時長下限 15 秒 → 5 秒，短戰鬥戰報可上傳；徹底擷取失敗（全員暱稱空白）的戰報正確判為不可上傳。
- **個人戰報清單完善** — 已上傳戰報正確顯示「已上傳」並禁用；由側欄／戰報管理上傳後清單同步刷新；按鈕文字隨語系即時切換。
- **標題列與側欄細節** — 浮窗標題列按鈕間距放寬、降低誤觸；側欄展開箭頭不再出現雙重提示、位置對齊面板頂部；「⋮」按鈕移至最右並正名「更多設置」；經典 DPS 格式補 `/s` 後綴。
- **社群平台語系跟隨** — 從程式內開啟社群平台時，網站語系自動與程式一致，不再受瀏覽器語言影響。

### 修正
- **更新交接修正** — 由程式啟動的更新程式套用更新時，主程式會正常退出、不再縮到系統匣；縮在系統匣時套用更新也能正常關閉；取消更新後新版本提示會恢復。
- **浮窗向上展開抖動修復** — BOSS 模式浮窗貼近畫面下緣向上展開時，視窗上下抖動閃爍的問題已修正。
- **浮窗邊界吸附卡死修復** — 浮窗大幅超出遊戲視窗邊界時卡在畫面外抓不回（重啟仍卡）的問題已修正；對角卡住也能吸回最近角落。
- **提示視窗黑底修復** — 上傳結果等提示視窗背景全黑不可讀的問題已修正。
- **英文介面佈局修正** — 上傳目標選擇視窗的英文按鈕不再截斷（視窗依內容自適應加寬）。
- **紅點徽章高 DPI 修正** — 150%／200% 系統縮放下紅點不再模糊。

### 已知限制
- **從 v9.2 更新的一次性過渡** — v9.2 沒有紅點提示與更新交接機制（兩者皆為本版新增）：v9.2 運行中不會收到新版提示（請重啟或在公告視窗手動檢查更新），且套用更新後**舊 v9.2 可能殘留在系統匣，請手動右鍵退出**。從 v9.3 起的後續更新不再有此情況。
- **試煉難度待實測回報** — 試煉資料已收錄，實機 BOSS 識別與標籤顯示待用戶回報。
- **大型野外 BOSS（幾十人同屏）持續觀察** — 5 人副本與野外 BOSS 已對齊官方水錶，幾十人同屏場景維持觀察。
- **獨佔全螢幕下浮窗無法顯示** — 獨佔全螢幕繞過 Windows DWM 合成層，所有置頂浮窗皆失效。請改用「無邊框全螢幕／視窗化全螢幕」。

## v9.2 (2026-07-11)

### 重要修正
- **暱稱顯示修復（遊戲更新適配）** — 遊戲更新後深淵地圖中，角色暱稱消失已修復。**若你先前使用 v9.1，暱稱目前為失效狀態，請務必更新。**
- **野外／多人場景傷害缺失徹底修復** — 在封包擷取與解析之間新增傳輸層 TCP 串流重組：順序封包零延遲直通、重傳自動去重、亂序自動重排、掉包自動隔離。徹底解決大型壓縮封包被切成多段傳輸時，因亂序／重傳／掉包造成的整包傷害事件丟失（v9.1「跨分段丟失」已知限制的治本）。已於 5 人副本與野外 BOSS 對齊官方水錶讀數。

### 浮窗改善
- **向上展開形態** — 浮窗貼近遊戲畫面下緣時，改為向上排列（標題列置底、第一名最靠近標題列），資料筆數變動時保持視窗底部錨定。
- **本人條目強調** — 首次辨識到你、以及你的總傷害增加時，本人排名列會有短暫的高亮、微位移與量條末端火花（純顯示效果，不影響統計數字）。
- **自訂背景圖完整繪製** — 自訂浮窗背景圖改為完整底板 + 等比裁切 + 可讀性遮罩；右鍵切換即時生效並自動記憶。
- **K/s → M/s 進位校正** — 數值在進位成 `1,000.0K/s` 前先轉為 `M/s`；三欄依實際字寬排列。

### 主視窗與戰報
- **戰報側欄改版** — 新增「戰報」導覽鈕（只展開；原箭頭仍可收合）；側欄文案整理為 返回全域／刷新清單／戰報管理／社群平台／個人分析／技能地圖；「上傳」入口改為「社群平台」（開啟 Aletheia 社群平台網站）。
- **逐筆戰報上傳鈕** — 側欄與個人戰報清單的每筆戰報都新增獨立上傳鈕（副本／舊模式戰報的按鈕禁用並提示限制）。

### 公告與右鍵選單
- **公告視窗重製** — 公告改為分卡片富文本（贊助／更新內容／下載提示），行距、連結與段落層次清晰，視窗加大且可調整尺寸，贊助地址／帳號可直接選取複製。
- **右鍵選單整理** — 「上傳顯示遊戲暱稱(本人)」移至 Discord 身分項目正下方；移除「取消啟動」（序號停用仍由公告視窗處理）；勾選框顯示與間距修正。
- **序號啟動鈕醒目化** — 未啟用時「啟動序號」由灰色文字連結改為品牌黃描邊按鈕。

### 已知限制
- **大型野外 BOSS（幾十人同屏）待用戶群實測** — 5 人副本與 2 人野外 BOSS 已驗收對齊官方水錶；原始「幾十人同屏」的 5% 缺失場景交由本版用戶群實測。
- **主題「風格」即時切換暫時下架** — 顏色／主題仍可透過設定調整；即時切換 UI 本版暫時移除，未來改為重啟生效再掛回。
- **獨佔全螢幕下浮窗無法顯示** — 獨佔全螢幕繞過 Windows DWM 合成層，所有置頂浮窗皆失效。請改用無邊框全螢幕。

## v9.1 (2026-07-10)

### 新功能
- **內建自動更新（新啟動入口 ALETHEIA-DPS.exe）** — 安裝包內建啟動器與更新程式
  - 請改用 `ALETHEIA-DPS.exe` 啟動（取代直接點主程式）
  - 之後版本會自動檢查並套用差異更新，不必再整包重新下載
  - 更新途中斷電或被強制關閉，下次啟動會自動回復
  - 本版仍為完整包下載，自動更新自 v9.1 之後的版本開始生效
- **手動檢查更新** — 公告視窗新增「檢查更新」按鈕，可隨時手動觸發更新檢查與套用
- **玩家本人裝備評分顯示** — 戰鬥細節面板新增「Gear」欄位，即時顯示玩家裝備評分；戰報一併記錄，重新開啟時同步顯示
- **社群平台完整戰報上傳** — 上傳至 Aletheia 社群平台的戰報現在收錄每個技能的完整指標（暴擊／強擊／完美／前方／後方／格擋／多段率、平均與最低傷害）與治癒量，社群平台據此提供職業技能榜與特化／烙印統計
- **上傳顯示本人遊戲暱稱開關** — 右鍵選單新增選項（預設關閉），開啟後上傳社群平台的戰報會顯示你的暱稱，關閉則匿名
- **序號「使用中」自動解除** — 序號因異常卡在「使用中」而無法啟用時，會自動釋放並重新啟用（僅序號本人有效），多數情況免除聯繫客服手動重置
- **浮窗標題關閉鈕** — 浮窗標題列右側新增關閉鈕，可直接隱藏浮窗

### 遊戲適配
- **DOT 技能獨立命名** — 殘火、凍傷等持續傷害分支顯示為專屬名稱（如「殘火 - DOT」「凍傷 - DOT」），涵蓋各強化階段，不再與本體技能混淆
- **拳星傷害少算修復** — 拳星的持續傷害（DOT／HOT）先前因技能識別遺漏被整組丟棄、導致拳星總傷害系統性偏低，現已修正
- **治癒／護盾識別擴充** — 治癒／護盾技能白名單擴充至 66 筆（新增破滅盾牌等），這些技能的持續效果不再被誤計為傷害
- **集氣技能階段後綴校正** — 修正部分集氣技能的階段判定，滿階正確顯示 MAX 後綴
- **移除誤標技能** — 修正「火焰地帶」等被誤標為特殊技能的項目

### 改善
- **浮窗吸附更滑順** — 拖曳浮窗放開自動貼齊遊戲邊界時，改為平滑滑入，不再瞬間跳位
- **浮窗吸附範圍擴大** — 拖曳放開後距遊戲邊界更遠即可自動貼齊
- **浮窗本人標記** — 排名列中「你」的暱稱膠囊右上角新增斜掛 YOU 標記，一眼辨識自己
- **浮窗欄位三分** — 「總傷害」「貢獻佔比」「DPS」拆為獨立三欄，移除舊「值／佔比」切換選單
- **浮窗標題精簡** — BOSS／計時模式標題不再顯示 session 總 DPS（保留戰鬥時長）；停留標題列按鈕時顯示三語功能提示
- **戰鬥細節新增「佔比」欄** — 技能表新增貢獻佔比欄，依該組總傷害計算
- **排名選中高亮升級** — 選中列改為膠囊圓邊發光，與量條圓弧一致
- **個人戰報視窗加寬** — 戰鬥細節顯示更寬敞（1200×720）

### 修正
- **多人場景傷害丟失修復** — 多人副本因大型壓縮封包被切割而丟失部分傷害的問題已修復，多人場景 DPS 統計重新對齊官方水錶讀數
- **頂級裝備高傷被丟棄修復** — 瞄準箭等技能在頂級裝備下的超高暴擊（突破 200 萬）被防溢位保險誤丟、導致次數與傷害同時偏低的問題已修復（單擊上限提升至 500 萬）
- **計時模式戰報回放 DOT 顯示修復** — 計時模式匯出的戰報重新開啟時，DOT 技能不再被併入本體，可正確獨立顯示
- **吸血劍跨職業誤判修復** — 跨職業共用的吸血劍不再造成 buff 歸屬誤判
- **戰報清單排序修正** — 戰報清單改依戰鬥發生時間排序，上傳後不再打亂順序
- **戰鬥細節技能排序修正** — 連續技分組改依組總傷害排序
- **上傳體驗改善** — 上傳進度改為明確的忙碌指示 + 逐目標即時狀態；修正進度視窗偶爾卡住不關閉的問題；上傳失敗改為友善的原因提示；預設上傳目標改為 Aletheia 社群平台
- **設定檔防損毀** — 設定檔（序號／語系／熱鍵／浮窗設定）改為更安全的寫入方式，程式即使在存檔瞬間當機也不再導致設定毀損或序號蒸發

### 已知限制
- **極少數大型封包跨分段仍可能遺漏** — 本版修復了多人場景壓縮封包跨分段的傷害丟失；非壓縮的超大型封包跨分段的完整重組尚未實作（目前未觀察到實際影響），後續版本治本
- **獨佔全螢幕下浮窗無法顯示** — 獨佔全螢幕繞過 Windows DWM 合成層，所有置頂浮窗皆失效（Discord／Steam／NVIDIA 同樣受限）。請改用無邊框全螢幕，視覺效果等同且浮窗正常。

</details>

<details>

<summary>简体中文</summary>

# Changelog

## v9.3 (2026-07-17)

### 重要行为变更
- **Discord 登录安全升级** — 序号启用／释放与战报上传一律由服务器验证 Discord 登录身份，杜绝冒用他人身份。**2026-07-06 之前登录且此后未重新登录的用户，更新后会被要求重新登录 Discord 一次**；近期登录过的用户无感。
- **战报上传同意改为启动必要条件** — 同意项移至启动公告窗口，条款升版 2.2，完整揭露上传内容；未同意无法进入主程序（旧条款「不同意不影响正常使用」的描述已订正）。旧版的同意纪录不沿用，更新后会要求重新阅读并同意；同意可随时在公告窗口勾选／取消，即时生效。
- **免费用户战报自动上传** — 免费用户的合规战报会匿名自动上传至 Aletheia 社群平台；Sponsor 预设关闭自动上传，可自行打开并保留手动选择上传目标。队友永远匿名；只有有效 Sponsor 且主动打开显名时，上传者本人才会显示游戏昵称。
- **全队匿名数据点** — 新战报会把每位已知职业且有伤害的队员作为匿名数据点纳入社群平台混合榜；职业／技能页维持 Sponsor 专属。历史战报未保存队友数据，无法回补。

### 新功能
- **BOSS 模式浮窗汇总行** — BOSS 战排名首行添加全队汇总：BOSS 图标 + BOSS 名称（红色）+ 全队总伤害 + 全队 DPS，以红色满条与玩家列区隔；标题列同步精简为计时与击杀标记。汇总行不回应点击／鼠标停留／右键。
- **新战报／新版本红点提示** — 主窗口、侧栏、右键菜单、系统匣与公告窗口同步显示面包屑红点，到达对应位置才清除；打开个人战报即清除新战报红点。
- **公告版本分页** — 公告窗口的更新内容以版本胶囊切换，可回看前版内容。
- **蜂窝上传网址对话框** — 上传永恒蜂窝成功后弹出可选取网址的对话框（拷贝链接／打开网页），不再强制开浏览器；批量多笔合并为单一对话框、一键拷贝全部。
- **首次启动自动语系** — 没有既存语言偏好时，依 Windows 语系自动选择繁中／简中／英文；手动选择永远优先。
- **自动上传状态可见化** — 战报管理可直接查看每份战报「已上传／待处理／不合规」与总数，不需进入其他窗口。

### 游戏适配
- **巴克隆空中岛「试炼」难度支持** — 2026-07-15 游戏更新添加的远征试炼难度完整收录（提耶／塔蒙／巴克隆三 BOSS），BOSS 总数 875 → 878；战报列表与战报管理正确显示「试炼」标签并排序。

### 改善
- **右键菜单连续操作** — 勾选型选项（透明度／尺寸／格式／语言等）点击后菜单保持打开、可连续调整；互斥选项成组单选；切换语言时菜单文本即时更新、不再闪烁。
- **战报管理升级** — 窗口加宽；筛选列添加语言下拉（与主窗口双向同步即时翻译）；添加「全部／可上传／不可上传」快速筛选；批量上传的合规检查依目标分流——仅「Aletheia 社群」目标套用社群标准，「永恒蜂窝」照传不误挡。
- **手动上传优先** — 背景补传进行中，手动上传一律插队优先送出；战报已在上传队列时再点上传会明确提示。
- **上传门槛调整** — 战斗时长下限 15 秒 → 5 秒，短战斗战报可上传；彻底截取失败（全员昵称空白）的战报正确判为不可上传。
- **个人战报清单完善** — 已上传战报正确显示「已上传」并禁用；由侧栏／战报管理上传后清单同步刷新；按钮文本随语系即时切换。
- **标题列与侧栏细节** — 浮窗标题列按钮间距放宽、降低误触；侧栏展开箭头不再出现双重提示、位置对齐面板顶部；「⋮」按钮移至最右并正名「更多设置」；经典 DPS 格式补 `/s` 后缀。
- **社群平台语系跟随** — 从程序内打开社群平台时，网站语系自动与程序一致，不再受浏览器语言影响。

### 修正
- **更新交接修正** — 由程序启动的更新程序套用更新时，主程序会正常退出、不再缩到系统匣；缩在系统匣时套用更新也能正常关闭；取消更新后新版本提示会恢复。
- **浮窗向上展开抖动修复** — BOSS 模式浮窗贴近画面下缘向上展开时，窗口上下抖动闪烁的问题已修正。
- **浮窗边界吸附卡死修复** — 浮窗大幅超出游戏窗口边界时卡在画面外抓不回（重启仍卡）的问题已修正；对角卡住也能吸回最近角落。
- **提示窗口黑底修复** — 上传结果等提示窗口背景全黑不可读的问题已修正。
- **英文接口布局修正** — 上传目标选择窗口的英文按钮不再截断（窗口依内容自适应加宽）。
- **红点徽章高 DPI 修正** — 150%／200% 系统缩放下红点不再模糊。

### 已知限制
- **从 v9.2 更新的一次性过渡** — v9.2 没有红点提示与更新交接机制（两者皆为本版添加）：v9.2 运行中不会收到新版提示（请重启或在公告窗口手动检查更新），且套用更新后**旧 v9.2 可能残留在系统匣，请手动右键退出**。从 v9.3 起的后续更新不再有此情况。
- **试炼难度待实测回报** — 试炼数据已收录，实机 BOSS 识别与标签显示待用户回报。
- **大型野外 BOSS（几十人同屏）持续观察** — 5 人副本与野外 BOSS 已对齐官方水表，几十人同屏场景维持观察。
- **独占全屏幕下浮窗无法显示** — 独占全屏幕绕过 Windows DWM 合成层，所有置顶浮窗皆失效。请改用「无边框全屏幕／窗口化全屏幕」。

## v9.2 (2026-07-11)

### 重要修正
- **昵称显示修复（游戏更新适配）** — 游戏更新后深渊地图中，角色昵称消失已修复。**若你先前使用 v9.1，昵称目前为失效状态，请务必更新。**
- **野外／多人场景伤害缺失彻底修复** — 在封包撷取与解析之间新增传输层 TCP 串流重组：顺序封包零延迟直通、重传自动去重、乱序自动重排、掉包自动隔离。彻底解决大型压缩封包被切成多段传输时，因乱序／重传／掉包造成的整包伤害事件丢失（v9.1「跨分段丢失」已知限制的治本）。已于 5 人副本与野外 BOSS 对齐官方水表读数。

### 浮窗改善
- **向上展开形态** — 浮窗贴近游戏画面下缘时，改为向上排列（标题列置底、第一名最靠近标题列），资料笔数变动时保持窗口底部锚定。
- **本人条目强调** — 首次辨识到你、以及你的总伤害增加时，本人排名列会有短暂的高亮、微位移与量条末端火花（纯显示效果，不影响统计数字）。
- **自订背景图完整绘制** — 自订浮窗背景图改为完整底板 + 等比裁切 + 可读性遮罩；右键切换即时生效并自动记忆。
- **K/s → M/s 进位校正** — 数值在进位成 `1,000.0K/s` 前先转为 `M/s`；三栏依实际字宽排列。

### 主窗口与战报
- **战报侧栏改版** — 新增「战报」导览钮（只展开；原箭头仍可收合）；侧栏文案整理为 返回全域／刷新清单／战报管理／社群平台／个人分析／技能地图；「上传」入口改为「社群平台」（开启 Aletheia 社群平台网站）。
- **逐笔战报上传钮** — 侧栏与个人战报清单的每笔战报都新增独立上传钮（副本／旧模式战报的按钮禁用并提示限制）。

### 公告与右键菜单
- **公告窗口重制** — 公告改为分卡片富文本（赞助／更新内容／下载提示），行距、连结与段落层次清晰，窗口加大且可调整尺寸，赞助地址／帐号可直接选取复制。
- **右键菜单整理** — 「上传显示游戏昵称(本人)」移至 Discord 身分项目正下方；移除「取消启动」（序号停用仍由公告窗口处理）；勾选框显示与间距修正。
- **序号启动钮醒目化** — 未启用时「启动序号」由灰色文字连结改为品牌黄描边按钮。

### 已知限制
- **大型野外 BOSS（几十人同屏）待用户群实测** — 5 人副本与 2 人野外 BOSS 已验收对齐官方水表；原始「几十人同屏」的 5% 缺失场景交由本版用户群实测。
- **主题「风格」即时切换暂时下架** — 颜色／主题仍可透过设定调整；即时切换 UI 本版暂时移除，未来改为重启生效再挂回。
- **独占全屏幕下浮窗无法显示** — 独占全屏幕绕过 Windows DWM 合成层，所有置顶浮窗皆失效。请改用无边框全屏幕。

## v9.1 (2026-07-10)

### 新功能
- **内置自动更新（新启动入口 ALETHEIA-DPS.exe）** — 安装包内置启动器与更新程序
  - 请改用 `ALETHEIA-DPS.exe` 启动（取代直接点主程序）
  - 之后版本会自动检查并套用差异更新，不必再整包重新下载
  - 更新途中断电或被强制关闭，下次启动会自动恢复
  - 本版仍为完整包下载，自动更新自 v9.1 之后的版本开始生效
- **手动检查更新** — 公告窗口新增「检查更新」按钮，可随时手动触发更新检查与套用
- **玩家本人装备评分显示** — 战斗细节面板新增「Gear」栏位，即时显示玩家装备评分；战报一并记录，重新开启时同步显示
- **社群平台完整战报上传** — 上传至 Aletheia 社群平台的战报现在收录每个技能的完整指标（暴击／强击／完美／前方／后方／格挡／多段率、平均与最低伤害）与治愈量，社群平台据此提供职业技能榜与特化／烙印统计
- **上传显示本人游戏昵称开关** — 右键菜单新增选项（预设关闭），开启后上传社群平台的战报会显示你的昵称，关闭则匿名
- **序号「使用中」自动解除** — 序号因异常卡在「使用中」而无法启用时，会自动释放并重新启用（仅序号本人有效），多数情况免除联系客服手动重置
- **浮窗标题关闭钮** — 浮窗标题列右侧新增关闭钮，可直接隐藏浮窗

### 游戏适配
- **DOT 技能独立命名** — 残火、冻伤等持续伤害分支显示为专属名称（如「残火 - DOT」「冻伤 - DOT」），涵盖各强化阶段，不再与本体技能混淆
- **拳星伤害少算修复** — 拳星的持续伤害（DOT／HOT）先前因技能识别遗漏被整组丢弃、导致拳星总伤害系统性偏低，现已修正
- **治愈／护盾识别扩充** — 治愈／护盾技能白名单扩充至 66 笔（新增破灭盾牌等），这些技能的持续效果不再被误计为伤害
- **集气技能阶段后缀校正** — 修正部分集气技能的阶段判定，满阶正确显示 MAX 后缀
- **移除误标技能** — 修正「火焰地带」等被误标为特殊技能的项目

### 改善
- **浮窗吸附更滑顺** — 拖曳浮窗放开自动贴齐游戏边界时，改为平滑滑入，不再瞬间跳位
- **浮窗吸附范围扩大** — 拖曳放开后距游戏边界更远即可自动贴齐
- **浮窗本人标记** — 排名列中「你」的昵称胶囊右上角新增斜挂 YOU 标记，一眼辨识自己
- **浮窗栏位三分** — 「总伤害」「贡献占比」「DPS」拆为独立三栏，移除旧「值／占比」切换菜单
- **浮窗标题精简** — BOSS／计时模式标题不再显示 session 总 DPS（保留战斗时长）；停留标题列按钮时显示三语功能提示
- **战斗细节新增「占比」栏** — 技能表新增贡献占比栏，依该组总伤害计算
- **排名选中高亮升级** — 选中列改为胶囊圆边发光，与量条圆弧一致
- **个人战报窗口加宽** — 战斗细节显示更宽敞（1200×720）

### 修正
- **多人场景伤害丢失修复** — 多人副本因大型压缩封包被切割而丢失部分伤害的问题已修复，多人场景 DPS 统计重新对齐官方水表读数
- **顶级装备高伤被丢弃修复** — 瞄准箭等技能在顶级装备下的超高暴击（突破 200 万）被防溢位保险误丢、导致次数与伤害同时偏低的问题已修复（单击上限提升至 500 万）
- **计时模式战报回放 DOT 显示修复** — 计时模式汇出的战报重新开启时，DOT 技能不再被并入本体，可正确独立显示
- **吸血剑跨职业误判修复** — 跨职业共用的吸血剑不再造成 buff 归属误判
- **战报清单排序修正** — 战报清单改依战斗发生时间排序，上传后不再打乱顺序
- **战斗细节技能排序修正** — 连续技分组改依组总伤害排序
- **上传体验改善** — 上传进度改为明确的忙碌指示 + 逐目标即时状态；修正进度窗口偶尔卡住不关闭的问题；上传失败改为友善的原因提示；预设上传目标改为 Aletheia 社群平台
- **设定档防损毁** — 设定档（序号／语系／热键／浮窗设定）改为更安全的写入方式，程序即使在存档瞬间当机也不再导致设定毁损或序号蒸发

### 已知限制
- **极少数大型封包跨分段仍可能遗漏** — 本版修复了多人场景压缩封包跨分段的伤害丢失；非压缩的超大型封包跨分段的完整重组尚未实作（目前未观察到实际影响），后续版本治本
- **独占全屏幕下浮窗无法显示** — 独占全屏幕绕过 Windows DWM 合成层，所有置顶浮窗皆失效（Discord／Steam／NVIDIA 同样受限）。请改用无边框全屏幕，视觉效果等同且浮窗正常。

</details>
