local player = game.Players.LocalPlayer
local isMobile = game:GetService("UserInputService").TouchEnabled -- Detect mobile devices

-- Create the ScreenGui
local gui = Instance.new("ScreenGui")
gui.Name = "LunaExecutor"
gui.Parent = player:WaitForChild("PlayerGui")

-- Create the Main Frame with Dark Mode
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 250, 0, 300)
frame.Position = isMobile and UDim2.new(0.5, -125, 0.3, 0) or UDim2.new(0.5, -125, 0.3, 0) -- Position in center for mobile and PC
frame.BackgroundTransparency = 0
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30) -- Dark Mode Background
frame.Parent = gui

-- If on mobile, shrink the frame
if isMobile then
    frame.Size = UDim2.new(0, 200, 0, 250) -- Shrink on mobile
end

-- Add Rounded Corners
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 10)
corner.Parent = frame

-- Create the Title
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.Position = UDim2.new(0, 0, 0, 0)
title.BackgroundTransparency = 1
title.Text = "Luna Executor"
title.TextColor3 = Color3.fromRGB(170, 85, 255) -- Purple
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20
title.Parent = frame

-- Add Decal Next to Title
local image = Instance.new("ImageLabel")
image.Size = UDim2.new(0, 40, 0, 40)
image.Position = UDim2.new(1, -45, 0, 0)
image.BackgroundTransparency = 1
image.Image = "rbxassetid://109422108240888" -- Luna Icon
image.Parent = title

-- Function to make UI draggable
local dragging = true
local dragInput, dragStart, startPos

frame.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = frame.Position
    end
end)

frame.InputChanged:Connect(function(input)
    if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
        local delta = input.Position - dragStart
        frame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

frame.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)

-- Create Notification at Bottom Right
local function createNotification(message)
    local notification = Instance.new("TextLabel")
    notification.Size = UDim2.new(0, 300, 0, 50)
    notification.Position = UDim2.new(1, -310, 1, -60) -- Position in bottom right for PC
    notification.BackgroundTransparency = 0.5
    notification.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    notification.Text = message
    notification.TextColor3 = Color3.fromRGB(255, 255, 255)
    notification.Font = Enum.Font.SourceSans
    notification.TextSize = 20
    notification.Parent = gui

    wait(3) -- Wait for 3 seconds before removing notification
    notification:Destroy()
end

-- Check if Mobile and Adjust Notification
if isMobile then
    createNotification("Lunar has successfully injected")
else
    createNotification("Lunar has successfully injected")
end

-- Function to create buttons
local function createButton(name, position, action)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0.8, 0, 0, 40)
    button.Position = UDim2.new(0.1, 0, position, 0)
    button.BackgroundTransparency = 1
    button.Text = name
    button.TextColor3 = Color3.fromRGB(170, 85, 255) -- Purple
    button.Font = Enum.Font.SourceSansItalic
    button.TextSize = 16
    button.Parent = frame

    -- Add Rounded Corners
    local buttonCorner = Instance.new("UICorner")
    buttonCorner.CornerRadius = UDim.new(0, 8)
    buttonCorner.Parent = button

    button.MouseButton1Click:Connect(action)
end

-- Admin Commands
local function kickAll()
    for _, plr in pairs(game.Players:GetPlayers()) do
        if plr ~= player then
            plr:Kick("You have been kicked by an admin.")
        end
    end
end

local function killAll()
    for _, plr in pairs(game.Players:GetPlayers()) do
        if plr.Character and plr.Character:FindFirstChild("Humanoid") then
            plr.Character.Humanoid.Health = 0
        end
    end
end

local function makeInvisible()
    if player.Character then
        for _, part in pairs(player.Character:GetChildren()) do
            if part:IsA("BasePart") or part:IsA("MeshPart") then
                part.Transparency = 1
            end
        end
    end
end

local function banPlayer()
    player:Kick("You have been permanently banned.")
end

local function moomGravity()
    game.Workspace.Gravity = 25 -- Low Gravity (Moon Effect)
end

-- Create Buttons
createButton("Kick All", 0.2, kickAll)
createButton("Kill All", 0.35, killAll)
createButton("Invisibility", 0.5, makeInvisible)
createButton("Ban (Yourself)", 0.65, banPlayer)
createButton("Moom Gravity", 0.8, moonGravity)
