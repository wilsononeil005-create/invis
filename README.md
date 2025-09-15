-- This script should be placed in a LocalScript within StarterPlayerScripts or StarterCharacterScripts
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

local function toggleInvisibility()
    local isInvisible = false

    -- Toggle the transparency of each part in the character
    for _, part in ipairs(character:GetDescendants()) do
        if part:IsA("BasePart") then
            if part.Transparency == 0 then
                part.Transparency = 1 -- Fully invisible
                isInvisible = true
            else
                part.Transparency = 0 -- Fully visible
                isInvisible = false
            end
        end
    end

    -- Optional: You can add logic to change the button text based on invisibility state
end

-- Create a GUI button to toggle invisibility
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "InvisibilityGui"
screenGui.Parent = player:WaitForChild("PlayerGui")

local toggleButton = Instance.new("TextButton")
toggleButton.Size = UDim2.new(0, 200, 0, 50)
toggleButton.Position = UDim2.new(0.5, -100, 0.5, -25)
toggleButton.Text = "Toggle Invisibility"
toggleButton.Parent = screenGui

toggleButton.MouseButton1Click:Connect(toggleInvisibility)

-- Create a collapsible button
local collapsibleButton = Instance.new("TextButton")
collapsibleButton.Size = UDim2.new(0, 200, 0, 50)
collapsibleButton.Position = UDim2.new(0.5, -100, 0.5, -75)
collapsibleButton.Text = "Collapse GUI"
collapsibleButton.Parent = screenGui

collapsibleButton.MouseButton1Click:Connect(function()
    screenGui.Visible = not screenGui.Visible
end)
