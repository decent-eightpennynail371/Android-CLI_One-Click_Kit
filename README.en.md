# Android CLI One-Click Kit (Windows)

> 🇺🇸 English. 🇰🇷 한국어(기본): **[README.md](README.md)**
>
> New to computers / IT? That's fine. If you can **double-click with a mouse**, you can use this. No commands to memorize.

A beginner-friendly kit that lets you **install, use, and remove** Google's official
**[Android CLI](https://developer.android.com/tools/agents/android-cli)** by just **double-clicking `.bat` files** — no typing in a black terminal.

---

## 📑 Table of contents

1. [What is this](#1-what-is-this)
2. [⚡ Quick start (5 min)](#2--quick-start-5-min)
3. [📥 How to download](#3--how-to-download)
4. [📂 Files / folder layout](#4--files--folder-layout)
5. [🧭 Overall workflow (order)](#5--overall-workflow-order)
6. [🛠️ How to install (step by step)](#6-️-how-to-install-step-by-step)
7. [▶️ How to use — the RUN.bat menu](#7-️-how-to-use--the-runbat-menu)
8. [⚙️ How it works (under the hood)](#8-️-how-it-works-under-the-hood)
9. [💻 Command reference](#9--command-reference)
10. [🆘 Troubleshooting](#10--troubleshooting)
11. [🗑️ How to uninstall](#11-️-how-to-uninstall)
12. [📱 Android Studio (optional — virtual phone)](#12--android-studio-optional--virtual-phone)
13. [🔒 Security & operational notes](#13--security--operational-notes)
14. [📜 License](#14--license)

---

## 1. What is this

- **Android CLI** = Google's **official command-line tool** (v1.0, May 2026) for creating Android projects, managing the SDK, searching official docs, etc. It's designed for AI agents (e.g. Claude, Codex, Gemini).
- **This kit** = a **thin wrapper that automates install/use/remove**. The tool itself is downloaded from **Google's official servers (`dl.google.com`)**. The kit hides nothing and sends nothing.

> In one line: **"a helper that lets you use Android CLI by double-clicking, with no commands."**

## 2. ⚡ Quick start (5 min)

1. Download this kit and unzip it → [3. How to download](#3--how-to-download)
2. In the folder, double-click **`시작하기.bat`** (Start Here) → read the screen and choose **`2`** (Install)
   - (Or just double-click `INSTALL.bat` directly.)
3. After install, double-click **`RUN.bat`** → pick an action from the numbered menu
4. To remove it later, double-click **`UNINSTALL.bat`**

> 💡 A blue warning or a Windows permission prompt may appear during install. That's **normal** → see [10. Troubleshooting](#10--troubleshooting).

## 3. 📥 How to download

1. On this GitHub page, click the green **`Code`** button → **`Download ZIP`**
2. Right-click the ZIP → **"Extract All"** → extract the **whole folder**
   - ⚠️ Extract the **entire folder**. The `lib` folder must stay with the `.bat` files.
3. Open the extracted folder and double-click **`시작하기.bat`** to start.

> Put it in a normal folder (Desktop, Documents). No admin-only folders needed.

## 4. 📂 Files / folder layout

```
Android-CLI_One-Click_Kit/
├── 시작하기.bat        ← Start Here (orientation + quick-launch menu)
├── 자가진단.bat        ← (optional) self-check, installs nothing
├── INSTALL.bat         ← install
├── RUN.bat             ← use (numbered menu)
├── UNINSTALL.bat       ← remove
├── lib/                ← actual scripts (do NOT delete or move!)
│   ├── common.ps1      · shared helpers (path detect · markers · PATH backup)
│   ├── welcome.ps1     · Start Here screen
│   ├── selfcheck.ps1   · self-check
│   ├── install.ps1     · install logic
│   ├── menu.ps1        · menu logic
│   └── uninstall.ps1   · uninstall logic
├── README.md           ← Korean doc (primary)
├── README.en.md        ← this file (English)
├── 왕초보_시작_가이드.md  ← extra beginner walkthrough (Korean)
└── LICENSE             ← Apache License 2.0
```

- The **`.bat`** files are tiny English launchers; all Korean UI and logic live in the **`.ps1` files under `lib`**.
- ❗ **If you delete `lib` or move a `.bat` out of the folder, it won't work** (it will tell you clearly).

## 5. 🧭 Overall workflow (order)

```
시작하기.bat  →  (optional) 자가진단.bat  →  INSTALL.bat  →  RUN.bat (use)  →  UNINSTALL.bat
 Start Here          self-check (no install)     install        numbered menu        clean removal
```

- **시작하기.bat (Start Here)**: shows the click order and lets you launch install/use/remove/check right there — the single front door.
- **자가진단.bat (self-check)**: installs nothing; checks Korean display, required tools, internet, and install status.

## 6. 🛠️ How to install (step by step)

1. Double-click **`INSTALL.bat`** (or `시작하기.bat` → `2`)
2. A black window shows "download/install may take 1–2 minutes" → **don't close it; wait.**
3. If a **blue warning** ("Windows protected your PC") appears → click **"More info"** → **"Run anyway"**. It's a Google official tool, so it's safe.
4. A **Windows permission prompt** may appear once (when using winget) → **"Yes / Allow".**
5. When you see `설치 완료!` (Install complete) and the location, you're done. Next, double-click **`RUN.bat`**.

> The method is chosen automatically: **`winget`** (Windows Package Manager) if present, otherwise Google's official **`curl`** script (no admin needed).

## 7. ▶️ How to use — the `RUN.bat` menu

Double-click `RUN.bat` to get a numbered menu. **Type a number and press Enter.**

| # | Action | Notes |
|---|---|---|
| **1** | Check install / status | Shows location & version briefly |
| **2** | Create a new project | Practice app folder (just Enter → `MyAndroidApp`) |
| **3** | Manage Android SDK | List / install / update dev components |
| **4** | Add skills | Add official helper skills to the current folder |
| **5** | Search docs | Search the official Android docs |
| **6** | Update | Update the Android CLI tool |
| **7** | Show help | Full `android` help (for developers, English) |
| **8** | [Note] Emulator | Virtual phone is via item 10 (Android Studio) |
| **9** | Plain explanation | "What is all this?" in simple terms |
| **10** | Get Android Studio | (optional) open the latest-stable download page + steps |
| **0** | Exit | Close the menu |

> 💡 First time? Try **`9`** (explanation) → **`1`** (status). This menu has **no delete function**. (Removal is only `UNINSTALL.bat`, which asks `yes` first.)

## 8. ⚙️ How it works (under the hood)

- **Install (`INSTALL.bat`)**: runs `winget install --id Google.AndroidCLI` or Google's official `curl.exe ... install.cmd` **in a cmd context**. `android.exe` typically lands in `C:\Users\<you>\AppData\AndroidCLI` and that path is added to your **User PATH**. The method/path used is recorded in `%LOCALAPPDATA%\android-cli-one-click-kit\` (used at removal).
- **Use (`RUN.bat`)**: wraps the installed `android` command in a Korean numbered menu.
- **Remove (`UNINSTALL.bat`)**: prefers the recorded install path and removes **only the folder and PATH entry it created**, after a safety check. PATH changes are backed up. **SDK data downloaded by `android sdk` (e.g. `.android`) is left untouched.**
- **Encoding**: `.bat` files are ASCII-only (so Korean never breaks in cmd); Korean UI is handled by UTF-8 PowerShell scripts.

## 9. 💻 Command reference

You don't need to type these (the menu does it), but for reference (menu `7` shows full help):

| Command | What it does |
|---|---|
| `android create` | Create a new Android project |
| `android sdk` | Install / list / update / remove SDK packages |
| `android skills` | Add / list / find / remove official skills |
| `android docs search` | Search official docs |
| `android run` | Deploy (run) an app on a device |
| `android emulator` | Manage virtual devices *(disabled in this CLI on Windows)* |
| `android info` | Print environment info (SDK location, version) |
| `android update` | Update the Android CLI tool |
| `android studio` | Android Studio integration *(requires Studio)* |
| `android --version` | Print version |

## 10. 🆘 Troubleshooting

| Symptom | Fix |
|---|---|
| **Nothing happens / window flashes and closes** | Just double-click (no admin). If it still fails, screenshot and ask for help. |
| **Blue warning ("Windows protected your PC")** | Click "More info" → "Run anyway". It's a Google official tool, safe. |
| **`Cannot find: lib\...ps1`** | You moved the `.bat` out, or unzipped only part. **Re-extract the whole folder.** |
| **Install seems stuck** | Download takes 1–2 min. Even if text pauses, **don't close**; wait. |
| **Installed but RUN says "not installed"** | Close and re-open `RUN.bat`, press `1` (PATH refresh). |
| **Korean shows as boxes (□) / question marks (?)** | Check via `자가진단.bat` item [1]. Very old Windows may need a terminal font change. |
| **Emulator (virtual phone) doesn't work** | This CLI's emulator is disabled on Windows. Use menu `10` to get **Android Studio**. → [Section 12](#12--android-studio-optional--virtual-phone) |

## 11. 🗑️ How to uninstall

1. Double-click **`UNINSTALL.bat`**
2. Check the shown location → type **`yes`** once
3. The install folder and PATH entry are removed; you'll see `제거 완료!` (Removed).

- If installed via `winget`, it's removed cleanly with `winget`.
- **SDK data** downloaded by `android sdk` is **preserved** (may be shared data; kept for safety).
- If PATH was changed, the original is backed up to:
  `%LOCALAPPDATA%\android-cli-one-click-kit\path-backup.txt`

## 12. 📱 Android Studio (optional — virtual phone)

- **Android Studio** is a large IDE (~1.5 GB) and is **optional** — **not required** to use this kit.
- However, to run a **"virtual phone (emulator)" on Windows**, Android Studio is effectively required (this CLI's emulator is disabled on Windows).
- To get it: `RUN.bat` → **`10`** → the official download page opens → big "Download Android Studio" button → pick **`.exe` (recommended)** → check the license agreement → download → double-click the `.exe` → Next/Install → Finish.
- ⚠️ Android Studio is **NOT removed** by this kit's `UNINSTALL.bat` (use its own uninstaller).

## 13. 🔒 Security & operational notes

- **No login, API key, or password needed.** The kit stores/sends no secrets.
- All downloads happen only over **HTTPS from Google's official servers (`dl.google.com`)**.
- Install method: `winget` (signed package, preferred if present) or Google's official `curl` script.
  - ℹ️ The build machine had no winget, so only the **curl path was actually verified**. The **winget path is unverified**.
- **No admin rights needed** — just double-click.
- **Do not delete or move the `lib` folder.** The kit won't work without it.
- This kit is an **unofficial helper, not affiliated with Google**.

## 14. 📜 License

Kit scripts: **Apache License 2.0** — copyright holder **SoDam AI Studio** ([LICENSE](LICENSE)).
The Android CLI and [android/skills](https://github.com/android/skills) follow their own licenses (Apache-2.0).

---

For an even gentler step-by-step (Korean), open **[왕초보_시작_가이드.md](왕초보_시작_가이드.md)**.
