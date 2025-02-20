---
title: "Exceptions"
---

When working with the **DH Save System**, you may encounter several exceptions. These are typically easy to resolve and often involve either attempting to save data with an existing ID or trying to save to a slot that hasn't been loaded. Here's how you can address the issues related to these exceptions:

## `MissingMethodException`

This exception occurs when a class that is being saved does not have a default constructor. The DH Save System requires a parameterless constructor to instantiate objects during deserialization.

#### **Solution**

Ensure that any class you intend to serialize with the DH Save System includes a default, parameterless constructor. If your class has constructors that take parameters, you must still provide a default constructor.

#### **Example**

```csharp
public class PlayerData
{
    public int score;
    public string name;

    // Default constructor
    public PlayerData()
    {
    }

    // Constructor with parameters
    public PlayerData(string name, int score)
    {
        this.name = name;
        this.score = score;
    }
}

try
{
    PlayerData playerData = new PlayerData("John Doe", 1000);
    SaveSystem.Save("playerData", playerData, isGlobal: false);
}
catch (MissingMethodException)
{
    // Ensure PlayerData class includes a default constructor
    Console.WriteLine("Ensure the PlayerData class has a default constructor.");
}
```

Adding a default constructor allows the serialization and deserialization processes to function correctly, avoiding the `MissingMethodException` and ensuring smooth operation of the DH Save System.

## `KeyAlreadyExistsException`

Occurs when attempting to save data with an ID that already exists within the specified scope (global or slot-specific).

#### **Solution**

Change the ID you're using for saving. Ensure it's unique to avoid conflicts.

**Example**

```csharp
try
{
    SaveSystem.Save("playerScore", 5000, isGlobal: false);
}
catch (KeyAlreadyExistsException)
{
    // Change the ID and try again
    SaveSystem.Save("playerScore1", 5000, isGlobal: false);
}
```

## `SaveSlotNotLoadedException`

Thrown when attempting to save to a slot that hasn't been loaded. This can occur if you try to save slot-specific data before a slot is active.

#### **Solution**

Before saving data to a slot, ensure that a slot is loaded. If you need to save data but no slot is loaded, either save it as global data or wait until a slot has been loaded.

**Example**

```csharp
try
{
    SaveSystem.Save("playerLocation", new Vector3(0, 0, 0), isGlobal: false);
}
catch (SaveSlotNotLoadedException)
{
    // Load a slot or save as global data instead
    SaveSystem.LoadSaveSlot("SlotName");
    SaveSystem.Save("playerLocation", new Vector3(0, 0, 0), isGlobal: false);
}
```

## `InvalidFieldTypeException`**,** `InvalidPropertyTypeException`

These exceptions occur when saving custom classes that use unsupported types, such as `Dictionary` or `Transform`, without converting them to a serializable form.

#### **Solution**

Convert unsupported types to their serializable counterparts provided by the save system, such as changing `Transform` to `SerializableTransform` and `Dictionary<TKey, TValue>` to `SerializableDictionary<TKey, TValue>`.

**Example**

```csharp
try
{
    var playerData = new CustomPlayerData
    {
        playerTransform = new SerializableTransform(player.transform),
        inventoryItems = new SerializableDictionary<string, int>(inventoryItems)
    };
    SaveSystem.Save("playerData", playerData, isGlobal: false);
}
catch (InvalidFieldTypeException)
{
    // Ensure all fields are using serializable types
}
catch (InvalidPropertyTypeException)
{
    // Ensure all properties are using serializable types
}
```

  
