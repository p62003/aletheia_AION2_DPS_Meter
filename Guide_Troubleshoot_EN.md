# Troubleshooting Guide

## Program Cannot Capture Data

### Quick Diagnostic Flowchart

```
Can the program launch?
├─ No → See "A. Program Cannot Launch"
└─ Yes
    Does the overlay show an ms value?
    ├─ No (always shows --ms) → See "B. No Packets At All"
    └─ Yes (has ms value)
        Does the ranking react at all after attacking? (including unnamed entries)
        ├─ No reaction at all → See "B2. Latency Present But No Data"
        └─ Reacts but incorrectly
            What color is the nickname indicator?
            ├─ Gray → See "C. Nickname Auto-Detection In Progress"
            ├─ Orange → See "D. Nickname Awaiting Match"
            └─ Green → See "E. Packets Normal But No Damage Data"
```

---

### A. Program Cannot Launch

**Symptoms**: Crashes immediately after double-clicking, no window appears, error messages

| Cause | Solution |
|-------|----------|
| **Npcap not installed** | Go to https://npcap.com to download and install Npcap (check WinPcap API compatibility mode) |
| **Outdated Npcap version** | Uninstall the old version and reinstall the latest Npcap |
| **Missing system components** | Install Visual C++ Redistributable (x64) |
| **Windows Defender blocking** | Packet capture tools are easily flagged by Windows Defender. Follow the steps below to add the entire program directory to exclusions |

**Windows Defender Exclusion Steps** (try this first when the program is unresponsive or crashes):

1. Right-click desktop → **Display settings**
2. Left side → **Privacy & security** → **Windows Security**
3. **Virus & threat protection** → **Manage settings**
4. Scroll down to "**Exclusions**" → **Add an exclusion** → **Folder**
5. Select the entire directory containing the program (e.g., `D:\Aletheia_DPS_Meter`)
6. Restart the program

> Users with other antivirus software (Kaspersky, Avast, Norton, etc.) should add the program directory to the whitelist in their respective software.

**Troubleshooting method**: Open Command Prompt (cmd) in the program's folder, type the program name to run it, and check the error messages.

---

### B. No Packets At All (ms shows --ms)

**Symptoms**: Program launches normally, but latency always shows `--ms` while the game is running

**Cause**: The packet capture layer cannot receive game traffic

| Cause | Solution |
|-------|----------|
| **Not running as administrator** | Right-click → Run as administrator (packet capture requires admin privileges) |
| **Npcap installed without compatibility mode** | Reinstall Npcap and check "Install Npcap in WinPcap API-compatible Mode" |
| **Using VPN/accelerator** | The program is already auto-compatible with most accelerators. If issues persist, see "B2 Step 3" |
| **Game not connected** | Confirm the game has logged in to character select or entered the game world (main menu/update screens have no game packets) |
| **Firewall blocking** | Windows Defender Firewall → Advanced settings → Confirm the program is not blocked in inbound rules |
| **PPPoE dial-up connection** | See "F. Known Limitations — PPPoE" |

---

### B2. Latency Present But No Data

**Symptoms**: ms has a value, but the ranking shows absolutely no reaction after attacking — not even unnamed entries

**What does this mean?**
An ms value means the program can see the packets you "send out" and the server's acknowledgment responses, but it **does not mean** the program can fully read the game data returned by the server. These are separate things.

**Try the following steps in order:**

**Step 1 — Reinstall Npcap**
1. Completely close the program and the game
2. Control Panel → Uninstall Npcap
3. Go to https://npcap.com to download the latest version
4. During installation, **make sure to check**:
   - ☑ Install Npcap in WinPcap API-compatible Mode
   - ☑ Support loopback traffic
5. Restart your computer after installation
6. Launch the program as administrator, then start the game and test

**Step 2 — Disable Network Offloading Features**

Windows network optimizations may cause the capture tool to see incomplete packets:

1. Open "Device Manager"
2. Expand "Network adapters" → right-click your internet-connected adapter → Properties
3. Switch to the "Advanced" tab
4. Find and **disable** the following items (not all may be present):
   - Large Send Offload v2 (IPv4) → Disabled
   - Large Send Offload v2 (IPv6) → Disabled
   - TCP Checksum Offload (IPv4) → Disabled
   - Receive Segment Coalescing → Disabled
5. Click OK → retest

> After disabling, if the program works correctly, you can re-enable them one by one to identify which setting caused the conflict.
> These settings only affect performance optimization; disabling them will not affect normal internet usage.

**Step 3 — Game Accelerators (ExitLag, GearUP, Leigod, UU, Xunyou, etc.)**

