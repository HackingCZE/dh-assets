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

### **Event-like Execution with SharedCommands**

If you want to invoke multiple methods across entirely different scripts simultaneously using the *exact same command name*, use the `[SharedCommand]` attribute! This acts like an event broadcast.

You can also precisely control the execution order using the `Order` property. Methods with lower `Order` values execute first. If `Order` is not defined, the system automatically runs them last, sorting them alphabetically by their script name, and prints a warning in the console log.

```csharp
public class GameManager : MonoBehaviour
{
    [SharedCommand("save.all", Order = 1)]
    public static void SaveGameWorld()
    {
        // Executes first
    }
}

public class InventoryManager : MonoBehaviour
{
    [SharedCommand("save.all", Order = 2)]
    public static void SavePlayerInventory()
    {
        // Executes after the GameManager
    }
}
```


### **Supported Parameter Types**

The Dev Console Pro handles type conversion natively for almost every common Unity type without requiring any boilerplate parsing code.

| Type | Examples & Native Support |
|------|---------------------------|
| **Primitives** | `int`, `float`, `double`, `decimal`, `string`, `bool` (supports `1`/`0` and `true`/`false`). |
| **Enums** | Native support. Just use your Enum as the parameter type and type its name (e.g. `EnemyType.Orc`). |
| **Vectors** | `Vector2`, `Vector3`. Use syntax like `new(0, 1.5, 0)`, `Vector3.down`, or `[0, 1.5, 0]`. |
| **Arrays** | Pass arrays using bracket syntax: `spawn [goblin, orc, troll]`. |
| **Colors** | Native support. Parsed via Unity's HTML parser (e.g., `red`, `cyan`, `#FF00FF`). |
| **GameObjects** | Pass GameObjects by name. Type `Enemy` and the console automatically finds `GameObject.Find("Enemy")`. |
| **Components** | Look up components natively using `GoName:ComponentType` (e.g. `Player:Rigidbody2D`). |

---

### **Parameter IntelliSense (Autocomplete)**

The Dev Console Pro features a powerful contextual suggestion engine. When the user types a command, it can suggest valid values for each specific parameter dynamically.

#### **Option A: Automatic Type Inference (Zero Setup)**
If you do nothing, the console automatically infers suggestion types for parameters!
```csharp
[Command("set.god.mode")]
public static void SetGodMode(bool enabled, KeyCode triggerKey, EnemyType enemyEnum, Color glowColor) 
{
    // Automatically suggests 'true'/'false' for enabled.
    // Automatically suggests Unity KeyCode list for triggerKey.
    // Automatically suggests EnemyType values for enemyEnum.
    // Automatically suggests basic color names (red, blue...) for glowColor.
}
```
*Note: String parameters with names like `sceneName` or `layer` will also be automatically inferred.*

#### **Option B: Method-level Attributes**
For simple cases, you can provide an array of `SuggestionType` values directly in the `[Command]` attribute:
```csharp
[Command("teleport", "Teleport to a GameObject", ParameterSuggestions = new[] { SuggestionType.GameObject })]
public static void Teleport(string target)
{
    // Typing "teleport " will suggest scene GameObjects
}
```

#### **Option C: Per-Parameter Attributes**
If you need complex suggestions (like suggesting GameObjects that only have a specific component attached), use the `[CommandParamSuggestion]` attribute.
```csharp
[Command("find", "Find objects with a specific component")]
public static void Find(
    [CommandParamSuggestion(SuggestionType.Component, typeof(Rigidbody2D))] string objectName)
{
    // The console will only suggest GameObjects that actually have a Rigidbody2D!
}
```

#### **Option D: Custom Dynamic Providers & Reverse Lookup**
You can provide your own dynamically generated lists of suggestions. Even better, if you use the Generic provider overload, the console will automatically map the strings in the UI back to actual object instances at execution time!

**1. Register the provider (e.g., in Awake):**
```csharp
// Passing a generic provider will automatically convert values to strings for UI
// AND it will automatically resolve the exact object instance during execution!
SuggestionProvider.RegisterCustomProvider<ScriptableRendererFeature>("render_features", () => myRendererData.rendererFeatures);
```

**2. Use the Custom ID in your command:**
```csharp
[Command("renderer.toggle")]
public static void ToggleFeature([CommandParamSuggestion("render_features")] ScriptableRendererFeature feature)
{
    // When you type "renderer.toggle ", it auto-suggests the names of the features.
    // When you hit enter, the actual 'feature' object reference is safely injected here!
    feature.SetActive(!feature.isActive);
}
```

---

### **List of Suggestion Types**

Here is the complete list of available `SuggestionType` enum values you can use:

| Type | Suggests | Caching |
|------|----------|---------|
| `None` | No suggestions (default) | — |
| `GameObject` | Active scene GameObjects | 0.5s |
| `Component` | GameObjects with a specific component (requires `typeof(T)`) | 1.0s per type |
| `CommandName` | Registered console command names | Always fresh |
| `KeyCode` | Unity `KeyCode` enum values | Once |
| `CustomEnum` | Values from the parameter's enum type | Instant |
| `Bool` / `Boolean` | `true` / `false` | Static |
| `SceneName` | Scenes added to the Build Settings | Once |
| `Tag` | Unity tags (built-in + custom) | Once |
| `Layer` | Non-empty layer names (0–31) | Once |
| `Custom` | Your own dynamically generated lists via string ID | Instant |
| `Vector2` | Standard Vector2 constants (e.g., `Vector2.up`) | Static |
| `Vector3` | Standard Vector3 constants (e.g., `Vector3.forward`) | Static |
| `Color` | Standard HTML color names (red, cyan, blue, etc.) | Static |

---

### **Advanced Parsing Features**

*   **Multi-Word Commands:** You can include spaces in command names (e.g., `[Command("spawn boss")]`). The autocomplete seamlessly handles multi-word groupings.
*   **Vector Syntax Rendering:** Vector values are color-coded in the UI to match Unity's standard Red/Green/Blue gizmos for absolute visual clarity!
*   **Nested Alias Parsing:** The robust nested context parser completely prevents autocomplete failures or logic breaks when you are writing complex nested aliases with bracket `[ ]` syntax.
