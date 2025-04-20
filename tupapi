
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("ilvudolly", "DarkTheme")

local player = game.Players.LocalPlayer
local dropdown = {}

-- Función para obtener la lista de jugadores
function GetList()
	dropdown = {}
	for _, v in pairs(game.Players:GetPlayers()) do
		table.insert(dropdown, v.Name)
	end
end

-- Target Menu
local TargetTab = Window:NewTab(" LoopMenu")
local TargetSection = TargetTab:NewSection(" Menu")
local KTab = Window:NewTab("Anti afk");
local KSection = KTab:NewSection("anti afk");




GetList() -- Cargar jugadores antes de crear el menú

local slcplr = TargetSection:NewDropdown("Select Player", "", dropdown, function(currentOption)
	_G.tplayer = currentOption
end)

TargetSection:NewButton("Refresh Dropdown", "", function()
	GetList()
	slcplr:Refresh(dropdown)
end)

TargetSection:NewButton("Teleport To Player", "", function()
	local p1 = player.Character.HumanoidRootPart
	p1.CFrame = game.Players[_G.tplayer].Character.HumanoidRootPart.CFrame
end)

TargetSection:NewToggle("Spectate Player", "", function(state)
	if state then
		getgenv().watch = true
		while watch do
			local viewing = game.Players[_G.tplayer]
			workspace.CurrentCamera.CameraSubject = viewing.Character
			wait()
		end
	else
		getgenv().watch = false
		workspace.CurrentCamera.CameraSubject = player.Character
	end
end)

TargetSection:NewToggle("Kill Player", "", function(state)
	if state then
		getgenv().killplr = true
		spawn(function()
			while killplr do
				wait(0.1)
				pcall(function()
					local target = game.Players[_G.tplayer]
					if target and target.Character and target.Character:FindFirstChild("HumanoidRootPart") then
						player.Character.HumanoidRootPart.CFrame = target.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 1)
					end
				end)
				for i = 1, 5 do
					game:GetService("ReplicatedStorage").Events.Punch:FireServer(0, 0.1, 1)
				end
			end
		end)
	else
		getgenv().killplr = false
	end
end)

TargetSection:NewToggle("Loop To Player", "", function(state)
	if state then
		getgenv().loopgoto = true
		spawn(function()
			while loopgoto do
				pcall(function()
					local target = game.Players[_G.tplayer]
					if target and target.Character and target.Character:FindFirstChild("HumanoidRootPart") then
						player.Character.HumanoidRootPart.CFrame = target.Character.HumanoidRootPart.CFrame
					end
				end)
				wait(0.1)
			end
		end)
	else
		getgenv().loopgoto = false
	end
end)

TargetSection:NewToggle("Laser", "", function(state)
	if state then
		getgenv().LaserL = true
		local event = game:GetService("ReplicatedStorage").Events.ToggleLaserVision
		local part = event:InvokeServer(true)
		while LaserL and part and _G.tplayer do
			wait()
			local target = game.Players:FindFirstChild(_G.tplayer)
			if target and target.Character and target.Character:FindFirstChild("HumanoidRootPart") then
				part.Position = target.Character.HumanoidRootPart.Position
			end
		end
		event:InvokeServer(false)
	else
		getgenv().LaserL = false
	end
end)

-- Self Menu
local STab = Window:NewTab("Rapid Menu")
local SSection = STab:NewSection("Menu")

SSection:NewToggle("Spawn Point", "", function(state)
	if state then
		getgenv().Deathcheck = true
		local varX = player.Character.UpperTorso.Position.X
		local varY = player.Character.UpperTorso.Position.Y
		local varZ = player.Character.UpperTorso.Position.Z
		spawn(function()
			while Deathcheck do
				if player.Character.Humanoid.Health == 0 then
					wait(6.5)
					player.Character.HumanoidRootPart.CFrame = CFrame.new(varX, varY, varZ)
				end
				wait(1)
			end
		end)
	else
		getgenv().Deathcheck = false
	end
end)

