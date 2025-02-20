---
title: "Properties"
---

## `GetCurrentSaveSlot`

Returns the currently loaded save slot.

**Example Usage:**

```
var currentSlot = SaveSystem.GetCurrentSaveSlot;
Debug.Log("Current Save Slot: " + currentSlot.SlotName);
```

## `GetSaveDataSlots`

Retrieves all created save slots.

**Example Usage:**

```
var allSlots = SaveSystem.GetSaveDataSlots;
foreach(var slot in allSlots) {
    Debug.Log("Slot Name: " + slot.SlotName);
}
```

## `GetGlobalData`

Returns a dictionary containing all global data.

**Example Usage:**

```
var globalData = SaveSystem.GetGlobalData;
foreach(var entry in globalData) {
    Debug.Log($"Key: {entry.Key}, Value: {entry.Value}");
}
```

## `GetSlotData`

Returns a dictionary with the current slot's data.

**Example Usage:**

```
var slotData = SaveSystem.GetSlotData;
foreach(var data in slotData) {
    Debug.Log($"Key: {data.Key}, Value: {data.Value}");
}
```

## `AreThereUnsavedSlotData`

Indicates whether there is unsaved data for the current slot.

**Example Usage:**

```
bool unsavedData = SaveSystem.AreThereUnsavedSlotData;
Debug.Log("Unsaved Slot Data: " + unsavedData);
```

## `AreThereUnsavedGlobalData`

Indicates whether there is unsaved global data.

**Example Usage:**

```
bool unsavedGlobalData = SaveSystem.AreThereUnsavedGlobalData;
Debug.Log("Unsaved Global Data: " + unsavedGlobalData);
```

## `IsSlotLoaded`

Checks if a save slot is currently loaded.

**Example Usage:**

```
bool isLoaded = SaveSystem.IsSlotLoaded;
Debug.Log("Is Slot Loaded: " + isLoaded);
```
