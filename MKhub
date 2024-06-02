-- Inicializando a UI
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Buttons = {}

-- Configurações da ScreenGui
ScreenGui.Name = "MKHub"
ScreenGui.Parent = game.CoreGui

-- Configurações do MainFrame
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
MainFrame.Size = UDim2.new(0, 200, 0, 400)
MainFrame.Position = UDim2.new(0, 0, 0, 0)

-- Configurações do Title
Title.Name = "Title"
Title.Parent = MainFrame
Title.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Title.Size = UDim2.new(1, 0, 0, 50)
Title.Font = Enum.Font.SourceSans
Title.Text = "MK HUB"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true

-- Função para criar botões
local function createButton(name, position, callback)
    local Button = Instance.new("TextButton")
    Button.Name = name
    Button.Parent = MainFrame
    Button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    Button.Size = UDim2.new(0, 180, 0, 30)
    Button.Position = UDim2.new(0, 10, 0, position)
    Button.Font = Enum.Font.SourceSans
    Button.Text = name
    Button.TextColor3 = Color3.fromRGB(255, 255, 255)
    Button.TextScaled = true
    Button.MouseButton1Click:Connect(callback)
    table.insert(Buttons, Button)
end

-- Funções dos scripts
local function changeColor(color)
    local player = game.Players.LocalPlayer
    if player and player.Character then
        for _, part in pairs(player.Character:GetChildren()) do
            if part:IsA("BasePart") then
                part.BrickColor = color
            end
        end
    end
end

local function changeSpeed(speed)
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.WalkSpeed = speed
    end
end

local function changeJumpPower(power)
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.JumpPower = power
    end
end

local function changeGravity(gravity)
    local workspace = game.Workspace
    if workspace and workspace.Gravity then
        workspace.Gravity = gravity
    end
end

local function setHealth(health)
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.Health = health
    end
end

local function setWalkSpeed(speed)
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.WalkSpeed = speed
    end
end

local function setJumpPower(power)
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.JumpPower = power
    end
end

-- Lista de funções de exemplo
local functionsList = {
    {name = "Aumentar velocidade para 100", func = function() changeSpeed(100) end},                     -- Aumentar a velocidade do personagem
    {name = "Ajustar gravidade para 50", func = function() changeGravity(50) end},                       -- Ajustar a gravidade do jogo
    {name = "Setar vida para 100", func = function() setHealth(100) end},                                -- Setar a vida do personagem para 100
    {name = "Setar velocidade de caminhada para 50", func = function() setWalkSpeed(50) end},            -- Setar a velocidade de caminhada do personagem
    {name = "Setar força de pulo para 150", func = function() setJumpPower(150) end},                    -- Setar a força de pulo do personagem
    {name = "Tornar invisível", func = function() setInvisible(true) end},                               -- Tornar o personagem invisível
    {name = "Tornar visível", func = function() setInvisible(false) end},                               -- Tornar o personagem visível
    {name = "MK HUB DOMINA BRUH!!!", func = function() print("MK HUB DOMINA BRUH!!!") end},             -- Imprimir uma mensagem de saudação no console
    {name = "Close", func = function() ScreenGui:Destroy() end},                                        -- Fechar a UI
    {name = "Enviar mensagem no console", func = function() print("Message for console") end},          -- Enviar uma mensagem para o console
    {name = "Mudar cor para vermelho", func = function() changeColor(Color3.fromRGB(255, 0, 0)) end},  -- Mudar a cor das partes do personagem para vermelho
}

-- Criando botões para cada função
for i, data in ipairs(functionsList) do
    createButton(data.name, 50 + (i - 1) * 35, data.func)
end

-- Adicionando a funcionalidade de arrastar a UI
local dragging
local dragInput
local dragStart
local startPos

local function update(input)
    local delta = input.Position - dragStart
    MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

MainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
        
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

MainFrame.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
        dragInput = input
    end
end)

game:GetService("UserInputService").InputChanged:Connect(function(input)
    if input == dragInput and dragging then
        update(input)
    end
end)

-- Função para tornar o personagem invisível ou visível
local function setInvisible(invisible)
    local player = game.Players.LocalPlayer
    if player and player.Character then
        for _, part in pairs(player.Character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Transparency = invisible and 1 or 0
            end
        end
    end
end
