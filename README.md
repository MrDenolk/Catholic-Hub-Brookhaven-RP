

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

----------------------------------------------------------------------------------------------------------------------------------
                                                         -- Tab: Avatar & Tool FE --
----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Avatar & Tool FE", "person"})
local section = Tab:AddSection({"FE Avatars"})

---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: House === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"House", "Home"})

local isUnbanActive = false
local SelectHouse = nil
local NoclipDoor = nil
local loopRunning = false

Tab:AddSection({"Remove Ban System"})

local function RemoveAllBannedBlocks()
    local count = 0
    for _, obj in ipairs(workspace:GetDescendants()) do
        if obj.Name == "BannedBlock" then
            obj:Destroy()
            count += 1
        end
    end
    return count
end

Tab:AddButton({
    Name = "Remove Ban",
    Description = " ",
    Callback = function()
        local removed = RemoveAllBannedBlocks()
        if removed > 0 then
            game.StarterGui:SetCore("SendNotification", {
                Title = "Remove Ban",
                Text = tostring(removed) .. " BannedBlock(s) removed",
                Duration = 4
            })
        else
            game.StarterGui:SetCore("SendNotification", {
                Title = "Remove Ban",
                Text = "No BannedBlock found.",
                Duration = 3
            })
        end
    end
})

Tab:AddToggle({
    Name = "Loop Remove Ban",
    Description = " ",
    Callback = function(Value)
        loopRunning = Value
        if Value then
            task.spawn(function()
                while loopRunning do
                    local removed = RemoveAllBannedBlocks()
                    if removed > 0 then
                        game.StarterGui:SetCore("SendNotification", {
                            Title = "Remove Ban",
                            Text = tostring(removed) .. " BannedBlock(s) removed",
                            Duration = 3
                        })
                    end
                    task.wait(1)
                end
            end)
        end
    end,
    Default = false,
    Flag = false
})

Tab:AddSection({"Simultaneous Functions for All Houses"})

local RunService = game:GetService("RunService")
local noclipDoor = false
local connection

local function setDoorCollision(state)
    for _, obj in ipairs(workspace:GetDescendants()) do
        if obj.Name == "001_HouseDoors" then
            if obj:IsA("BasePart") then
                obj.CanCollide = state
            elseif obj:IsA("Model") then
                for _, part in ipairs(obj:GetDescendants()) do
                    if part:IsA("BasePart") then
                        part.CanCollide = state
                    end
                end
            end
        end
    end
end

Tab:AddToggle({
    Name = "Noclip Door",
    Description = " ",
    Default = false,
    Callback = function(Value)
        noclipDoor = Value

        if Value then
            setDoorCollision(false)

            connection = RunService.Stepped:Connect(function()
                setDoorCollision(false)
            end)
        else
            if connection then
                connection:Disconnect()
                connection = nil
            end
            setDoorCollision(true)
        end
    end
})

---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: Utilities Player === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Utilities Player", "Paint"})
Tab:AddSection({"Esp System"})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local ESPEnabled = {
    Body = false,
    Name = false,
    Lines = false
}

local SelectedColor = Color3.fromRGB(255, 0, 0)
local RGBMode = false
local ESPObjects = {}
local FontSize = 30

local function clearESP()
    for _, v in pairs(ESPObjects) do
        for _, obj in pairs(v) do
            if obj.Destroy then
                obj:Destroy()
            elseif obj.Remove then
                obj:Remove()
            end
        end
    end
    ESPObjects = {}
end

