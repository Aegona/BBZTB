_G.AutoFarm = true
_G.BringMob = true

 
function CheckQuest()
        local Lv = game:GetService("Players").LocalPlayer.Data.Level.Value
            if Lv == 1 or Lv <= 9 then
                Mon = "Bandit [Lv. 5]"
                NameMon = "Bandit"
                LvQuest = 1
                NameQuest = "BanditQuest1"
                CFrameMon = CFrame.new(1038.2711181640625, 24.537282943725586, 1550.2586669921875)
                CFrameQuest = CFrame.new(1059.8109130859375, 16.362747192382812, 1549.0882568359375)
            elseif Lv == 10 or Lv <= 14 then
                Mon = "Monkey [Lv. 14]"
                NameMon = "Monkey"
                LvQuest = 1
                NameQuest = "JungleQuest"
                CFrameMon = CFrame.new(-1443.7662353515625, 61.851966857910156, -47.555946350097656)
                CFrameQuest = CFrame.new(-1599.8194580078125, 36.852149963378906, 153.0706024169922)
                elseif Lv == 15 or Lv <= 29 then
                Mon = "Gorilla [Lv. 20]"
                NameMon = "Gorilla"
                LvQuest = 2
                NameQuest = "JungleQuest"
                CFrameMon = CFrame.new(-1443.7662353515625, 61.851966857910156, -47.555946350097656)
                CFrameQuest = CFrame.new(-1599.8194580078125, 36.852149963378906, 153.0706024169922) 
        end 
    end


 function TP(P)
   local Distance = (P.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude -- จุดที่จะไป Position Only
   local Speed = 300 -- ความเร็วของมึง
   tweenService, tweenInfo = game:GetService("TweenService"), TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear)
   tween = tweenService:Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart, tweenInfo, {CFrame = P})
   tween:Play()
 end

spawn(function()
    while wait() do
        if _G.BringMob then
            pcall(function()
            CheckQuest()
       for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
for x,y in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
if v.Name == Mon then
    if y.Name == Mon then
 print("Bring")
   v.HumanoidRootPart.CFrame = y.HumanoidRootPart.CFrame
   v.HumanoidRootPart.Size = Vector3.new(60,60,60)
   y.HumanoidRootPart.Size = Vector3.new(60,60,60)
   v.HumanoidRootPart.Transparency = 1
   v.HumanoidRootPart.CanCollide = false
   y.HumanoidRootPart.CanCollide = false
   v.Humanoid.WalkSpeed = 0
   y.Humanoid.WalkSpeed = 0
   v.Humanoid.JumpPower = 0
   y.Humanoid.JumpPower = 0
   if sethiddenproperty then
     sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
end
end
end
end
end
end)
end
end
end)


spawn(function()
    while wait() do
        if _G.AutoFarm then
            pcall(function()
            CheckQuest()
 print("Farm1")
    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
 print("TPCQ")
    TP(CFrameQuest)
    if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5 then
    wait(.1)
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LvQuest)
    end
    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,NameMon) then
print("Forcheck")
            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                if v.Name == Mon and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid")   then
print("Then")
                    if v.Humanoid.Health > 0 then
                    repeat wait()
                        click()
                        Equip(_G.SelectWeapon)
                        HealthMin = v.Humanoid.MaxHealth * 90 / 100
                        Magma = (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
                        if Magma <= 230 then
                            if v.Humanoid.Health > HealthMin then
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,14)
                                else
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,15,0)
                            end
                        end
                            if v.Humanoid.Health > HealthMin then
                        Distance = (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude 
                        Speed = 300 
                        tweenService, tweenInfo = game:GetService("TweenService"), TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear)
                        tween = tweenService:Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart, tweenInfo, {CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,14)})
                        tween:Play() 
                        else
                        Distance = (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude 
                        Speed = 300 
                        tweenService, tweenInfo = game:GetService("TweenService"), TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear)
                        tween = tweenService:Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart, tweenInfo, {CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,15,0)})
                        tween:Play()
                            end
                        v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                        v.HumanoidRootPart.CanCaillde = false
                    until _G.AutoFarm == false or v.Humanoid.Health <= 0
                    else
                        TP(CFrameMon)
                    end
                    if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,NameMon) then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                    end
                    if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
                        _G.AutoFarm = false
                        wait(3)
                        _G.AutoFarm = true
                        end
                end
                end
        end
        end
       end)
end
end
end)


spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function()
        if _G.AutoFarm then
        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") then
            setfflag("HumanoidParallelRemoveNoPhysics", "False")
            setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
            game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
            end
        end
    end)
end)



