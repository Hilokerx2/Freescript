# Freescript

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Noname Hub", "Ocean")

local Tab = Window:NewTab("Update")
local Section = Tab:NewSection("New Menu")


Section:NewToggle("Kill Aura", "Noname Hub", function(state)
    if state then
_G.killaura = true

while _G.killaura do wait()
local dist = math.huge
    local target = nil
    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if v.ClassName == "Model" then
                    local magnitude = (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.Head.Position).magnitude
                    if magnitude < dist then
                        dist = magnitude
                        target = v.Name
                        v.Humanoid.Health = 0
                        print(target)
                    end
        end
    end
    end

    else
_G.killaura = false

while _G.killaura do wait()
local dist = math.huge
    local target = nil
    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if v.ClassName == "Model" then
                    local magnitude = (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.Head.Position).magnitude
                    if magnitude < dist then
                        dist = magnitude
                        target = v.Name
                        v.Humanoid.Health = 0
                        print(target)
                    end
        end
    end
    end

    end
end)

Section:NewToggle("Fast Attack", "FastAttack", function(state)
    if state then
_G.FastAttack = true

spawn(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
        local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
        Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
        Combat.activeController.timeToNextAttack = 0
    end)
end) 
end)


spawn(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        game:GetService'VirtualUser':CaptureController()
        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
    end)
end) 
end)
    else
_G.FastAttack = false
    end
end)


local Tab = Window:NewTab("Shop")
local Section = Tab:NewSection("Fruit")





local Tab = Window:NewTab("UI Script")
local Section = Tab:NewSection("UI")

Section:NewKeybind("Close Script", "Close", Enum.KeyCode.RightControl, function()
	Library:ToggleUI()
end)
