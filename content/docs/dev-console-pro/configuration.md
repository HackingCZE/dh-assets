---
title: "Configuration & Project Settings"
weight: 4
---

### **Project Settings Hub**

Every behavior and visual aspect of the Dev Console Pro can be cleanly managed from the Unity Editor.

Navigate to **Edit → Project Settings → Dev Console Pro** to access the settings panel. All settings feature detailed hover tooltips explaining what they do.

#### **UI & Layout Configuration**
*   **Syntax Position Options:** You can independently configure where the parameter hints (e.g. `<X> <Y> <Z>`) and the colored live syntax overlay render. Choose to dock them at the top of the command panel or have them float cleanly right above your input bar.
*   **Default Log Zoom:** Define the default zoom/font size (from 50% to 300%) for the logs in the right panel. The top bar also dynamically wraps its buttons seamlessly when resizing!
*   **Console Height & Panel Ratio:** Control exactly how much screen space the console uses and how wide the left (command list) and right (log view) panels are.
*   **Zebra Striping:** Enable a premium dark slate zebra-striping aesthetic on the panels to dramatically improve readability.

#### **Behavior & Logic**
*   **Toggle Key:** Change the key used to open/close the console (Default is `~` / BackQuote).
*   **Reflection Fallback:** Toggle the ability to execute raw C# expressions via Reflection. You can disable this in shipped release builds if you are worried about security/exploits.
*   **Pause While Open:** When enabled, the console automatically sets `Time.timeScale = 0` while open, effectively freezing the game, and restores it when closed.
*   **Fuzzy Search Strictness:** Control how lenient the autocomplete algorithm is when matching your typos.

#### **Logging Options**
*   **Intercept Unity Logs:** When enabled, all native `Debug.Log`, `Debug.LogWarning`, and `Debug.LogError` calls throughout your entire codebase will be intercepted and cleanly formatted inside the in-game Dev Console with rich timestamps and type badges.
*   **Filter Defaults:** Control which log types (Info, Warning, Error) are visible by default when the console opens.

### **Command Aliases**
Aliases act as shortcuts. You can map long, complex commands to short, easy-to-type abbreviations.

*   You can set these in the Project Settings panel under the **Command Aliases** section.
*   Or configure them at runtime by typing `alias <shortcut> <target_command>` in the console.

### **Keybindings**
You can bind any console command to a keyboard key so it executes instantly without having to open the console!

*   You can configure these in the Project Settings panel.
*   Or at runtime via the console by typing `bind F1 "time.scale 0"`.
*   These are saved securely via a persistent `ScriptableObject` so your keybinds carry over between sessions.
