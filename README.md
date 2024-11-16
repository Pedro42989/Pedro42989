-- abaixo estará lib da nossa UI

local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/7yhx/kwargs_Ui_Library/main/source.lua"))()

local UI = Lib:Create{
   Theme = "Dark", -- or any other theme
   Size = UDim2.new(0, 555, 0, 400) -- default
}

local Main = UI:Tab{
   Name = "inicia"
}

local Divider = Main:Divider{
   Name = "inicia shit"
}

local QuitDivider = Main:Divider{
   Name = "sair"
}

local player = game.Players.LocalPlayer
local car = player.Character:WaitForChild("Car")

-- Função para iniciar a corrida
local function startRace()
    -- Teleporta o carro para a linha de partida
    car:SetPrimaryPartCFrame(CFrame.new(Vector3.new(0, 0, 0))) -- Ajuste as coordenadas conforme necessário
    wait(1)
    
    -- Simula a pressão da tecla para acelerar
    local virtualUser = game:GetService("VirtualUser")
    virtualUser:CaptureController()
    virtualUser:SetKeyDown("w")
    wait(5) -- Tempo para completar a corrida, ajuste conforme necessário
    virtualUser:SetKeyUp("w")
end

-- Loop para repetir a corrida automaticamente
while true do
    startRace()
    wait(10) -- Tempo de espera entre as corridas, ajuste conforme necessário
end