local function createESP(player)
    if player == LocalPlayer then return end
    local character = player.Character
    if not character then return end

    ESPObjects[player] = {}
    
    if ESPEnabled.Body then
        local highlight = Instance.new("Highlight")
        highlight.FillColor = SelectedColor
        highlight.OutlineColor = SelectedColor
        highlight.FillTransparency = 0.7
        highlight.OutlineTransparency = 0
        highlight.Adornee = character
        highlight.Parent = character
        table.insert(ESPObjects[player], highlight)
    end
    
    if ESPEnabled.Name then
        local billboard = Instance.new("BillboardGui")
        billboard.Size = UDim2.new(0, 200, 0, 50)
        billboard.AlwaysOnTop = true
        billboard.Adornee = character:FindFirstChild("Head")
        billboard.Parent = character

        local label = Instance.new("TextLabel")
        label.Size = UDim2.new(1, 0, 1, 0)
        label.BackgroundTransparency = 1
        label.TextColor3 = SelectedColor
        label.TextStrokeTransparency = 0
        label.Font = Enum.Font.SourceSansBold
        label.TextScaled = false
        label.TextSize = FontSize
        label.Text = player.Name
        label.Parent = billboard

        RunService.RenderStepped:Connect(function()
            if character and character:FindFirstChild("HumanoidRootPart") and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                local dist = math.floor((character.HumanoidRootPart.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude)
                label.Text = player.Name .. " (" .. dist .. "m)"
                label.TextSize = FontSize
            end
        end)
        table.insert(ESPObjects[player], billboard)
    end
    
    if ESPEnabled.Lines then
        local line = Drawing.new("Line")
        line.Thickness = 2
        line.Transparency = 1
        line.Color = SelectedColor

        RunService.RenderStepped:Connect(function()
            if not character:FindFirstChild("HumanoidRootPart") or not LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                line.Visible = false
                return
            end

            local root = character.HumanoidRootPart
            local localRoot = LocalPlayer.Character.HumanoidRootPart
            local rootPos, onScreen1 = workspace.CurrentCamera:WorldToViewportPoint(root.Position)
            local localPos, onScreen2 = workspace.CurrentCamera:WorldToViewportPoint(localRoot.Position)

            if onScreen1 and onScreen2 then
                line.From = Vector2.new(localPos.X, localPos.Y)
                line.To = Vector2.new(rootPos.X, rootPos.Y)
                line.Color = SelectedColor
                line.Visible = true
            else
                line.Visible = false
            end
        end)
        table.insert(ESPObjects[player], line)
    end
end

local function updateAllESP()
    clearESP()
    for _, player in pairs(Players:GetPlayers()) do
        createESP(player)
    end
end

Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function()
        task.wait(1)
        updateAllESP()
    end)
end)

Players.PlayerRemoving:Connect(function(player)
    if ESPObjects[player] then
        for _, obj in pairs(ESPObjects[player]) do
            if obj.Destroy then
                obj:Destroy()
            elseif obj.Remove then
                obj:Remove()
            end
        end
        ESPObjects[player] = nil
    end
end)

task.spawn(function()
    while task.wait() do
        if RGBMode then
            local t = tick()
            local r = math.abs(math.sin(t * 2)) * 255
            local g = math.abs(math.sin(t * 2 + 2)) * 255
            local b = math.abs(math.sin(t * 2 + 4)) * 255
            SelectedColor = Color3.fromRGB(r, g, b)
            updateAllESP()
        end
    end
end)

local colorList = {
    ["Red"] = Color3.fromRGB(255, 0, 0),
    ["Green"] = Color3.fromRGB(0, 255, 0),
    ["Blue"] = Color3.fromRGB(0, 0, 255),
    ["Yellow"] = Color3.fromRGB(255, 255, 0),
    ["Purple"] = Color3.fromRGB(128, 0, 128),
    ["Cyan"] = Color3.fromRGB(0, 255, 255),
    ["White"] = Color3.fromRGB(255, 255, 255),
    ["Black"] = Color3.fromRGB(0, 0, 0),
    ["Orange"] = Color3.fromRGB(255, 140, 0),
    ["Pink"] = Color3.fromRGB(255, 0, 255),
    ["RGB"] = "RGB"
}

local colorNames = {}
for name in pairs(colorList) do
    table.insert(colorNames, name)
end

Tab:AddDropdown({
    Name = "ESP Color",
    Description = " ",
    Options = colorNames,
    Default = "Red",
    Callback = function(value)
        if colorList[value] == "RGB" then
            RGBMode = true
        else
            RGBMode = false
            SelectedColor = colorList[value]
            updateAllESP()
        end
    end
})

Tab:AddToggle({
    Name = "ESP Body",
    Description = " ",
    Default = false,
    Callback = function(Value)
        ESPEnabled.Body = Value
        updateAllESP()
    end
})

Tab:AddToggle({
    Name = "ESP Name and Distance",
    Description = " ",
    Default = false,
    Callback = function(Value)
        ESPEnabled.Name = Value
        updateAllESP()
    end
})

Tab:AddToggle({
    Name = "ESP Lines",
    Description = " ",
    Default = false,
    Callback = function(Value)
        ESPEnabled.Lines = Value
        updateAllESP()
    end
})

