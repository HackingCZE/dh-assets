---
title: "Configuration"
---

### **SaveSystemSettings**

Located under **Project Settings/Save System Settings**, this component is crucial for setting up your encryption key and managing save data preferences.

Key Features:

-   **Generate Encrypt Key**: Click to generate a new encryption key, which is immediately set as the current key.

-   **Key History**: Maintains a history of used keys (default is 5) to recover from accidental changes.

-   **Auto Save Global Data**: Automatically saves global data upon any addition or modification.

-   **Auto Save Slot Data**: Enables automatic saving for the currently loaded slot, with a customizable delay (`Auto Save Slot Data Delay Time` in minutes).

![](/shaders/images/image5.png)

### **Save Data Window**

Accessible via Tools/Save Data, this utility provides a visual interface for managing save data directly in the Unity Editor.

Capabilities:

-   **SaveSystemManager Integration**: Automatically creates a `SaveSystemManager` in the current scene if not present, allowing for runtime data management.

-   **Data Viewing and Editing**: Separate sections for **GLOBAL** and **SLOT** data, including a search function by ID.

-   **Slot Data Management**: Offers the ability to browse through slots or view the current slot's data in the editor.

![](/shaders/images/image6.png)
