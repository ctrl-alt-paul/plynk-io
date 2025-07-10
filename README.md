# 🎮 PLYNK-IO — Player Link, Input Output

[![Buy Me a Beer](https://github.com/ctrl-alt-paul/plynk-io/blob/main/buymeabeer.png)](https://buymeacoffee.com/ctrl_alt_paul)  
[![Sponsor on GitHub](https://img.shields.io/badge/Sponsor%20on-GitHub-%23EA4AAA?logo=github)](https://github.com/sponsors/Ctrl-Alt-Paul)

[📖 **View the full PLYNK-IO Wiki →**](https://github.com/ctrl-alt-paul/plynk-io/wiki)

**PLYNK-IO** is a gloriously overengineered I/O control system for emulated arcade games. It hijacks game data in real time — from memory addresses to emulator broadcasts — and lets you fire it off to real-world devices like LEDs, serial devices, WLED devices, motors, solenoids, and anything else you can bolt to a cabinet.

It happily listens to **MAME**, **TeknoParrot** (via Boomslangnz’s legendary OutputBlaster), and any other emulator shouting out `WM_COPYDATA`.  Or, if you’re the kind of person who enjoys living dangerously, you can skip the messages and rip data straight from memory using the magic you pulled from your favourite CheatEngine voodoo.

PLYNK-IO also supports **GitHub-integrated Community Profiles** — because what’s better than your own overengineered setup? Everyone else’s. You can browse, download, and contribute memory and message profiles directly from within the app. Submit yours to the hive mind, vote on the good stuff, and skip the painful trial-and-error when someone else has already mapped every byte of weirdness for your game. It’s crowdsourced chaos, version-controlled.

Many, many hours (and probably too much caffeine) have gone into getting this first release to a point where it doesn’t explode on launch. But this is just the beginning — if you’ve got suggestions, feature ideas, or spot something that needs fixing, I’m all ears. PLYNK-IO is built to grow, evolve, and get weirder — with your help.

Whether you’re just lighting up a few buttons or building a feedback system that could scare small pets, PLYNK-IO turns software into hardware chaos — in all the best ways.

Also in the works is PLYNK, a frontend game launcher (think LaunchBox, but less bloated and more sync-happy) designed specifically for multi-machine setups and linked arcade play. It’s another part of the same glorious mess — the expanding PLYNK family.

## 🚀 Features at a Glance

- 🧠 **Memory Reader** — poll live game data from RAM using process injection  
- 💬 **Message Listener** — intercept `WM_COPYDATA` broadcasts from MAME and other emulators  
- 🧩 **Game Profiles** — bundle memory + message mappings and assign them to running processes  
- ⚙️ **Device Support** — output to:
  - 🎛️ **PacDrive** (USB LED controllers)  
  - 🔌 **Serial Devices** (COM-port microcontrollers)  
  - 🌈 **WLED** (Wi‑Fi LED strips and effects)  
- 🧪 **Value Transforms** — manipulate any input with inline JavaScript (math, conditions, logic)  
- 🎨 **LED Effects** — fully map game values to segment colours, brightness, and animation profiles  
- 📈 **Live Dashboard** — monitor game data, output activity, device health and logging in real time  
- 📦 **JSON Config Profiles** — portable, shareable, editable outside the app
- 🌐 **GitHub Community Integration** — submit, browse, import, and vote on memory/message profiles  
  - 🗳️ **Feedback System** — vote ✅ 🟡 ❌ on community profiles and leave feedback in-app  
  - 🧾 **Profile Submission Tools** — submit your own profiles to GitHub directly from the app  
- 📡 **Live Log System** — 16 categories, filterable, stream-based, and exportable  
- 🧠 **Auto Profile Detection** — identifies running games via process or messages  
- 🪝 **Pointer Chain Support** — for deep memory lookups and dynamic addresses

---

## 🛠️ Built With

| Layer             | Stack                                              |
|-------------------|----------------------------------------------------|
| Frontend          | React 18 + TypeScript + Vite                       |
| UI Styling        | Tailwind CSS + Shadcn UI                           |
| Desktop Platform  | Electron (Node.js + Chromium)                      |
| Native Layer      | C++ modules for WM_COPYDATA interception           |
| Devices Supported | Serial (COM), USB HID (PacDrive), HTTP (WLED)      |
| IPC Layer         | Electron IPC bridges between UI and device logic   |

---

## 📷 Core Modules

### 🖥️ Dashboard
Your real-time control panel:
- Displays live connection status for all devices and active processes
- Monitors outputs: current value, raw value, mapped device, and channel
- Offers toggles for memory polling and message listening
- Category-based logging with colour-coded channels
- Realtime memory + message state, polling health, and timeout detection

---

### 🎮 Game Manager
The heart of the app:
- Bind a process name (e.g. `mame64.exe`, `d1a.exe`) to a game profile
- Link memory + message profiles and assign their outputs to specific hardware
- Supports JavaScript transformations (`value > 50 ? 255 : 0`, etc.)
- Supports active/inactive toggles, duplication, and profile inheritance

---

### 🔍 Memory Manager
Fine-tuned memory extraction:
- Attach to a running process and scan absolute, module-relative, or pointer-chain addresses
- Supports multiple data types: Int, Float, Double, Byte, etc.
- Apply bitmasks, formatting, and inversion
- Uses polling intervals (1ms–5s) and value caching
- Visual inspection of raw vs transformed vs output value
- GitHub Community Profile system: submit, browse, vote, and comment

---

### 💬 Message Manager
WM_COPYDATA handler built for MAME-style output:
- Listens for Windows messages on a hidden native window
- Maps key-value pairs to output labels (`id_2`, `id_34`, etc.)
- Triggers hardware dispatch in real-time
- Supports `__MAME_START__` and `__GAME_NAME__` reserved keys
- Reusable profiles for message-based output
- GitHub Community Profile system: submit, browse, vote, and comment

---

### ⚙️ Device Manager
Bridge to the physical world:
- **PacDrive**: USB discovery, test outputs, assign channels
- **Serial**: COM port selection, baud rate, handshaking, test signal dispatch
- **WLED**: IP-addressed, rules-based light control, segment mapping, full effect library access
- Device detection, connection status, diagnostics, and inline configuration

---

### 🌈 WLED Profiles
Advanced lighting logic:
- Rule-based profiles triggered by memory or message values
- Supports `exact`, `range`, and `threshold` rule types
- Define segments, effect IDs, brightness, and RGB colour
- Can control multiple segments from a single game variable
- WLED config import support

---

### 🌐 GitHub Community Profiles
Submit, browse, and vote on game profiles directly within the app.
- **Submit Profiles** — Share your memory or message profiles with the community. Adds a new GitHub issue with full metadata and JSON payload.
- **Browse Community** — Explore shared profiles with vote counts, status labels, and import options. Filter by game name, emulator, or contributor.
- **Vote on Accuracy** — Rate profiles as ✅ Working, 🟡 Partial, or ❌ Not Working. Add feedback to help other users.
- **Secure OAuth** — GitHub login via device flow. Only public permissions are requested. Tokens are stored locally and encrypted.
- **Memory & Message Support** — The community system supports both Memory and Message profiles with the same submission and feedback workflow.
> Every vote strengthens the community database — don’t just import, contribute!

---

### 📜 Logging System
Custom-built for internal diagnostics:
- 16 log categories: memory, message, WLED, dispatch, GitHub API, and more
- Color-coded filtering UI with toggles per type
- Real-time streaming via Electron IPC
- Auto-scroll, virtualization, consolidation, and export to file
- Performance-friendly for high-volume debug use

---

## 🧠 Data Flow

```
Game (Emulated) 
  └── Memory Read ➜ Transform ➜ Output Mapping ➜ Hardware
  └── Message Event ➜ Parse ➜ Transform ➜ Output Mapping ➜ Hardware
```

---

## 💡 Ideas for Future Versions

- Scripting
- WebSocket or UDP device output (for ultra low-latency)  
- Input signal mapping (buttons, encoders → game actions)  
- GUI-based LED segment preview and effect testing  
- Screen monitoring  
- Profile sync to cloud or GitHub Gist  
- Replay & visualise logged output sessions

---

## 💡 Inspiration

PLYNK‑IO draws from legends in the emulator‑to‑hardware space:

- **Boomslangnz (OutputBlaster)** – the real‑time output wizard whose work influenced PLYNK‑IO architecture  
- **Howard_Casto (MameHooker)** – pioneer of message‑driven hardware mapping in emulators

---

## 🙏 Special Thanks

A huge shout-out to:

- **Boomslangnz** – creator of OutputBlaster  
- **Howard_Casto** – mastermind behind MameHooker  
- **Aaron Giles** – whose emulator output code laid much of the groundwork

Your work lit the fuse for PLYNK‑IO — thank you!

---

## 📜 License

MIT License  
© 2025 [**CtrlAltPaul**](https://github.com/CtrlAltPaul)

Use it, mod it, share it. Just don’t blame me if you blow up a LED strip while racing.

---

## 🦾 Built By

Created by **CtrlAltPaul**, for people who love arcade rigs, cables everywhere, and watching their desk light up like Tokyo in the rain.

> _“Reads memory like a psychic. Slaps LEDs like a DJ. Powers feedback like Zeus with a USB cable.”_

---

## 📫 Get Involved

If this made your rig cooler, raise an Issue, submit a PR, or just star the repo.  
Have an idea? Hit me up on GitHub or Reddit: **@CtrlAltPaul**

---
