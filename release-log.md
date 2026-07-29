# Changelog

<details>

<summary>English</summary>

## v9.4.1 (2026-07-30)

> This version does **not** require re-consenting to the upload terms (they remain at v2.3, unchanged from v9.4).

### New Features
- **"Frontal" Column Added to Combat Details** — The skill table now includes the one damage type that was missing from it: **Frontal**, placed between "Perfect" and "Back". It appears consistently in the overlay's combat details, the main window's combat details, and personal report details. **Older reports have no such value and will show 0%**; only reports produced from this version onward carry real numbers.
- **"Show Overlay" Toggle in the Right-Click Menu** — A checkable "Show Overlay" entry has been added to the quick-actions section. The checkmark reflects whether the overlay is currently visible. After hiding the overlay you can still bring it back from the main window's right-click menu or the system tray.

### Improvements
- **Main Window and Personal Report Detail Window Widened** — Both windows now open wider by default so the new Frontal column fits; without this the column would be cut off. Window sizes are not remembered, so the new size applies the next time you launch.

### Fixes
- **Cross-Class Shared Skill Renamed to "Earth's Blessing"** — A Cleric's buff causes teammates to deal damage from that skill as well. This shared damage previously displayed under the same name as the Cleric's own skill, "Earth Punishment", which made it easy to misread as a skill the teammate cast themselves. It is now named "Earth's Blessing". The Cleric's own "Earth Punishment" display is unchanged. The community leaderboards have been updated to match.

