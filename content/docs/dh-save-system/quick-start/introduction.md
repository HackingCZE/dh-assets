---
title: "Introduction"
weight: 1
---


Welcome to the DH Save System documentation. This guide provides all the information needed to integrate and utilize the DH Save System within your Unity projects. Designed to offer a robust and secure method for saving and loading game data, this system supports a wide variety of data types and ensures the security of your data through encryption.

## 1. Overview

The DH Save System distinguishes between global data (e.g., game settings) and slot-specific data (e.g., player progress) to provide flexible and secure data management. With built-in encryption and easy-to-use interfaces, it's an essential tool for Unity developers looking to implement reliable save and load functionality.

{{< link-card
  title="Overview"
  href="/docs/dh-save-system/quick-start/overview"
>}}

## 2. Configuration

**SaveSystemSettings:** Accessible via **Project Settings**, this component allows for the configuration of encryption keys, auto-saving preferences, and key history management.

**Save Data Window:** A Unity Editor tool for viewing saved data directly, enhancing the development and debugging process.

{{< link-card
  title="Configuration"
  href="/docs/dh-save-system/configuration"
>}}

## 3. SaveSystemManager

A runtime component that loads saved data upon game start. It supports custom converters for non-serializable classes, ensuring that all game data can be efficiently saved and loaded.

{{< link-card
  title="SaveSystemManager"
  href="/docs/dh-save-system/save-system-manager"
>}}

## 4. Basic Operations

### Saving Data

Illustrates how to save both global and slot-specific data, with examples for various data types, including dictionaries and transforms.

{{< link-card
  title="Saving Data"
  href="/docs/dh-save-system/basic-operations#saving-data"
>}}

### Loading Data

Guides on retrieving saved data, with an emphasis on type safety and handling optional data.


{{< link-card
  title="Loading Data"
  href="/docs/dh-save-system/basic-operations#loading-data"
>}}

## 5. Encryption

Details the encryption mechanism used to secure saved data, including setting up encryption keys and managing key history for data recovery.

{{< link-card
  title="Encryption"
  href="/docs/dh-save-system/enryption"
>}}

## **6. SaveDataSlot Class**

The `SaveDataSlot` class manages individual game save slots within the DH Save System, encapsulating slot details like name, save timestamp, progress, and custom data. It simplifies save slot manipulation and querying, offering a robust framework for game save management.

{{< link-card
  title="SaveDataSlot Class"
  href="/docs/dh-save-system/save-data-slot-class"
>}}

### Properties

-   **SlotName, LastSave, Progress, IndexSlot, SavePath, OtherData**: Essential slot details including custom data storage.

### Methods

-   **SetSlotName, SetProgress, SetOtherData&lt;T&gt;, GetOtherData&lt;T&gt;**: Update slot information and manage custom data, supporting flexible data types for comprehensive save management.

## 7. SaveSystem Class

The `SaveSystem` class is the core of the DH Save System, providing essential functionalities for saving and loading data. It facilitates access to both global data and individual save slots, ensuring secure and efficient data management across your game.

### Properties

-   **GetCurrentSaveSlot, GetSaveDataSlots, GetGlobalData, GetSlotData:** Accessors for retrieving current slots, all slots, and their respective data.

{{< link-card
  title="Properties"
  href="/docs/dh-save-system/save-system-class/properties"
>}}

### Methods

-   Comprehensive coverage of all methods, from `Save` and `Load` to more specialized functions like `LoadTransform` and `Serialize`.

{{< link-card
  title="Methods"
  href="/docs/dh-save-system/save-system-class/methods"
>}}

## 8. Exceptions

Explains common exceptions (e.g., `KeyAlreadyExistsException`, `SaveSlotNotLoadedException`) and provides strategies for resolution, ensuring robust error handling.

{{< link-card
  title="Exceptions"
  href="/docs/dh-save-system/exceptions"
>}}

## 9. Working with Serializable Types


### SerializableDictionary and SerializableTransform

Demonstrates converting complex data types into serializable formats for saving, and vice versa for loading, complete with examples.

{{< link-card
  title="Methods"
  href="/docs/dh-save-system/working-with-serializable-types"
>}}


## Contact & Support

For support, bug reports, or contributions, please contact via email: `support@hurtaweb.cz`. We welcome your feedback and contributions to the project.
