---
title: "Custom Commands & IntelliSense"
weight: 3
---

### **Registering Custom Commands**

Creating a custom command is as simple as adding the `[Command]` attribute to any method in your game, whether it's static or part of a `MonoBehaviour`.

```csharp
using DevConsole;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    // The method will be automatically discovered on startup!
    [Command("spawn.enemy", "Spawns an enemy at the player's position.")]
    public static void SpawnEnemy(string type, int count)
    {
        // Your logic here.
    }
}
```

### **Parameter IntelliSense (Autocomplete)**

The Dev Console Pro is extremely smart when it comes to auto-suggesting parameter values. By default, **it automatically infers types**! If your method takes a `bool`, it suggests `true`/`false`. If it takes a `KeyCode`, it suggests all Unity KeyCodes.

However, you can explicitly define what the console should suggest using the `[CommandParamSuggestion]` attribute.

#### **Suggesting GameObjects or Components:**
```csharp
[Command("teleport", "Teleport to a specific GameObject")]
public static void Teleport(
    [CommandParamSuggestion(SuggestionType.GameObject)] string targetName)
{
    // The console will scan the active scene and suggest GameObject names!
}

[Command("find", "Find objects with a specific component")]
public static void Find(
    [CommandParamSuggestion(SuggestionType.Component, typeof(Rigidbody2D))] string objectName)
{
    // The console will only suggest GameObjects that actually have a Rigidbody2D!
}
```

#### **Custom Dynamic Suggestions (Reverse-Lookup):**
You can provide your own lists of suggestions dynamically. Even better, if you use the Generic provider overload, the console will automatically map the strings in the UI back to actual object instances at execution time!

**1. Register the provider (e.g. in Awake or Start):**
```csharp
// Provide a list of active ScriptableObjects, ScriptableRendererFeatures, etc.
SuggestionProvider.RegisterCustomProvider<ScriptableRendererFeature>("render_features", () => myRendererData.rendererFeatures);
```

**2. Use the Custom ID in your command:**
```csharp
[Command("renderer.toggle")]
public static void ToggleFeature(
    [CommandParamSuggestion("render_features")] ScriptableRendererFeature feature)
{
    // When you type "renderer.toggle ", it auto-suggests the names of the features.
    // When you hit enter, 'feature' is perfectly injected as the actual reference!
    feature.SetActive(!feature.isActive);
}
```

### **Advanced Features**

*   **Multi-Word Commands:** You can include spaces in command names (e.g., `[Command("spawn boss")]`). The autocomplete seamlessly handles multi-word groupings.
*   **Vector Syntax:** The console supports standard Unity vector inputs natively. You can write `gravity new(0, -9.81, 0)` or use shorthand like `Vector3.down`. Vector values are color-coded to match Unity's Red/Green/Blue gizmos!
*   **Array Parsing:** Pass arrays simply by wrapping items in brackets: `spawn [goblin, orc, troll]`.
