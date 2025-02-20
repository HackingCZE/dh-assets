---
title: "Working with Serializable Types"
---

## `SerializableDictionary`

To save a `Dictionary` type **that is** **in custom class**, it must be stored using `SerializableDictionary`. Upon loading a `SerializableDictionary`, you can easily convert it back to a standard `Dictionary` type using the `.ToDictionary()` method.  
When you saving just **simple** `Dictionary`, you can use standard `Dictionary` type.

**Usage Example**

Saving a `Dictionary`

```
// Assuming you have a Dictionary you wish to save
Dictionary<string, int> playerScores = new Dictionary<string, int>
{
    { "player1", 100 },
    { "player2", 200 }
};

// Convert to SerializableDictionary and save
SerializableDictionary<string, int> serializableScores = new SerializableDictionary<string, int>(playerScores);
SaveSystem.Save("playerScores", serializableScores, isGlobal: true);
```

Loading a `Dictionary`

```
// Load the SerializableDictionary
SerializableDictionary<string, int> loadedScores = SaveSystem.Load<SerializableDictionary<string, int>>("playerScores", isGlobal: true);

// Convert back to Dictionary
Dictionary<string, int> playerScores = loadedScores.ToDictionary();
```

## `SerializableTransform`

For saving `Transform` properties, use `SerializableTransform`. Unlike directly setting a transform, `SerializableTransform` requires you to apply the stored values to a target transform using the `.ApplyToTransform(Transform)` method.

**Usage Example**

Saving a `Transform`

```
// Create a SerializableTransform from a GameObject's transform
SerializableTransform serializableTransform = new SerializableTransform(playerGameObject.transform);

// Save the SerializableTransform
SaveSystem.Save("playerTransform", serializableTransform, isGlobal: false);
```

Loading and Applying a `Transform`

```
// Load the SerializableTransform
SerializableTransform loadedTransform = SaveSystem.Load<SerializableTransform>("playerTransform", isGlobal: false);

// Apply the loaded transform values to a GameObject's transform
loadedTransform.ApplyToTransform(playerGameObject.transform);
```

## `SerializableFloat2`

For saving 2D vector types (such as `Float2` from a mathematics library), use `SerializableFloat2`. This type ensures that 2D vector data can be serialized and deserialized properly.

When `SerializableFloat2` **is used within a custom class, it must** be utilized to ensure serialization compatibility. It includes a method, `.ToFloat2()`, to convert back to the original vector type.

**Usage Example**

Saving a `Float2`

```
// Assuming you have a Float2 representing player position
Float2 playerPosition = new Float2(1.5f, 2.5f);

// Convert to SerializableFloat2 and save
SerializableFloat2 serializablePosition = new SerializableFloat2(playerPosition);
SaveSystem.Save("playerPosition", serializablePosition, isGlobal: true);
```

Loading a `Float2`

```
// Load the SerializableFloat2
SerializableFloat2 loadedPosition = SaveSystem.Load<SerializableFloat2>("playerPosition", isGlobal: true);

// Convert back to Float2
Float2 playerPosition = loadedPosition.ToFloat2();
```

## `SerializableFloat3`

For saving 3D vector types (such as `Float3` from a mathematics library), use `SerializableFloat3`. This type is necessary for the serialization and deserialization of 3D vector data.

Similar to `SerializableFloat2`, when `SerializableFloat3` is part of a custom class, it must be used to maintain serialization compatibility. It provides a `.ToFloat3()` method for converting the serialized data back into its original vector form.

**Usage Example**

Saving `Float3`

```
// Assuming you have a Float3 representing player velocity
Float3 playerVelocity = new Float3(0.5f, 0.0f, 1.0f);

// Convert to SerializableFloat3 and save
SerializableFloat3 serializableVelocity = new SerializableFloat3(playerVelocity);
SaveSystem.Save("playerVelocity", serializableVelocity, isGlobal: false);
```

Loading `Float3`

```
// Load the SerializableFloat3
SerializableFloat3 loadedVelocity = SaveSystem.Load<SerializableFloat3>("playerVelocity", isGlobal: false);

// Convert back to Float3
Float3 playerVelocity = loadedVelocity.ToFloat3();
```
