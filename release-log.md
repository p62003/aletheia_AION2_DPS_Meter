# Changelog

<details>

<summary>English</summary>

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
