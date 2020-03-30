# Player Input
A new API was created for controlling player inputs. The new system is extensible and strives to not hide any events or artifacts in black boxes, allowing full freedom to modify the API. The API also helps conform the APIs of many different types of input, so setting up controller inputs and keyboard inputs should be simple. There are a set of out-of-the-box defaults that make getting started quick.

---

## Setting up
Version: 2019.1 or higher
Manual Steps:
- Install preview package
    - Open package manager: Window -> Package Manager
    - Open advanced select "Show preview packages"
    - Find and install "Input System"
- Enable for code in Project Settings
    - Open preferences: Edit -> Project Settings
    - Select "Player"
    - Find "Active Input Handling" and select "Input System Package"

---

## Player Input Component
[API Docs](https://docs.unity3d.com/Packages/com.unity.inputsystem@0.9/manual/Components.html#playerinput-component)

---

## Using PlayerInput in Script
If you are using a `PlayerInput` component on your player, a few "housekeeping" things are taken care of for you. Things you still have to do:

Initialize your input actions in the `Awake()` method. Some examples will show other work being done to get the callback context from the input actions instance. The `PlayerInput` component abstracts that away.
```csharp
YourInputActions inputActions;
void Awake()
{
    this.inputActions = new YourInputActions();
}
```

(For now,) you must manually define the `InputValue` type in your event method. For example, if you have defined a "move" action on your input actions and wish to retrieve a Vector2 to represent player movement:
```csharp
void onMove(UnityEngine.PlayerInput.InputValue inputValue) {
    Vector2 movementVector = inputValue.Get<Vector2>();
}
```