The program has built-in universal accelerator compatibility and will automatically detect accelerator proxy connections and choose the correct sniffing method. In most cases, **no additional configuration is needed**.

If data still cannot be captured while using an accelerator:

**Option A — Verify startup order**:
1. Start the accelerator and connect first
2. Then start the game and reach the character screen
3. Finally start this program

> The program analyzes the game's network connections at startup, so the game must already be connected.

**Option B — Use the diagnostic tool**:
1. Main window toolbar → click the "Diagnose" button
2. Follow the on-screen instructions for a self-check
3. Attack a monster during the test window
4. Check if the results pass

> If the self-check passes but the main program still doesn't work, it may be a different issue (see Steps 4, 5).
> If the self-check also fails, send the generated environment diagnostic report (JSON saved to desktop) to the developer.

**Option C — Verify Npcap Loopback support**:
- Most accelerators forward game traffic through localhost proxy
- The program needs Npcap's Loopback sniffing capability to capture this traffic
- When reinstalling Npcap, make sure to check "**Support loopback traffic**"

**Option D — Temporarily disable the accelerator to test**:
1. Completely exit the accelerator
2. Connect directly and launch the program to test
3. If direct connection works normally → confirms it's an accelerator compatibility issue
4. Send the diagnostic tool's environment report to the developer

**Step 4 — Verify Network Interface**

If your computer has multiple network adapters (e.g., both wired and wireless), the packet capture tool may be reading the wrong interface:

1. Confirm which connection the game is using (wired / Wi-Fi)
2. Temporarily disable unused network adapters:
   - Settings → Network & Internet → Advanced network settings
   - Disable unused adapters
3. Restart the program and test

**Step 5 — Antivirus/Security Software**

Some antivirus software may intercept or modify network packets:

1. Temporarily disable the "Network Protection" or "Packet Inspection" feature of your antivirus
2. Add this program to your antivirus software's whitelist/exclusion list
3. Retest

**If none of the above works**: Please report your system information (see "Contact Support" at the bottom). The developer will need to investigate further.

---

### C. Nickname Auto-Detection In Progress (Gray Indicator ●)

**Symptoms**: ms has a value, but the overlay title shows default text, ranking is blank

**Cause**: The program has not yet detected your game nickname from packets

**Solution**:
1. Confirm the game is logged in and you've entered the game world
2. Perform a scene transition (Loading) — e.g., teleport, enter a dungeon, switch channels
3. After the scene transition, attack any target
4. The program will automatically extract the nickname from packets; the indicator should turn green within seconds

> Nickname detection is fully automatic — no manual input needed. The program identifies your character through game packets (3336 opcode).

---

### D. Nickname Awaiting Match (Orange Indicator ●)

**Symptoms**: ms has a value, nickname detected, indicator is orange, ranking is blank

**Cause**: Nickname detected but the corresponding actor_id has not yet been found in packets

| Scenario | Explanation |
|----------|-------------|
| **Just entered a scene** | Normal behavior. After attacking or being attacked, the program can match your actor_id from packets |
| **During scene transition** | actor_id is reassigned after scene transitions; another attack is needed to re-match |

**Solution**: Attack any target once. The indicator should turn green within seconds.

---

### E. Packets Normal But No Damage Data (Green Indicator ●)

**Symptoms**: ms has a value, nickname matched (green indicator), but ranking doesn't update after attacking targets

| Cause | Solution |
|-------|----------|
| **Global mode requires class identification** | Global rankings only show characters with "nickname + class" identified. Initially, you may need to attack a few more times for the program to detect your class |
| **Timer mode already settled** | Timer mode auto-settles 10 seconds after the last attack (title turns red + ✓). Click the reset button ↻ to start a new timer |
| **Dungeon mode not triggered** | After entering a dungeon, the first attack is needed to trigger dungeon mode and start calculations |

---

### F. Known Limitations

| Limitation | Description |
|------------|-------------|
| **Xunyou Accelerator** | Xunyou routes game traffic to a proxy port on the local machine's physical IP (not localhost). This traffic doesn't pass through the physical network cable, so Npcap cannot capture it. This is a Windows networking architecture limitation, not a bug in this program. **Recommendation**: Switch to another verified accelerator (ExitLag, Leigod, UU, GearUP, LagoFast) |
| **HiCn Dolphin Accelerator** | HiCn intercepts packets at the WFP/NDIS driver layer, making them invisible to Npcap. **Recommendation**: Switch to another verified accelerator |
| **PPPoE dial-up (computer-side dial)** | See "F-1. Computer-Side PPPoE Dial-Up" below |
| **Timer + BOSS mode overlap** | Entering a BOSS fight while in Timer mode may cause both modes to run simultaneously |

