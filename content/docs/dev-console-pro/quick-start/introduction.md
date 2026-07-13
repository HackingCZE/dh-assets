---
title: "Getting Started"
weight: 2
---

### **Zero-Setup Installation**

The Dev Console Pro requires absolutely zero scene setup. There are no prefabs to drag into your canvas, no EventSystems to configure, and no UI elements to instantiate.

1. Import the **Dev Console Pro** package into your Unity Project.
2. Enter **Play Mode** in the Unity Editor (or build your game).
3. Press the **`~` (Tilde/BackQuote)** key on your keyboard to instantly open the console.

### **Basic Usage**

*   **Toggle Console:** Press `~` to open or close the console (this key can be changed in Project Settings).
*   **Submit Command:** Type a command and press `Enter`.
*   **Autocomplete:** Type part of a command and press `Tab` to autocomplete. Pressing `Tab` multiple times will cycle through available options.
*   **Navigate History:** Use `Shift + Up Arrow` and `Shift + Down Arrow` to cycle through previously executed commands.
*   **Quick Help:** Type `help` to see a fully formatted table of all registered built-in and custom commands.

### **The Reflection Evaluator Fallback**

If you type a command that isn't explicitly registered via the `[Command]` attribute, the Dev Console will attempt to evaluate it as raw C# code using Reflection.

```csharp
// Example Reflection Commands you can type directly into the console:
Time.timeScale = 0.5
Application.targetFrameRate
Debug.Log("Hello from console!")
Screen.width
```
This incredibly powerful feature allows you to debug and modify internal engine state or your game's public static variables on the fly without writing custom commands for everything.