Tab:AddSlider({
    Name = "Tamanho do Texto ESP",
    Description = " ",
    Min = 1,
    Max = 100,
    Default = 30,
    Callback = function(value)
        FontSize = math.clamp(value, 1, 100)
        updateAllESP()
    end
})

---------------------------------------------------------------------------------------------------------------------------------
local Section = Tab:AddSection({"Name and Bio VIP Free"})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local rgbSpeed = 1

Tab:AddSlider({
    Name = "Speed RGB/Gradient",
    Description = "",
    Min = 1,
    Max = 5,
    Increment = 1,
    Default = 3,
    Callback = function(Value)
        rgbSpeed = Value
    end
})

local function getRainbowColor(speedMultiplier)
    local h = (tick() * speedMultiplier % 5) / 5
    return Color3.fromHSV(h, 1, 1)
end

local function fireServer(eventName, args)
    local event = game:GetService("ReplicatedStorage"):FindFirstChild("RE")
    if event and event:FindFirstChild(eventName) then
        pcall(function()
            event[eventName]:FireServer(unpack(args))
        end)
    end
end

local colorOptions = {
    "Red",
    "Green",
    "Blue",
    "Yellow",
    "Purple",
    "Orange",
    "Pink",
    "Cyan",
    "White",
    "Black"
}

local colorMap = {
    Red = Color3.fromRGB(255, 0, 0),
    Green = Color3.fromRGB(0, 255, 0),
    Blue = Color3.fromRGB(0, 0, 255),
    Yellow = Color3.fromRGB(255, 255, 0),
    Purple = Color3.fromRGB(128, 0, 128),
    Orange = Color3.fromRGB(255, 165, 0),
    Pink = Color3.fromRGB(255, 192, 203),
    Cyan = Color3.fromRGB(0, 255, 255),
    White = Color3.fromRGB(255, 255, 255),
    Black = Color3.fromRGB(0, 0, 0)
}

local selectedColor1 = "Red"
local selectedColor2 = "Blue"
local gradientActive = false
local gradientThread = nil

Tab:AddDropdown({
    Name = "First Color",
    Description = "",
    Default = "Red",
    Options = colorOptions,
    Callback = function(Value)
        selectedColor1 = Value
    end
})

Tab:AddDropdown({
    Name = "Second Color",
    Description = "",
    Default = "Blue",
    Options = colorOptions,
    Callback = function(Value)
        selectedColor2 = Value
    end
})


local function lerpColor(color1, color2, t)
    t = math.clamp(t, 0, 1)
    return Color3.new(
        color1.R + (color2.R - color1.R) * t,
        color1.G + (color2.G - color1.G) * t,
        color1.B + (color2.B - color1.B) * t
    )
end

Tab:AddToggle({
    Name = "Gradient Name/Bio",
    Default = false,
    Callback = function(state)
        gradientActive = state
        if gradientThread then
            task.cancel(gradientThread)
            gradientThread = nil
        end
        
        if state then
            gradientThread = task.spawn(function()
                while gradientActive and LocalPlayer and LocalPlayer.Character do
                    -- Obter as cores selecionadas
                    local color1 = colorMap[selectedColor1]
                    local color2 = colorMap[selectedColor2]
                    
                    -- Criar efeito de ida e volta
                    local time = tick() * rgbSpeed
                    local t = (math.sin(time) + 1) / 2  -- Varia de 0 a 1 e volta
                    
                    -- Interpolar entre as cores
                    local currentColor = lerpColor(color1, color2, t)
                    
                    -- Aplicar ao nome e bio
                    fireServer("1RPNam1eColo1r", { "PickingRPNameColor", currentColor })
                    fireServer("1RPNam1eColo1r", { "PickingRPBioColor", currentColor })
                    
                    task.wait(0.03)
                end
            end)
        end
    end
})

local nameBioRGBActive = false
local rainbowThread = nil

Tab:AddToggle({
    Name = "Name + Bio RGB",
    Default = false,
    Callback = function(state)
        nameBioRGBActive = state
        if rainbowThread then
            task.cancel(rainbowThread)
            rainbowThread = nil
        end
        
        if gradientThread then
            task.cancel(gradientThread)
            gradientThread = nil
        end
        
        if state then
            rainbowThread = task.spawn(function()
                while nameBioRGBActive and LocalPlayer.Character do
                    local color = getRainbowColor(rgbSpeed)
                    fireServer("1RPNam1eColo1r", { "PickingRPNameColor", color })
                    fireServer("1RPNam1eColo1r", { "PickingRPBioColor", color })
                    task.wait(0.03)
                end
            end)
        end
    end
})

