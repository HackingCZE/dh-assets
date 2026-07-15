---
title: "Changelog"
weight: 99
---

All notable changes to the Dev Console Pro package will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.2.0] - 2026-07-15
### Added
- **Color IntelliSense**: The IntelliSense engine now automatically infers parameters of type `Color` or `Color32` and suggests a rich list of standard HTML color names (e.g., `red`, `cyan`, `magenta`).
- **SharedCommand Execution Order**: Added `Order` property to `[SharedCommand]`. Commands with identical names are now perfectly sorted, running lower Order values first.
- **SharedCommand Fallback Sorting**: Scripts with undefined orders now automatically fall back to alphabetical script name sorting.
- **Synchronous Method Logging**: Implemented real-time interleaving logs during `[SharedCommand]` execution (e.g. `[SharedCommand] Running 'save.all' from script GameManager (Order: 1)`).

### Fixed
- Reverted Project Settings IMGUI layout to a standard one-column format to maintain Unity UX consistency.

## [2.1.0] - 2026-07-13
### Added
- **Auto-Wrapping Toolbar**: The top right toolbar (Warning/Error/Info toggles, Search, Zoom) now dynamically wraps to multiple rows when the console window is resized to a narrow width, preventing UI overlap.
- **Log Zoom Control**: Added `[-] 100% [+]` buttons directly to the console UI to dynamically adjust the font size of the output logs from 50% to 300%.
- **Default Log Zoom Setting**: Added a `DefaultLogZoom` preference to the Project Settings to save the preferred font size persistently.

## [2.0.0] - 2026-07-10
### Added
- **Aliases UI System**: Introduced a robust Command Aliases system to the Project Settings, allowing developers to create shorthand aliases for complex, multi-command strings (e.g. `boss_fight` -> `spawn boss; godmode true; timescale 0.5`).
- **Floating Syntax Overlay**: Added a premium floating real-time syntax highlighter that tracks the cursor and injects parameter hints directly above the text input!
- **Position Configurations**: Added Project Settings to independently anchor the Colored Syntax and Parameter Hints (Top or Bottom).
- **Advanced Vector Parsing**: Implemented native robust parsing for `Vector2` and `Vector3` (supports `new(1, 0, 0)`, `[1, 0, 0]`, or `Vector3.down`).
- **RGB Vector Rendering**: Vector parameter hints are now beautifully color-coded to match Unity's standard Red/Green/Blue gizmo colors.
- **Zebra Striping**: Added optional dark slate Zebra Striping to both the Command List and Log History panels for enhanced readability.
- **Collapse Logs Button**: Added a Unity-style `Collapse` button to deduplicate identical logs and render a numeric badge (e.g., `(5)`).

### Changed
- Massively upgraded internal UI aesthetics with rich badging (`[OK]`, `[INFO]`, `[ERROR]`).
- Renamed project branding to **Dev Console Pro**.

## [1.5.0] - 2026-07-05
### Added
- **Reflection Evaluator Fallback**: When a registered command isn't found, the console can now automatically evaluate raw C# expressions via reflection (e.g., `Time.timeScale = 2` or `Camera.main.fieldOfView = 90`).
- **Custom Suggestion Providers**: Implemented a powerful reverse-lookup API (`SuggestionProvider.RegisterCustomProvider<T>`) to supply dynamically generated arrays to the IntelliSense engine.
- **Automatic Type Inference**: The IntelliSense engine now automatically infers and caches `bool`, `Enum`, `GameObject`, `Component`, `Scene`, `Tag`, and `Layer` parameters without requiring any manual setup.

## [1.0.0] - 2026-06-25
### Added
- **Trie-Powered Autocomplete**: Blazing fast fuzzy-search autocomplete powered by a custom Trie data structure.
- **Intercept Unity Logs**: Option to automatically route all `Debug.Log`, `Debug.LogWarning`, and `Debug.LogError` calls into the Dev Console.
- **Project Settings Window**: Integrated the settings UI directly into `Edit -> Project Settings -> Dev Console Pro`.
- **Command History**: Added `Shift + Up/Down` keybinds to cycle through previously executed commands.
- **FPS Counter**: Added an optional, unobtrusive mini FPS overlay in the top corner.

## [0.1.0] - Initial Release
### Added
- Core IMGUI rendering loop.
- Simple `[Command]` attribute routing.
- Basic parameter tokenization.
