-- ========== SALVAR SKIN ANTES DE CARREGAR O HUB ==========

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local function SaveSkin()
    local SaveOutfit = ReplicatedStorage:FindFirstChild("Remotes") and ReplicatedStorage.Remotes:FindFirstChild("SaveOutfit")
    if SaveOutfit then
        pcall(function()
            SaveOutfit:InvokeServer(50, "Catholic Hub")
        end)
    end
end

local function LoadSkin()
    local LoadOutfit = ReplicatedStorage:FindFirstChild("Remotes") and ReplicatedStorage.Remotes:FindFirstChild("LoadOutfit")
    if LoadOutfit then
        pcall(function()
            LoadOutfit:InvokeServer(50)
        end)
    end
end

-- Tenta salvar de várias formas
task.spawn(function()
    task.wait(2)
    SaveSkin()
    task.wait(1)
    SaveSkin()
    task.wait(1)
    SaveSkin()
end)

-- ========== FIM DO SALVAR ==========

-- ========== RESTAURAR SKIN DEPOIS DO HUB ==========

task.spawn(function()
    task.wait(5)
    
    -- Tenta carregar várias vezes
    for i = 1, 15 do
        LoadSkin()
        task.wait(0.3)
    end
    
    -- Quando o personagem mudar
    LocalPlayer.CharacterAdded:Connect(function()
        task.wait(2)
        for i = 1, 10 do
            LoadSkin()
            task.wait(0.2)
        end
    end)
end)

-- ========== FIM DA RESTAURAÇÃO ==========

game.StarterGui:SetCore("SendNotification", {
    Title = "Welcome to Catholic Hub!",
    Text = "Look at the credits in the first tab!",
    Duration = 5,
})

--------------------------------------------------------------------------------------------------------------------------------
loadstring(game:HttpGet("https://pastebin.com/raw/N4xSxRQU"))()

local redzlib = loadstring(game:HttpGet("https://pastefy.app/WTFg1Qpp/raw"))()

local Window = redzlib:MakeWindow({
    Title = "Catholic Hub | Brookhaven RP",
    SubTitle = "by Denolk・Version 1.1 Remade",
    SaveFolder = "catholichubfolder"
  })

  Window:AddMinimizeButton({
    Button = { Image = "rbxassetid://88281998871219", BackgroundTransparency = 0 },
    Corner = { CornerRadius = UDim.new(35, 1) },
})

--------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: credits === --
--------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Credits", "info"})
Tab:AddSection({"Hub Credits"})

Tab:AddDiscordInvite({
    Name = "Catholic Hub",
    Description = "Join our Discord server",
    Logo = "rbxassetid://98296601157312",
    Invite = "https://discord.gg/hW8vab2wDw",
})

Tab:AddSection({ "User Information" })

local player = game.Players.LocalPlayer

Tab:AddParagraph({ "Username:", player.Name })
Tab:AddParagraph({ "User ID:", tostring(player.UserId) })
Tab:AddParagraph({ "Account Age:", tostring(player.AccountAge) .. " days" })

Tab:AddSection({ "System Information" })

local function detectExecutor()
    if identifyexecutor then
        local exec = identifyexecutor()
        return exec and exec or "Unknown"
    elseif syn then
        return "Synapse X"
    elseif KRNL_LOADED then
        return "KRNL"
    elseif fluxus then
        return "Fluxus"
    else
        return "Unknown Executor"
    end
end

Tab:AddParagraph({ "Executor:", detectExecutor() })
Tab:AddParagraph({ "Game:", "Brookhaven RP" })
Tab:AddParagraph({ "Place ID:", tostring(game.PlaceId) })

Tab:AddSection({ "Server Information" })

