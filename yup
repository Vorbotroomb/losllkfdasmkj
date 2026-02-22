-- CONFIGURAÇÃO DO BACKDOOR (Mude para o caminho do seu Remote)
local BackdoorRemote = game:GetService("ReplicatedStorage"):FindFirstChild("execute") 

local function SendToServer(code)
    if BackdoorRemote then
        -- O formato depende de como o seu backdoor recebe o comando
        BackdoorRemote:FireServer(code)
    else
        warn("Backdoor Remote não encontrado!")
    end
end

-- Interface Principal
local ScreenGui = Instance.new("ScreenGui", game:GetService("CoreGui"))
local Frame = Instance.new("Frame", ScreenGui)
Frame.Size = UDim2.new(0, 220, 0, 350)
Frame.Position = UDim2.new(0.5, -110, 0.5, -175)
Frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Frame.BorderSizePixel = 0

local Layout = Instance.new("UIListLayout", Frame)
Layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
Layout.Padding = UDim.new(0, 5)

-- Função para criar botões de "Poder Real" (Server-Side)
local function CreateHackButton(txt, serverCode)
    local btn = Instance.new("TextButton", Frame)
    btn.Size = UDim2.new(0.9, 0, 0, 30)
    btn.Text = txt
    btn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    btn.TextColor3 = Color3.new(1, 1, 1)
    
    btn.MouseButton1Click:Connect(function()
        SendToServer(serverCode)
    end)
end

--- COMANDOS SERVER-SIDE (Onde a mágica acontece) ---

-- 1. Unanchor All (Tudo cai para TODOS)
CreateHackButton("Unanchor ALL", [[
    for _, obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("BasePart") then obj.Anchored = false end
    end
]])

-- 2. Decal Spam (Imagens em tudo)
CreateHackButton("Decal Spam", [[
    for _, obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("BasePart") then
            local d = Instance.new("Decal", obj)
            d.Texture = "rbxassetid://126344075041306" -- Substitua pelo ID da imagem
            d.Face = "All"
        end
    end
]])

-- 3. Skybox & Music
CreateHackButton("Chaos Theme (Sky/Music)", [[
    local s = Instance.new("Sky", game.Lighting)
    s.SkyboxBk = "rbxassetid://600830446"
    -- Adiciona música no SoundService para todos ouvirem
    local m = Instance.new("Sound", game.Workspace)
    m.SoundId = "rbxassetid://1837879011" 
    m.Volume = 10
    m:Play()
]])

-- 4. Realm Teleport (O Desafio)
-- Teleporta TODOS os jogadores para o ID fornecido
CreateHackButton("REALM TELEPORT ALL", [[
    local TS = game:GetService("TeleportService")
    local ID = 126344075041306
    for _, p in pairs(game.Players:GetPlayers()) do
        TS:Teleport(ID, p)
    end
]])

-- 5. Face Orange All
CreateHackButton("Face Orange All", [[
    for _, p in pairs(game.Players:GetPlayers()) do
        pcall(function()
            p.Character.Head.face.Texture = "rbxassetid://126344075041306"
        end)
    end
]])
