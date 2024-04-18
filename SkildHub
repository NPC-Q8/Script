local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/laagginq/ui-libraries/main/shit-lib/src.lua"))()

--[[

my attempt on making a ui :skull:

features coming soon:
sliders
keybinds
color pickers
notification


sorry i rushed this in a few hours lol



]]

local win = lib:Create("Skild Hub","by NPC-Q8")
local a = win:tab("Main",false)
local b = win:tab("Scripts",false)

a:toggle("Auto ParryGod",false,function(v)getgenv().config = getgenv().config or {
    hit_time = 0.5, -- // recommended 0.25 to 0.75 \ --
 
    mode = 'Always', -- // Hold , Toggle , Always \ --
    deflect_type = 'Remote', -- // Key Press , Remote \ --
    notifications = true,
    keybind = Enum.KeyCode.V
}
 
loadstring(game:HttpGet("https://raw.githubusercontent.com/Hosvile/Refinement/main/MC%3ABlade%20Ball%20Parry%20V4.0.0",true))()
    print(v)   
end)

a:button("Auto Spam",function() local function get_plr()
  return game.Players.LocalPlayer
end

local function get_plrChar()
  local plrChar = get_plr().Character
  if plrChar then
    return plrChar
  end
end

local function get_plrRP()
  local plrRP = get_plrChar():FindFirstChild("HumanoidRootPart")
  if plrRP then
    return plrRP
  end
end

local function playerJump()
  pcall(function()
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
  end)
end

local function get_PlayersNumber()
  local Alive = workspace:WaitForChild("Alive", 20):GetChildren()
  local PlayersNumber = 0
  for _,v in pairs(Alive) do
    if v and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 50 then
      PlayersNumber = PlayersNumber + 1
    end
  end
  return PlayersNumber
end

local function get_ProxyPlayer()
  local Players = workspace:WaitForChild("Alive"):GetChildren()
  local Distance = math.huge
  local plr = game.Players.LocalPlayer
  local plrRP = plr.Character:FindFirstChild("HumanoidRootPart")
  local Player = nil
  
  for _,plr1 in pairs(Players) do
    if plr1.Name ~= plr.Name and plrRP and plr1:FindFirstChild("HumanoidRootPart") and plr1:FindFirstChild("Humanoid") and plr1.Humanoid.Health > 50 then
      local magnitude = (plr1.HumanoidRootPart.Position - plrRP.Position).Magnitude
      if magnitude <= Distance then
        Distance = magnitude
        Player = plr1
      end
    end
  end
  return Player
end

local function Click_Button()
  task.spawn(function()
    local plr = game.Players.LocalPlayer
    local plrFind = workspace.Alive:FindFirstChild(plr.Name)
    if plrFind then
      local plrs = 0
      for _,v in pairs(workspace:WaitForChild("Alive", 10):GetChildren()) do
        plrs = plrs + 1
      end
      if plrs > 1 then
        local args = {[1] = 1.5,[2] = CFrame.new(-254, 112, -119) * CFrame.Angles(-2, 0, 2),[3] = {
        ["2617721424"] = Vector3.new(-273, -724, -20),
        },[4] = {[1] = 910,[2] = 154}}
        game:GetService("ReplicatedStorage").Remotes.ParryAttempt:FireServer(unpack(args))task.wait()
      end
    end
  end)
end

task.spawn(function()
  while task.wait() do
    if getgenv().SpamClickA then
      Click_Button()
    end
  end
end)

local function DetectSpam()
  local Balls = workspace:WaitForChild("Balls", 20)
  
  local OldPos = Vector3.new()
  local OldTick1 = tick()
  
  local OldBall = Balls
  local TargetPlayer = ""
  local SpamNum = 0
  local BallSpeed = 0
  local BallDistance = 0
  
  task.spawn(function()
    local OldTick = tick()
    local OldPos = Vector3.new()
    while getgenv().DetectSpam do task.wait()
      local plrRP = get_plrRP()
      local Ball = Balls:FindFirstChildOfClass("Part")
      if plrRP and Ball then
        BallDistance = (plrRP.Position - Ball.Position).Magnitude
        BallSpeed = (OldPos - Ball.Position).Magnitude
        if tick() - OldTick >= 1/60 then
          OldTick = tick()
          OldPos = Ball.Position
        end
      end
    end
  end)
  
  while getgenv().DetectSpam do task.wait()
    local Ball = Balls:FindFirstChildOfClass("Part")
    local plrRP = get_plrRP()
    local ProxyPlayer = get_ProxyPlayer()
    
    if not Ball then
      getgenv().SpamClickA = false
    end
  
    if Ball and Ball:GetAttribute("realBall") and OldBall ~= Ball then
    
      Ball.Changed:Connect(function()task.wait()
        local Ball = Balls:FindFirstChildOfClass("Part")
        
        if Ball then
          TargetPlayer = Ball:GetAttribute("target")
          
          if ProxyPlayer and TargetPlayer == ProxyPlayer.Name or get_plr() and TargetPlayer == get_plr().Name then
            SpamNum = SpamNum + 1
          else
            SpamNum = 0
          end
          
          local args = ProxyPlayer and ProxyPlayer:FindFirstChild("HumanoidRootPart")
          local HL1 = ProxyPlayer and ProxyPlayer:FindFirstChild("Highlight")
          local HL2 = get_plrChar() and get_plrChar():FindFirstChild("Highlight")
          
          if plrRP and HL1 and args or plrRP and HL2 and args then
            local DistancePlayer = (ProxyPlayer.HumanoidRootPart.Position - plrRP.Position).Magnitude
            local DistanceBall = (Ball.Position - plrRP.Position).Magnitude
            
            if get_PlayersNumber() < 3 then
              if DistancePlayer <= 30 and DistanceBall <= 35 and SpamNum >= 2 then
                getgenv().SpamClickA = true
              else
                getgenv().SpamClickA = false
              end
            else
              if DistancePlayer <= 30 and DistanceBall <= 35 and SpamNum >= 3 then
                getgenv().SpamClickA = true
              else
                getgenv().SpamClickA = false
              end
            end
          else
            getgenv().SpamClickA = false
          end
        end
      end)
      OldBall = Ball
    end
  end
end

getgenv().DetectSpam = true
DetectSpam()
    print("Button Pressed")
end)
 

