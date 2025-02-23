---
title: "Methods"
---

## `TryGetRight`

Tries to get the Navigation component of the UI element to the right.

#### **Parameters**

-   `rightNavigation`: The Navigation component found on the right, if any.

#### **Returns**

-   `bool`: True if a Navigation component was found on the right, false otherwise.

**Example Usage**

```csharp
Navigation rightNav;
bool found = currentNavigaton.TryGetRight(out rightNav);
```

## `TryGetLeft`

Tries to get the Navigation component of the UI element to the left.

#### **Parameters**

-   `leftNavigation`: The Navigation component found on the left, if any.

#### **Returns**

-   `bool`: True if a Navigation component was found on the left, false otherwise.

**Example Usage**

```csharp
Navigation leftNav;
bool found = currentNavigaton.TryGetLeft(out leftNav);
```

## `TryGetUp`

Tries to get the Navigation component of the UI element above.

#### **Parameters**

-   `upNavigation`: The Navigation component found above, if any.

#### **Returns**

-   `bool`: True if a Navigation component was found above, false otherwise.

**Example Usage**

```csharp
Navigation upNav;
bool found = currentNavigaton.TryGetUp(out upNav);
```

## `TryGetDown`

Tries to get the Navigation component of the UI element below.

#### **Parameters**

-   `downNavigation`: The Navigation component found below, if any.

#### **Returns**

-   `bool`: True if a Navigation component was found below, false otherwise.

**Example Usage**

```csharp
Navigation downNav;
bool found = currentNavigaton.TryGetDown(out downNav);
```

## `MoveRight`

Moves the selection to the right.

**Example Usage**

```csharp
Navigation.MoveRight();
```

## `MoveLeft`

Moves the selection to the left.

**Example Usage**

```csharp
Navigation.MoveLeft();
```

## `MoveUp`

Moves the selection upwards.

**Example Usage**

```csharp
Navigation.MoveUp();
```

## `MoveDown`

Moves the selection downwards.

**Example Usage**

```csharp
Navigation.MoveDown();
```

## `Move`

Moves the selection in the specified direction.

#### **Parameters**

-   `moveDirection`: Direction to move the selection.

**Example Usage**

```csharp
Navigation.Move(MoveDirection.Right);
```

## `SetSelected`

Sets the currently selected GameObject in the EventSystem to the specified navigation.

#### **Parameters**

-   `navigation`: Navigation object to set as selected.

**Example Usage**

```csharp
Navigation.SetSelected(navigationComponent);
```

## `GetSelected`

Retrieves the Navigation component of the currently selected GameObject in the EventSystem. Throws an exception if the selected GameObject doesn't have a Navigation component.

#### **Returns**

-   `Navigation`: Navigation component of the currently selected GameObject.

**Example Usage**

```csharp
try
{
    Navigation currentNav = Navigation.GetSelected();
}
catch (Exception ex)
{
    Debug.LogError("Error: " + ex.Message);
}
```