local players = game:GetService("Players")
Tab:AddParagraph({ "Online Players:", tostring(#players:GetPlayers()) .. "/" .. tostring(players.MaxPlayers) })
Tab:AddParagraph({ "Server ID:", game.JobId })

local function getTime()
    return os.date("%H:%M:%S")
end

local function getDate()
    return os.date("%d/%m/%Y")
end

Tab:AddSection({ "Time Information" })

Tab:AddParagraph({ "Current Time:", getTime() })
Tab:AddParagraph({ "Current Date:", getDate() })

Tab:AddSection({ "Developer Links" })

Tab:AddButton({
    Name = "Copy TikTok Denolk",
    Callback = function()
        setclipboard("@mrdenolk")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Username copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy TikTok Link",
    Callback = function()
        setclipboard("https://www.tiktok.com/@mrdenolk")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Link copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy TikTok Catholic Hub",
    Callback = function()
        setclipboard("@catholic_hub0")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Username copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy TikTok Link",
    Callback = function()
        setclipboard("https://www.tiktok.com/@catholic_hub0")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Link copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy All Info",
    Callback = function()
        local info = "=== Catholic Hub Info ===\n"
        info = info .. "User: " .. player.Name .. "\n"
        info = info .. "ID: " .. player.UserId .. "\n"
        info = info .. "Executor: " .. detectExecutor() .. "\n"
        info = info .. "Server: " .. #players:GetPlayers() .. "/" .. players.MaxPlayers .. "\n"
        info = info .. "Time: " .. getTime() .. " | " .. getDate() .. "\n"
        info = info .. "========================"
        
        setclipboard(info)
        game.StarterGui:SetCore("SendNotification", {
            Title = "Success",
            Text = "Info copied to clipboard!",
            Duration = 3
        })
    end
})

Tab:AddSection({ "Development Team" })

Tab:AddParagraph({ "Owner & Sub-Owner:", "Denolk & Mayke" })
Tab:AddParagraph({ "Manager & Developer:", "Streex..." })
Tab:AddParagraph({ "Admins:", "Ghost and DemoxianYT" })
Tab:AddParagraph({ "Moderators:", "Nplayboy, PH, Ixi362" })
Tab:AddParagraph({ "Testers:", "Fhata & Bryan... (In-complete)" })

Tab:AddSection({ "Hub Information" })

Tab:AddParagraph({ "Name:", "Catholic Hub" })
Tab:AddParagraph({ "Version:", "1.1 Remade" })
Tab:AddParagraph({ "Game:", "Brookhaven RP" })

task.spawn(function()
    while task.wait(1) do

    end
end)

 ---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Local Player === --
-----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Local Player", "User"})
local Section = Tab:AddSection({"Local Player Effects"})

Tab:AddSlider({
    Name = "Player Speed (local)",
    Increase = 1,
    MinValue = 16,
    MaxValue = 1000,
    Default = 16,
    Callback = function(Value)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        
        if humanoid then
            humanoid.WalkSpeed = Value
        end
    end
})
 
Tab:AddSlider({
    Name = "Player Jump (local)",
    Increase = 1,
    MinValue = 50,
    MaxValue = 1000,
    Default = 50,
    Callback = function(Value)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        
        if humanoid then
            humanoid.JumpPower = Value
        end
    end
})
 
Tab:AddSlider({
    Name = "Player Gravity (local)",
    Increase = 1,
    MinValue = 0,
    MaxValue = 1000,
    Default = 196.2,
    Callback = function(Value)
        game.Workspace.Gravity = Value
    end
})
 
local InfiniteJumpEnabled = false
 
 game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfiniteJumpEnabled then
       local character = game.Players.LocalPlayer.Character
       if character and character:FindFirstChild("Humanoid") then
          character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
       end
    end
end)

Tab:AddButton({
    Name = "Reset Speed, Gravity, Jump Power",
    Callback = function()
        -- Resetar Speed
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.WalkSpeed = 16 
            humanoid.JumpPower = 50 
        end
        
        game.Workspace.Gravity = 196.2 
        

        InfiniteJumpEnabled = false
    end
})
 
Tab:AddToggle({
    Name = "Infinite Jump",
    Default = false,
    Callback = function(Value)
       InfiniteJumpEnabled = Value
    end
})

local UltimateNoclip = {
    Enabled = false,
    Connections = {},
    SoccerBalls = {}
}

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer

local function managePlayerCollisions(character)
    if not character then return end
    
    for _, part in ipairs(character:GetDescendants()) do
        if part:IsA("BasePart") then
            part.CanCollide = not UltimateNoclip.Enabled
            part.Anchored = false
        end
    end
end

local function voidProtection(rootPart)
    if rootPart.Position.Y < -500 then
        local safeCFrame = CFrame.new(0, 100, 0)
        local rayParams = RaycastParams.new()
        rayParams.FilterDescendantsInstances = {LocalPlayer.Character}
        
        local result = Workspace:Raycast(rootPart.Position, Vector3.new(0, 500, 0), rayParams)
        rootPart.CFrame = result and CFrame.new(result.Position + Vector3.new(0, 5, 0)) or safeCFrame
    end
end

local function manageSoccerBalls()
    local soccerFolder = Workspace:FindFirstChild("Com", true)
                      and Workspace.Com:FindFirstChild("001_SoccerBalls")
    
    if soccerFolder then
        for _, ball in ipairs(soccerFolder:GetChildren()) do
            if ball.Name:match("^Soccer") then
                pcall(function()
                    ball.CanCollide = not UltimateNoclip.Enabled
                    ball.Anchored = UltimateNoclip.Enabled
                end)
                UltimateNoclip.SoccerBalls[ball] = true
            end
        end
        
        if not UltimateNoclip.Connections.BallAdded then
            UltimateNoclip.Connections.BallAdded = soccerFolder.ChildAdded:Connect(function(ball)
                if ball.Name:match("^Soccer") then
                    task.wait(0.3)
                    pcall(function()
                        ball.CanCollide = not UltimateNoclip.Enabled
                        ball.Anchored = UltimateNoclip.Enabled
                    end)
                end
            end)
        end
    end
end

local section = Tab:AddSection({"Manage Player Boards"})

local textoPlaca = ""
local selectedPlaca = nil

local function getPlayersListPlaca()
    local list = {}
    for _, plr in ipairs(Players:GetPlayers()) do
        if plr ~= LocalPlayer then
            table.insert(list, plr.Name)
        end
    end
    return list
end

local function trocaPlaca(all, txt)
    if all then
        for _, v in next, Players:GetPlayers() do
            if v.Character and v.Character:FindFirstChild("Sign") then
                v.Character:FindFirstChild("Sign").ToolSound:FireServer("Sign", "SignWords", txt)
            end
        end
    else
        if selectedPlaca then
            local target = Players:FindFirstChild(selectedPlaca)
            if target and target.Character and target.Character:FindFirstChild("Sign") then
                target.Character:FindFirstChild("Sign").ToolSound:FireServer("Sign", "SignWords", txt)
            end
        end
    end
end

Tab:AddTextBox({
    Name = "Text on the Plate",
    PlaceholderText = "Texto da placa",
    Callback = function(value)
        textoPlaca = value
    end
})

Tab:AddButton({
    Name = "Rewrite ALL Plate",
    Callback = function()
        trocaPlaca(true, textoPlaca)
    end
})

 ---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Raid Sky === --
-----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Raid Sky", "cloud"})
local Section = Tab:AddSection({"SkyBox Functions"})

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local LocalPlayer = Players.LocalPlayer

local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local ChangeCharacterBody = Remotes:WaitForChild("ChangeCharacterBody")

local BodyId = "100839513065432"
local CurrentTrack
local Humanoid, Animator
local LoopAnim = false

local function SetupCharacter(char)
	Humanoid = char:WaitForChild("Humanoid")
	Animator = Humanoid:FindFirstChildOfClass("Animator")
	if not Animator then
		Animator = Instance.new("Animator")
		Animator.Parent = Humanoid
	end
end

SetupCharacter(LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait())
LocalPlayer.CharacterAdded:Connect(SetupCharacter)

local function ApplyBody()
	pcall(function()
		ChangeCharacterBody:InvokeServer({
			[1] = tonumber(BodyId)
		})
	end)
end

local function ResetBody()
	pcall(function()
		local args = {
			[1] = {
				[1] = 0,
				[2] = 0,
				[3] = 0,
				[4] = 0,
				[5] = 0,
				[6] = 0
			}
		}
		ChangeCharacterBody:InvokeServer(unpack(args))
	end)
end

local function PlayAnimation()
	if not Animator then return end
	local Anim = Instance.new("Animation")
	Anim.AnimationId = "rbxassetid://70883871260184"
	local track = Animator:LoadAnimation(Anim)
	track.Priority = Enum.AnimationPriority.Action
	track.Looped = false
	track:Play()
	CurrentTrack = track
end

local function StopAnimation()
	LoopAnim = false
	if CurrentTrack then
		pcall(function()
			CurrentTrack:Stop()
		end)
	end
end

Tab:AddToggle({
	Name = "SkyBox FE",
	Description = "",
	Default = false,
	Callback = function(Value)
		if Value then
			LoopAnim = true
			task.spawn(function()
				while LoopAnim do
					PlayAnimation()
					task.wait(0.001)
				end
			end)
			task.delay(1.2, ApplyBody)
		else
			StopAnimation()
			ResetBody()
		end
	end
})

local Camisas = {
    ["C00lkid"] = 88508273882423,
    ["Tubers93"] = 138121234806572,
    ["Night"] = 4921509323,
    ["Sky"] = 14820056722,
    ["Horror"] = 11714553713,
    ["Hacker"] = 9567541545,
    ["Blood"] = 881133247,
}

local CamisaNomes = {}
for nome in pairs(Camisas) do
    table.insert(CamisaNomes, nome)
end

table.sort(CamisaNomes)

Tab:AddDropdown({
    Name = "Shirts",
    Options = CamisaNomes,
    Callback = function(selecionada)
        local id = Camisas[selecionada]
        if id then
            ReplicatedStorage.Remotes.WearShirt:InvokeServer(id)
        end
    end
})


Tab:AddTextBox({
    Name = "Shirt ID",
    PlaceholderText = "Enter the Shirt ID",
    Callback = function(Value)
        local id = tonumber(Value)
        if id then
            pcall(function()
                ReplicatedStorage.Remotes.WearShirt:InvokeServer(id)
            end)
        end
    end
})

local Section = Tab:AddSection({"FleshBang Functions"})

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local ChangeCharacterBody = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("ChangeCharacterBody")

local LoopAnim = false
local CurrentTrack

local function ApplyFreshBang()
	pcall(function()
		local args = {
			[1] = {
				[1] = 96655874457685,
				[2] = 123402086843885,
				[3] = 78300682916056,
				[4] = 86276701020724,
				[5] = 78409653958165,
				[6] = 120668655481073
			}
		}
		ChangeCharacterBody:InvokeServer(unpack(args))
	end)
end

local function ResetBody()
	pcall(function()
		local args = {
			[1] = {
				[1] = 0,
				[2] = 0,
				[3] = 0,
				[4] = 0,
				[5] = 0,
				[6] = 0
			}
		}
		ChangeCharacterBody:InvokeServer(unpack(args))
	end)
end

local function PlayAnimation()
	local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
	local humanoid = char:WaitForChild("Humanoid")
	local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)
	local Anim = Instance.new("Animation")
	Anim.AnimationId = "rbxassetid://70883871260184"
	local track = animator:LoadAnimation(Anim)
	track.Priority = Enum.AnimationPriority.Action
	track.Looped = false
	track:Play()
	CurrentTrack = track
end

local function StopAnimation()
	LoopAnim = false
	if CurrentTrack then
		pcall(function()
			CurrentTrack:Stop()
		end)
	end
end

Tab:AddToggle({
	Name = "FreshBang",
	Description = "",
	Default = false,
	Callback = function(Value)
		if Value then
			LoopAnim = true
			task.spawn(function()
				while LoopAnim do
					PlayAnimation()
					task.wait(0.05)
				end
			end)
			task.delay(1.2, ApplyFreshBang)
		else
			StopAnimation()
			ResetBody()
		end
	end
})


local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local LocalPlayer = Players.LocalPlayer
local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local ChangeBodyColor = Remotes:WaitForChild("ChangeBodyColor")

local primaryColors = {
	"White","Black","Really red","Bright blue","Bright green",
	"Bright yellow","Bright orange","Bright purple","Bright pink"
}

local rgbColors = {
	"Really red","Bright orange","Bright yellow","Bright green",
	"Bright bluish green","Bright blue","Bright violet","Bright pink"
}

local mode = "None"
local rgbEnabled = false

Tab:AddDropdown({
	Name = "Body Color",
	Options = {"None","Primary Colors","RGB"},
	Default = "None",
	Callback = function(v)
		mode = v
		rgbEnabled = v == "RGB"
		if rgbEnabled then
			task.spawn(function()
				while rgbEnabled do
					for _, c in ipairs(rgbColors) do
						if not rgbEnabled then break end
						ChangeBodyColor:FireServer(c)
						task.wait(0.25)
					end
				end
			end)
		end
	end
})

Tab:AddDropdown({
	Name = "Primary Body Color",
	Options = primaryColors,
	Default = primaryColors[1],
	Callback = function(v)
		if mode == "Primary Colors" then
			ChangeBodyColor:FireServer(v)
		end
	end
})

local rgbAtivo = false
local rgbThread

local cores = {
    "Light reddish violet","Salmon","Sunrise","Carnation pink","Pink","Hot pink",
    "Really red","Tawny","Burgundy","Maroon","Cocoa","Rust","CGA brown","Beige",
    "Brick yellow","Burlap","Fawn brown","Br. yellowish orange","Olive","New Yeller",
    "Br. yellowish green","Mint","Artichoke","Lime green","Grime","Forest green",
    "Parsley green","Earth green","Slime green","Toothpaste","Pastel light blue",
    "Cyan","Bright blue","Really blue","Dark blue","Navy blue","Royal purple",
    "Magenta","Bright violet","Eggplant","Mulberry","Institutional white",
    "Mid gray","Cloudy grey","Flint","Fossil","Medium stone grey",
    "Dark stone grey","Smoky grey","Black","Really black","Dirt brown",
    "Pine Cone","Brown","Dark nougat","Light orange","Pastel brown"
}

local function iniciarRGB()
    if rgbThread then return end
    rgbThread = task.spawn(function()
        while rgbAtivo do
            for _, cor in ipairs(cores) do
                if not rgbAtivo then break end
                pcall(function()
                    ReplicatedStorage.Remotes.ChangeBodyColor:FireServer(cor)
                end)
                task.wait(0.02) 
            end
        end
        rgbThread = nil
    end)
end

Tab:AddToggle({
    Name = "RGB Body (Speed)",
    Default = false,
    Callback = function(v)
        rgbAtivo = v
        if v then
            iniciarRGB()
        end
    end
})

local Section = Tab:AddSection({"Spin Settings (SkyBox FE & FleshBang)"})

local spinEnabled = false
local spinSpeed = 10
local spinDirection = 1 -- 1 = direita, -1 = esquerda

Tab:AddToggle({
	Name = "Spin Body",
	Description = "",
	Default = false,
	Callback = function(v)
		spinEnabled = v
		if v then
			task.spawn(function()
				while spinEnabled do
					local char = LocalPlayer.Character
					if char and char:FindFirstChild("HumanoidRootPart") then
						local root = char.HumanoidRootPart
						root.CFrame = root.CFrame * CFrame.Angles(0, math.rad(spinSpeed * spinDirection), 0)
					end
					task.wait(0.02)
				end
			end)
		end
	end
})

Tab:AddToggle({
    Name = "Spin Direction (Right/Left)",
    Description = "",
    Default = true, -- true = direita, false = esquerda
    Callback = function(v)
        if v then
            spinDirection = 1  -- Direita
        else
            spinDirection = -1 -- Esquerda
        end
    end
})

Tab:AddSlider({
    Name = "Spin Speed",
    Description = "",
    MinValue = 1,
    MaxValue = 1000,
    Default = 10,
    Increase = 1,
    Callback = function(v)
        spinSpeed = v
    end
})

----------------------------------------------------------------------------------------------------------------------------------
                                                         -- Tab:  Avatar --
----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Avatar", "shirt"})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Remotes = ReplicatedStorage:WaitForChild("Remotes")

local Section = Tab:AddSection({"Copy Avatar"})
local Target = nil

local function GetPlayerNames()
    local playerNames = {}
    for _, player in ipairs(Players:GetPlayers()) do
        if player.Name ~= LocalPlayer.Name then
            table.insert(playerNames, player.Name)
        end
    end
    return playerNames
end

local Dropdown = Tab:AddDropdown({
    Name = "Player List",
    Description = "",
    Options = GetPlayerNames(),
    Default = "",
    Flag = "player list",
    Callback = function(playername)
        Target = playername
    end
})

local function UpdatePlayers()
    Dropdown:Set(GetPlayerNames())
end

UpdatePlayers()
Players.PlayerAdded:Connect(UpdatePlayers)
Players.PlayerRemoving:Connect(UpdatePlayers)

Tab:AddButton({
    Name = "Update List",
    Callback = UpdatePlayers
})

Tab:AddButton({
    Name = "Copy Avatar",
    Callback = function()
        if not Target then return end
        local LP = LocalPlayer
        local LChar = LP.Character
        local TPlayer = Players:FindFirstChild(Target)
        if not (TPlayer and TPlayer.Character) then return end

        local LHumanoid = LChar and LChar:FindFirstChildOfClass("Humanoid")
        local THumanoid = TPlayer.Character:FindFirstChildOfClass("Humanoid")
        if not (LHumanoid and THumanoid) then return end

        local LDesc = LHumanoid:GetAppliedDescription()
        local PDesc = THumanoid:GetAppliedDescription()

        -- Reset Accessories
        for _, acc in ipairs(LDesc:GetAccessories(true)) do
            if acc.AssetId and tonumber(acc.AssetId) then
                Remotes.Wear:InvokeServer(tonumber(acc.AssetId))
                task.wait(0.2)
            end
        end

        if tonumber(LDesc.Shirt) then Remotes.Wear:InvokeServer(tonumber(LDesc.Shirt)); task.wait(0.2) end
        if tonumber(LDesc.Pants) then Remotes.Wear:InvokeServer(tonumber(LDesc.Pants)); task.wait(0.2) end
        if tonumber(LDesc.Face) then Remotes.Wear:InvokeServer(tonumber(LDesc.Face)); task.wait(0.2) end

        -- Apply Body Parts
        local argsBody = {{PDesc.Torso, PDesc.RightArm, PDesc.LeftArm, PDesc.RightLeg, PDesc.LeftLeg, PDesc.Head}}
        Remotes.ChangeCharacterBody:InvokeServer(unpack(argsBody))
        task.wait(0.5)

        if tonumber(PDesc.Shirt) then Remotes.Wear:InvokeServer(tonumber(PDesc.Shirt)); task.wait(0.3) end
        if tonumber(PDesc.Pants) then Remotes.Wear:InvokeServer(tonumber(PDesc.Pants)); task.wait(0.3) end
        if tonumber(PDesc.Face) then Remotes.Wear:InvokeServer(tonumber(PDesc.Face)); task.wait(0.3) end

        for _, v in ipairs(PDesc:GetAccessories(true)) do
            if v.AssetId and tonumber(v.AssetId) then
                Remotes.Wear:InvokeServer(tonumber(v.AssetId))
                task.wait(0.3)
            end
        end

        -- Skin Colors
        local SkinColor = TPlayer.Character:FindFirstChild("Body Colors")
        if SkinColor then Remotes.ChangeBodyColor:FireServer(tostring(SkinColor.HeadColor)); task.wait(0.3) end

        -- Animations
        if tonumber(PDesc.IdleAnimation) then Remotes.Wear:InvokeServer(tonumber(PDesc.IdleAnimation)); task.wait(0.3) end

        -- RP Name & Bio
        local Bag = TPlayer:FindFirstChild("PlayersBag")
        if Bag then
            if Bag:FindFirstChild("RPName") and Bag.RPName.Value ~= "" then Remotes.RPNameText:FireServer("RolePlayName", Bag.RPName.Value); task.wait(0.3) end
            if Bag:FindFirstChild("RPBio") and Bag.RPBio.Value ~= "" then Remotes.RPNameText:FireServer("RolePlayBio", Bag.RPBio.Value); task.wait(0.3) end
            if Bag:FindFirstChild("RPNameColor") then Remotes.RPNameColor:FireServer("PickingRPNameColor", Bag.RPNameColor.Value); task.wait(0.3) end
            if Bag:FindFirstChild("RPBioColor") then Remotes.RPNameColor:FireServer("PickingRPBioColor", Bag.RPBioColor.Value); task.wait(0.3) end
        end
    end
})

Tab:AddSection({"Custom Skins"})
if not _G.togglesInitialized then _G.togglesInitialized = {} end

local originalSkinSaved = false

local function SaveOriginalSkin()
    if not originalSkinSaved then
        pcall(function()
            local SaveOutfit = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("SaveOutfit")
            SaveOutfit:InvokeServer(50, "Catholic Hub Original")
            originalSkinSaved = true
        end)
    end
end

local function LoadOriginalSkin()
    pcall(function()
        local LoadOutfit = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("LoadOutfit")
        LoadOutfit:InvokeServer(50)
    end)
end

Tab:AddToggle({
    Name = "Small Avatar",
    Default = false,
    Callback = function(Value)
        if not _G.togglesInitialized.Small then 
            _G.togglesInitialized.Small = true 

            SaveOriginalSkin()
            return 
        end
        
        local body = {104157277410075, 86280536086607, 81974054542977, 74524984742501, 122626731952977, 134082579}
        if Value then 
            Remotes.ChangeCharacterBody:InvokeServer(body) 
        else 
            LoadOriginalSkin() 
        end
    end
})

Tab:AddToggle({
    Name = "Giant Avatar",
    Default = false,
    Callback = function(Value)
        if not _G.togglesInitialized.Giant then 
            _G.togglesInitialized.Giant = true 

            SaveOriginalSkin()
            return 
        end
        
        local body = {17713016036, 17713016151, 17713015861, 17713021340, 17713016191, 6340213}
        if Value then 
            Remotes.ChangeCharacterBody:InvokeServer(body) 
        else 
            LoadOriginalSkin() 
        end
    end
})

Tab:AddSection({"Effects Avatar"})

local effectList = {
    {name = "Yellow Hearts", id = "18635672195", code = "001HeartsYellow"},
    {name = "Green Hearts", id = "18635727693", code = "002HeartsGreen"},
    {name = "Blue Hearts", id = "18635732186", code = "003HeartsBlue"},
    {name = "Purple Hearts", id = "18635723426", code = "004HeartsPurple"},
    {name = "Pink Hearts", id = "18635726250", code = "005HeartsPink"},
    {name = "Red Hearts", id = "18635729673", code = "006HeartsRed"},
    {name = "Orange Dots", id = "18637252424", code = "010DotsOrange"},
    {name = "Yellow Dots", id = "18637263004", code = "011DotsYellow"},
    {name = "Green Dots", id = "18637265264", code = "013DotsGreen"},
    {name = "Blue Dots", id = "18637256859", code = "014DotsBlue"},
    {name = "Purple Dots", id = "18637261058", code = "015DotsPurple"},
    {name = "Pink Dots", id = "18637259328", code = "016DotsPink"},
    {name = "Red Dots", id = "18637267290", code = "017DotsRed"},
    {name = "White Twinkle", id = "18637115654", code = "020TwinkleWhite"},
    {name = "Yellow Twinkle", id = "18637118923", code = "021TwinkleYellow"},
    {name = "Green Twinkle", id = "18637151114", code = "022TwinkleGreen"},
    {name = "Purple Twinkle", id = "18637153880", code = "023TwinklePurple"},
    {name = "Pink Twinkle", id = "18637157071", code = "024TwinklePink"},
    {name = "Red Twinkle", id = "18637155247", code = "025TwinkleRed"},
    {name = "White Fire", id = "18637074370", code = "030FireWhite"},
    {name = "Orange Fire", id = "18637025451", code = "031FireOrange"},
    {name = "Green Fire", id = "18637078598", code = "032FireGreen"},
    {name = "Blue Fire", id = "18637076370", code = "033FireBlue"},
    {name = "Purple Fire", id = "18637070174", code = "034FirePurple"},
    {name = "Black Fire", id = "18637072603", code = "035FireBlack"},
    {name = "Small Yellow Hearts", id = "18637339451", code = "040SmallHeartsYellow"},
    {name = "Small Green Hearts", id = "18637337576", code = "041SmallHeartsGreen"},
    {name = "Small Blue Hearts", id = "18637345162", code = "042SmallHeartsBlue"},
    {name = "Small Purple Hearts", id = "18637335865", code = "043SmallHeartsPurple"},
    {name = "Small Pink Hearts", id = "18637343416", code = "044SmallHeartsPink"},
    {name = "Small Red Hearts", id = "18637341847", code = "045SmallHeartsRed"},
    {name = "White Sparks", id = "18637383085", code = "050SparksWhite"},
    {name = "Green Sparks", id = "18637385236", code = "051SparksGreen"},
    {name = "Blue Sparks", id = "18637386856", code = "052SparksBlue"},
    {name = "Purple Sparks", id = "18637442447", code = "053SparksPurple"},
    {name = "Pink Sparks", id = "18637445897", code = "054SparksPink"},
    {name = "Red Sparks", id = "18637447550", code = "055SparksRed"},
    {name = "Green Bubbles", id = "18637493072", code = "061BubbleGreen"},
    {name = "Blue Bubbles", id = "18637499282", code = "062BubbleBlue"},
    {name = "Purple Bubbles", id = "18637497343", code = "063BubblePurple"},
    {name = "Red Bubbles", id = "18637500927", code = "064BubbleRed"},
    {name = "White Music", id = "18637675173", code = "070MusicWhite"},
    {name = "Green Music", id = "18637677789", code = "071MusicGreen"},
    {name = "Blue Music", id = "18637680960", code = "072MusicBlue"},
    {name = "Purple Music", id = "18637679384", code = "073MusicPurple"},
    {name = "Red Music", id = "18637672698", code = "074MusicRed"},
    {name = "White Smoke", id = "18637791748", code = "080SmokeWhite"},
    {name = "Yellow Smoke", id = "18637800482", code = "081SmokeYellow"},
    {name = "Orange Smoke", id = "18637793920", code = "082SmokeOrange"},
    {name = "Green Smoke", id = "18637789299", code = "083SmokeGreen"},
    {name = "Blue Smoke", id = "18637803021", code = "084SmokeBlue"},
    {name = "Purple Smoke", id = "18637813360", code = "085SmokePurple"},
    {name = "Red Smoke", id = "18637796598", code = "086SmokeRed"},
    {name = "Black Smoke", id = "18637798529", code = "087SmokeBlack"},
    {name = "White Star", id = "18637942956", code = "090StarWhite"},
    {name = "Orange Star", id = "18637946172", code = "091StarOrange"},
    {name = "Green Star", id = "18637934500", code = "092StarGreen"},
    {name = "Blue Star", id = "18637940338", code = "093StarBlue"},
    {name = "Purple Star", id = "18637944796", code = "094StarPurple"},
    {name = "Pink Star", id = "18637947820", code = "095StarPink"},
    {name = "Red Star", id = "18637949457", code = "096StarRed"}
}

local selectedEffect = effectList[1]

local dropdownOptions = {}
for _, effect in ipairs(effectList) do
    table.insert(dropdownOptions, effect.name)
end

local Dropdown = Tab:AddDropdown({
    Name = "Select Effect",
    Options = dropdownOptions,
    Default = effectList[1].name,
    Callback = function(option)
        for _, effect in ipairs(effectList) do
            if effect.name == option then
                selectedEffect = effect
                break
            end
        end
    end
})

Tab:AddButton({
    Name = "Equip Effect",
    Callback = function()
        game:GetService("ReplicatedStorage").Remotes.ApplyEmmiter:InvokeServer(selectedEffect.id, selectedEffect.code)
    end
})

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local ChangeCharacterBody = Remotes:WaitForChild("ChangeCharacterBody")
local SaveOutfit = Remotes:WaitForChild("SaveOutfit")
local LoadOutfit = Remotes:WaitForChild("LoadOutfit")

local SavedSkins = {}
local nextSlot = 100

local function LoadSavedSkins()
    local success, data = pcall(function()
        return readfile("CatholicHub_Skins.json")
    end)
    
    if success and data then
        pcall(function()
            SavedSkins = game:GetService("HttpService"):JSONDecode(data)
            local maxSlot = 99
            for slot, _ in pairs(SavedSkins) do
                if tonumber(slot) and tonumber(slot) > maxSlot then
                    maxSlot = tonumber(slot)
                end
            end
            nextSlot = maxSlot + 1
        end)
    end
end

local function SaveSkinsToFile()
    pcall(function()
        local json = game:GetService("HttpService"):JSONEncode(SavedSkins)
        writefile("CatholicHub_Skins.json", json)
    end)
end

LoadSavedSkins()


----------------------------------------------------------------------------------------------------------------------------------
                                                         -- Tab: Avatar & Tool FE --
----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Avatar & Tool FE", "person"})
local section = Tab:AddSection({"FE Avatars"})

local section = Tab:AddSection({"FE Tools"})
