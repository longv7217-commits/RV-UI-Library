# RV-UI-Library
Library for roblox script
GUI library for Roblox with modern features.
## Features
- ✅ Draggable window with Roblox's new drag detection (hand cursor)
- ✅ Drag bar with "Drag Here" text
- ✅ Minimize button (-) at top
- ✅ Config system with Save/Load (file-based)
- ✅ Key system toggle (true/false)
- ✅ Text input fields
- ✅ Override external code (loadstring compatible)
- ✅ Tabs, Buttons, Toggles, Sliders, Dropdowns, Textboxes, Keybinds
- ✅ Notifications
- ✅ Smooth animations

## Usage

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/YOUR_USER/YOUR_REPO/main/source.lua"))()

local Window = Library:CreateWindow({
    Title = "PeakUI Example",
    KeySystem = false, -- true to enable key system
    Key = "PEAK-2024", -- the key needed if KeySystem is true
})

local Tab = Window:CreateTab("Main")

Tab:CreateButton({
    Name = "Click Me",
    Callback = function()
        print("Clicked!")
    end,
})

Tab:CreateToggle({
    Name = "Enable Feature",
    CurrentValue = false,
    Flag = "FeatureToggle",
    Callback = function(value) print(value) end,
})

Tab:CreateSlider({
    Name = "Speed",
    Min = 1, Max = 100, CurrentValue = 16,
    Flag = "SpeedSlider",
    Callback = function(v) print(v) end,
})

Tab:CreateInput({
    Name = "Player Name",
    Placeholder = "Enter name...",
    Flag = "PlayerInput",
    Callback = function(text) print(text) end,
})

Tab:CreateDropdown({
    Name = "Select Option",
    Options = {"A", "B", "C"},
    Flag = "DropdownFlag",
    Callback = function(opt) print(opt) end,
})

Tab:CreateKeybind({
    Name = "Toggle Key",
    CurrentKeybind = "E",
    Flag = "KeybindFlag",
    Callback = function() print("pressed") end,
})

Library:Notify({
    Title = "Hello",
    Content = "Welcome to PeakUI!",
    Duration = 5,
})