a:button("Auto Detect Spam",function() getgenv().AutoDetectSpam = true

--///////////////////////////////////////////////////////////////////--

local Alive = workspace:WaitForChild("Alive", 9e9)
local Players = game:GetService("Players")
local Player = Players.LocalPlayer

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Remotes = ReplicatedStorage:WaitForChild("Remotes", 9e9)
local ParryAttempt = Remotes:WaitForChild("ParryAttempt", 9e9)
local Balls = workspace:WaitForChild("Balls", 9e9)

--///////////////////////////////////////////////////////////////////--

local function get_ProxyPlayer()
  local Distance = math.huge
  local plrRP = Player.Character and Player.Character:FindFirstChild("HumanoidRootPart")
  local PlayerReturn = nil
  
  for _,plr1 in pairs(Alive:GetChildren()) do
    if plr1:FindFirstChild("Humanoid") and plr1.Humanoid.Health > 50 then
      if plr1.Name ~= Player.Name and plrRP and plr1:FindFirstChild("HumanoidRootPart") then
        local magnitude = (plr1.HumanoidRootPart.Position - plrRP.Position).Magnitude
        if magnitude <= Distance then
          Distance = magnitude
          PlayerReturn = plr1
        end
      end
    end
  end
  return PlayerReturn
end

local function SuperClick()
  task.spawn(function()
    if IsAlive() and #Alive:GetChildren() > 1 then
      local args1 = 0.5
      local args2 = CFrame.new()
      local args3 = {["enzo"] = Vector3.new()}
      local args4 = {500, 500}
      
      if args1 and args2 and args3 and args4 then
        ParryAttempt:FireServer(args1, args2, args3, args4)
      end
    end
  end)
end

task.spawn(function()
  while task.wait() do
    if getgenv().SpamClickA and getgenv().AutoDetectSpam then
      SuperClick()
    end
  end
end)

local ParryCounter = 0
local DetectSpamDistance = 0

local function GetBall(ball)
  local Target = ""
  
  ball:GetPropertyChangedSignal("Position"):Connect(function()
    local PlayerPP = Player and Player.Character and Player.Character.PrimaryPart
    local NearestPlayer = get_ProxyPlayer()
    
    if ball and PlayerPP and NearestPlayer and NearestPlayer.PrimaryPart then
      local PlayerDistance = (PlayerPP.Position - NearestPlayer.PrimaryPart.Position).Magnitude
      local BallDistance = (PlayerPP.Position - ball.Position).Magnitude
      
      DetectSpamDistance = 25 + math.clamp(ParryCounter / 3, 0, 25)
      
      if ParryCounter > 2 and PlayerDistance < DetectSpamDistance and BallDistance < 55 then
        getgenv().SpamClickA = true
      else
        getgenv().SpamClickA = false
      end
    end
  end)
  ball:GetAttributeChangedSignal("target"):Connect(function()
    Target = ball:GetAttribute("target")
    local NearestPlayer = get_ProxyPlayer()
    
    if NearestPlayer then
      if Target == NearestPlayer.Name or Target == Player.Name then
        ParryCounter = ParryCounter + 1
      else
        ParryCounter = 0
      end
    end
  end)
end

for _,ball in pairs(Balls:GetChildren()) do
  if ball and not ball:GetAttribute("realBall") then
    return
  end
  
  GetBall(ball)
end

Balls.ChildAdded:Connect(function(ball)
  if not getgenv().AutoDetectSpam then
    return
  elseif ball and not ball:GetAttribute("realBall") then
    return
  end
  
  getgenv().SpamClickA = false
  ParryCounter = 0
  GetBall(ball)
end)
    print("Button Pressed")
end)