SSection:NewToggle("Rapid Punch", "", function(state)
	if state then
		getgenv().rapid = true
		game:GetService("UserInputService").InputEnded:Connect(function(input, processed)
			if not processed and input.UserInputType == Enum.UserInputType.MouseButton1 and rapid then
				for i = 1, 10 do
					game:GetService("ReplicatedStorage").Events.Punch:FireServer(0, 0.1, 1)
				end
			end
		end)
	else
		getgenv().rapid = false
	end
end)

SSection:NewToggle("Super Rapid Punch", "", function(state)
	if state then
		getgenv().superrapid = true
		game:GetService("UserInputService").InputEnded:Connect(function(input, processed)
			if not processed and input.UserInputType == Enum.UserInputType.MouseButton1 and superrapid then
				for i = 1, 50 do
					game:GetService("ReplicatedStorage").Events.Punch:FireServer(0, 0.1, 1)
				end
			end
		end)
	else
		getgenv().superrapid = false
	end
end)

SSection:NewToggle("Super Heavy Rapid Punch", "", function(state)
	if state then
		getgenv().superhrapid = true
		game:GetService("UserInputService").InputEnded:Connect(function(input, processed)
			if not processed and input.UserInputType == Enum.UserInputType.MouseButton1 and superhrapid then
				for i = 1, 50 do
					game:GetService("ReplicatedStorage").Events.Punch:FireServer(0.4, 0.01, 1)
				end
			end
		end)
	else
		getgenv().superhrapid = false
	end
end)

KSection:NewButton("Enable Anti-AFK", "Activa anti-afk con GUI", function()
	local vu = game:GetService("VirtualUser")
	game:GetService("Players").LocalPlayer.Idled:Connect(function()
		vu:Button2Down(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
		wait(1)
		vu:Button2Up(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
	end)

	local ScreenGui = Instance.new("ScreenGui")
	local Frame = Instance.new("Frame")
	local Title = Instance.new("TextLabel")
	local Subtitle = Instance.new("TextLabel")
	local Signature = Instance.new("TextLabel")

	ScreenGui.Name = "AntiAFK_GUI"
	ScreenGui.ResetOnSpawn = false
	ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

	Frame.Parent = ScreenGui
	Frame.BackgroundColor3 = Color3.new(0, 0, 0)
	Frame.Size = UDim2.new(0, 250, 0, 120)
	Frame.Position = UDim2.new(0.5, -125, 0.4, 0)
	Frame.BorderSizePixel = 0
	Frame.Active = true
	Frame.Draggable = true -- <- Esto permite moverlo

	Title.Name = "Title"
	Title.Parent = Frame
	Title.BackgroundTransparency = 1
	Title.Position = UDim2.new(0, 0, 0, 10)
	Title.Size = UDim2.new(1, 0, 0, 30)
	Title.Font = Enum.Font.GothamBold
	Title.Text = "Anti Afk"
	Title.TextColor3 = Color3.fromRGB(255, 0, 0)
	Title.TextScaled = true

	Subtitle.Name = "Subtitle"
	Subtitle.Parent = Frame
	Subtitle.BackgroundTransparency = 1
	Subtitle.Position = UDim2.new(0, 0, 0, 45)
	Subtitle.Size = UDim2.new(1, 0, 0, 25)
	Subtitle.Font = Enum.Font.Gotham
	Subtitle.Text = "Activate"
	Subtitle.TextColor3 = Color3.fromRGB(255, 0, 0)
	Subtitle.TextScaled = true

	Signature.Name = "Signature"
	Signature.Parent = Frame
	Signature.BackgroundTransparency = 1
	Signature.Position = UDim2.new(0, 0, 0, 75)
	Signature.Size = UDim2.new(1, 0, 0, 20)
	Signature.Font = Enum.Font.Gotham
	Signature.Text = "by ilvudolly"
	Signature.TextColor3 = Color3.fromRGB(255, 0, 0)
	Signature.TextScaled = true
end)