---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: Car === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Car", "Car"})
local Section = Tab:AddSection({"Motor Controls (Car / Boat / Smaller Vehicles)"})

-- ===== VALUES =====
local speedValue = 200
local turboValue = 11.3
local defaultWalkSpeed = 16

-- ===== SERVICES =====
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- ===== UTILS =====
local function getCharacter()
    return LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
end

-- ===== HORSE CHECK =====
local function isHorse(model)
    if not model or not model:IsA("Model") then return false end

    -- nomes comuns de cavalo no Brookhaven
    local name = model.Name:lower()
    if name:find("horse") or name:find("cavalo") then
        return true
    end

    -- seat direto no modelo (igual bike/cavalo)
    if model:FindFirstChildWhichIsA("Seat", true)
        or model:FindFirstChildWhichIsA("VehicleSeat", true) then
        return true
    end

    return false
end

-- ===== CAR SPEED =====
local function applyCarSpeed(vehicle)
    local seat = vehicle:FindFirstChild("Seats")
        and vehicle.Seats:FindFirstChildWhichIsA("VehicleSeat")
    if not seat then return end

    pcall(function()
        seat.MaxSpeed = speedValue
    end)

    for _, v in pairs(seat:GetChildren()) do
        if v:IsA("NumberValue") then
            v.Value = speedValue
        end
    end
end

-- ===== HORSE SPEED =====
local function applyHorseSpeed(horse)
    local seat = horse:FindFirstChildWhichIsA("Seat", true)
        or horse:FindFirstChildWhichIsA("VehicleSeat", true)
    if not seat then return end

    pcall(function()
        seat.MaxSpeed = speedValue
    end)

    for _, v in pairs(seat:GetChildren()) do
        if v:IsA("NumberValue") then
            v.Value = speedValue
        end
    end

    if horse.PrimaryPart then
        horse.PrimaryPart.AssemblyLinearVelocity =
            horse.PrimaryPart.CFrame.LookVector * speedValue
    end
end

-- ===== CAR TURBO =====
local function applyCarTurbo(vehicle)
    local seat = vehicle:FindFirstChild("Seats")
        and vehicle.Seats:FindFirstChildWhichIsA("VehicleSeat")
    if not seat then return end

    for _, v in pairs(seat:GetChildren()) do
        if v:IsA("NumberValue") and v.Name:lower():find("turbo") then
            v.Value = turboValue
        end
    end
end

-- ===== BOAT SPEED =====
local function applyBoatSpeed(vehicle)
    local body = vehicle:FindFirstChild("Body")
    if not body then return end

    for _, obj in pairs(body:GetDescendants()) do
        if obj:IsA("NumberValue") then
            obj.Value = speedValue
        end
    end

    if vehicle.PrimaryPart then
        vehicle.PrimaryPart.AssemblyLinearVelocity =
            vehicle.PrimaryPart.CFrame.LookVector * speedValue
    end
end

-- ===== APPLY SPEED ALL VEHICLES =====
local function applySpeedAllVehicles()
    local folder = workspace:FindFirstChild("Vehicles")
    if not folder then return end

    for _, v in pairs(folder:GetChildren()) do
        if v:FindFirstChild("Seats") then
            applyCarSpeed(v)

        elseif v:FindFirstChild("Body") then
            applyBoatSpeed(v)

        elseif isHorse(v) then
            applyHorseSpeed(v)
        end
    end
end

-- ===== APPLY TURBO ALL CARS =====
local function applyTurboAllCars()
    local folder = workspace:FindFirstChild("Vehicles")
    if not folder then return end

    for _, v in pairs(folder:GetChildren()) do
        if v:FindFirstChild("Seats") then
            applyCarTurbo(v)
        end
    end
end

-- ===== PLAYER SPEED (BIKE / SKATE / PATINS) =====
local function applyPlayerSpeed()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = speedValue
    end
end

local function resetPlayerSpeed()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = defaultWalkSpeed
    end
end