a:button("Visualize Part",function() loadstring(game:HttpGet("https://raw.githubusercontent.com/tunthuhere/mthucuti/main/part"))()
    print("Button Pressed")
end)

a:button("Hold Block To Spam",function() getgenv().SpamSpeed = 1
loadstring(game:HttpGet("https://raw.githubusercontent.com/Hosvile/Refinement/main/MC%3ABlade%20Ball%20Spam",true))()
    print("Button Pressed")
end)

a:button("Manuel Spam ( Mobile&Pc)",function() loadstring(game:HttpGet("https://raw.githubusercontent.com/RaxorHUd/Manual-Spam/main/V2"))()
    print("Button Pressed")
end)

a:button("     Aim",function()
    print("Button Pressed")
end)

a:button("Aim Mechanism",function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Hosvile/Refinement/main/M%3ABlade%20Ball%20Mechanism",true))()
    print("Button Pressed")
end)

a:toggle("Auto Curve The Ball",false,function(v) --game:GetService("StarterGui"):SetCore("DevConsoleVisible",true)

warn("exed")

local UserInputService = game:GetService("UserInputService")

local Players = game:GetService("Players")
local Local = Players.LocalPlayer

local Camera = workspace.CurrentCamera

local script = Local.Character:WaitForChild("BaseUIS")

local Held, Tap = {}, nil
UserInputService.InputBegan:Connect(function(input)
	local start = os.clock()
	if input.UserInputType == Enum.UserInputType.Touch then
		table.insert(Held, input)
		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				local time = os.clock()-start
				if time <= 0.125 then
					Tap = input
				end
				table.remove(Held, table.find(Held, input))
			end
		end)
	end
end)

local old; old = hookmetamethod(game, "__namecall", function(self, ...)
	local args, method = {...}, getnamecallmethod()
	if method == "FireServer" and self.Name == "ParryAttempt" and Tap then
		local Hit = Tap
		--warn(unpack(args[4]))
		args[4][1] = math.floor(Hit.Position.X)
		args[4][2] = math.floor(Hit.Position.Y)
		--warn(unpack(args[4]))
		Tap = nil
	elseif method == "FireServer" and self.Name == "ParryAttempt" and not Tap then
		--warn("No Tap")
	end
	return old(self, unpack(args))
end)
    print(v)   