---

### F-1. Computer-Side PPPoE Dial-Up (Cannot Capture Data)

**What is this?**

"PPPoE dial-up" is an internet connection method commonly used with Taiwan's Chunghwa Telecom, FarEasTone, and Taiwan Mobile broadband/fiber optic services (HiNet FTTX/ADSL).
The key isn't "whether you use PPPoE" but "**who is performing the dial-up**":

| Where the dial happens | Can the program work? | Explanation |
|---|---|---|
| **Router dials** (most common) | ✅ Normal | The modem/ONT connects to a wireless router (ASUS, TP-Link, Xiaomi, etc.), and the router handles the PPPoE login. Your computer sees a normal home network |
| **Computer dials directly** (rare) | ❌ Cannot capture | The modem connects directly to your computer's network port, and you must click "Broadband Connection" and enter credentials each time you boot up |

**Why does computer-side dial-up fail?**

When the computer dials itself, game traffic goes through Windows' built-in "**Broadband Connection**" virtual interface, and the packet capture library used by Aletheia (Npcap) **cannot see** this virtual interface — this is a Windows system-level limitation, not a program bug. In the same scenario, if the router handles the dial-up instead, the computer sees normal Ethernet traffic, and the program can capture it normally.

---

**How to determine which type you have?**

The quickest way — check whether you **need to manually click "Broadband Connection" after booting up** to get online:

- ✅ Internet works immediately after booting — open a browser and it works → **Router dial-up** (this isn't your issue; see other sections)
- ❌ You need to click the "Broadband Connection" icon on your desktop and enter credentials after booting → **Computer-side dial-up** (this is your issue)

Or a more definitive method:
1. Press `Win + R`, type `ncpa.cpl`, press Enter
2. The window that opens lists all network connections on your computer
3. If there's an entry called "**Broadband Connection**" with a "Connected" status → it's computer-side dial-up

---

**Solution — Move the dial-up to the router**

You'll need: a wireless/wired router. If you already have one but are only using it as a Wi-Fi AP, it can be reconfigured.

**Simple steps**:

1. **Get your credentials**: Find the PPPoE username and password you currently use for dial-up (the one from your ISP). If you've forgotten them, call customer service or check the ISP's member website
2. **Rewire**: Unplug the network cable from your computer that connects to the ONT (modem), and plug it into the router's **WAN port** (usually labeled WAN or in a different color)
3. **Connect computer to router**: Use another network cable from the router's **LAN port** to your computer (or connect via Wi-Fi to the router)
4. **Access router settings page**: Open a browser, enter `192.168.1.1` or `192.168.0.1` in the address bar (depends on the router brand — usually printed on the back), and enter the router admin credentials
5. **Find WAN/Internet settings**: Select the connection type as "**PPPoE**", enter the credentials from step 1, and save
6. **Remove the computer's "Broadband Connection"**: `Win + R` → `ncpa.cpl` → right-click "Broadband Connection" → Delete (or Disable)
7. **Reboot and test**: Your computer should be able to get online without any manual action. Launch the game and Aletheia — everything should work normally

> 💡 **Not sure how to do this?** Just call your ISP's customer service and say "I want to move the PPPoE dial-up from my computer to my router." They'll help. Or ask a tech-savvy friend — the whole process usually takes less than 10 minutes.

> ⚠️ **Why can't the program just support this directly?** Technically, it would require rewriting the core packet capture architecture to parse PPPoE frames. This is a future improvement being evaluated but needs time to validate. For now, please use the above workaround.

---

### G. Other Common Issues

| Symptom | Cause | Solution |
|---------|-------|----------|
| **Abnormally high DPS values** | Damage concentrated in the first few seconds | Observe cDPS (combat average) instead of instantaneous DPS |
| **Overlay won't drag** | Lock feature is enabled | Click the lock button in the overlay's top-right corner to unlock |
| **Overlay position at top-left** | The program auto-positions the overlay to the game window's top-left on each launch | Drag it to your preferred position; it will be remembered for the current session |
| **Some text unchanged after switching language** | Some panels need to be reopened | Close and reopen the overlay or combat details panel |

---

## Contact Support

If none of the above steps solve the problem, please provide the following information:

1. **Diagnostic report** (Main window toolbar → "Diagnose" button → Run environment diagnostics → JSON file on desktop)
2. **Operating system version** (Windows 10/11, 64-bit)
3. **Npcap version** (Control Panel → Programs and Features → find Npcap)
4. **Network connection type** (wired / Wi-Fi / accelerator name / PPPoE dial-up)
5. **Whether running as administrator**
6. **Overlay indicator color and ms value**