-- ===== BOOST ATTACHED MODELS (HOVERBOARD ETC) =====
local function boostAttachedObjects()
    local char = getCharacter()
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return end

    for _, v in pairs(char:GetChildren()) do
        if v:IsA("Model") and v.PrimaryPart then
            v.PrimaryPart.AssemblyLinearVelocity =
                root.CFrame.LookVector * speedValue
        end
    end
end

-- ===== UI =====
Tab:AddTextBox({
    Name = "Speed",
    PlaceholderText = "200",
    Callback = function(v)
        local n = tonumber(v)
        if n then speedValue = n end
    end
})

Tab:AddTextBox({
    Name = "Turbo",
    PlaceholderText = "11.3",
    Callback = function(v)
        local n = tonumber(v)
        if n then turboValue = n end
    end
})

Tab:AddButton({
    Name = "Apply Speed (Car & Boat)",
    Callback = function()
        applySpeedAllVehicles()
    end
})

Tab:AddButton({
    Name = "Apply Turbo (Car / No Boat)",
    Callback = function()
        applyTurboAllCars()
    end
})

Tab:AddButton({
    Name = "Apply Speed (Smaller Vehicles)",
    Callback = function()
        applyPlayerSpeed()
    end
})



-- ===== AUTO RESET PLAYER SPEED =====

local RunService = game:GetService("RunService")

local usingSpeedItem = false

local function isUsingVehicleOrItem()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if not humanoid then return false end

    -- Se estiver sentado (carro, bike, etc)
    if humanoid.SeatPart then
        return true
    end

    -- Se tiver algum modelo preso ao personagem (hoverboard, skate)
    for _, v in pairs(char:GetChildren()) do
        if v:IsA("Model") and v.PrimaryPart then
            return true
        end
    end

    return false
end

-- Loop leve e seguro
RunService.Heartbeat:Connect(function()
    local char = LocalPlayer.Character
    if not char then return end

    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if not humanoid then return end

    local usingNow = isUsingVehicleOrItem()

    -- Começou a usar algo
    if usingNow then
        usingSpeedItem = true

    -- Parou de usar → reseta automaticamente
    elseif usingSpeedItem then
        humanoid.WalkSpeed = defaultWalkSpeed
        usingSpeedItem = false
    end
end)



-- ===== ANTI IMPULSO (BIKE / HORSE / ITEMS) =====

local RunService = game:GetService("RunService")
local wasUsing = false

RunService.Heartbeat:Connect(function()
    local char = LocalPlayer.Character
    if not char then return end

    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    local root = char:FindFirstChild("HumanoidRootPart")
    if not humanoid or not root then return end

    local usingNow = humanoid.SeatPart ~= nil

    if wasUsing and not usingNow then
        humanoid.WalkSpeed = defaultWalkSpeed
        root.AssemblyLinearVelocity = Vector3.zero
        root.AssemblyAngularVelocity = Vector3.zero
    end

    wasUsing = usingNow
end)


local Section = Tab:AddSection({"Spawn Car ( Metheds Kill & Fling )"})

Tab:AddButton({
    Name = "Spawn Bus",
    Description = " ", -- Optional
    Callback = function ()
     local args = {
	"PickingCar",
	"SchoolBus"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Ca1r"):FireServer(unpack(args))

   print("Button Clicked")
    end
})


Tab:AddButton({
    Name = "Spawn tow truck ( For Fling )",
    Description = " ", -- Optional
    Callback = function ()
        local args = {
	"PickingCar",
	"TowTruck"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Ca1r"):FireServer(unpack(args))

print("Button Clicked")
    end
})


Tab:AddButton({
    Name = "Spawn truck Car Semi",
    Description = " ", -- Optional
    Callback = function ()
    local args = {
	"PickingCar",
	"Semi"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Ca1r"):FireServer(unpack(args))

    print("Button Clicked")
    end
})


local Section = Tab:AddSection({"All Car Functions"})

shared.g = shared.g or {}
shared.g.Players = game:GetService("Players")
shared.g.Workspace = game:GetService("Workspace")
shared.g.LocalPlayer = shared.g.Players.LocalPlayer
shared.g.Camera = shared.g.Workspace.CurrentCamera

local VehicleHub = {}
VehicleHub.Players = shared.g.Players
VehicleHub.Workspace = shared.g.Workspace
VehicleHub.LocalPlayer = shared.g.LocalPlayer
VehicleHub.Camera = shared.g.Camera

function VehicleHub:ShowNotification(message)
end

function VehicleHub:ToggleFallDamage(disable)
    if not self.LocalPlayer.Character or not self.LocalPlayer.Character:FindFirstChild("Humanoid") then return false end
    local humanoid = self.LocalPlayer.Character.Humanoid
    if disable then
        humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, false)
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, false)
        humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp, true)
        humanoid.PlatformStand = false
        return true
    else
        humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, true)
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, true)
        return false
    end
