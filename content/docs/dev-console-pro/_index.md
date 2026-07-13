---
title: "Dev Console Pro"
weight: 1
---

## **Overview**

**Dev Console Pro** is a powerful, lightweight, zero-setup in-game developer console for Unity. Designed for modern Unity development, it bypasses complex UI setups (no Canvas, UGUI, or UI Toolkit required) by rendering entirely through robust IMGUI. 

Just drop the package into your project, press **~**, and you instantly have access to advanced debugging, command execution, and deep C# reflection evaluation.

### **Core Features:**
*   **Zero Boilerplate Setup**: Auto-instantiates at runtime. No prefabs or scene dependencies.
*   **IntelliSense & Autocomplete**: Trie-based autocomplete with fuzzy search and context-aware parameter hints.
*   **Reflection Evaluator**: Directly execute C# expressions (e.g. `Time.timeScale = 0.5`) without registering them.
*   **Custom Commands**: Easily turn any method into a console command using the `[Command]` attribute.
*   **Log Interception**: Automatically intercepts `Debug.Log`, `LogWarning`, and `LogError` with precise timestamps.
*   **Dynamic UX**: Premium floating syntax highlighting, customizable UI layouts, and zebra-striping.
