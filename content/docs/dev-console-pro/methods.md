---
title: "Methods & API"
weight: 6
---

While the Dev Console automatically intercepts Unity's native `Debug.Log`, `Debug.LogWarning`, and `Debug.LogError` calls, you can also interact directly with the `ConsoleCore` API to trigger custom formatted logs, clear the console, or force a log flush.

To use these methods, make sure you include the namespace:
```csharp
using DevConsole;
```

---

## `ConsoleCore.LogResult`

Logs a command result or output directly to the console in a bright green success color. It skips the standard Unity queue and renders synchronously.

#### **Parameters**

-   `message`: The string message to display.

**Example Usage**

```csharp
[Command("teleport")]
public static void Teleport()
{
    // ... logic ...
    ConsoleCore.LogResult("Teleported successfully to (0, 0, 0)");
}
```

---

## `ConsoleCore.LogSuccess`

Logs a message with a cyan timestamp and a `[SUCCESS]` badge. This is natively used by the console to signify when a command executes properly but produces no other output.

#### **Parameters**

-   `message`: The string message to display.

**Example Usage**

```csharp
ConsoleCore.LogSuccess("The background generation task completed!");
```

---

## `ConsoleCore.LogError`

Bypasses Unity's native `Debug.LogError` and pushes a red error log directly to the Dev Console UI. Useful if you want an error in the console but do not want it polluting the Unity Editor log file.

#### **Parameters**

-   `message`: The error message.

**Example Usage**

```csharp
ConsoleCore.LogError("Could not find the specified configuration file.");
```

---

## `ConsoleCore.Log`

The base logging method. Allows you to inject a completely custom log with a specific `LogType` and even override the badge string (e.g. replacing `[INFO]` with `[SYSTEM]`).

#### **Parameters**

-   `message`: The text to display.
-   `type` (Optional): The `LogType` (Log, Warning, Error) which dictates color formatting.
-   `customType` (Optional): A string to replace the default badge tag.

**Example Usage**

```csharp
ConsoleCore.Log("Network connected.", LogType.Log, "<color=cyan>[NETWORK]</color>");
```

---

## `ConsoleCore.Instance.ClearLogs`

Wipes all currently stored logs, warnings, and errors from the console UI. (This does not touch Unity's native Editor log window).

**Example Usage**

```csharp
ConsoleCore.Instance?.ClearLogs();
```

---

## `ConsoleCore.Instance.FlushPendingLogs`

Force-flushes any intercepted Unity `Debug.Log` calls immediately into the console UI. 

Because `Debug.Log` calls are intercepted asynchronously via Unity's `Application.logMessageReceivedThreaded`, they usually do not appear in the console until the next frame. Calling this method forces the console to dequeue and print them instantly.

**Example Usage**

```csharp
Debug.Log("Standard Unity Log");
ConsoleCore.Instance?.FlushPendingLogs(); // Forces the log into the UI right now!
```