### Known Limitations
- **Close the App Manually After an Update (Not Fixed in This Version)** — After the updater finishes downloading and closes, the DPS main program does not exit on its own. Please close it manually; the new version then launches automatically and **the update completes correctly**. This limitation has existed since v9.3 and applies to the v9.4 → v9.4.1 update as well. The evidence needed for a fix is not yet available (the updater's source is outside this project); the investigation continues.
- **Changing Windows Display Scaling May Freeze or Corrupt the App — Please Restart It** — Change detection and a restart prompt are in place, but Windows event-dispatch timing does not guarantee the prompt appears before the freeze. Stack analysis confirms the freeze happens inside the Qt framework's native layer, beyond this app's reach. Please close the app before changing display scaling.
- **A Few Reports May Show a Wrong Gear Score** — There is a known gear-score read anomaly in some cases (correct sometimes and wrong other times on the same character, with a constant wrong value). The original hypothesis was disproven by live sampling and the investigation continues; combat data and DPS are unaffected.
- **Trial Difficulty Pending Field Reports** — Trial data is in place (v9.3), but boss identification and report tagging still await user reports, as we cannot enter Trial content on our side.
- **Very Large Field Bosses (Dozens On-Screen) — Under Observation** — 5-player dungeons and field bosses are verified against the official meter; dozens-on-screen scenarios remain under observation.
- **Overlay Not Visible in Exclusive Fullscreen** — Exclusive Fullscreen bypasses the Windows DWM compositor, hiding all topmost overlays. Use Borderless / Windowed Fullscreen instead.
- **Combat Details May Be Cut Off on Small Screens at High Scaling** — With one more column, combat details need a wider layout, so the rightmost columns can be cut off on combinations such as 1366×768 at 125% scaling. This already happened before the Frontal column was added; this version needs a little more width still. If you hit it, lower the display scaling or use a higher resolution.

</details>

<details>

<summary>繁體中文</summary>

## v9.4.1 (2026-07-30)

> 本版**不需重新同意**上傳條款（條款維持 v9.4 的 2.3，無變更）。

### 新功能
- **戰鬥細節新增「前方」欄** — 技能表補上七種傷害類型中唯一缺席的「前方」，插在「完美」與「後方」之間，浮窗戰鬥細節、主視窗戰鬥細節、個人戰報細節三處一致。**舊戰報無此數值，前方欄會顯示 0%**；本版之後產生的戰報才有實際數值。
- **右鍵選單新增「顯示浮窗」開關** — 快捷操作區加入可勾選的「顯示浮窗」，勾選狀態即為浮窗當下的顯示狀態。浮窗關閉後，仍可從主視窗右鍵選單或系統匣右鍵重新開啟。

### 改善
- **主視窗與個人戰報細節視窗加寬** — 兩個視窗的預設寬度都加大，用以容納新增的前方欄；未加寬時前方欄會被裁切。視窗尺寸不記憶，更新後啟動即為新尺寸。

### 修正
- **跨職業共享技能正名「大地祝福」** — 治癒星的 buff 會讓隊友也造成該技能的傷害，這份共享傷害先前與治癒星本體技能同名顯示為「大地懲罰」，容易誤讀為隊友自己施放的技能，本版正名為「大地祝福」。治癒星本體的「大地懲罰」顯示不變。社群平台排行榜同步更新。

### 已知限制
- **更新完成後需手動關閉主程式（本版未修復）** — 更新程式下載完成並關閉後，DPS 主程式不會自動退出，請手動關閉；關閉後新版本會自動啟動並完成更新，**更新結果正確**。此限制自 v9.3 起存在，v9.4 → v9.4.1 的更新同樣會遇到。修復所需的證據尚未取得（更新程式的原始碼不在本專案內），調查中。
- **切換 Windows 顯示縮放比後可能卡死或顯示異常，請重新啟動本程式** — 已加入變更偵測與重啟提示，但 Windows 的事件派發時機不保證提示能趕在卡死前彈出。堆疊分析確認卡死發生在 Qt 框架原生層，本程式無法自行恢復。切換縮放比前請先關閉本程式。
- **少數戰報的裝備評分可能顯示錯誤** — 已知有裝分讀取異常的個案（同一角色時對時錯、錯值固定）。原假設經實機採樣推翻，現場證據尚未取得，調查中；戰鬥數據與 DPS 不受影響。
- **試煉難度 BOSS 識別待實機回報** — 試煉資料已入庫（v9.3），但開發側無法進場試煉副本，識別與戰報標籤仍待外部用戶回報。
- **大型野外 BOSS（幾十人同屏）持續觀察** — 5 人副本與野外 BOSS 已對齊官方水錶，幾十人同屏場景維持觀察。
- **獨佔全螢幕下浮窗無法顯示** — 獨佔全螢幕繞過 Windows DWM 合成層，所有置頂浮窗皆失效。請改用「無邊框全螢幕／視窗化全螢幕」。
- **小螢幕高縮放比下戰鬥細節可能被裁切** — 欄位變多後戰鬥細節需要更寬的版面，在 1366×768 搭配 125% 縮放這類組合下，右側欄位可能被切掉。此情況在加入前方欄之前即已存在，本版需要的寬度再多一些。若遇到，可降低顯示縮放比或改用較高解析度。

</details>

<details>

<summary>简体中文</summary>

## v9.4.1 (2026-07-30)

> 本版**不需重新同意**上传条款（条款维持 v9.4 的 2.3，无变更）。

### 新功能
- **战斗细节新增「前方」栏** — 技能表补上七种伤害类型中唯一缺席的「前方」，插在「完美」与「后方」之间，浮窗战斗细节、主窗口战斗细节、个人战报细节三处一致。**旧战报无此数值，前方栏会显示 0%**；本版之后产生的战报才有实际数值。
- **右键菜单新增「显示浮窗」开关** — 快捷操作区加入可勾选的「显示浮窗」，勾选状态即为浮窗当下的显示状态。浮窗关闭后，仍可从主窗口右键菜单或系统托盘右键重新开启。

### 改善
- **主窗口与个人战报细节窗口加宽** — 两个窗口的默认宽度都加大，用以容纳新增的前方栏；未加宽时前方栏会被裁切。窗口尺寸不记忆，更新后启动即为新尺寸。

### 修正
- **跨职业共享技能正名「大地祝福」** — 治愈星的 buff 会让队友也造成该技能的伤害，这份共享伤害先前与治愈星本体技能同名显示为「大地惩罚」，容易误读为队友自己施放的技能，本版正名为「大地祝福」。治愈星本体的「大地惩罚」显示不变。社群平台排行榜同步更新。

### 已知限制
- **更新完成后需手动关闭主程序（本版未修复）** — 更新程序下载完成并关闭后，DPS 主程序不会自动退出，请手动关闭；关闭后新版本会自动启动并完成更新，**更新结果正确**。此限制自 v9.3 起存在，v9.4 → v9.4.1 的更新同样会遇到。修复所需的证据尚未取得（更新程序的源代码不在本项目内），调查中。
- **切换 Windows 显示缩放比后可能卡死或显示异常，请重新启动本程序** — 已加入变更侦测与重启提示，但 Windows 的事件派发时机不保证提示能赶在卡死前弹出。堆栈分析确认卡死发生在 Qt 框架原生层，本程序无法自行恢复。切换缩放比前请先关闭本程序。
- **少数战报的装备评分可能显示错误** — 已知有装分读取异常的个案（同一角色时对时错、错值固定）。原假设经实机采样推翻，现场证据尚未取得，调查中；战斗数据与 DPS 不受影响。
- **试炼难度 BOSS 识别待实机回报** — 试炼数据已入库（v9.3），但开发侧无法进场试炼副本，识别与战报标签仍待外部用户回报。
- **大型野外 BOSS（几十人同屏）持续观察** — 5 人副本与野外 BOSS 已对齐官方水表，几十人同屏场景维持观察。
- **独占全屏幕下浮窗无法显示** — 独占全屏幕绕过 Windows DWM 合成层，所有置顶浮窗皆失效。请改用「无边框全屏幕／窗口化全屏幕」。
- **小屏幕高缩放比下战斗细节可能被裁切** — 栏位变多后战斗细节需要更宽的版面，在 1366×768 搭配 125% 缩放这类组合下，右侧栏位可能被切掉。此情况在加入前方栏之前即已存在，本版需要的宽度再多一些。若遇到，可降低显示缩放比或改用较高分辨率。

</details>
