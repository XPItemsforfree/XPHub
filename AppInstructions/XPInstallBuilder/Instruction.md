<div align="center">

```text
+-----------------------------------------------------------------------+
|  [?]  XPInstall Builder - Setup Wizard                        [_][X]  |
+-----------------------------------------------------------------------+
|                                                                       |
|   📦  Package any folder into a 2001-certified Setup.exe              |
|       Zero admin popups. Zero Electron bloat. 100% Tahoma 8.25pt.     |
|                                                                       |
+-----------------------------------------------------------------------+
```

![Windows XP](https://img.shields.io/badge/Aesthetic-Luna%20Beige%20%23ECE9D8-D4D0C8?style=for-the-badge&logo=windows-xp&logoColor=003399)
![.NET 8](https://img.shields.io/badge/Engine-.NET%208.0%20WinForms-0055EA?style=for-the-badge)
![Floppy Disks](https://img.shields.io/badge/Floppy%20Disks%20Required-0-3B9C35?style=for-the-badge)

</div>

---

### 🖥️ What Is This?

**XPInstallBuilder** is a single-file C# setup packager that takes your modern app folder, stuffs it into a `.zip`, slaps a classic Windows XP Setup GUI on top of it, and compiles a standalone **`Setup.exe`**. 

When someone runs your `Setup.exe`, it extracts everything straight into `%LOCALAPPDATA%` (so Windows UAC doesn't have a panic attack) and drops crisp `.lnk` shortcuts on their Start Menu and Desktop.

> 💡 **Fun Fact:** The exact same `.exe` acts as **both** the Builder and the Installer. If it finds an embedded payload inside itself, it puts on its *"Install Wizard"* hat. If not, it opens the Builder. Dual-personality software—just like Windows XP Home vs. Professional.

---

### 💾 System Requirements (To Build `Setup.exe`)

| Component | Requirement | Why? |
| :--- | :--- | :--- |
| **OS** | Windows (x64) | Because `WScript.Shell` shortcuts don't work on a toaster. |
| **SDK** | **.NET 8.0 SDK** (`dotnet` in PATH) | Runs `dotnet publish` behind the scenes to forge your standalone `Setup.exe`. |
| **Source File** | `Program.cs` nearby | The builder searches up to 8 parent folders for `Program.cs` so it can clone its own brain into `Setup.exe`. |
| **RAM** | 128 MB *(64 MB if you close Chrome)* | Strictly for emotional authenticity. |

---

### 🛠️ How to Build a `Setup.exe`

1. **Launch `XPInstallBuilder`**
   * Marvel briefly at that `RGB(236, 233, 216)` beige background.
2. **Choose `Program Folder`**
   * Point it at the folder containing your app and its files.
3. **Choose `Output Folder`**
   * Where your shiny new `Setup.exe` will land (defaults to your Desktop so you can actually find it).
4. **Configure the `Shortcut Editor (%LOCALAPPDATA%)`**
   * **App Name:** What shows up in the title bar (`MyApp - Setup`).
   * **`%LOCALAPPDATA%\<Folder>`:** The exact subfolder where your files will live on the user's PC.
   * **Shortcut Name:** What the `.lnk` file will be called.
   * **Desktop shortcut:** Check this unless you want users losing your app forever in the Start Menu.
   * **File It Opens:** Click **`Pick File...`** and select your main `.exe` inside the Program Folder.
   * **Shortcut Icon (Optional):** Feed it a `.ico` file to brand both `Setup.exe` and the generated shortcut.
5. **Click `Build Setup.exe`**
   * Sit back while it compresses your files, embeds `config.json` + `payload.zip`, and compiles a self-contained `win-x64` binary.

---

### 💿 What Happens When Someone Runs Your `Setup.exe`?

```text
+-------------------------------------------------------------------+
|  [i]  MyApp - Setup                                       [_][X]  |
+-------------------------------------------------------------------+
|  Install MyApp                                                    |
|  Installs files to %LOCALAPPDATA% and creates your shortcut.      |
|-------------------------------------------------------------------|
|  Install Path:                                                    |
|  [ C:\Users\You\AppData\Local\MyApp                           ]   |
|                                                                   |
|  [████████████████████████████████████████████████████] 100%      |
|                                                                   |
|  Created With XPInstall                  [ Install ]  [ Launch ]  |
+-------------------------------------------------------------------+
```

1. User double-clicks **`Setup.exe`**.
2. User clicks **`Install`** -> Files extract, Start Menu & Desktop shortcuts appear, progress bar hits a deeply satisfying `100%`.
3. User clicks **`Launch`** -> Your app boots immediately and the installer politely excuses itself.

---

### ⚠️ Troubleshooting & Error Dialogs

```text
+-------------------------------------------------------------------+
|  [X]  XPInstall - Troubleshooting                           [X]   |
+-------------------------------------------------------------------+
|                                                                   |
|   (X)  "Could not locate Program.cs"                              |
|        Keep Program.cs within 8 folders above the .exe, or the    |
|        builder forgets how to build itself.                       |
|                                                                   |
|   (!)  "Why is it frozen after clicking Build?"                   |
|        It's running a full self-contained .NET publish. Do NOT    |
|        click Build 47 times like it's Internet Explorer 6.        |
|                                                                   |
|   (i)  "Windows SmartScreen is yelling at me!"                    |
|        Unsigned single-file .exes spook Windows Defender. Click   |
|        [More info] -> [Run anyway]. You literally made it.        |
|                                                                   |
|                              [   OK   ]                           |
+-------------------------------------------------------------------+
```

---

<div align="center">
  <sub><i>"It is now safe to distribute your software."</i> — Part of <b>XPHub</b> by <b>XPItemsforfree</b> (MIT License)</sub>
</div>
