---
title: "Built-in Features & Commands"
weight: 5
---

### **List of Built-in Commands**

The Dev Console comes packed with several essential commands out-of-the-box:

| Command | Description |
|---------|-------------|
| `help` | Prints all available commands in a formatted table. |
| `aliases` | Prints all registered command aliases in a formatted table. |
| `alias <shortcut> <target_command>` | Creates a command alias shortcut. |
| `bind <key> <command>` | Binds a key to a console command. |
| `unbind <key>` | Removes a key binding. |
| `binds` | Lists all active key bindings. |
| `clear` | Clears the console log view. |
| `quit` | Exits the application (stops Play mode in Editor). |
| `version` / `info` | Shows game version and Unity engine version. |
| `sysinfo` | Displays OS, CPU, GPU, and RAM hardware information. |
| `time.scale <value>` | Sets `Time.timeScale` to speed up, slow down, or pause the game. |
| `gravity <Vector3>` | Sets `Physics.gravity` using Vector3 syntax. |
| `fps.show` | Toggles the built-in minimal FPS counter overlay. |
| `gc` | Forces a full managed garbage collection pass. |
| `say <message>` | Echoes a message to the console (supports HTML rich text tags). |
| `scene.load <name>` | Loads a scene by name or build index. |
| `scene.restart` | Reloads the currently active scene. |

### **Log Formatting & Filtering**

The console intercepts standard Unity logs and renders them gracefully:
*   Each log includes a high-precision `[HH:mm:ss]` timestamp.
*   Logs are badge-labeled with `[INFO]`, `[WARNING]`, `[ERROR]`, or `[OK]`.
*   A search bar on the top-right allows instant filtering of logs by text.
*   Toggle buttons let you quickly show or hide Warnings and Errors.
*   The `[-] 100% [+]` buttons allow you to dynamically zoom the text size of the logs from 50% to 300%.

### **Execution Profiling & Auto-Success**

Whenever you execute a command, the console automatically profiles its runtime and prints it cleanly in cyan (e.g. `[0.4ms]`). 

If a method returns `void` and produces no logs of its own, the console is smart enough to generate a generic success log (`[OK] MyCommand executed successfully.`) so you always have visual confirmation that your action actually fired!
