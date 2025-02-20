---
title: "SaveDataSlot Class"
---

The `SaveDataSlot` class represents an individual save slot in your game, encapsulating details such as the slot's name, save progress, and additional custom data. It is designed to work seamlessly with the DH Save System, allowing for the creation, modification, and management of save slots without directly manipulating save files.

## **Properties**

-   **SlotName**: The name of the save slot.

-   **LastSave**: Timestamp of the last save action.

-   **Progress**: A float value indicating the player's progress.

-   **IndexSlot**: The index of the slot.

-   **SavePath**: The file path where the slot data is saved.

-   **OtherData**: Custom data that developers can store related to the save slot.

## **Methods**

## `SetSlotName`

Updates the name of the save slot.

**Example Usage:**

```csharp
saveDataSlot.SetSlotName("NewSlotName");
```

## `SetProgress`

Updates the progress value of the save slot.

**Example Usage:**

```csharp
saveDataSlot.SetProgress(0.5f); // 50% progress
```

## `SetOtherData<T>`

Sets custom data of any type to the save slot and optionally saves this data immediately.

#### **Parameters**

-   **newOtherData**: The custom data to set.

-   **saveImmediately**: If true, the data is saved immediately to disk.

**Example Usage**

```csharp
// Assuming CustomData is a custom class you want to save as other data
CustomData customData = new CustomData { /* initialization */ };
saveDataSlot.SetOtherData(customData, saveImmediately: true);
```

This method serializes the `newOtherData` into JSON, stores it in the save slot, and optionally saves the global data immediately if `saveImmediately` is set to true.

## `GetOtherData<T>`

Retrieves the custom "other data" stored in the save slot, if any, and deserializes it back into the original data type.

#### **Returns**

-   The retrieved data of type T, or the default value for type T if not found.

**Example Usage**

```csharp
CustomData customData = saveDataSlot.GetOtherData<CustomData>();
```

This method deserializes the JSON stored in the `otherData` field of the save slot back into the specified type `T`, allowing for easy access to custom data stored in each save slot.

## **Working with SaveDataSlot**

Save slots are managed through the global data structure and are accessible via the Save Data Window under the name "**SLOTS**". It's crucial not to use "**SLOTS**" as a key for your own save data to avoid conflicts.

### **Creating and Removing Save Slots**

Save slots are created and removed through the `SaveSystem` class, using methods such as `CreateNewSaveSlot` and `RemoveSaveSlot`. The `SavePath` is automatically generated, and the `LastSave` timestamp is updated upon calling `SaveSystem.SaveData()`, which saves the slot and its current state.

**Example: Creating a New Save Slot**

```csharp
SaveSystem.CreateNewSaveSlot("Slot1", indexSlot: 1);
```

**Example: Removing a Save Slot**

```csharp
SaveSystem.RemoveSaveSlot("Slot1", indexSlot: 1);
```

## **Note on Data Access**

Access to `SaveDataSlot` properties is straightforward, utilizing public properties without the need for serialization/deserialization methods. This makes retrieving data like progress, slot name, and last save time efficient and direct, streamlining the process of working with save slots in your game.
