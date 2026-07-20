# Changelog

<details>

<summary>English</summary>

## v9.4 (2026-07-21)

### Important Behavior Changes
- **Upload Terms Updated to v2.3 — Re-consent Required** — Clause 2 now explicitly lists **your server** among the collected items (including teammates in the same fight, used for server-based leaderboard categorization and statistics). **The exclusion of nicknames and actor IDs is unchanged** — teammate nicknames and actor IDs are still never transmitted. Old v2.2 consent records don't carry over: **the announcement window on first launch after updating will ask you to read and agree again, and you cannot enter the main program without consenting** (the same startup gate as v9.3).
- **Reports Now Include Your Server** — Uploads now carry a server field for the uploader and every participant, so community leaderboards can categorize and rank by server. Data accumulates from this version onward; existing cloud reports have no such field and can't be backfilled.

### New Features
- **Left/Right-Click Skill Coloring** — Skill names are colored by their trigger key (light blue for left-click, orange-red for right-click), consistently across combat details and the skill map. Existing semantic colors for DoT / healing skills are unaffected.
- **Display Scaling Change Notice** — When a Windows display-scaling change is detected (e.g. 100% → 175%), the app now prompts you to restart it, so the interface doesn't get stuck at the wrong size.

### Improvements
- **Overlay Drags Freely Anywhere** — Edge snapping has been removed: the overlay is no longer pulled back to the game window's edges and can sit anywhere on screen, **including on another monitor** (previously prevented by snapping). Upward expansion is retained and still picks its direction from the game window's position.

### Fixes
- **High-DPI Cross-Monitor Window Blowup Fixed** — Fixed the abnormal window enlargement reported at 2K with 125% scaling. The cause was the Qt framework re-applying scaling when a window moves between monitors of different DPI — not a configuration problem on your side.

### Known Limitations
- **Close the App Manually After an Update** — After the updater finishes downloading and closes, the DPS main program does not exit on its own. Please close it manually; the new version then launches automatically and the update completes correctly. v9.3's update-handoff fix turned out to be only half effective (the launcher's settle-and-relaunch works; the main program's automatic exit does not fire). A fix is in progress.
- **Changing Windows Display Scaling May Freeze or Corrupt the App — Please Restart It** — Change detection and a restart prompt are in place, but Windows event-dispatch timing does not guarantee the prompt appears before the freeze. Stack analysis confirms the freeze happens inside the Qt framework's native layer, beyond this app's reach. Please close the app before changing display scaling.
- **A Few Reports May Show a Wrong Gear Score** — There is a known gear-score read anomaly in some cases (correct sometimes and wrong other times on the same character, with a constant wrong value). The original hypothesis was disproven by live sampling and the investigation continues; combat data and DPS are unaffected.
- **Trial Difficulty Pending Field Reports** — Trial data is in place (v9.3), but boss identification and report tagging still await user reports, as we cannot enter Trial content on our side.
- **Very Large Field Bosses (Dozens On-Screen) — Under Observation** — 5-player dungeons and field bosses are verified against the official meter; dozens-on-screen scenarios remain under observation.
- **Overlay Not Visible in Exclusive Fullscreen** — Exclusive Fullscreen bypasses the Windows DWM compositor, hiding all topmost overlays. Use Borderless / Windowed Fullscreen instead.

</details>

<details>

<summary>繁體中文</summary>

## v9.4 (2026-07-21)

### 重要行為變更
- **上傳同意條款升版 2.3，更新後需重新同意** — 條款第二條明列「所屬伺服器」為蒐集項目（含同場隊員，用於排行榜之伺服器分類與統計）。**暱稱與 actor ID 的排除承諾維持不變**，同場隊員仍不傳送暱稱或 actor ID。舊版 2.2 的同意紀錄不沿用：**更新後首次啟動的公告視窗會要求重新閱讀並勾選同意，未同意無法進入主程式**（與 v9.3 相同的啟動閘機制）。
- **戰報上傳新增所屬伺服器** — 上傳內容加入伺服器欄位（上傳者本人與每位參與者），社群平台排行榜可依伺服器分類統計。資料自本版起累積，既有雲端戰報無此欄位、無法回補。

### 新功能
- **左右鍵技能著色** — 技能名稱依觸發鍵著色（左鍵水藍、右鍵橘紅），戰鬥細節與技能地圖一致；DOT／治癒等既有語意色不受影響。
- **顯示縮放比變更提示** — 偵測到 Windows 顯示縮放比變更（例如 100% → 175%）時提示重新啟動本程式，避免介面停留在錯誤尺寸。

### 改善
- **浮窗改為任意位置自由拖曳** — 移除邊界磁吸：浮窗不再被吸附或拉回遊戲視窗邊界，可放在畫面任意位置，**包含拖到其他螢幕**（先前受磁吸限制無法跨螢幕擺放）。「向上展開」形態保留，仍依遊戲視窗位置決定展開方向。

