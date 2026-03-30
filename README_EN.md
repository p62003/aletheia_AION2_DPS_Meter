**English** | **[繁體中文](README.md)**

# Aletheia — AION2 DPS Meter

A non-invasive, real-time DPS meter for AION2 (Aion: Legions of War, TW server).

Calculates combat data in real time via passive network packet sniffing — **no memory modification, no packet tampering, no automation of any kind**.

![Main Window](images/mainwindow_en.png)

---

## Features

### Four Display Modes
- **Global** — Real-time DPS rankings for all nearby players
- **Timer** — Training dummy mode with 10s idle auto-finalize; DOT does not extend the timer
- **Dungeon** — Automatically activates upon entering an instance; independent party stats, auto-finalize on exit
- **Boss** — Whitelisted bosses are tracked automatically; auto-finalize on boss death

### Real-Time Overlay
- Fully Canvas-rendered, high performance with zero lag
- Semi-transparent overlay with custom background image support
- Normal / Mini size toggle (right-click menu)
- Right-click to switch display modes (total damage/percentage, DPS format)
- **Hover Skill Panel** — hover over a player's rank row to see full skill breakdown
- **Skill Damage Bars** — visual bars for each skill's damage contribution
- **DOT Classification** — direct hits and DOT damage split automatically
- **Auto-Position** — overlay snaps to the game window on startup
- Class-colored DPS bars + text shadows + faction icons (Elyos / Asmodian)
- Pairing status indicator + real-time network latency (RTT) + accelerator detection
- 4K DPI auto-scaling + 1080P window auto-fit
- Persistent settings (opacity/size/display mode auto-saved)

### In-Game Screenshots

| Normal Mode | Mini Mode |
|:---:|:---:|
| ![Overlay Normal](images/overlayer_normal_1080.png) | ![Overlay Mini](images/overlayer_mini_1080.png) |

| Hover Skill Panel | Right-Click Menu |
|:---:|:---:|
| ![Hover Panel](images/overlayer_hover_en.png) | ![Right-Click Menu](images/overlayer_menu_en.png) |

### Skill MAP — Full Party Skill Timeline

A 2D timeline view of the entire party's skill casts — "What was everyone doing at this exact moment?"

- X-axis = time, Y-axis = one row per skill per player
- Multi-level collapse (player-level + skill-level), skill hide/restore
- Region select analysis (Alt+drag) — cross-player stats for casts / damage / CPM
- Semantic-colored skill icon borders (crit red / strong orange / perfect purple / DoT cyan / heal green)
- Playhead-centered zoom, Fit button, combo chain grouping

| Full Party Overview + Region Select | Zoomed-In Skill Detail |
|:---:|:---:|
| ![Skill MAP Overview](images/skillmap_main.png) | ![Skill MAP Detail](images/skillmap_main2.png) |

| English Mode with Healing Stats |
|:---:|
| ![Skill MAP EN HPS](images/skillmap_en_hps.png) |

### Combat Analysis
- Skill breakdown: damage share, crit rate, average hit, specialization indicators
- Skill timeline: cast sequence tracking for rotation and combo analysis
- **cHPS Healing Stats** — combat detail, reports, and analyzer all support healing metrics
- Report system: auto-generated reports on dungeon/boss/timer session finalization
- **Report Panel** — built-in panel with search/filter/upload
- **Report Upload** — one-click upload to Eternal Hive for sharing
- **Report Analyzer** — compare performance against historical class averages, with damage/healing mode toggle
- Summon damage automatically merged under the summoner
- Healing skills tracked in a separate section (damage/healing don't overlap)

### Report Upload

Upload combat reports to Eternal Hive for detailed analysis and skill timelines:

| Report Overview | Skill Timeline |
|:---:|:---:|
| ![Hive Report](images/hive_report.png) | ![Skill Timeline](images/hive_report2.png) |

### Companion Tools

| Report Analyzer (Damage/Healing Toggle) | Customizer | Network Diagnostics |
|:---:|:---:|:---:|
| ![Report Analyzer](images/analyze_tool_en2.png) | ![Customizer](images/custom_tool_en.png) | ![Network Diagnostics](images/network_tool.png) |

- **Aletheia Analyzer** — report analysis with damage/healing mode toggle, compare against historical class averages
- **Aletheia SkillMAP** — full party skill timeline, 2D MAP visualization of all party members' skill casts
- **Aletheia Customizer** — standalone settings tool (overlay config/theme management/hotkey recording/background toggle)
- **Aletheia Network Diagnostics** — self-check tool for troubleshooting packet capture issues (EN/ZH bilingual)

### Additional Features
- Eternal Hive PvE score / avatar API integration
- Server identification (36 servers)
- JSON theme system (colors, fonts, backgrounds)
- Universal accelerator support (ExitLag / UU / Razer / GearUP / LagoFast / Clash)
- Accelerator auto-detection — status bar shows detected accelerator name and port, auto-switch on packet loss
- Auto character detection (automatically identifies your character on login)
- System tray icon (closing main window keeps app running; double-click to restore)
- Win32 API hotkeys — no global keyboard hooks, zero interference with macros
- Full English localization for skills, dungeons, and boss names

---

## Installation & Usage

### Requirements
- Windows 10/11
- [Npcap](https://npcap.com/#download) (check "Install Npcap in WinPcap API-compatible Mode" during installation)

### Quick Start
1. Install Npcap
2. Download the latest version → [Releases](../../releases)
3. Extract, then **right-click → Run as Administrator**
4. Launch the game and data will appear automatically

### Global Hotkeys
| Hotkey | Function |
|--------|----------|
| `Alt+Q` | Show / Hide overlay |
| `Alt+E` | Show / Hide main window |

> Hotkeys are customizable via Aletheia Customizer or settings.json.

---

## FAQ

**Q: Why is there no data?**

A: Make sure Npcap is installed (WinPcap-compatible mode), the application is running as Administrator, and the game is active.

**Q: Latency shows a value but there is no damage data?**

A: v7.31 automatically supports most game accelerators with candidate auto-switching. If issues persist, use the included "Aletheia Network Diagnostic Tool" for self-diagnosis.

**Q: Why does my antivirus keep flagging it?**

A: Windows Defender's ML model may flag executables without an EV code signing certificate. Please add the main program and companion tools to your exclusion list. We plan to purchase an EV certificate when funding allows.

**Q: How accurate is the data?**

A: v7.31 adds combo chain grouping, DOT classification, and skill merging for more precise damage attribution. Godstone and summon damage are included in totals.

---

## Disclaimer

This software is provided solely for technical research and combat data analysis. It calculates combat data exclusively through passive network packet analysis — it does not modify game memory, alter network packets, or provide any form of automation.

Despite its non-invasive design, the game publisher's definition of "third-party tools" may vary. Please review AION2's official policy before use. The developer assumes no legal liability or obligation to compensate for any account restrictions or losses resulting from the use of this software. By running the application, you agree to this disclaimer.

---

## Contact & Support

- Discord: https://discord.gg/x52CBg4rcE
- Email: dont.stop.ha@gmail.com
- Donate (CTBC Bank 822): 7505-4015-7378

Your support keeps this project alive.
