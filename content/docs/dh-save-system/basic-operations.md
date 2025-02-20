---
title: "Basic Operations"
---

### **Saving Data**

Global Data Example:

```
// Save resolution settings as global data
SaveSystem.Save("resolution", new Vector2(1920, 1080), isGlobal: true);
```

Slot Data Example:

```
// Save player score in the current slot
SaveSystem.Save("playerScore", 5000, isGlobal: false);
```

### **Loading Data**

Global Data Example:

```
// Load resolution settings
Vector2 resolution = SaveSystem.Load<Vector2>("resolution", isGlobal: true);
```

Slot Data Example:

```
// Load player score from the current slot
int score = SaveSystem.Load<int>("playerScore", isGlobal: false);
```