### 修正
- **高 DPI 跨螢幕視窗異常放大修復** — 修正 2K 125% 縮放環境回報的視窗異常放大。根因為 Qt 框架在不同 DPI 的螢幕間移動視窗時重複套用縮放，非使用者的設定問題。

### 已知限制
- **更新完成後需手動關閉主程式** — 更新程式下載完成並關閉後，DPS 主程式不會自動退出，請手動關閉；關閉後新版本會自動啟動，更新結果正確。v9.3 的更新交接修正實測只生效一半（launcher 的結算與重啟正常，主程式自動退出未觸發），修復中。
- **切換 Windows 顯示縮放比後可能卡死或顯示異常，請重新啟動本程式** — 已加入變更偵測與重啟提示，但 Windows 的事件派發時機不保證提示能趕在卡死前彈出。堆疊分析確認卡死發生在 Qt 框架原生層，本程式無法自行恢復。切換縮放比前請先關閉本程式。
- **少數戰報的裝備評分可能顯示錯誤** — 已知有裝分讀取異常的個案（同一角色時對時錯、錯值固定）。原假設經實機採樣推翻，現場證據尚未取得，調查中；戰鬥數據與 DPS 不受影響。
- **試煉難度 BOSS 識別待實機回報** — 試煉資料已入庫（v9.3），但開發側無法進場試煉副本，識別與戰報標籤仍待外部用戶回報。
- **大型野外 BOSS（幾十人同屏）持續觀察** — 5 人副本與野外 BOSS 已對齊官方水錶，幾十人同屏場景維持觀察。
- **獨佔全螢幕下浮窗無法顯示** — 獨佔全螢幕繞過 Windows DWM 合成層，所有置頂浮窗皆失效。請改用「無邊框全螢幕／視窗化全螢幕」。

</details>

<details>

<summary>简体中文</summary>

## v9.4 (2026-07-21)

### 重要行为变更
- **上传同意条款升版 2.3，更新后需重新同意** — 条款第二条明列「所属服务器」为搜集项目（含同场队员，用于排行榜之服务器分类与统计）。**昵称与 actor ID 的排除承诺维持不变**，同场队员仍不传送昵称或 actor ID。旧版 2.2 的同意纪录不沿用：**更新后首次启动的公告窗口会要求重新阅读并勾选同意，未同意无法进入主程序**（与 v9.3 相同的启动闸机制）。
- **战报上传新增所属服务器** — 上传内容加入服务器字段（上传者本人与每位参与者），社群平台排行榜可依服务器分类统计。数据自本版起累积，既有云端战报无此字段、无法回补。

### 新功能
- **左右键技能着色** — 技能名称依触发键着色（左键水蓝、右键橘红），战斗细节与技能地图一致；DOT／治疗等既有语义色不受影响。
- **显示缩放比变更提示** — 侦测到 Windows 显示缩放比变更（例如 100% → 175%）时提示重新启动本程序，避免界面停留在错误尺寸。

### 改善
- **浮窗改为任意位置自由拖曳** — 移除边界磁吸：浮窗不再被吸附或拉回游戏窗口边界，可放在画面任意位置，**包含拖到其他屏幕**（先前受磁吸限制无法跨屏幕摆放）。「向上展开」形态保留，仍依游戏窗口位置决定展开方向。

### 修正
- **高 DPI 跨屏幕窗口异常放大修复** — 修正 2K 125% 缩放环境回报的窗口异常放大。根因为 Qt 框架在不同 DPI 的屏幕间移动窗口时重复套用缩放，非使用者的设定问题。

### 已知限制
- **更新完成后需手动关闭主程序** — 更新程序下载完成并关闭后，DPS 主程序不会自动退出，请手动关闭；关闭后新版本会自动启动，更新结果正确。v9.3 的更新交接修正实测只生效一半（launcher 的结算与重启正常，主程序自动退出未触发），修复中。
- **切换 Windows 显示缩放比后可能卡死或显示异常，请重新启动本程序** — 已加入变更侦测与重启提示，但 Windows 的事件派发时机不保证提示能赶在卡死前弹出。堆栈分析确认卡死发生在 Qt 框架原生层，本程序无法自行恢复。切换缩放比前请先关闭本程序。
- **少数战报的装备评分可能显示错误** — 已知有装分读取异常的个案（同一角色时对时错、错值固定）。原假设经实机采样推翻，现场证据尚未取得，调查中；战斗数据与 DPS 不受影响。
- **试炼难度 BOSS 识别待实机回报** — 试炼数据已入库（v9.3），但开发侧无法进场试炼副本，识别与战报标签仍待外部用户回报。
- **大型野外 BOSS（几十人同屏）持续观察** — 5 人副本与野外 BOSS 已对齐官方水表，几十人同屏场景维持观察。
- **独占全屏幕下浮窗无法显示** — 独占全屏幕绕过 Windows DWM 合成层，所有置顶浮窗皆失效。请改用「无边框全屏幕／窗口化全屏幕」。

</details>