end)

a:button("Look at ball",function() sa = Value
    while sa do
    wait(.0)
    for _,ball in next, workspace.Balls:GetChildren() do
    game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position, ball.Position)
    end
  end
    print("Button Pressed")
end)

a:toggle("Auto Farm Coin&Win",false,function(v) getgenv().god = true
while getgenv().god and task.wait() do
    for _,ball in next, workspace.Balls:GetChildren() do
        if ball then
            if game:GetService("Players").LocalPlayer.Character and game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position, ball.Position)
                if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Highlight") then
                    game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = ball.CFrame * CFrame.new(0, 0, (ball.Velocity).Magnitude * -0.5)
                    game:GetService("ReplicatedStorage").Remotes.ParryButtonPress:Fire()
                end
            end
        end
    end
end
    print(v)
end)

b:button("Booster Anti Lag V1",function() local ToDisable = {
	Textures = true,
	VisualEffects = true,
	Parts = true,
	Particles = true,
	Sky = true
}

local ToEnable = {
	FullBright = false
}

local Stuff = {}

for _, v in next, game:GetDescendants() do
	if ToDisable.Parts then
		if v:IsA("Part") or v:IsA("Union") or v:IsA("BasePart") then
			v.Material = Enum.Material.SmoothPlastic
			table.insert(Stuff, 1, v)
		end
	end
	
	if ToDisable.Particles then
		if v:IsA("ParticleEmitter") or v:IsA("Smoke") or v:IsA("Explosion") or v:IsA("Sparkles") or v:IsA("Fire") then
			v.Enabled = false
			table.insert(Stuff, 1, v)
		end
	end
	
	if ToDisable.VisualEffects then
		if v:IsA("BloomEffect") or v:IsA("BlurEffect") or v:IsA("DepthOfFieldEffect") or v:IsA("SunRaysEffect") then
			v.Enabled = false
			table.insert(Stuff, 1, v)
		end
	end
	
	if ToDisable.Textures then
		if v:IsA("Decal") or v:IsA("Texture") then
			v.Texture = ""
			table.insert(Stuff, 1, v)
		end
	end
	
	if ToDisable.Sky then
		if v:IsA("Sky") then
			v.Parent = nil
			table.insert(Stuff, 1, v)
		end
	end
end

game:GetService("TestService"):Message("Effects Disabler Script : Successfully disabled "..#Stuff.." assets / effects. Settings :")

for i, v in next, ToDisable do
	print(tostring(i)..": "..tostring(v))
end

if ToEnable.FullBright then
    local Lighting = game:GetService("Lighting")
    
    Lighting.FogColor = Color3.fromRGB(255, 255, 255)
    Lighting.FogEnd = math.huge
    Lighting.FogStart = math.huge
    Lighting.Ambient = Color3.fromRGB(255, 255, 255)
    Lighting.Brightness = 5
    Lighting.ColorShift_Bottom = Color3.fromRGB(255, 255, 255)
    Lighting.ColorShift_Top = Color3.fromRGB(255, 255, 255)
    Lighting.OutdoorAmbient = Color3.fromRGB(255, 255, 255)
    Lighting.Outlines = true
end
	loadstring(game:HttpGet("https://pastebin.com/raw/pVSqS5fb"))()
    print("Button Pressed")
end)

b:button("Booster Anti Lag V2",function() _G.Settings = {
    Players = {
        ["Ignore Me"] = true, -- Ignore your Character
        ["Ignore Others"] = true -- Ignore other Characters
    },
    Meshes = {
        Destroy = false, -- Destroy Meshes
        LowDetail = true -- Low detail meshes
    },
    Images = {
        Invisible = true, -- Invisible Images
        LowDetail = false, -- Low detail images
        Destroy = false, -- Destroy Images
    },
    ["No Particles"] = true, -- Disables all ParticleEmitter, Trail, Smoke, Fire and Sparkles
    ["No Camera Effects"] = true, -- Disables all PostEffect's (Camera/Lighting Effects)
    ["No Explosions"] = true, -- Makes Explosion's invisible
    ["No Clothes"] = true, -- Removes Clothing from the game
    ["Low Water Graphics"] = true, -- Removes Water Quality
    ["No Shadows"] = true, -- Remove Shadows
    ["Low Rendering"] = true, -- Lower Rendering
    ["Low Quality Parts"] = true -- Lower quality parts
}
loadstring(game:HttpGet("https://angxlzz.dev/boostFps.lua"))()
    print("Button Pressed")
end)

b:button("Booster Anti Lag V3",function()_G.Settings = {
    Players = {
        ["Ignore Me"] = true, -- Ignore your Character
        ["Ignore Others"] = true-- Ignore other Characters
    },
    Meshes = {
        Destroy = false, -- Destroy Meshes
        LowDetail = true -- Low detail meshes (NOT SURE IT DOES ANYTHING)
    },
    Images = {
        Invisible = true, -- Invisible Images
        LowDetail = false, -- Low detail images (NOT SURE IT DOES ANYTHING)
        Destroy = false, -- Destroy Images
    },
    ["No Particles"] = true, -- Disables all ParticleEmitter, Trail, Smoke, Fire and Sparkles
    ["No Camera Effects"] = true, -- Disables all PostEffect's (Camera/Lighting Effects)
    ["No Explosions"] = true, -- Makes Explosion's invisible
    ["No Clothes"] = true, -- Removes Clothing from the game
    ["Low Water Graphics"] = true, -- Removes Water Quality
    ["No Shadows"] = true, -- Remove Shadows
    ["Low Rendering"] = true, -- Lower Rendering
    ["Low Quality Parts"] = true -- Lower quality parts
}
loadstring(game:HttpGet("https://raw.githubusercontent.com/CasperFlyModz/discord.gg-rips/main/FPSBooster.lua"))()
    print("Button Pressed")
end)

b:button("Booster Remove Effect",function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Hosvile/Refinement/main/Destroy%20Particle%20Emitters",true))()
    print("Button Pressed")
end)

b:button("Eps Player",function() local FillColor = Color3.fromRGB(1,1,1)
local DepthMode = "AlwaysOnTop"
local FillTransparency = 0.5
local OutlineColor = Color3.fromRGB(1,0,0)
local OutlineTransparency = 0

local CoreGui = game:FindService("CoreGui")
local Players = game:FindService("Players")
local lp = Players.LocalPlayer
local connections = {}

local Storage = Instance.new("Folder")
Storage.Parent = CoreGui
Storage.Name = "Highlight_Storage"

local function Highlight(plr)
    local Highlight = Instance.new("Highlight")
    Highlight.Name = plr.Name
    Highlight.FillColor = FillColor
    Highlight.DepthMode = DepthMode
    Highlight.FillTransparency = FillTransparency
    Highlight.OutlineColor = OutlineColor
    Highlight.OutlineTransparency = 0
    Highlight.Parent = Storage
    
    local plrchar = plr.Character
    if plrchar then
        Highlight.Adornee = plrchar
    end

    connections[plr] = plr.CharacterAdded:Connect(function(char)
        Highlight.Adornee = char
    end)
end

Players.PlayerAdded:Connect(Highlight)
for i,v in next, Players:GetPlayers() do
    Highlight(v)
end

Players.PlayerRemoving:Connect(function(plr)
    local plrname = plr.Name
    if Storage[plrname] then
        Storage[plrname]:Destroy()
    end
    if connections[plr] then
        connections[plr]:Disconnect()
    end
end)
    print("Button Pressed")
end)

b:button("Fps Name Player",function() 
local settings = {
    Color = Color3.fromRGB(0.0980392, 0.0980392, 0.0980392),
    Size = 8,
    Transparency = 1, -- 1 Visible - 0 Not Visible
    AutoScale = true
}

local space = game:GetService("Workspace")
local player = game:GetService("Players").LocalPlayer
local camera = space.CurrentCamera

local function NewText(color, size, transparency)
    local text = Drawing.new("Text")
    text.Visible = false
    text.Text = ""
    text.Position = Vector2.new(0, 0)
    text.Color = color
    text.Size = size
    text.Center = true
    text.Transparency = transparency
    return text
end

local function Visibility(state, lib)
    for u, x in pairs(lib) do
        x.Visible = state
    end
end

local function Size(size, lib)
    for u, x in pairs(lib) do
        x.Size = size
    end
end

for i, v in pairs(game:GetService("Players"):GetPlayers()) do
    local library = {
        name = NewText(settings.Color, settings.Size, settings.Transparency)
    }
    local function ESP()
        local connection
        connection = game:GetService("RunService").RenderStepped:Connect(function()
            if v.Character ~= nil and v.Character:FindFirstChild("Humanoid") ~= nil and v.Character:FindFirstChild("HumanoidRootPart") ~= nil and v.Name ~= player.Name and v.Character.Humanoid.Health > 0 then
                local HumanoidRootPart_Pos, OnScreen = camera:WorldToViewportPoint(v.Character.HumanoidRootPart.Position)
                if OnScreen then
                    library.name.Text = v.Name
                    library.name.Position = Vector2.new(HumanoidRootPart_Pos.X, HumanoidRootPart_Pos.Y)
                    --// AutoScale
                    if settings.AutoScale then
                        local distance = (Vector3.new(camera.CFrame.X, camera.CFrame.Y, camera.CFrame.Z) - v.Character.HumanoidRootPart.Position).magnitude
                        local textsize = math.clamp(1/distance*1000, 2, 30) -- 2 is min text size, 30 is max text size, change to your liking
                        Size(textsize, library)
                    else 
                        Size(settings.Size, library)
                    end
                    --//--
                    Visibility(true, library)
                else 
                    Visibility(false, library)
                end
            else 
                Visibility(false, library)
                if game.Players:FindFirstChild(v.Name) == nil then
                    connection:Disconnect()
                end
            end
        end)
    end
    coroutine.wrap(ESP)()
end

game.Players.PlayerAdded:Connect(function(newplr)
    print(newplr)
    local library = {
        name = NewText(settings.Color, settings.Size, settings.Transparency)
    }
    local function ESP()
        local connection
        connection = game:GetService("RunService").RenderStepped:Connect(function()
            if newplr.Character ~= nil and newplr.Character:FindFirstChild("Humanoid") ~= nil and newplr.Character:FindFirstChild("HumanoidRootPart") ~= nil and newplr.Name ~= player.Name and newplr.Character.Humanoid.Health > 0 then
                local HumanoidRootPart_Pos, OnScreen = camera:WorldToViewportPoint(newplr.Character.HumanoidRootPart.Position)
                if OnScreen then
                    library.name.Text = newplr.Name
                    library.name.Position = Vector2.new(HumanoidRootPart_Pos.X, HumanoidRootPart_Pos.Y)
                    --// AutoScale
                    if settings.AutoScale then
                        local distance = (Vector3.new(camera.CFrame.X, camera.CFrame.Y, camera.CFrame.Z) - newplr.Character.HumanoidRootPart.Position).magnitude
                        local textsize = math.clamp(1/distance*1000, 2, 30) -- 2 is min text size, 20 is max text size, change to your liking
                        Size(textsize, library)
                    else 
                        Size(settings.Size, library)
                    end
                    --//--
                    Visibility(true, library)
                else 
                    Visibility(false, library)
                end
            else 
                Visibility(false, library)
                if game.Players:FindFirstChild(newplr.Name) == nil then
                    connection:Disconnect()
                end
            end
        end)
    end
    coroutine.wrap(ESP)()
end)
    print("Button Pressed")
end)

b:button("Infinite Yield",function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source",true))()
    print("Button Pressed")
end)