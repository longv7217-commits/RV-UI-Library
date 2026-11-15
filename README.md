RV UI Library
A UI library for Roblox, written in Luau. Used for making menus, hubs, and UI scripts for games.
The main file is library.txt. Copy the entire file into your executor and use it as shown in the example below.

Credit: realvux

Quick Start

lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/longv7217-commits/RV-UI-Library/refs/heads/main/Rv-UI%20Main%20Source"))()

local Window = Library:CreateWindow({
    Title = "RV Hub",
    Subtitle = "v1.0.0",
    Theme = "Dark",
    Keybind = Enum.KeyCode.RightShift,
})

local Tab = Window:CreateTab("Main", "Main")
Tab:CreateToggle("Auto Farm", false, function(v) print(v) end)
Tab:CreateSlider("Speed", 0, 100, 16, function(v) print(v) end)
If your executor blocks HttpGet, download the file and use loadstring(readfile("library.txt"))() instead of the loadstring line above.
If you run it twice, the library automatically deletes the old GUI before creating a new one, so you won't have 2 overlapping UIs.

Window, Dragging, Minimizing, Tab Switching, Resizing
Window
Library:CreateWindow returns a Window. Each Window has a TopBar, a TabBar on the left, Content on the right, and a Footer that is hidden by default.

Window:SetTitle(text) changes the title.

Window:SetSubtitle(text) changes the subtitle line.

Window:SetFooter(text) shows the Footer. Pass an empty string to hide it.

Window:Minimize() minimizes. Window:Restore() restores it. Window:Show() / Window:Hide() completely hides/shows it. Window:Toggle() toggles the state. Window:Maximize() / Window:Unmaximize() maximizes / reverts.

Window:SetKeybind(keycode) changes the show/hide keybind. Default is RightShift.

Window:SetSearchVisible(true/false) shows/hides the search bar.

Window:SetTheme("Ocean") changes the theme. Window:SetAccent(Color3) changes the accent color.

Window:Destroy() destroys that Window.

Library:Destroy() destroys the entire UI and disconnects all connections.

Dragging, Active, and Draggable
This is the part that prevents interference from the game outside.

All draggable frames have Active = true and Draggable = true: Main, TopBar, MiniBar, resize button. Child frames like TabBar, Content, Card, and buttons are also set to Active = true when created through their creation functions, so clicking on the UI doesn't fall through to the game, doesn't make the character move, or rotate the camera.

How to drag: hold the mouse on the TopBar and drag. The MakeDraggable function saves the starting mouse position and the Window's initial position, then adds the mouse delta. When the mouse is released, it stops. The MiniBar can also be dragged separately.

Note: Because the TopBar is a child of the Main frame, dragging the TopBar will drag the entire Main frame, not just the TopBar alone. That is the library's mechanism, not a Roblox bug.

Minus Button, Horizontal Bar
The - button on the TopBar is not to close it completely. Clicking it hides the Main frame and replaces it with a horizontal bar that is almost as wide as the screen, located at the top, similar to Rayfield's style.

This bar has: an accent-colored dot, the UI name, and the subtitle...