end

function VehicleHub:TeleportToSeat(seat, car)
    if not self.LocalPlayer.Character or not self.LocalPlayer.Character:FindFirstChild("Humanoid") then
        self:ShowNotification("Character not found!")
        return false
    end
    local humanoid = self.LocalPlayer.Character.Humanoid
    local rootPart = self.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
    if not rootPart then
        self:ShowNotification("Character root part not found!")
        return false
    end

    humanoid.Sit = false
    task.wait(0.1)

    rootPart.CFrame = seat.CFrame + Vector3.new(0, 5, 0)
    task.wait(0.1)

    seat:Sit(humanoid)
    task.wait(0.5)
    return humanoid.SeatPart == seat
end

function VehicleHub:TeleportToVoid(car)
    if not car then
        self:ShowNotification("Invalid vehicle!")
        return
    end
    if not car.PrimaryPart then
        local body = car:FindFirstChild("Body", true) or car:FindFirstChild("Chassis", true)
        if body and body:IsA("BasePart") then
            car.PrimaryPart = body
        else
            self:ShowNotification("Vehicle primary part not found!")
            return
        end
    end
    local voidPosition = Vector3.new(0, -1000, 0)
    car:SetPrimaryPartCFrame(CFrame.new(voidPosition))
    task.wait(0.5)
end

function VehicleHub:TeleportToPlayer(car, playerPos)
    if not car then
        self:ShowNotification("Invalid vehicle!")
        return
    end
    if not car.PrimaryPart then
        local body = car:FindFirstChild("Body", true) or car:FindFirstChild("Chassis", true)
        if body and body:IsA("BasePart") then
            car.PrimaryPart = body
        else
            self:ShowNotification("Vehicle primary part not found!")
            return
        end
    end
    local targetPos = playerPos + Vector3.new(5, 0, 5)
    car:SetPrimaryPartCFrame(CFrame.new(targetPos))
    task.wait(0.5)
end

function VehicleHub:ExitCarAndReturn(originalPos)
    if not self.LocalPlayer.Character or not self.LocalPlayer.Character:FindFirstChild("Humanoid") then return end
    local humanoid = self.LocalPlayer.Character.Humanoid
    if humanoid.SeatPart then
        humanoid.Sit = false
    end
    task.wait(0.1)
    if originalPos then
        self.LocalPlayer.Character:PivotTo(CFrame.new(originalPos))
    end
end

function VehicleHub:UpdateVehicleList()
    local vehiclesFolder = self.Workspace:FindFirstChild("Vehicles")
    local carList = {}
    
    if vehiclesFolder then
        for _, car in ipairs(vehiclesFolder:GetChildren()) do
            if car.Name:match("Car$") then
                table.insert(carList, car.Name)
            end
        end
    end
    
    return carList
end

Tab:AddToggle({
    Name = "Kill All Server Cars",
    Description = " ",
    Default = false,
    Callback = function(state)
        local originalPosition
        local teleportActive = state
        local fallDamageDisabled = false

        if state then
            if VehicleHub.LocalPlayer.Character and VehicleHub.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                originalPosition = VehicleHub.LocalPlayer.Character.HumanoidRootPart.Position
            else
                VehicleHub:ShowNotification("Character not found!")
                return
            end

            fallDamageDisabled = VehicleHub:ToggleFallDamage(true)

            spawn(function()
                local vehiclesFolder = VehicleHub.Workspace:FindFirstChild("Vehicles")
                if not vehiclesFolder then
                    VehicleHub:ShowNotification("Vehicles folder not found!")
                    return
                end

                local cars = {}
                for _, car in ipairs(vehiclesFolder:GetChildren()) do
                    if car.Name:match("Car$") then
                        table.insert(cars, car)
                    end
                end

                for _, car in ipairs(cars) do
                    if not teleportActive then break end

                    local vehicleSeat = car:FindFirstChildWhichIsA("VehicleSeat", true)
                    if vehicleSeat and vehicleSeat.Occupant == nil then
                        local success = VehicleHub:TeleportToSeat(vehicleSeat, car)
                        if success then
                            VehicleHub:TeleportToVoid(car)
                            VehicleHub:ExitCarAndReturn(originalPosition)
                            task.wait(1)
                        end
                    end
                end

                if teleportActive then
                    teleportActive = false
                    VehicleHub:ToggleFallDamage(false)
                end
            end)
        else
            teleportActive = false
            VehicleHub:ToggleFallDamage(false)
        end
    end
})

