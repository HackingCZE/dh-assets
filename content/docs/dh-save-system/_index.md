---
title: "DH Save System"
---

## Introduction

Welcome to the DH Save System documentation. This guide provides all the information needed to integrate and utilize the DH Save System within your Unity projects. Designed to offer a robust and secure method for saving and loading game data, this system supports a wide variety of data types and ensures the security of your data through encryption.

## Table of Contents

1.  **[Overview](/docs/dh-save-system/overview)**

2.  **[Configuration](/a/docs/uIry3YMlSYoYvqpu)**

3.  **[SaveSystemManager](/a/docs/mrAV3aAp0DDuhGWr)**

4.  **[Basic Operations](/a/docs/h56FTgvliwDXw7zw)**

    -   [Saving Data](/a/docs/h56FTgvliwDXw7zw)

    -   [Loading Data](/a/docs/h56FTgvliwDXw7zw)

5.  **[Encryption](/a/docs/QTlNOodnMp70GPvu)**

6.  **[SaveDataSlot Class](/a/docs/5pLGvPjQuSXYIBLG)**

7.  **[SaveSystem Class](/a/docs/SRyxooC7jkgOZwaI)**

    -   [Properties](/a/docs/poPO7rGdPxadRUqI)

    -   [Methods](/a/docs/lOwdG6onONhHMCTu)

8.  **[Exceptions](/a/docs/Dr02rUWiZnV165CZ)**

9.  **[Working with Serializable Types](/a/docs/8qrIcRNmlGsA58fS)**

## 1. Overview

The DH Save System distinguishes between global data (e.g., game settings) and slot-specific data (e.g., player progress) to provide flexible and secure data management. With built-in encryption and easy-to-use interfaces, it's an essential tool for Unity developers looking to implement reliable save and load functionality.

## 2. Configuration

**SaveSystemSettings:** Accessible via **Project Settings**, this component allows for the configuration of encryption keys, auto-saving preferences, and key history management.

**Save Data Window:** A Unity Editor tool for viewing saved data directly, enhancing the development and debugging process.

## 3. SaveSystemManager

A runtime component that loads saved data upon game start. It supports custom converters for non-serializable classes, ensuring that all game data can be efficiently saved and loaded.

## 4. Basic Operations

### [Saving Data](/a/docs/h56FTgvliwDXw7zw)

Illustrates how to save both global and slot-specific data, with examples for various data types, including dictionaries and transforms.

### [Loading Data](/a/docs/h56FTgvliwDXw7zw)

Guides on retrieving saved data, with an emphasis on type safety and handling optional data.

## 5. Encryption

Details the encryption mechanism used to secure saved data, including setting up encryption keys and managing key history for data recovery.

### [Encryption](/a/docs/QTlNOodnMp70GPvu)

## **6. SaveDataSlot Class**

The `SaveDataSlot` class manages individual game save slots within the DH Save System, encapsulating slot details like name, save timestamp, progress, and custom data. It simplifies save slot manipulation and querying, offering a robust framework for game save management.

### [Properties](/a/docs/5pLGvPjQuSXYIBLG)

-   **SlotName, LastSave, Progress, IndexSlot, SavePath, OtherData**: Essential slot details including custom data storage.

### [Methods](/a/docs/5pLGvPjQuSXYIBLG)

-   **SetSlotName, SetProgress, SetOtherData&lt;T&gt;, GetOtherData&lt;T&gt;**: Update slot information and manage custom data, supporting flexible data types for comprehensive save management.

## 7. SaveSystem Class

The `SaveSystem` class is the core of the DH Save System, providing essential functionalities for saving and loading data. It facilitates access to both global data and individual save slots, ensuring secure and efficient data management across your game.

### [Properties](/a/docs/SRyxooC7jkgOZwaI)

-   **GetCurrentSaveSlot, GetSaveDataSlots, GetGlobalData, GetSlotData:** Accessors for retrieving current slots, all slots, and their respective data.

### [Methods](/a/docs/SRyxooC7jkgOZwaI)

-   Comprehensive coverage of all methods, from `Save` and `Load` to more specialized functions like `LoadTransform` and `Serialize`.

## 8. Exceptions

Explains common exceptions (e.g., `KeyAlreadyExistsException`, `SaveSlotNotLoadedException`) and provides strategies for resolution, ensuring robust error handling.

### [Exceptions](/a/docs/Dr02rUWiZnV165CZ)

## 9. Working with Serializable Types

### [SerializableDictionary and SerializableTransform](/a/docs/8qrIcRNmlGsA58fS)

Demonstrates converting complex data types into serializable formats for saving, and vice versa for loading, complete with examples.

## Contact & Support

For support, bug reports, or contributions, please contact via email: `support@hurtaweb.cz`. We welcome your feedback and contributions to the project.
