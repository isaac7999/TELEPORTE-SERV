-- Serviços
local Players = game:GetService("Players")
local TeleportService = game:GetService("TeleportService")
local LocalPlayer = Players.LocalPlayer

-- Criar ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

-- Frame principal
local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0,300,0,150)
Frame.Position = UDim2.new(0.5,-150,0.5,-75)
Frame.BackgroundColor3 = Color3.fromRGB(50,50,50)
Frame.BorderSizePixel = 0
Frame.Parent = ScreenGui
Frame.Active = true
Frame.Draggable = true -- Permite mover a UI

-- Botão X para fechar
local CloseButton = Instance.new("TextButton")
CloseButton.Size = UDim2.new(0,30,0,30)
CloseButton.Position = UDim2.new(1,-35,0,5)
CloseButton.BackgroundColor3 = Color3.fromRGB(200,50,50)
CloseButton.TextColor3 = Color3.fromRGB(255,255,255)
CloseButton.Text = "X"
CloseButton.Parent = Frame

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- Label
local Label = Instance.new("TextLabel")
Label.Size = UDim2.new(1, -20, 0, 30)
Label.Position = UDim2.new(0,10,0,10)
Label.BackgroundTransparency = 1
Label.TextColor3 = Color3.fromRGB(255,255,255)
Label.Text = "Digite o Job ID:"
Label.TextXAlignment = Enum.TextXAlignment.Left
Label.Parent = Frame

-- TextBox para digitar Job ID
local TextBox = Instance.new("TextBox")
TextBox.Size = UDim2.new(1,-20,0,40)
TextBox.Position = UDim2.new(0,10,0,50)
TextBox.PlaceholderText = "Ex: 1234567890abcdef"
TextBox.ClearTextOnFocus = false
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(0,0,0)
TextBox.BackgroundColor3 = Color3.fromRGB(200,200,200)
TextBox.Parent = Frame

-- Botão Teleportar
local TeleportButton = Instance.new("TextButton")
TeleportButton.Size = UDim2.new(1,-20,0,40)
TeleportButton.Position = UDim2.new(0,10,0,100)
TeleportButton.BackgroundColor3 = Color3.fromRGB(50,150,50)
TeleportButton.TextColor3 = Color3.fromRGB(255,255,255)
TeleportButton.Text = "Teleportar"
TeleportButton.Parent = Frame

TeleportButton.MouseButton1Click:Connect(function()
    local jobId = TextBox.Text
    if jobId and jobId ~= "" then
        TeleportService:TeleportToPlaceInstance(game.PlaceId, jobId, LocalPlayer)
    else
        warn("Digite um Job ID válido!")
    end
end)