local Section = Tab:AddSection({"Car Functions"})

local Dropdown = Tab:AddDropdown({
    Name = "Select Player Car",
    Description = " ",
    Default = nil,
    Options = VehicleHub:UpdateVehicleList(),
    Callback = function(selectedCar)
        _G.SelectedVehicle = selectedCar
    end
})

Tab:AddToggle({
    Name = "View Selected Car Camera",
    Description = " ",
    Default = false,
    Callback = function(state)
        if state then
            if not _G.SelectedVehicle or _G.SelectedVehicle == "" then
                VehicleHub:ShowNotification("No car selected!")
                return
            end

            local vehiclesFolder = VehicleHub.Workspace:FindFirstChild("Vehicles")
            if not vehiclesFolder then
                VehicleHub:ShowNotification("Vehicles folder not found!")
                return
            end

            local vehicle = vehiclesFolder:FindFirstChild(_G.SelectedVehicle)
            if not vehicle then
                VehicleHub:ShowNotification("Selected car not found!")
                return
            end

            local vehicleSeat = vehicle:FindFirstChildWhichIsA("VehicleSeat", true)
            if not vehicleSeat then
                VehicleHub:ShowNotification("Car seat not found!")
                return
            end

            VehicleHub.OriginalCameraSubject = VehicleHub.Camera.CameraSubject
            VehicleHub.OriginalCameraType = VehicleHub.Camera.CameraType

            VehicleHub.Camera.CameraSubject = vehicleSeat
            VehicleHub.Camera.CameraType = Enum.CameraType.Follow
            VehicleHub:ShowNotification("Camera set to " .. _G.SelectedVehicle .. "!")
        else
            if VehicleHub.OriginalCameraSubject then
                VehicleHub.Camera.CameraSubject = VehicleHub.OriginalCameraSubject
                VehicleHub.Camera.CameraType = VehicleHub.OriginalCameraType or Enum.CameraType.Custom
                VehicleHub:ShowNotification("Camera restored!")
                VehicleHub.OriginalCameraSubject = nil
                VehicleHub.OriginalCameraType = nil
            end
        end
    end
})

VehicleHub.Workspace:WaitForChild("Vehicles").ChildAdded:Connect(function()
    Dropdown:Set(VehicleHub:UpdateVehicleList())
end)
VehicleHub.Workspace:WaitForChild("Vehicles").ChildRemoved:Connect(function()
    Dropdown:Set(VehicleHub:UpdateVehicleList())
end)

local Section = Tab:AddSection({"Kill and Bring Functions"})

Tab:AddButton({
    Name = "Destroy Selected Car",
    Description = " ",
    Callback = function()
        if not _G.SelectedVehicle or _G.SelectedVehicle == "" then
            VehicleHub:ShowNotification("No car selected!")
            return
        end

        local vehiclesFolder = VehicleHub.Workspace:FindFirstChild("Vehicles")
        if not vehiclesFolder then
            VehicleHub:ShowNotification("Vehicles folder not found!")
            return
        end

        local vehicle = vehiclesFolder:FindFirstChild(_G.SelectedVehicle)
        if not vehicle then
            VehicleHub:ShowNotification("Selected car not found!")
            return
        end

        local vehicleSeat = vehicle:FindFirstChildWhichIsA("VehicleSeat", true)
        if not vehicleSeat then
            VehicleHub:ShowNotification("Car seat not found!")
            return
        end

        if vehicleSeat.Occupant then
            VehicleHub:ShowNotification("Cannot kill car, someone is in the driver seat!")
            return
        end

        local originalPos
        if VehicleHub.LocalPlayer.Character and VehicleHub.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            originalPos = VehicleHub.LocalPlayer.Character.HumanoidRootPart.Position
        else
            VehicleHub:ShowNotification("Player character not found!")
            return
        end

        VehicleHub:ToggleFallDamage(true)
        local success = VehicleHub:TeleportToSeat(vehicleSeat, vehicle)
        if success then
            VehicleHub:TeleportToVoid(vehicle)
            VehicleHub:ShowNotification("Car " .. _G.SelectedVehicle .. " teleported to void!")
            VehicleHub:ExitCarAndReturn(originalPos)
        else
            VehicleHub:ShowNotification("Failed to sit in car!")
        end
        VehicleHub:ToggleFallDamage(false)
    end
})

