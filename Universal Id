--[[
    Eclipse | Universal Game ID
    made by @ronzy.exe on Discord
    https://discord.gg/76tHHGBrfz
]]

local Players = game:GetService("Players")
local MarketplaceService = game:GetService("MarketplaceService")
local HttpService = game:GetService("HttpService")

local Player = Players.LocalPlayer

local GameId = game.GameId
local PlaceId = game.PlaceId
local JobId = game.JobId

local function CopyToClipboard(value)
    if typeof(setclipboard) == "function" then
        setclipboard(tostring(value))
        return true
    elseif typeof(toclipboard) == "function" then
        toclipboard(tostring(value))
        return true
    end

    return false
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "EclipseGameID"
ScreenGui.ResetOnSpawn = false

pcall(function()
    ScreenGui.Parent = game:GetService("CoreGui")
end)

if not ScreenGui.Parent then
    ScreenGui.Parent = Player:WaitForChild("PlayerGui")
end

local Main = Instance.new("Frame")
Main.Name = "Main"
Main.Size = UDim2.fromOffset(360, 245)
Main.Position = UDim2.new(0.5, -180, 0.5, -122)
Main.BackgroundColor3 = Color3.fromRGB(17, 17, 24)
Main.BorderSizePixel = 0
Main.Parent = ScreenGui

Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 12)

local Stroke = Instance.new("UIStroke")
Stroke.Color = Color3.fromRGB(112, 82, 255)
Stroke.Thickness = 1.5
Stroke.Parent = Main

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, -20, 0, 38)
Title.Position = UDim2.fromOffset(12, 5)
Title.BackgroundTransparency = 1
Title.Text = "Eclipse | Universal Game ID"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 16
Title.Parent = Main

local function CreateEntry(label, value, y)
    local Name = Instance.new("TextLabel")
    Name.Size = UDim2.fromOffset(85, 30)
    Name.Position = UDim2.fromOffset(12, y)
    Name.BackgroundTransparency = 1
    Name.Text = label
    Name.TextColor3 = Color3.fromRGB(175, 175, 195)
    Name.Font = Enum.Font.GothamMedium
    Name.TextSize = 12
    Name.TextXAlignment = Enum.TextXAlignment.Left
    Name.Parent = Main

    local ValueBox = Instance.new("TextBox")
    ValueBox.Size = UDim2.fromOffset(155, 30)
    ValueBox.Position = UDim2.fromOffset(95, y)
    ValueBox.BackgroundColor3 = Color3.fromRGB(29, 29, 40)
    ValueBox.TextColor3 = Color3.fromRGB(235, 235, 245)
    ValueBox.Text = tostring(value)
    ValueBox.Font = Enum.Font.Code
    ValueBox.TextSize = 11
    ValueBox.ClearTextOnFocus = false
    ValueBox.TextEditable = false
    ValueBox.Parent = Main
    Instance.new("UICorner", ValueBox).CornerRadius = UDim.new(0, 6)

    local Copy = Instance.new("TextButton")
    Copy.Size = UDim2.fromOffset(75, 30)
    Copy.Position = UDim2.fromOffset(257, y)
    Copy.BackgroundColor3 = Color3.fromRGB(103, 75, 235)
    Copy.Text = "Copiar"
    Copy.TextColor3 = Color3.new(1, 1, 1)
    Copy.Font = Enum.Font.GothamBold
    Copy.TextSize = 11
    Copy.Parent = Main
    Instance.new("UICorner", Copy).CornerRadius = UDim.new(0, 6)

    Copy.Activated:Connect(function()
        if CopyToClipboard(value) then
            Copy.Text = "Copiado!"
        else
            ValueBox:CaptureFocus()
            ValueBox.SelectionStart = 1
            ValueBox.CursorPosition = #tostring(value) + 1
            Copy.Text = "Seleciona"
        end

        task.delay(1.5, function()
            if Copy.Parent then
                Copy.Text = "Copiar"
            end
        end)
    end)
end

CreateEntry("GameId:", GameId, 53)
CreateEntry("PlaceId:", PlaceId, 94)
CreateEntry("JobId:", JobId, 135)

local Footer = Instance.new("TextLabel")
Footer.Size = UDim2.new(1, -20, 0, 25)
Footer.Position = UDim2.fromOffset(12, 181)
Footer.BackgroundTransparency = 1
Footer.Text = "Universal Roblox | Eclipse"
Footer.TextColor3 = Color3.fromRGB(140, 140, 160)
Footer.Font = Enum.Font.Gotham
Footer.TextSize = 11
Footer.Parent = Main

local Close = Instance.new("TextButton")
Close.Size = UDim2.fromOffset(30, 26)
Close.Position = UDim2.new(1, -37, 0, 8)
Close.BackgroundColor3 = Color3.fromRGB(48, 39, 65)
Close.Text = "X"
Close.TextColor3 = Color3.new(1, 1, 1)
Close.Font = Enum.Font.GothamBold
Close.TextSize = 12
Close.Parent = Main
Instance.new("UICorner", Close).CornerRadius = UDim.new(0, 6)

Close.Activated:Connect(function()
    ScreenGui:Destroy()
end)

-- Arrastar a janela
local UserInputService = game:GetService("UserInputService")
local dragging = false
local dragStart, startPosition

Title.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1
        or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPosition = Main.Position
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and (
        input.UserInputType == Enum.UserInputType.MouseMovement
        or input.UserInputType == Enum.UserInputType.Touch
    ) then
        local delta = input.Position - dragStart
        Main.Position = UDim2.new(
            startPosition.X.Scale,
            startPosition.X.Offset + delta.X,
            startPosition.Y.Scale,
            startPosition.Y.Offset + delta.Y
        )
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1
        or input.UserInputType == Enum.UserInputType.Touch then
        dragging = false
    end
end)
