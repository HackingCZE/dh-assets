---
title: "Methods"
---

## `Save<T>`

Saves a value to global or slot data.

#### **Parameters**

-   `ID`: Unique identifier for the data entry.

-   `value`: Value to save.

-   `isGlobal`: True for global data, false for slot-specific data.

**Example Usage**

```
SaveSystem.Save("playerHealth", 100, isGlobal: false);
```

## `Load<T>`

Loads a value of type T using the specified ID from either global or slot-specific data.

#### **Parameters**

-   `ID`: The unique identifier for the data to load.

-   `isGlobal`: True for global data, false for slot-specific data.

**Example Usage**

```
int playerHealth = SaveSystem.Load<int>("playerHealth", isGlobal: false);
```

## `TryLoad<T>`

Attempts to load data of a specified type using the given ID from either global or slot-specific data.

#### **Parameters**

-   `returnData`: Output parameter for the loaded data.

-   `ID`: The unique identifier for the data to load.

-   `isGlobal`: True for global data, false for slot-specific data.

**Example Usage**

```
bool success = SaveSystem.TryLoad(out int playerHealth, "playerHealth", isGlobal: false);
```

## `LoadTransform`

Loads and applies transform data to a single target transform.

#### **Parameters**

-   `targetTransform`: The target transform to apply data to.

-   `ID`: The unique identifier for the data.

-   `isGlobal`: True for global data, false for slot-specific data.

**Example Usage**

```
SaveSystem.LoadTransform(player.transform, "playerPosition", isGlobal: false);
```

## `Update<T>`

Updates existing data with the specified ID in either global or slot-specific storage.

#### **Parameters**

-   `ID`: The unique identifier for the data entry.

-   `value`: The new value to store.

-   `isGlobal`: True to update global data, false for slot-specific data.

**Example Usage**

```
SaveSystem.Update("playerHealth", 150, isGlobal: false);
```

## `UpdateOrSave<T>`

Updates an existing entry with the specified ID or saves a new entry if it does not exist.

#### **Parameters**

-   `ID`: The unique identifier for the data entry.

-   `value`: The value to update or save.

-   `isGlobal`: True to operate on global data, false for slot-specific data.

**Example Usage**

```
SaveSystem.UpdateOrSave("playerScore", 5000, isGlobal: false);
```

## `Remove`

Removes a data entry with the specified ID from either global or slot-specific storage.

#### **Parameters**

-   `ID`: The unique identifier for the data entry to be removed.

-   `isGlobal`: True to remove from global data, false for slot-specific data.

**Example Usage**

```
SaveSystem.Remove("playerHealth", isGlobal: false);
```

## `ClearData`

Clears all data within a specified scope (global or slot-specific) without removing the slots themselves. Optionally saves the changes immediately.

#### **Parameters**

-   `isGlobal`: Determines whether to clear global data or data specific to the current slot.

-   `saveImmediately`: If true, the changes are saved immediately after clearing the data.

**Example Usage:**

```
SaveSystem.ClearData(isGlobal: true, saveImmediately: true); 
Debug.Log("Global data cleared and saved.");
```

## `CreateNewSaveSlot`

Creates a new save slot with the specified name and index, and saves it.

#### **Parameters**

-   `slotName`: The name of the new save slot.

-   `indexSlot`: The index of the new save slot.

**Example Usage:**

```
SaveSystem.CreateNewSaveSlot("New Slot", 1); 
Debug.Log("New save slot created.");
```

## `LoadSaveSlot`

Loads the save slot with the specified name into memory, replacing any currently loaded data.

#### **Parameters**

-   `slotName`: The name of the save slot to load.

**Example Usage:**

```
try {
    SaveSystem.LoadSaveSlot("Slot Name");
    Debug.Log("Save slot loaded.");
} catch(SaveSlotNotLoadedException ex) {
    Debug.LogError("Error loading slot: " + ex.Message);
}
```

## `RemoveSaveSlot`

Removes a save slot with the specified name and index, deletes its associated save file, and updates global data accordingly.

#### **Parameters**

-   `slotName`: The name of the save slot to remove.

-   `indexSlot`: The index of the save slot to remove.

**Example Usage:**

```
bool removed = SaveSystem.RemoveSaveSlot("Slot to Remove", 0);
Debug.Log("Save slot removed: " + removed);
```

## `SaveData`

Saves the current slot data to disk and updates the global save data.

**Example Usage:**

```
try {
    SaveSystem.SaveData();
    Debug.Log("Data saved successfully.");
} catch(SaveSlotNotLoadedException ex) {
    Debug.LogError("Error saving data: " + ex.Message);
}
```

## `LoadData`

Loads data from a 'specified path and optionally applies provided JSON converters for custom deserialization.

#### **Parameters**

-   `jsonConverters`: (Optional) A list of `JsonConverter` instances for custom serialization settings.

**Example Usage:**

```
List<JsonConverter> converters = new List<JsonConverter> { new MyCustomConverter() };
SaveSystem.LoadData(converters);
Debug.Log("Data loaded with custom converters.");
```

## `SaveGlobalData`

Saves global data, including information about all save slots, to disk.

**Example Usage**

```
SaveSystem.SaveGlobalData();
```

## `Contains`

Checks if the specified ID exists in either global or slot-specific data.

#### **Parameters**

-   `ID`: The unique identifier to check.

-   `isGlobal`: True to check in global data, false for slot-specific data.

**Example Usage**

```
bool exists = SaveSystem.Contains("playerHealth", isGlobal: false);
```

## `Deserialize<T>`

Deserializes JSON data into an object of the specified type.

#### **Parameters**

-   `json`: The encrypted JSON string to deserialize.

**Example Usage**

```
string jsonData = "{ \"playerHealth\": 100 }"; // Encrypted JSON string 
int playerHealth = SaveSystem.Deserialize<int>(jsonData);
```

## `Serialize`

Serializes an object into a JSON string and encrypts it.

#### **Parameters**

-   `value`: The object to serialize.

#### **Example Usage**

```
PlayerData playerData = new PlayerData { Health = 100, Score = 5000 }; 
string encryptedJsonData = SaveSystem.Serialize(playerData);
```