Tab:AddButton({
    Name = "Bring Selected Car",
    Description = " ",
    Callback = function()
        if not _G.SelectedVehicle or _G.SelectedVehicle == "" then
            VehicleHub:ShowNotification("No car selected!")
            return
        end

        local vehiclesFolder = VehicleHub.Workspace:FindFirstChild("Vehicles")
        if not vehiclesFolder then
            VehicleHub:ShowNotification("Vehicles folder not found!")
            return
        end

        local vehicle = vehiclesFolder:FindFirstChild(_G.SelectedVehicle)
        if not vehicle then
            VehicleHub:ShowNotification("Selected car not found!")
            return
        end

        local vehicleSeat = vehicle:FindFirstChildWhichIsA("VehicleSeat", true)
        if not vehicleSeat then
            VehicleHub:ShowNotification("Car seat not found!")
            return
        end

        if vehicleSeat.Occupant then
            VehicleHub:ShowNotification("Cannot teleport car, someone is in the driver seat!")
            return
        end

        local originalPos
        if VehicleHub.LocalPlayer.Character and VehicleHub.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            originalPos = VehicleHub.LocalPlayer.Character.HumanoidRootPart.Position
        else
            VehicleHub:ShowNotification("Player character not found!")
            return
        end

        VehicleHub:ToggleFallDamage(true)
        local success = VehicleHub:TeleportToSeat(vehicleSeat, vehicle)
        if success then
            VehicleHub:TeleportToPlayer(vehicle, originalPos)
            VehicleHub:ShowNotification("Car " .. _G.SelectedVehicle .. " teleported to you!")
            VehicleHub:ExitCarAndReturn(originalPos)
        else
            VehicleHub:ShowNotification("Failed to sit in car!")
        end
        VehicleHub:ToggleFallDamage(false)
    end
})

Tab:AddButton({
    Name = "Bring All Cars",
    Description = " ",
    Callback = function()
        local originalPos
        if VehicleHub.LocalPlayer.Character and VehicleHub.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            originalPos = VehicleHub.LocalPlayer.Character.HumanoidRootPart.Position
        else
            VehicleHub:ShowNotification("Player character not found!")
            return
        end

        local vehiclesFolder = VehicleHub.Workspace:FindFirstChild("Vehicles")
        if not vehiclesFolder then
            VehicleHub:ShowNotification("Vehicles folder not found!")
            return
        end

        VehicleHub:ToggleFallDamage(true)
        local cars = {}
        for _, car in ipairs(vehiclesFolder:GetChildren()) do
            if car.Name:match("Car$") then
                table.insert(cars, car)
            end
        end

        for _, car in ipairs(cars) do
            local vehicleSeat = car:FindFirstChildWhichIsA("VehicleSeat", true)
            if vehicleSeat and vehicleSeat.Occupant == nil then
                local success = VehicleHub:TeleportToSeat(vehicleSeat, car)
                if success then
                    VehicleHub:TeleportToPlayer(car, originalPos)
                    VehicleHub:ExitCarAndReturn(originalPos)
                    VehicleHub:ShowNotification("Car " .. car.Name .. " teleported to you!")
                    task.wait(1)
                end
            end
        end

        VehicleHub:ToggleFallDamage(false)
        if #cars == 0 then
            VehicleHub:ShowNotification("No cars available to teleport!")
        end
    end
})

local fallDamageDisabled = false
VehicleHub.LocalPlayer.CharacterAdded:Connect(function(character)
    local humanoid = character:WaitForChild("Humanoid")
    if fallDamageDisabled then
        humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, false)
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, false)
        humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp, true)
        humanoid.PlatformStand = false
    else
        humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, true)
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, true)
    end
end)
