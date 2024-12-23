local lp = game.Players.LocalPlayer
local function getNPC()
    local dist, thing = math.huge
    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if v.Name == "Bandit [Lv. 5]" then
            local mag = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).magnitude
            if mag < dist then 
                dist = mag 
                thing = v 
            end
        end
    end
    return thing
end
 
local TweenService  = game:GetService("TweenService")
local noclipE       = false
local antifall      = false
 
local function noclip()
    for i, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
        if v:IsA("BasePart") and v.CanCollide == true then
            v.CanCollide = false
            game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0,0,0)
        end
    end
end
 
local function moveto(obj, speed)
    local info = TweenInfo.new(((game.Players.LocalPlayer.Character.HumanoidRootPart.Position - obj.Position).Magnitude)/ speed,Enum.EasingStyle.Linear)
    local tween = TweenService:Create(game.Players.LocalPlayer.Character.HumanoidRootPart, info, {CFrame = obj})
 
    if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
        antifall = Instance.new("BodyVelocity", game.Players.LocalPlayer.Character.HumanoidRootPart)
        antifall.Velocity = Vector3.new(0,0,0)
        noclipE = game:GetService("RunService").Stepped:Connect(noclip)
        tween:Play()
    end
 
    tween.Completed:Connect(function()
        antifall:Destroy()
        noclipE:Disconnect()
    end)
end
 
getgenv().bandit = true
while bandit do task.wait()
    pcall(function()
        moveto(getNPC().HumanoidRootPart.CFrame + Vector3.new(0,0,0), 100)
        game:GetService("VirtualUser"):ClickButton1(Vector2.new(9e9, 9e9))
    end)
end
