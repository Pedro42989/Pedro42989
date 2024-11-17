local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Orion/main/source"))()
local Window = OrionLib:MakeWindow({Name = "Roblox Hitbox Expander Universal", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Tab = Window:MakeTab({Name = "Main", Icon = "rbxassetid://4483345998", PremiumOnly = false})
local Section = Tab:AddSection({Name = "Script"})

Tab:AddButton({
    Name = "Expand Non-Player Hitbox",
    Callback = function()
        local function expandNonPlayerHitbox()
            local localPlayer = game.Players.LocalPlayer
            for _, npc in ipairs(game.Workspace:GetDescendants()) do
                pcall(function()
                    if npc:IsA("Model") and npc:FindFirstChild("Humanoid") and not npc:FindFirstChild("HumanoidRootPart") then
                        local hitbox = npc:FindFirstChild("Humanoid") or npc.PrimaryPart
                        if hitbox then
                            hitbox.Size = Vector3.new(10, 10, 10)
                            hitbox.CanCollide = false
                            hitbox.Transparency = 0.5
                            hitbox.Color = Color3.fromRGB(255, 0, 0)
                        end
                    end
                end)
            end
        end
        while true do
            expandNonPlayerHitbox()
            wait(1)
        end
    end
})

Tab:AddButton({
    Name = "Expand Player Hitbox (Team Check)",
    Callback = function()
        local function expandPlayerHitbox()
            local localPlayer = game.Players.LocalPlayer
            for _, player in ipairs(game.Players:GetPlayers()) do
                pcall(function()
                    if player ~= localPlayer and player.Team ~= localPlayer.Team and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                        local hitbox = player.Character:FindFirstChild("HumanoidRootPart")
                        if hitbox then
                            hitbox.Size = Vector3.new(10, 10, 10)
                            hitbox.CanCollide = false
                            hitbox.Transparency = 0.5
                            hitbox.Color = Color3.fromRGB(255, 0, 0)
                        end
                    end
                end)
            end
        end
        while true do
            expandPlayerHitbox()
            wait(1)
        end
    end
})

Tab:AddButton({
    Name = "Expand All Player Hitboxes",
    Callback = function()
        local function expandAllPlayerHitboxes()
            local localPlayer = game.Players.LocalPlayer
            for _, player in ipairs(game.Players:GetPlayers()) do
                pcall(function()
                    if player ~= localPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                        local hitbox = player.Character:FindFirstChild("HumanoidRootPart")
                        if hitbox then
                            hitbox.Size = Vector3.new(10, 10, 10)
                            hitbox.CanCollide = false
                            hitbox.Transparency = 0.5
                            hitbox.Color = Color3.fromRGB(255, 0, 0)
                        end
                    end
                end)
            end
        end
        while true do
            expandAllPlayerHitboxes()
            wait(1)
        end
    end
})
