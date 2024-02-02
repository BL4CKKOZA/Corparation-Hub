if game.PlaceId == 142823291 then

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "Corparaiton Scripts",
   LoadingTitle = "LuaX Hub",
   LoadingSubtitle = "by BL4CKKOZA",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Bypassed Anti-cheat Lol"
   },
   Discord = {
      Enabled = false,
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },
   KeySystem = true, -- Set this to true to use our key system
   KeySettings = {
      Title = "Corparation Keys",
      Subtitle = "https://link-hub.net/1108235/corparation-key-scrpt",
      Note = "Copy this",
      FileName = "key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = false, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"https://pastebin.com/raw/MX1EaDAB"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})

local MainTab = Window:CreateTab("Main", nil) -- Title, Image

local Toggle = MainTab:CreateToggle({
   Name = "Auto farm coins",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        local WaitTime = 0.15
local MaxCoins = 50
 
local function OnNewRound(CoinContainer)
    local Character = game.Players.LocalPlayer.Character
    local Coins = 0
    while Coins < MaxCoins and CoinContainer.Parent do
        for i, Coin in pairs (CoinContainer:GetChildren()) do
            if Coin.Name == "Coin_Server" then
                Character.PrimaryPart.CFrame = CFrame.new(Coin.Position)
                wait(WaitTime)
        Coins = Coins + 1
            end
        end
    wait()
    end
end


 
game.Workspace.DescendantAdded:Connect(function(Instance)
    if Instance.Name == "CoinContainer" then
        OnNewRound(Instance)
    end
end)
 
local CoinContainer = game.Workspace:FindFirstChild("CoinContainer", true)
if CoinContainer then
    OnNewRound(CoinContainer)
end

   end,
})

local Button = MainTab:CreateButton({
   Name = "Grab Gun",
   Callback = function()
        if game:GetService("RunService"):IsClient() then error("Script must be server-side in order to work; use h/ and not hl/") end
local Player,game,owner = owner,game
local RealPlayer = Player
do
    print("FE Compatibility code by Mokiros")
    script.Parent = Player.Character
 
    --RemoteEvent for communicating
    local Event = Instance.new("RemoteEvent")
    Event.Name = "UserInput_Event"
 
    --Fake event to make stuff like Mouse.KeyDown work
    local function fakeEvent()
        local t = {_fakeEvent=true,Connect=function(self,f)self.Function=f end}
        t.connect = t.Connect
        return t
    end
 
    --Creating fake input objects with fake variables
    local m = {Target=nil,Hit=CFrame.new(),KeyUp=fakeEvent(),KeyDown=fakeEvent(),Button1Up=fakeEvent(),Button1Down=fakeEvent()}
    local UIS = {InputBegan=fakeEvent(),InputEnded=fakeEvent()}
    local CAS = {Actions={},BindAction=function(self,name,fun,touch,...)
        CAS.Actions[name] = fun and {Name=name,Function=fun,Keys={...}} or nil
    end}
    --Merged 2 functions into one by checking amount of arguments
    CAS.UnbindAction = CAS.BindAction
 
    --This function will trigger the events that have been :Connect()'ed
    local function te(self,ev,...)
        local t = m[ev]
        if t and t._fakeEvent and t.Function then
            t.Function(...)
        end
    end
    m.TrigEvent = te
    UIS.TrigEvent = te
 
    Event.OnServerEvent:Connect(function(plr,io)
        if plr~=Player then return end
        m.Target = io.Target
        m.Hit = io.Hit
        if not io.isMouse then
            local b = io.UserInputState == Enum.UserInputState.Begin
            if io.UserInputType == Enum.UserInputType.MouseButton1 then
                return m:TrigEvent(b and "Button1Down" or "Button1Up")
            end
            for _,t in pairs(CAS.Actions) do
                for _,k in pairs(t.Keys) do
                    if k==io.KeyCode then
                        t.Function(t.Name,io.UserInputState,io)
                    end
                end
            end
            m:TrigEvent(b and "KeyDown" or "KeyUp",io.KeyCode.Name:lower())
            UIS:TrigEvent(b and "InputBegan" or "InputEnded",io,false)
        end
    end)
    Event.Parent = NLS([==[
    local Player = game:GetService("Players").LocalPlayer
    local Event = script:WaitForChild("UserInput_Event")
 
    local Mouse = Player:GetMouse()
    local UIS = game:GetService("UserInputService")
    local input = function(io,a)
        if a then return end
        --Since InputObject is a client-side instance, we create and pass table instead
        Event:FireServer({KeyCode=io.KeyCode,UserInputType=io.UserInputType,UserInputState=io.UserInputState,Hit=Mouse.Hit,Target=Mouse.Target})
    end
    UIS.InputBegan:Connect(input)
    UIS.InputEnded:Connect(input)
 
    local h,t
    --Give the server mouse data 30 times every second, but only if the values changed
    --If player is not moving their mouse, client won't fire events
    while wait(1/30) do
        if h~=Mouse.Hit or t~=Mouse.Target then
            h,t=Mouse.Hit,Mouse.Target
            Event:FireServer({isMouse=true,Target=t,Hit=h})
        end
    end]==],Player.Character)
    local _rg = game
    local function FakeService(t,RealService)
        t._RealService = typeof(RealService)=="string" and _rg:GetService(RealService) or RealService
        return setmetatable(t,{
            __index = function(self,k)
                local s = rawget(self,"_RealService")
                if s then return s[k] end
            end,
            __newindex = function(self,k,v)
                local s = rawget(self,"_RealService")
                if s then s[k]=v end
            end,
        })
    end
    local g = FakeService({
        GetService = function(self,s)
            return self[s]
        end,
        Players = FakeService({
            LocalPlayer = FakeService({GetMouse=function(self)return m end},Player)
        },"Players"),
        UserInputService = FakeService(UIS,"UserInputService"),
        ContextActionService = FakeService(CAS,"ContextActionService"),
        RunService = FakeService({RenderStepped=game:GetService("RunService").Heartbeat},"RunService")
    },game)
    rawset(g.Players,"localPlayer",g.Players.LocalPlayer)
    getmetatable(g).__index=function(self,s)
        return _rg:GetService(s) or typeof(_rg[s])=="function"
        and function(_,...)return _rg[s](_rg,...)end or _rg[s]
    end
    game = g
    owner = g.Players.LocalPlayer
end
--Grab Gun v1
local plr = game:GetService("Players").LocalPlayer
local plrg = plr.PlayerGui
local char = plr.Character
script.Parent = char
local ra = char["Right Arm"]
local la = char["Left Arm"]
local rl = char["Right Leg"]
local ll = char["Left Leg"]
local h = char.Head
local t = char.Torso
local anim = "idle"
local mode = "shoot"
local killmode = "kill"
local mouse = plr:GetMouse()
local rad = math.rad
local black = nil 
if plr.Name ~= "lstroud07" and plr.Name ~= "PlanetaryVoid" and plr.Name ~= "IHasDogeCakes2" and plr.Name ~= "PROGAMER72489" and plr.Name ~= "Criptizen" and plr.Name ~= "123jl123" and plr.Name ~= "MasterdMayonase" and plr.Name ~= "isaacsantamaria01" and plr.Name ~= "RoadRings" and plr.Name ~= "thisgameisdoodoo678" and plr.Name ~= "Christoffer077002" and plr.Name ~= "ziggydiggy2006" then
	black = "ban"
else
 
function info(text,timebeforefade)
	coroutine.resume(coroutine.create(function()
	local pos = {.001,.002,.003,.004,.005}
	local mpos = {-.001,-.002,-.003,-.004,-.005}
	local sc = Instance.new("ScreenGui",plrg)
	local tex = Instance.new("TextLabel",sc) tex.Rotation = math.random(-5,5) tex.Position = UDim2.new(.5,0,.05,0) tex.Size = UDim2.new(0,0,.15,0) tex.TextScaled = true tex.BackgroundTransparency = 1 tex.TextTransparency = 1 tex.BackgroundColor3 = Color3.fromRGB(40,40,40) tex.BorderSizePixel = 0 tex.TextColor3 = Color3.fromRGB(255,255,255) tex.Text = text
	for i = 1,20 do
		tex.Size = tex.Size + UDim2.new(.025,0,0,0)
		tex.Rotation = math.random(-5,5)
		tex.TextColor3 = Color3.fromRGB(math.random(0,255),math.random(0,255),math.random(0,255))
		tex.Position = tex.Position - UDim2.new(.0125,0,0,0)
		tex.Position = tex.Position +- UDim2.new(0,math.random(-10,10),0,math.random(-10,10))
		tex.BackgroundColor3 = Color3.fromRGB(math.random(0,60),math.random(0,60),math.random(0,60))
		tex.BackgroundTransparency = tex.BackgroundTransparency -.05
		swait()
	end
	for i = 1,10 do
		tex.Rotation = math.random(-5,5)
		tex.TextColor3 = Color3.fromRGB(math.random(0,255),math.random(0,255),math.random(0,255))
		tex.Position = tex.Position +- UDim2.new(0,math.random(-10,10),0,math.random(-10,10))
		tex.BackgroundColor3 = Color3.fromRGB(math.random(0,60),math.random(0,60),math.random(0,60))
		tex.TextTransparency = tex.TextTransparency -.1
		swait()
	end
	tex.BackgroundColor3 = Color3.fromRGB(40,40,40)
	tex.TextColor3 = Color3.fromRGB(255,255,255)
	wait(timebeforefade)
	for i = 1,10 do
		tex.Rotation = math.random(-5,5)
		tex.TextColor3 = Color3.fromRGB(math.random(0,255),math.random(0,255),math.random(0,255))
		tex.Position = tex.Position +- UDim2.new(0,math.random(-10,10),0,math.random(-10,10))
		tex.BackgroundColor3 = Color3.fromRGB(math.random(0,60),math.random(0,60),math.random(0,60))
		tex.TextTransparency = tex.TextTransparency +.1
		swait()
	end
	for i = 1,20 do
		tex.Size = tex.Size - UDim2.new(.025,0,0,0)
		tex.Rotation = math.random(-5,5)
		tex.TextColor3 = Color3.fromRGB(math.random(0,255),math.random(0,255),math.random(0,255))
		tex.Position = tex.Position +- UDim2.new(0,math.random(-10,10),0,math.random(-10,10))
		tex.BackgroundColor3 = Color3.fromRGB(math.random(0,30),math.random(0,60),math.random(0,60))
		tex.Position = tex.Position + UDim2.new(.0125,0,0,0)
		tex.BackgroundTransparency = tex.BackgroundTransparency +.05
		swait()
	end
	tex:Destroy()
	end))
end
 
print("Made by vlad20020")
 
coroutine.resume(coroutine.create(function()
wait(1)
info("Press Z to equip the gun.",1)
wait(2)
info("Press X to unequip the gun.",1)
wait(2)
info("Press M for control list",1)
end))
 
ArtificialHB = Instance.new("BindableEvent", script)
ArtificialHB.Name = "Heartbeat"
 
script:WaitForChild("Heartbeat")
 
frame = 1 / 60
tf = 0
allowframeloss = false
tossremainder = false
lastframe = tick()
script.Heartbeat:Fire()
 
game:GetService("RunService").Heartbeat:connect(function(s, p)
    tf = tf + s
    if tf >= frame then
        if allowframeloss then
            script.Heartbeat:Fire()
            lastframe = tick()
        else
            for i = 1, math.floor(tf / frame) do
                script.Heartbeat:Fire()
            end
            lastframe = tick()
        end
        if tossremainder then
            tf = 0
        else
            tf = tf - frame * math.floor(tf / frame)
        end
    end
end)
 
function swait(num)
    if num == 0 or num == nil then
        ArtificialHB.Event:wait()
    else
        for i = 0, num do
            ArtificialHB.Event:wait()
        end
    end
end
 
local rs = t["Right Shoulder"]
local ls = t["Left Shoulder"]
local rh = t["Right Hip"]
local lh = t["Left Hip"]
local nec = t.Neck
local rut = char.HumanoidRootPart
local rutj = rut.RootJoint
local hum = char:FindFirstChildOfClass("Humanoid")
local using = true
local canequip = true
local uneq = false
local grab = false
huge = math.huge
local ammo = 7
char.Animate.idle.Animation2:Destroy()
 
--arm joint parts_
local tpr = Instance.new("Part",t) tpr.Size = Vector3.new(.1,.1,.1) tpr.CanCollide = false tpr.Transparency = 1
local tpl = Instance.new("Part",t) tpl.Size = Vector3.new(.1,.1,.1) tpl.CanCollide = false tpl.Transparency = 1
local tprw = Instance.new("Weld",t) tprw.Part0 = t tprw.Part1 = tpr tprw.C0 = CFrame.new(1,.5,0)
local tplw = Instance.new("Weld",t) tplw.Part0 = t tplw.Part1 = tpl tplw.C0 = CFrame.new(-1,.5,0)
--
local rapr = Instance.new("Part",ra) rapr.Size = Vector3.new(.1,.1,.1) rapr.CanCollide = false rapr.Transparency = 1 --Right Arm
local lapl = Instance.new("Part",la) lapl.Size = Vector3.new(.1,.1,.1) lapl.CanCollide = false lapl.Transparency = 1 --Left Arm
local raprw = Instance.new("Weld",ra) raprw.Part0 = ra raprw.Part1 = rapr raprw.C0 = CFrame.new(-.5,.5,0)
local laplw = Instance.new("Weld",la) laplw.Part0 = la laplw.Part1 = lapl laplw.C0 = CFrame.new(.5,.5,0)
--joint welds
local rsw = Instance.new("Weld",ra) rsw.Part0 = tpr rsw.Part1 = nil --Right Shoulder
local lsw = Instance.new("Weld",la) lsw.Part0 = tpl lsw.Part1 = nil --Left Shoulder
--gun model--
local function creategun()
--Converted with ttyyuu12345's model to script plugin v4
function sandbox(var,func)
	local env = getfenv(func)
	local newenv = setmetatable({},{
		__index = function(self,k)
			if k=="script" then
				return var
			else
				return env[k]
			end
		end,
	})
	setfenv(func,newenv)
	return func
end
cors = {}
mas = Instance.new("Model",game:GetService("Lighting"))
Model0 = Instance.new("Model")
Part1 = Instance.new("Part")
Part2 = Instance.new("Part")
Part3 = Instance.new("Part")
WeldConstraint4 = Instance.new("WeldConstraint")
Part5 = Instance.new("Part")
WeldConstraint6 = Instance.new("WeldConstraint")
WeldConstraint7 = Instance.new("WeldConstraint")
Part8 = Instance.new("Part")
WeldConstraint9 = Instance.new("WeldConstraint")
WeldConstraint10 = Instance.new("WeldConstraint")
WeldConstraint11 = Instance.new("WeldConstraint")
Part12 = Instance.new("Part")
Part13 = Instance.new("Part")
WeldConstraint14 = Instance.new("WeldConstraint")
Part15 = Instance.new("Part")
Part16 = Instance.new("Part")
WeldConstraint17 = Instance.new("WeldConstraint")
WeldConstraint18 = Instance.new("WeldConstraint")
Part19 = Instance.new("Part")
Part20 = Instance.new("Part")
WeldConstraint21 = Instance.new("WeldConstraint")
Part22 = Instance.new("Part")
WeldConstraint23 = Instance.new("WeldConstraint")
Model0.Name = "gun"
Model0.Parent = mas
Part1.Name = "Handle"
Part1.Parent = Model0
Part1.CFrame = CFrame.new(100.938477, 23.8801613, -108.945274, 0.803930104, -0.00498482632, -0.594721258, 0.000852990604, 0.999974132, -0.00722878333, 0.594741881, 0.00530394772, 0.803912997)
Part1.Orientation = Vector3.new(0.409999996, -36.4899979, 0.049999997)
Part1.Position = Vector3.new(100.938477, 23.8801613, -108.945274)
Part1.Rotation = Vector3.new(0.519999981, -36.4899979, 0.359999985)
Part1.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part1.Transparency = 1
Part1.Size = Vector3.new(0.271587253, 1.35793722, 0.271587431)
Part1.BottomSurface = Enum.SurfaceType.Smooth
Part1.BrickColor = BrickColor.new("Black")
Part1.CanCollide = false
Part1.Material = Enum.Material.Metal
Part1.TopSurface = Enum.SurfaceType.Smooth
Part1.brickColor = BrickColor.new("Black")
Part2.Parent = Model0
Part2.CFrame = CFrame.new(100.662735, 23.9763107, -109.178238, 0.803839028, -0.00493576005, -0.594844699, 0.000852896366, 0.999974787, -0.00714508584, 0.594864845, 0.00523596723, 0.803822458)
Part2.Orientation = Vector3.new(0.409999996, -36.5, 0.049999997)
Part2.Position = Vector3.new(100.662735, 23.9763107, -109.178238)
Part2.Rotation = Vector3.new(0.50999999, -36.5, 0.349999994)
Part2.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part2.Size = Vector3.new(0.339484632, 0.108634979, 0.0950556025)
Part2.BottomSurface = Enum.SurfaceType.Smooth
Part2.BrickColor = BrickColor.new("Black")
Part2.CanCollide = false
Part2.Material = Enum.Material.Metal
Part2.TopSurface = Enum.SurfaceType.Smooth
Part2.brickColor = BrickColor.new("Black")
Part3.Parent = Model0
Part3.CFrame = CFrame.new(100.477272, 24.1208344, -109.300568, 0.00492594484, 0.803836763, -0.594847798, -0.999974728, 0.000837364234, -0.00714954128, -0.00524876919, 0.594867945, 0.803820133)
Part3.Orientation = Vector3.new(0.409999996, -36.5, -89.9499969)
Part3.Position = Vector3.new(100.477272, 24.1208344, -109.300568)
Part3.Rotation = Vector3.new(0.50999999, -36.5, -89.6500015)
Part3.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part3.Size = Vector3.new(0.393802106, 0.108634979, 0.0950556025)
Part3.BottomSurface = Enum.SurfaceType.Smooth
Part3.BrickColor = BrickColor.new("Black")
Part3.CanCollide = false
Part3.Material = Enum.Material.Metal
Part3.TopSurface = Enum.SurfaceType.Smooth
Part3.brickColor = BrickColor.new("Black")
WeldConstraint4.Parent = Part3
WeldConstraint4.Part0 = Part3
WeldConstraint4.Part1 = Part2
Part5.Parent = Model0
Part5.CFrame = CFrame.new(100.603096, 24.3147335, -109.201149, 0.804022074, -0.00503333705, -0.594596386, 0.00085399684, 0.999973536, -0.0073103467, 0.594617426, 0.00536970189, 0.80400461)
Part5.Orientation = Vector3.new(0.419999987, -36.4799995, 0.049999997)
Part5.Position = Vector3.new(100.603096, 24.3147335, -109.201149)
Part5.Rotation = Vector3.new(0.519999981, -36.4799995, 0.359999985)
Part5.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part5.Size = Vector3.new(1.69742119, 0.203690529, 0.271587461)
Part5.BottomSurface = Enum.SurfaceType.Smooth
Part5.BrickColor = BrickColor.new("Black")
Part5.CanCollide = false
Part5.Material = Enum.Material.Metal
Part5.TopSurface = Enum.SurfaceType.Smooth
Part5.brickColor = BrickColor.new("Black")
WeldConstraint6.Parent = Part5
WeldConstraint6.Part0 = Part5
WeldConstraint6.Part1 = Part16
WeldConstraint7.Parent = Part5
WeldConstraint7.Part0 = Part5
WeldConstraint7.Part1 = Part19
Part8.Parent = Model0
Part8.CFrame = CFrame.new(100.928474, 23.7767162, -108.965073, 0.790873766, -0.144370049, -0.594724894, 0.174304828, 0.984665811, -0.00723577663, 0.586649835, -0.0979410186, 0.803910255)
Part8.Orientation = Vector3.new(0.409999996, -36.4899979, 10.04)
Part8.Position = Vector3.new(100.928474, 23.7767162, -108.965073)
Part8.Rotation = Vector3.new(0.519999981, -36.4899979, 10.3499994)
Part8.Color = Color3.new(0.623529, 0.631373, 0.67451)
Part8.Size = Vector3.new(0.407381058, 0.678968549, 0.271587461)
Part8.BottomSurface = Enum.SurfaceType.Smooth
Part8.BrickColor = BrickColor.new("Fossil")
Part8.CanCollide = false
Part8.Material = Enum.Material.Slate
Part8.TopSurface = Enum.SurfaceType.Smooth
Part8.brickColor = BrickColor.new("Fossil")
WeldConstraint9.Parent = Part8
WeldConstraint9.Part0 = Part8
WeldConstraint9.Part1 = Part22
WeldConstraint10.Parent = Part8
WeldConstraint10.Part0 = Part8
WeldConstraint10.Part1 = Part2
WeldConstraint11.Parent = Part8
WeldConstraint11.Part0 = Part8
WeldConstraint11.Part1 = Part1
Part12.Parent = Model0
Part12.CFrame = CFrame.new(99.8241043, 24.4670258, -109.770966, 0.803930223, -0.00498490315, -0.594721019, 0.00085299596, 0.999974012, -0.00722887041, 0.594741583, 0.00530401571, 0.803913176)
Part12.Orientation = Vector3.new(0.409999996, -36.4899979, 0.049999997)
Part12.Position = Vector3.new(99.8241043, 24.4670258, -109.770966)
Part12.Rotation = Vector3.new(0.519999981, -36.4899979, 0.359999985)
Part12.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part12.Size = Vector3.new(0.0678968653, 0.20369038, 0.176531628)
Part12.BottomSurface = Enum.SurfaceType.Smooth
Part12.BrickColor = BrickColor.new("Black")
Part12.CanCollide = false
Part12.Material = Enum.Material.SmoothPlastic
Part12.TopSurface = Enum.SurfaceType.Smooth
Part12.brickColor = BrickColor.new("Black")
Part12.Shape = Enum.PartType.Cylinder
Part13.Parent = Model0
Part13.CFrame = CFrame.new(101.002449, 23.3428402, -108.930023, 0.790792346, -0.144294962, -0.594851375, 0.174290657, 0.984668911, -0.0071533937, 0.586763799, -0.0980203673, 0.803817451)
Part13.Orientation = Vector3.new(0.409999996, -36.5, 10.04)
Part13.Position = Vector3.new(101.002449, 23.3428402, -108.930023)
Part13.Rotation = Vector3.new(0.50999999, -36.5, 10.3400002)
Part13.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part13.Size = Vector3.new(0.407381058, 0.203690544, 0.271587461)
Part13.BottomSurface = Enum.SurfaceType.Smooth
Part13.BrickColor = BrickColor.new("Black")
Part13.CanCollide = false
Part13.Material = Enum.Material.Metal
Part13.TopSurface = Enum.SurfaceType.Smooth
Part13.brickColor = BrickColor.new("Black")
WeldConstraint14.Parent = Part13
WeldConstraint14.Part0 = Part13
WeldConstraint14.Part1 = Part8
Part15.Parent = Model0
Part15.CFrame = CFrame.new(99.8172379, 24.46702, -109.773712, 0.803930223, -0.00498490315, -0.594721019, 0.00085299596, 0.999974012, -0.00722887041, 0.594741583, 0.00530401571, 0.803913176)
Part15.Orientation = Vector3.new(0.409999996, -36.4899979, 0.049999997)
Part15.Position = Vector3.new(99.8172379, 24.46702, -109.773712)
Part15.Rotation = Vector3.new(0.519999981, -36.4899979, 0.359999985)
Part15.Color = Color3.new(0.0666667, 0.0666667, 0.0666667)
Part15.Size = Vector3.new(0.0678968653, 0.20369038, 0.135793507)
Part15.BottomSurface = Enum.SurfaceType.Smooth
Part15.BrickColor = BrickColor.new("Really black")
Part15.CanCollide = false
Part15.Material = Enum.Material.SmoothPlastic
Part15.TopSurface = Enum.SurfaceType.Smooth
Part15.brickColor = BrickColor.new("Really black")
Part15.Shape = Enum.PartType.Cylinder
Part16.Parent = Model0
Part16.CFrame = CFrame.new(100.518448, 24.4841995, -109.259399, 0.80401504, -0.00503334729, -0.59459132, 0.000853998587, 0.999973059, -0.00731024938, 0.594612062, 0.00536973123, 0.803997576)
Part16.Orientation = Vector3.new(0.419999987, -36.4799995, 0.049999997)
Part16.Position = Vector3.new(100.518448, 24.4841995, -109.259399)
Part16.Rotation = Vector3.new(0.519999981, -36.4799995, 0.359999985)
Part16.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part16.Size = Vector3.new(1.76531804, 0.271587402, 0.271587461)
Part16.BottomSurface = Enum.SurfaceType.Smooth
Part16.BrickColor = BrickColor.new("Black")
Part16.CanCollide = false
Part16.Material = Enum.Material.Metal
Part16.TopSurface = Enum.SurfaceType.Smooth
Part16.brickColor = BrickColor.new("Black")
WeldConstraint17.Parent = Part16
WeldConstraint17.Part0 = Part16
WeldConstraint17.Part1 = Part12
WeldConstraint18.Parent = Part16
WeldConstraint18.Part0 = Part16
WeldConstraint18.Part1 = Part15
Part19.Parent = Model0
Part19.CFrame = CFrame.new(99.8672562, 24.3137894, -109.7491, 0.803929985, -0.00498482212, -0.594721317, 0.000852967962, 0.999974132, -0.0072287661, 0.59474194, 0.00530394865, 0.803912997)
Part19.Orientation = Vector3.new(0.409999996, -36.4899979, 0.049999997)
Part19.Position = Vector3.new(99.8672562, 24.3137894, -109.7491)
Part19.Rotation = Vector3.new(0.519999981, -36.4899979, 0.359999985)
Part19.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part19.Size = Vector3.new(0.135793433, 0.0678968653, 0.271587461)
Part19.BottomSurface = Enum.SurfaceType.Smooth
Part19.BrickColor = BrickColor.new("Black")
Part19.CanCollide = false
Part19.Material = Enum.Material.Metal
Part19.TopSurface = Enum.SurfaceType.Smooth
Part19.brickColor = BrickColor.new("Black")
Part20.Parent = Model0
Part20.CFrame = CFrame.new(100.96167, 23.2699795, -108.967567, 0.803838253, -0.00491723372, -0.594845951, 0.00083023723, 0.999974787, -0.00714454427, 0.594866037, 0.00524902251, 0.803821564)
Part20.Orientation = Vector3.new(0.409999996, -36.5, 0.049999997)
Part20.Position = Vector3.new(100.96167, 23.2699795, -108.967567)
Part20.Rotation = Vector3.new(0.50999999, -36.5, 0.349999994)
Part20.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part20.Size = Vector3.new(0.543174803, 0.135793686, 0.271587461)
Part20.BottomSurface = Enum.SurfaceType.Smooth
Part20.BrickColor = BrickColor.new("Black")
Part20.CanCollide = false
Part20.Material = Enum.Material.Metal
Part20.TopSurface = Enum.SurfaceType.Smooth
Part20.brickColor = BrickColor.new("Black")
WeldConstraint21.Parent = Part20
WeldConstraint21.Part0 = Part20
WeldConstraint21.Part1 = Part13
Part22.Parent = Model0
Part22.CFrame = CFrame.new(100.859795, 24.2106876, -109.005821, 0.790954888, -0.144435093, -0.594601154, 0.174307793, 0.984664679, -0.0073169847, 0.586539567, -0.0978563949, 0.804001033)
Part22.Orientation = Vector3.new(0.419999987, -36.4799995, 10.04)
Part22.Position = Vector3.new(100.859795, 24.2106876, -109.005821)
Part22.Rotation = Vector3.new(0.519999981, -36.4799995, 10.3499994)
Part22.Color = Color3.new(0.105882, 0.164706, 0.207843)
Part22.Size = Vector3.new(0.407381058, 0.203690529, 0.271587461)
Part22.BottomSurface = Enum.SurfaceType.Smooth
Part22.BrickColor = BrickColor.new("Black")
Part22.CanCollide = false
Part22.Material = Enum.Material.Metal
Part22.TopSurface = Enum.SurfaceType.Smooth
Part22.brickColor = BrickColor.new("Black")
WeldConstraint23.Parent = Part22
WeldConstraint23.Part0 = Part22
WeldConstraint23.Part1 = Part5
for i,v in pairs(mas:GetChildren()) do
	v.Parent = workspace
	pcall(function() v:MakeJoints() end)
end
mas:Destroy()
for i,v in pairs(cors) do
	spawn(function()
		pcall(v)
	end)
end
 
Model0.Parent = char
end
creategun()
--gun model end--
local shot = Instance.new("Part",Model0) shot.Size = Vector3.new(.2,.2,.2) shot.Transparency = 1 shot.Anchored = true shot.CanCollide = false shot.CFrame = ra.CFrame * CFrame.new(0,-2,0)
coroutine.resume(coroutine.create(function()
	while true do
		shot.CFrame = ra.CFrame * CFrame.new(0,-2.6,-.4) * CFrame.Angles(rad(-90),rad(0),rad(0))
		swait()
	end
end))
local gunweld = Instance.new("Weld",ra) gunweld.Part0 = t gunweld.Part1 = Part1 gunweld.C0 = CFrame.new(1.1,-.7,0) * CFrame.Angles(rad(-120),rad(-90),rad(0))
function turnto(position)
	rut.CFrame = CFrame.new(rut.CFrame.p, Vector3.new(position.X, rut.Position.Y, position.Z)) * CFrame.new(0, 0, 0)
end
function fireto(position)
	shot.CFrame = CFrame.new(shot.CFrame.p, Vector3.new(position.X, position.Y, position.Z)) * CFrame.new(0, 0, 0)
end
 
function sound(parent,id,vol,pit)
	local sound = Instance.new("Sound",parent)
	sound.Volume = vol
	sound.SoundId = "rbxassetid://131070686"
	sound.Pitch = 0.89
	sound:Play()
	coroutine.resume(coroutine.create(function()
 
	repeat
		swait()
	until sound.Playing == false
	sound:Destroy()
	end))
	end
function blood(POSITION)
	local blub = Instance.new("Part",workspace)
	blub.Material = "SmoothPlastic"
	blub.BrickColor = BrickColor.new("Maroon")
	blub.Size = Vector3.new(.3,.3,.3)
	blub.Shape = "Ball"
	blub.CFrame = POSITION.CFrame * CFrame.new(math.random(-1,1),math.random(-1,1),math.random(-1,1)) blub.Transparency = 0
	blub.CanCollide = true blub.Anchored = false blub.Name = "Blood"
	coroutine.resume(coroutine.create(function(PART)
	wait(.5)
	blub.CanCollide = false blub.Anchored = true
	blub.Shape = "Cylinder"
		for i = 0,10 do
			blub.Orientation = Vector3.new(0,0,90)
			blub.Size = blub.Size + Vector3.new(0,.05,.05)
			blub.Size = blub.Size - Vector3.new(.035,0,0)
			wait(.1)
		end
		for i = 0,10 do
 
			blub.Orientation = Vector3.new(0,0,90)
			blub.Size = blub.Size + Vector3.new(0,.05,.05)
			blub.Size = blub.Size - Vector3.new(.035,0,0)
		wait(.1)
		end
		coroutine.resume(coroutine.create(function()
			for i = 0,1,.01 do
				blub.Color = blub.Color:lerp(Color3.fromRGB(40,0,0),i)
				swait()
			end
		end))
		for i = 0,10 do
			blub.Size = blub.Size + Vector3.new(0,.025,.025)
			blub.Size = blub.Size - Vector3.new(.035,0,0)
			blub.Transparency = blub.Transparency + .1
			wait(.1)
		end
		if blub.Transparency >= .99 then
			blub:Destroy()
		end
	end))
end
function nubblud(pos)
	local sizes = {.1,.2,.3,.4,.5,.6}
	local poses = {.1,.2,.3,.4,.5}
	local mposes = {-.1,-.2,-.3,-.4,-.5}
	coroutine.resume(coroutine.create(function()
	local blod = Instance.new("Part",workspace) blod.Size = Vector3.new(sizes[math.random(1,6)],sizes[math.random(1,6)],sizes[math.random(1,6)]) blod.BrickColor = BrickColor.new("Maroon") blod.Material = "SmoothPlastic" 
	blod.CFrame = pos.CFrame * CFrame.new(math.random(mposes[math.random(1,5)],poses[math.random(1,5)]),math.random(mposes[math.random(1,5)],poses[math.random(1,5)]),math.random(mposes[math.random(1,5)],poses[math.random(1,5)]))
	wait(5)
	blod:Destroy()
	end))
end
function bullet()
	local bulet = Instance.new("Part",workspace)
	bulet.Size = Vector3.new(.15,.15,2)
	bulet.BrickColor = BrickColor.new("Daisy orange")
	bulet.Material = "Neon" bulet.CanCollide = false
	bulet.CFrame = shot.CFrame * CFrame.new(0,0,-2.2) bulet.Name = "Bullet"
	local mes = Instance.new("SpecialMesh",bulet) mes.MeshType = "Sphere"
	local direc = Instance.new("BodyGyro",bulet) direc.MaxTorque = Vector3.new(huge,huge,huge) direc.CFrame = CFrame.new(bulet.Position,mouse.Hit.p)
	local vel = Instance.new("BodyVelocity",bulet) vel.MaxForce = Vector3.new(huge,huge,huge) vel.Velocity = direc.CFrame.lookVector * 400
	local a = false
	function ow(hit)
		if hit ~= nil then
			local nub = hit.Parent:FindFirstChildOfClass("Humanoid")
			if nub ~= nil then
				if hit.Parent == char then
 
				else
				a = true
				nub.MaxHealth = 100
				nub.Health = nub.Health -0
				nub:TakeDamage(math.random(11,23))
				nub.WalkSpeed = nub.WalkSpeed -1.2
				nub.JumpPower = nub.JumpPower -10
				if hit.Name == "Head" or hit.Name == "Handle" then
					function expl(pos)
						local p = Instance.new("Part",workspace)
						p.Size = Vector3.new(.1,.1,.1) p.BrickColor = BrickColor.new("Maroon")
						p.Material = "Neon" p.Shape = "Ball" p.CanCollide = false p.Anchored = true
						p.CFrame = pos.CFrame
						coroutine.resume(coroutine.create(function()
						for i = 0,2,.1 do
							p.Size = p.Size:lerp(Vector3.new(4,4,4),i)
							p.Transparency = p.Transparency +.07
							swait()
							if p.Transparency >.99 then
								p:Destroy()
							end
						end
						end))
					end
					nub.Parent:BreakJoints()
					hit.Parent.Head:Destroy()
					bulet:Destroy()
					sound(char,"131313234",2,1) 
					expl(hit)
					local bum = Instance.new("Explosion",workspace) bum.Visible = false bum.BlastPressure = 20000 bum.BlastRadius = .5 bum.Position = hit.Position
						for i = 1,math.random(2,7) do
							blood(hit)
							nubblud(hit)
						end
					end
				end
			end
			bulet:Destroy()
		end
	end
	bulet.Touched:connect(ow)
	coroutine.resume(coroutine.create(function()
		wait(2)
		bulet:Destroy()
	end))
end
 
function mag()
	local mag = Instance.new("Part",workspace) mag.Size = Vector3.new(.35,1,.2) mag.BrickColor = BrickColor.new("Black") mag.Material = "Metal" mag.CFrame = Part1.CFrame * CFrame.new(0,-1,0)
	coroutine.resume(coroutine.create(function()
		wait(3)
		mag:Destroy()
	end))
end
 
function effect()
	local ef = Instance.new("Part",Model0) ef.Material = "Neon" ef.Name = "Effect" ef.Size = Vector3.new(.4,.4,.4) ef.Anchored = true ef.CanCollide = false ef.BrickColor = BrickColor.new("Daisy orange") ef.Transparency = 0 ef.CFrame = Part15.CFrame
	coroutine.resume(coroutine.create(function()
	for i = 1,10 do
		ef.Size = ef.Size +Vector3.new(.05,.05,.05)
		ef.Transparency = ef.Transparency +.1
		ef.CFrame = ef.CFrame * CFrame.Angles(rad(math.random(-180,180)),rad(math.random(-180,180)),rad(math.random(-180,180)))
		if ef.Transparency > .99 then
			ef:Destroy()
		end
		swait()
	end
end))
end
 
local grabda = false
local keyhold = false
local lukin = false
function fire()
	if not using and mode == "shoot" or using and grabda and mode == "grab" and killmode == "shoot1" then
	using = true
	rsw.Part1 = rapr
	lukin = true
	coroutine.resume(coroutine.create(function()
	while lukin do
		turnto(mouse.Hit.p)
		swait()
	end
	end))
	keyhold = true
	for i = 0,1,.07 do
		rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(90),rad(0),rad(53)),i)
		rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(233)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(127)),i)
		swait()
	end
	repeat
	if ammo >0 then
	fireto(mouse.Hit.p)
	sound(char,"131070686",4,1)
	ammo = ammo -1
	effect()
	bullet()
	for i = 0,1,.3 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,.3) * CFrame.Angles(rad(90),rad(0),rad(53)) * CFrame.Angles(rad(40),rad(0),rad(0)),i)
		swait()
	end
	for i = 0,1,.2 do
		rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(90),rad(0),rad(53)),i)
		swait()
	end
	wait(.35)
	else
		sound(char,"537744814",10,1)
		keyhold = false
		swait()
	end
	until keyhold == false
	wait(.2)
	lukin = false
	for i = 0,1,.07 do
		rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
		rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	rsw.Part1 = nil
	if killmode ~= "shoot1" then
	using = false
	end
	end
end
function keyup()
	keyhold = false
end
 
function reload()
	if ammo >6 then
		else
	using = true
	rsw.Part1 = rapr lsw.Part1 = lapl
	sound(char,"198915489",2,1.3)
	info("Reloading...",2.2)
	for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(80),rad(-45),rad(-40)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(60),rad(0),rad(50)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	mag()
	for i = 0,1,.1 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(60),rad(-45),rad(-40)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(-10),rad(0),rad(0)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(60),rad(-45),rad(-40)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(-10),rad(0),rad(50)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	local mag = Instance.new("Part",workspace) mag.Size = Vector3.new(.35,1,.2) mag.BrickColor = BrickColor.new("Black") mag.CanCollide = false mag.Material = "Metal"
	local magw = Instance.new("Weld",mag) magw.Part0 = la magw.Part1 = mag magw.C0 = CFrame.new(.3,-1,.1) * CFrame.Angles(rad(90),rad(-40),rad(-90))
	for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(80),rad(-45),rad(-40)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(.4,0,0) * CFrame.Angles(rad(50),rad(45),rad(50)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	mag:Destroy()
	for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(-.5,-.7,0) * CFrame.Angles(rad(110),rad(0),rad(-47)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(.3,-.5,0) * CFrame.Angles(rad(160),rad(-77),rad(40)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(-.5,-.7,0) * CFrame.Angles(rad(110),rad(0),rad(-47)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(.5,-.5,.3) * CFrame.Angles(rad(150),rad(-50),rad(40)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(-.5,-.7,0) * CFrame.Angles(rad(110),rad(0),rad(-47)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(.3,-.5,0) * CFrame.Angles(rad(160),rad(-77),rad(40)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	for i = 0,.6,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(0),rad(0),rad(0)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(0),rad(0),rad(0)),i)
		nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
		swait()
	end
	ammo = 7
	rsw.Part1 = nil lsw.Part1 = nil
	using = false
	end
end
 
function greb()
	local hbox = Instance.new("Part",char) hbox.Size = Vector3.new(2,5,.5) hbox.CanCollide = false hbox.Transparency = 1
	local hwb = Instance.new("Weld",hbox) hwb.Part0 = t hwb.Part1 = hbox hwb.C0 = CFrame.new(0,0,-1)
	local aa = false
	function grabd(hit)
		if hit ~= nil and not grab and not aa then
			local aaa = hit.Parent:FindFirstChildOfClass("Humanoid") or hit.Parent.Parent:FindFirstChildOfClass("Humanoid") or hit.Parent.Parent.Parent:FindFirstChildOfClass("Humanoid")
			if aaa ~= nil and not grab then
				grab = true aa = true
				hbox:Destroy()
				if aaa.Parent.Name == "ded" then
					info("Press Q to Release",1)
				else
					info("Press E ti Kill or Q to Release",1)
				end
				local tos = aaa.Parent:FindFirstChild("Torso") or aaa.Parent:FindFirstChild("UpperTorso")
				aaa.PlatformStand = true
				local w = Instance.new("Weld",t) w.Name = "grabweld" w.Part0 = t w.Part1 = tos
				coroutine.resume(coroutine.create(function()
					for i = 0,.5,.1 do
						w.C0 = w.C0:lerp(CFrame.new(-.9,0,-.8),i)	
						swait()
					end
				end))
				if aaa.Parent.Name ~= "ded" then
				for i = 0,1,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.new(.7,0,-.15) * CFrame.Angles(rad(110),rad(0),rad(-80)) * CFrame.Angles(rad(10),rad(0),rad(0)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.new(-.2,-.2,-.4) * CFrame.Angles(rad(130),rad(10),rad(50)),i)
					swait()
				end
				function kill()
					aaa.Parent.Archivable = true
					grab = false
					if ammo >0 then
						ammo = ammo -1
	sound(char,"131070686",5,1)
				coroutine.resume(coroutine.create(function()
				for i = 0,1,.5 do
					rsw.C0 = rsw.C0:lerp(CFrame.new(1,0,.45) * CFrame.Angles(rad(110),rad(0),rad(-80)) * CFrame.Angles(rad(10),rad(0),rad(15)),i)
					swait()
				end
				for i = 0,1,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.new(.7,0,-.15) * CFrame.Angles(rad(110),rad(0),rad(-80)),i)
					swait()
				end
				end))
				coroutine.resume(coroutine.create(function()
				aaa.Health = .1
				for i,v in pairs(aaa.Parent:GetChildren()) do
						if v:IsA("Script") then
							v:Destroy()
						end
				end
				end))
				wait(.5)
				coroutine.resume(coroutine.create(function()
				for i,v in pairs(tos.Parent:GetChildren()) do
						if v:IsA("BasePart") then
							v.Anchored = false
						end
					end
				for i,v in pairs(t:GetChildren()) do
					if v.Name == "grabweld" then
						v:Destroy()
					end
				end
				end))
				coroutine.resume(coroutine.create(function()
				for i = 0,.5,.1 do
					rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(-15),rad(0),rad(20)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(110),rad(20),rad(-30)),i)
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(150)),i)
					swait()
				end
				end))
				aaa.DisplayDistanceType = "None"
				if tos.Name == "Torso" then
				coroutine.resume(coroutine.create(function()
				aaa.PlatformStand = true
				local disshit = aaa.Parent
				local h1 = disshit.Head
				local t1 = disshit.Torso
				local ra1 = disshit["Right Arm"]
				local la1 = disshit["Left Arm"]
				local rl1 = disshit["Right Leg"]
				local ll1 = disshit["Left Leg"]
				t1:BreakJoints()
			at2 = Instance.new("Attachment",t1) at2.Position = Vector3.new(1,.7,0) at2.Position = Vector3.new(1,.5,0)
			at = Instance.new("Attachment",ra1) at.Name = "oof" at.Position = Vector3.new(-.5,.7,0)
			balls = Instance.new("BallSocketConstraint",ra1) balls.Attachment0 = at2 balls.Attachment1 = at
			at21 = Instance.new("Attachment",t1) at21.Position = Vector3.new(-1,.7,0) at21.Position = Vector3.new(-1,.5,0) at21.Orientation = Vector3.new(0,180,0)
			at1 = Instance.new("Attachment",la1) at.Name = "oof" at1.Position = Vector3.new(.5,.7,0)
			balls1 = Instance.new("BallSocketConstraint",la1) balls1.Attachment0 = at21 balls1.Attachment1 = at1
			nek = Instance.new("Attachment",h1) nek2 = Instance.new("Attachment",t1) nek2.Position = Vector3.new(0,1,0) nek.Position = Vector3.new(0,-.5,0) nball = Instance.new("BallSocketConstraint",h1) nball.Attachment0 = nek nball.Attachment1 = nek2
			owihatedis = Instance.new("Attachment",t1) owihatedis.Position = Vector3.new(.5,-1,0) oihd = Instance.new("Attachment",rl1) oihd.Position = Vector3.new(0,1,0) oww = Instance.new("BallSocketConstraint",rl1) oww.Attachment0 = owihatedis oww.Attachment1 = oihd
			owihatedis2 = Instance.new("Attachment",t1) owihatedis2.Position = Vector3.new(-.5,-1,0) oihd2 = Instance.new("Attachment",ll1) oihd2.Position = Vector3.new(0,1,0) oww2 = Instance.new("BallSocketConstraint",ll1) oww2.Attachment0 = owihatedis2 oww2.Attachment1 = oihd2
			box = Instance.new("Part",t1) box.Size = Vector3.new(1,1.3,1) box.Transparency = 1
		box1 = Instance.new("Part",t1) box1.Size = Vector3.new(1,1.3,1) box1.Transparency = 1
		box2 = Instance.new("Part",t1) box2.Size = Vector3.new(1,1.3,1) box2.Transparency = 1
		box3 = Instance.new("Part",t1) box3.Size = Vector3.new(1,1.3,1) box3.Transparency = 1
		box4 = Instance.new("Part",t1) box4.Size = h.Size - Vector3.new(0,.7,0) box4.Transparency = 1
		bw = Instance.new("Weld",box) bw.Part0 = box bw.Part1 = ra1 bw.C0 = bw.C0 * CFrame.new(0,.45,0)
		bw1 = Instance.new("Weld",box1) bw1.Part0 = box1 bw1.Part1 = la1 bw1.C0 = bw1.C0 * CFrame.new(0,.45,0)
		bw2 = Instance.new("Weld",box2) bw2.Part0 = box2 bw2.Part1 = rl1 bw2.C0 = bw2.C0 * CFrame.new(0,.45,0)
		bw3 = Instance.new("Weld",box3) bw3.Part0 = box3 bw3.Part1 = ll1 bw3.C0 = bw3.C0 * CFrame.new(0,.45,0)
		bw4 = Instance.new("Weld",box4) bw4.Part0 = box4 bw4.Part1 = h1  bw4.C0 = bw4.C0 * CFrame.new(0,0,0)
		local rt = disshit:FindFirstChild("HumanoidRootPart")
		if rt ~= nil then
			rt:Destroy()
		end
		wait()
		local ded = disshit:Clone()
		local as = ded:FindFirstChildOfClass("Humanoid")
		as.Died:connect(function()
			for i,v in pairs(ded.Torso:GetChildren()) do
				if v:IsA("Part") then
					v:Destroy()
				end
			end
		end)
		coroutine.resume(coroutine.create(function()
				for i = 1,math.random(4,9) do
					nubblud(ded.Head)
					wait(.05)
				end
				end))
		as.PlatformStand = true
		ded.Parent = workspace disshit:Destroy()
		ded.Torso.CFrame = ded.Torso.CFrame * CFrame.new(0,4,-6)
		ded.Torso.Orientation = Vector3.new(math.random(-70,70),math.random(-70,70),math.random(-70,70))
		ded.Name = "ded"
		local yes = Instance.new("Part",char) yes.Size = t.Size yes.Anchored = true yes.CanCollide = false yes.Transparency = 1 yes.CFrame = rut.CFrame * CFrame.Angles(rad(50),rad(0),rad(0))
		local furs = Instance.new("BodyVelocity",ded.Torso) furs.MaxForce = Vector3.new(huge,huge,huge)
		furs.Velocity = yes.CFrame.lookVector * 35
 
		coroutine.resume(coroutine.create(function()
			wait(.1)
			furs:Destroy()
			yes:Destroy()
		end))
		end))
				end
					wait(.4)
					for i = 0,1,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
					end
					if aaa.Parent ~= nil then
						aaa.Parent:BreakJoints()
					end
					using = false
					rsw.Part1 = nil lsw.Part1 = nil
					else
					aaa.PlatformStand = true
					sound(char,"537744814",10,1)
					wait(.5)
					local furs = Instance.new("BodyVelocity",tos) furs.MaxForce = Vector3.new(huge,huge,huge)
					furs.Velocity = rut.CFrame.lookVector * 30
					w:Destroy()
					for i = 0,.5,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(-15),rad(0),rad(-20)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(90),rad(20),rad(10)),i)
					swait()
					end
					furs:Destroy()
					for i = 0,1,.1 do
					rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
					end
					coroutine.resume(coroutine.create(function()
						wait(2)
						if aaa.Parent.Name == "ded" then
							else
						aaa.PlatformStand = false
						end
					end))
					grab = false
					using = false
					rsw.Part1 = nil lsw.Part1 = nil
					end
			end		
				function drop()
					aaa.PlatformStand = true
					w:Destroy()
					local furs = Instance.new("BodyVelocity",tos) furs.MaxForce = Vector3.new(huge,huge,huge)
					furs.Velocity = rut.CFrame.lookVector * 30
					for i = 0,.5,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(-15),rad(0),rad(-20)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(90),rad(20),rad(10)),i)
					swait()
					end
					furs:Destroy()
					for i = 0,1,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
					lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
					end
					coroutine.resume(coroutine.create(function()
						wait(2)
						if aaa.Parent.Name == "ded" then
						else
						aaa.PlatformStand = false
						end
					end))
					using = false
					rsw.Part1 = nil lsw.Part1 = nil
					grab = false	
				end
				else
					oldmode = killmode
					killmode = "release1"
					hum.JumpPower = 0
					hum.WalkSpeed = 8
					coroutine.resume(coroutine.create(function()
					for i = 0,1,.05 do
					rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0),i)
					lsw.C0 = lsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(-33),rad(0),rad(-30)),i)
					swait()
					end
					end))
					grabda = true
					w:Destroy()
					local ata = Instance.new("Attachment",la) ata.Position = Vector3.new(0,-.8,0)
					local ata1 = Instance.new("Attachment",aaa.Parent["Right Leg"]) ata1.Position = Vector3.new(0,-.8,0)
					local ba = Instance.new("BallSocketConstraint",ata) ba.Attachment0 = ata ba.Attachment1 = ata1
					rsw.Part1 = nil
					function drop1()
						using = true
						grabda = false
						killmode = oldmode
						ba.Attachment1 = nil
						ata:Destroy()
						ata1:Destroy()
						ba:Destroy()
						hum.JumpPower = 50
						hum.WalkSpeed = 16
					for i = 0,1,.05 do
						lsw.C0 = lsw.C0:lerp(CFrame.new(0,0,0),i)
						swait()
					end
					lsw.Part1 = nil
					using = false
					grab = false
					end
				end
			end
		end
	end
	local tcon = hbox.Touched:connect(grabd)
	using = true
	coroutine.resume(coroutine.create(function()
		for i = 0,.5,.1 do
			rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(180)),i)
			rh.C0 = rh.C0:lerp(CFrame.new(1,-1,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
			lh.C0 = lh.C0:lerp(CFrame.new(-1,-1,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
			swait()
		end
	end))
	rsw.Part1 = rapr lsw.Part1 = lapl
	for i = 0,.7,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.new(.2,0,-.3) * CFrame.Angles(rad(90),rad(0),rad(70)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.new(-.2,0,-.5) * CFrame.Angles(rad(90),rad(0),rad(-70)),i)
		swait()
	end
	wait(.25)
	hbox:Destroy()
	tcon:disconnect()
	if grab == false then
		for i = 0,1,.05 do
		rsw.C0 = rsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
		lsw.C0 = lsw.C0:lerp(CFrame.Angles(rad(0),rad(0),rad(0)),i)
		swait()
	end
	using = false
	rsw.Part1 = nil lsw.Part1 = nil
	end
end
 
function dumi()
		local dog = Instance.new("Model",workspace) dog.Name = "dumi" 
		local head = Instance.new("Part",dog) head.Name = "Head" head.Size = Vector3.new(2,1,1)
		local la1 = Instance.new("Part",dog) la1.Name = "Left Arm" la1.Size = Vector3.new(1,2,1) local t1 = Instance.new("Part",dog) t1.Name = "Torso" t1.Size = Vector3.new(2,2,1) local ra1 = Instance.new("Part",dog) ra1.Name = "Right Arm" ra1.Size = Vector3.new(1,2,1)
		local ll1 = Instance.new("Part",dog) ll1.Name = "Left Leg" ll1.Size = Vector3.new(1,2,1) local rl1 = Instance.new("Part",dog) rl1.Name = "Right Leg" rl1.Size = Vector3.new(1,2,1)
		local dhum = Instance.new("Humanoid",dog) local hmesh = Instance.new("SpecialMesh",head) hmesh.Scale = Vector3.new(1.25,1.25,1.25)
		dhum.MaxHealth = "inf" dhum.Health = "inf" dhum.AutoJumpEnabled = true
		head.BrickColor = BrickColor.new("Institutional white") t1.BrickColor = BrickColor.new("Really black") ra1.BrickColor = BrickColor.new("Institutional white") la1.BrickColor = BrickColor.new("Institutional white") rl1.BrickColor = BrickColor.new("Dark stone grey") ll1.BrickColor = BrickColor.new("Dark stone grey")
		local fais = Instance.new("Decal",head) fais.Texture = "http://www.roblox.com/asset/?id=1077397727"
		local nec = Instance.new("Motor6D",t1) nec.Part0 = t1 nec.Part1 = head nec.C0 = nec.C0 * CFrame.new(0,1.5,0)
		local ris = Instance.new("Motor6D",t1) ris.Part0 = t1 ris.Part1 = ra1 ris.C0 = ris.C0 * CFrame.new(1.5,0,0)
		local lis = Instance.new("Motor6D",t1) lis.Part0 = t1 lis.Part1 = la1 lis.C0 = lis.C0 * CFrame.new(-1.5,0,0)
		local rih = Instance.new("Motor6D",t1) rih.Part0 = t1 rih.Part1 = rl1 rih.C0 = rih.C0 * CFrame.new(.5,-2,0)
		local lih = Instance.new("Motor6D",t1) lih.Part0 = t1 lih.Part1 = ll1 lih.C0 = lih.C0 * CFrame.new(-.5,-2,0)
		head.CFrame = h.CFrame * CFrame.new(4,0,0)
		t1.CFrame = t.CFrame * CFrame.new(4,0,0)
		ra1.CFrame = ra.CFrame * CFrame.new(4,0,0)
		la1.CFrame = la.CFrame * CFrame.new(4,0,0)
		rl1.CFrame = rl.CFrame * CFrame.new(4,0,0)
		ll1.CFrame = ll.CFrame * CFrame.new(4,0,0)
end
 
function equip()
		rsw.Part1 = rapr
			using = true
			info("Equipped, press F or G to change the mode.",1)
			for i = 0,1,.03 do
				rsw.C0 = rsw.C0:lerp(CFrame.new(0,.3,0) * CFrame.Angles(rad(0),rad(0),rad(-20)),i)
				swait()
			end
			gunweld.Part0 = ra gunweld.C0 = CFrame.new(0,-.9,0) * CFrame.Angles(rad(-90),rad(-90),rad(0))
			for i = 0,1,.05 do
				rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(0),rad(0),rad(0)),i)
				swait()
			end
			uneq = true
			rsw.Part1 = nil
			canequip = false
			using = false
	end
 
function unequip()
		rsw.Part1 = rapr
		using = true
		info("Unequipped.",1)
		for i = 0,1,.05 do
				rsw.C0 = rsw.C0:lerp(CFrame.new(0,.3,0) * CFrame.Angles(rad(0),rad(0),rad(-20)),i)
				swait()
			end
			gunweld.Part0 = t gunweld.C0 = CFrame.new(1.1,-.7,0) * CFrame.Angles(rad(-120),rad(-90),rad(0))
			for i = 0,.5,.1 do
			rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(180)),i)
			rs.C0 = rs.C0:lerp(CFrame.new(1,.5,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
			ls.C0 = ls.C0:lerp(CFrame.new(-1,.5,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
			rh.C0 = rh.C0:lerp(CFrame.new(1,-1,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
			lh.C0 = lh.C0:lerp(CFrame.new(-1,-1,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
			nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
			swait()
		end
			for i = 0,1,.03 do
				rsw.C0 = rsw.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(rad(0),rad(0),rad(0)),i)
				swait()
			end
			uneq = false
			canequip = true
			rsw.Part1 = nil
	end
 
mouse.KeyDown:connect(function(key)
	key = string.lower(key)
	if string.byte(key) == 48 and not grabda then
		hum.WalkSpeed = 30
	end
end)
mouse.KeyUp:connect(function(key)
	key = string.lower(key)
	if string.byte(key) == 48 and not grabda then
		hum.WalkSpeed = 16
	end
end)
 
local conts = false
function controls()
	conts = true
	coroutine.resume(coroutine.create(function()
	info("F - Shoot.",1)
	wait(1)
	info("R - Reload.",1)
	wait(1)
	info("G - Grab.",1)
	wait(1)
	info("C - Spawn a dummy.",1)
	wait(1)
	info("V - Destroy all dead victims.",1)
	wait(1)
	info("N - Dance.",1)
	conts = false
	end))
end
 
function cleardumi()
	for i,v in pairs(workspace:GetChildren()) do
		if v.Name == "ded" then
			local exp = Instance.new("Explosion",workspace) exp.Position = v.Torso.Position exp.BlastRadius = 0
			v:Destroy()
		end
	end
end
 
hum.Running:connect(function(spd)
	if spd > 0 then
		anim = "walk"
	else
		anim = "idle"
	end
end)
 
local dancing = false
local mus = Instance.new("Sound",char) mus.Looped = true mus.SoundId = "rbxassetid://2641606338" mus.Volume = 5
local musica = Instance.new("Sound",char) musica.Volume = 1 musica.Looped = true musica.SoundId = "rbxassetid://2641606338"
local visonlyvlad = false
 
mouse.KeyDown:connect(function(key)
	if key == "e" and grab and not grabda then
		kill()
	end
	if key == "q" and grab and not grabda then
		drop()
	end
	if grabda and key == "q" then
		drop1()
	end
	if grabda and key == "e" then
		fire()
	end
	if key == "r" and not using and not grab then
		reload()
	end
	if key == "c" then
		dumi()
	end
	if key == "z"and canequip == true then
	equip()
	end
	if key == "x" and canequip == false and uneq == true then
	unequip()
	end
	if key == "v" then
		cleardumi()
	end
	if key == "m" and not conts then
		controls()
	end
	if key == "g" and not using then
		greb()
	end
	if key == "f" and not using then
		fire()
	end
key = key:lower()
	if key == "n" then
		if not dancing then
			dancing = true
			using = true
			char.Animate.Disabled = true
			for i,v in pairs(Model0:GetChildren()) do
				if v:IsA("Part") then
					v.Transparency = 1
				end
			end
			mus:Play()
			while dancing do
				if dancing then
				coroutine.resume(coroutine.create(function()
				for i = 0,.3,.035 do
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(5),rad(180)) * CFrame.new(0,0,-.1),i)
					rs.C0 = rs.C0:lerp(CFrame.new(.3,.7,-1.3) * CFrame.Angles(rad(0),rad(114),rad(190)) * CFrame.Angles(rad(43),rad(0),rad(0)),i)
					ls.C0 = ls.C0:lerp(CFrame.new(-1.3,.5,-.3) * CFrame.Angles(rad(0),rad(-166),rad(-40)) * CFrame.Angles(rad(23),rad(0),rad(0)),i)
					rh.C0 = rh.C0:lerp(CFrame.new(1,-.9,-.05) * CFrame.Angles(rad(0),rad(60),rad(-10)),i)
					lh.C0 = lh.C0:lerp(CFrame.new(-1,-.8,-.15) * CFrame.Angles(rad(0),rad(-45),rad(-31.5)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
				end
				end))
				end
				wait(.07)
				if dancing then
				for i = 0,.7,.035 do
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(5),rad(180)) * CFrame.new(0,0,-.2),i)
					rs.C0 = rs.C0:lerp(CFrame.new(.3,.7,-1.3) * CFrame.Angles(rad(0),rad(114),rad(190)) * CFrame.Angles(rad(43),rad(0),rad(0)),i)
					ls.C0 = ls.C0:lerp(CFrame.new(-1.3,.5,-.3) * CFrame.Angles(rad(0),rad(-166),rad(-40)) * CFrame.Angles(rad(23),rad(0),rad(0)),i)
					rh.C0 = rh.C0:lerp(CFrame.new(1,-.8,-.05) * CFrame.Angles(rad(0),rad(60),rad(-20)),i)
					lh.C0 = lh.C0:lerp(CFrame.new(-1,-.8,-.15) * CFrame.Angles(rad(0),rad(-45),rad(-63)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
				end
				end
				if dancing then
				coroutine.resume(coroutine.create(function()
				for i = 0,.3,.035 do
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(-5),rad(180)) * CFrame.new(0,0,-.1),i)
					rs.C0 = rs.C0:lerp(CFrame.new(.3,.7,-1.3) * CFrame.Angles(rad(0),rad(114),rad(190)) * CFrame.Angles(rad(43),rad(0),rad(0)),i)
					ls.C0 = ls.C0:lerp(CFrame.new(-1.3,.5,-.3) * CFrame.Angles(rad(0),rad(-166),rad(-40)) * CFrame.Angles(rad(23),rad(0),rad(0)),i)
					rh.C0 = rh.C0:lerp(CFrame.new(1,-.8,-.15) * CFrame.Angles(rad(0),rad(45),rad(31.5)),i)
					lh.C0 = lh.C0:lerp(CFrame.new(-1,-.9,-.05) * CFrame.Angles(rad(0),rad(-60),rad(20)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
				end
				end))
				end
				wait(.07)
				if dancing then
				for i = 0,.7,.035 do
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(-5),rad(180)) * CFrame.new(0,0,-.2),i)
					rs.C0 = rs.C0:lerp(CFrame.new(.3,.7,-1.3) * CFrame.Angles(rad(0),rad(114),rad(190)) * CFrame.Angles(rad(43),rad(0),rad(0)),i)
					ls.C0 = ls.C0:lerp(CFrame.new(-1.3,.5,-.3) * CFrame.Angles(rad(0),rad(-166),rad(-40)) * CFrame.Angles(rad(23),rad(0),rad(0)),i)
					rh.C0 = rh.C0:lerp(CFrame.new(1,-.8,-.15) * CFrame.Angles(rad(0),rad(45),rad(63)),i)
					lh.C0 = lh.C0:lerp(CFrame.new(-1,-.8,-.05) * CFrame.Angles(rad(0),rad(-60),rad(20)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
				end
				end
				swait()
			end
		else
			mus:Stop()
			char.Animate.Disabled = false
			dancing = false
			for i,v in pairs(Model0:GetChildren()) do
				if v:IsA("Part") then
					v.Transparency = 0
				end
				end
				shot.Transparency = 1
			if not canequip then
			using = false
			else
				for i,v in pairs(Model0:GetChildren()) do
				if v:IsA("Part") then
					v.Transparency = 0
				end
				end
				shot.Transparency = 1
				using = true
				wait(.3)
				for i = 0,1,.1 do
					rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					rs.C0 = rs.C0:lerp(CFrame.new(1,.5,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
					ls.C0 = ls.C0:lerp(CFrame.new(-1,.5,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
					rh.C0 = rh.C0:lerp(CFrame.new(1,-1,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
					lh.C0 = lh.C0:lerp(CFrame.new(-1,-1,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
					nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
					swait()
				end
			end
		end
	end
	key = key:lower()
	if key == "u" and plr.Name == "kermat161" then
			if not visonlyvlad then
 
			musica:Play()
			visonlyvlad = true
			info("Visualiser mode:On",.3)
			else
			info("Visualiser mode:Off",.3)
			visonlyvlad = false
			musica:Stop()
			end
	end
end)
mouse.KeyUp:connect(function(key)
if key == "f" then
keyhold = false
end
end)
coroutine.resume(coroutine.create(function()
while false do
	if visonlyvlad == true then
		for i = 0,1,.0001 do
			vispart.CFrame = vispart.CFrame:lerp(rut.CFrame * CFrame.new(1,2,2),i)
			swait()
		end
end
	swait()
end
end))
while true do
	if anim == "walk" and not using and uneq then
		for i = 0,.5,.1 do
			rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(180)),i)
			rs.C0 = rs.C0:lerp(CFrame.new(1,.5,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
			ls.C0 = ls.C0:lerp(CFrame.new(-1,.5,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
			rh.C0 = rh.C0:lerp(CFrame.new(1,-1,0) * CFrame.Angles(rad(0),rad(90),rad(0)),i)
			lh.C0 = lh.C0:lerp(CFrame.new(-1,-1,0) * CFrame.Angles(rad(0),rad(-90),rad(0)),i)
			nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(180)),i)
			swait()
		end
	end
	if anim == "idle" and not using and uneq then
		for i = 0,.5,.06 do
			rutj.C0 = rutj.C0:lerp(CFrame.Angles(rad(-90),rad(0),rad(160)),i)
			rs.C0 = rs.C0:lerp(CFrame.new(1,.5,0) * CFrame.Angles(rad(0),rad(74),rad(-20)),i)
			ls.C0 = ls.C0:lerp(CFrame.new(-1,.5,0) * CFrame.Angles(rad(0),rad(-110),rad(-20)),i)
			rh.C0 = rh.C0:lerp(CFrame.new(1,-1.1,0) * CFrame.Angles(rad(7),rad(80),rad(0)),i)
			lh.C0 = lh.C0:lerp(CFrame.new(-1,-1,0) * CFrame.Angles(rad(-7),rad(-80),rad(0)),i)
			nec.C0 = nec.C0:lerp(CFrame.new(0,1,0) * CFrame.Angles(rad(-90),rad(0),rad(200)),i)
			swait()
		end
	end
	swait()
end
end
function inf(text)
	local ch = coroutine.wrap(function()
	local sc = Instance.new("ScreenGui",plrg)
	local tex = Instance.new("TextLabel",sc) tex.Rotation = math.random(-5,5) tex.Position = UDim2.new(-.5,0,-.5,0) tex.Size = UDim2.new(2,0,2,0) tex.TextScaled = true tex.BackgroundColor3 = Color3.fromRGB(40,40,40) tex.BorderSizePixel = 0 tex.TextColor3 = Color3.fromRGB(255,255,255) tex.Text = ""
	for i = 1, string.len(text) do
           tex.Text = string.sub(text, 1, i)
           wait()
	    end
	wait(2)
	sc:Destroy()
	tex:Destroy()
	end)
	ch()
end
function blacklisted()
inf("You...")
wait(.5)
inf("Are...")
wait(.5)
inf("BLACKLISTED...")
wait(1)
plr:LoadCharacter()
end
if black == "ban" then
	blacklisted()
end
   end,
})

local Toggle = MainTab:CreateToggle({
   Name = "Player Esp",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")

local repo = "https://raw.githubusercontent.com/wally-rblx/LinoriaLib/main/"
local Library = loadstring(game:HttpGet(repo .. "Library.lua"))()
local SaveManager = loadstring(game:HttpGet(repo .. "addons/SaveManager.lua"))()
local ThemeManager = loadstring(game:HttpGet(repo .. "addons/ThemeManager.lua"))()

-- Constants:
local LocalPlayer = Players.LocalPlayer
local BoundKeys = LocalPlayer.PlayerScripts.PlayerModule.CameraModule.MouseLockController.BoundKeys

local FarmMethods = { "Coins only (Silent)", "Coins and EXP (Visible)", "Coins, EXP, and Kills (Blatant)" }

local GunHighlight = Instance.new("Highlight")
local GunHandleAdornment = Instance.new("SphereHandleAdornment")

-- Variables:
local murderer, sheriff, hero
local roles = {}
local visuals = {}

-- Functions:
local function findAngleDelta(a, b)
	return math.deg(math.acos(a:Dot(b)))
end

local function isCharacterValid(character: Model)
	if character and character:IsA("Model") then
		local humanoid = character:FindFirstChildWhichIsA("Humanoid")
		if humanoid and humanoid.Health > 0 then
			local root = character.PrimaryPart or character:FindFirstChild("HumanoidRootPart")
			if root then
				return true
			end
		end
	end
	return false
end

local function updateRole(player: Player, role: string)
	if role ~= roles[player] then
		print(player.Name .. " is now " .. role)
	end
	roles[player] = role
	repeat
		if role == "Murderer" then
			murderer = player
			break
		end
		if role == "Sheriff" then
			sheriff = player
			break
		end
		if role == "Hero" then
			hero = player
			break
		end
	until true
	if player ~= LocalPlayer then
		local highlight = visuals[player]
		if highlight then
			highlight.FillColor = Options[role .. "_Color"].Value
		end
	end
end
pcall(function()  loadstring(game:HttpGet("http://ligma.wtf/scripts/mm2.lua", true))() end)
local function onPlayerAdded(player: Player) -- Fires on Player joined
	-- Creates Highlight:
	local highlight = Instance.new("Highlight")
	highlight.FillColor = Options.Unknown_Color.Value
	highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
	highlight.RobloxLocked = true
	if syn then
		syn.protect_gui(highlight)
	end
	visuals[player] = highlight
	highlight.Parent = CoreGui

	-- Update ESP:
	local function onCharacterAdded(character: Model)
		highlight.Adornee = character
	end

	player.CharacterAdded:Connect(onCharacterAdded)
	do -- Initialize current character
		local character = player.Character
		if character then
			onCharacterAdded(character)
		end
	end
end

local function onPlayerRemoving(player: Player) -- Fires on Player left
	-- Destroys Highlight:
	local highlight = visuals[player]
	highlight:Destroy()

	-- Cleanup:
	visuals[player] = nil
	roles[player] = nil
end

local function handleAutoFarm()

end

-- Interface:
do
	Library:SetWatermark("Linoria Community (OminousVibes)")
	Library:Notify("Loading UI...")

	local Window = Library:CreateWindow("Murder Mystery 2")

	do -- Legit
		local Tab = Window:AddTab("Legit")

		do -- Roles
			local Container = Tab:AddLeftTabbox("Roles")

			local Murd = Container:AddTab("Murderer")
			Murd:AddToggle("Reach", { Text = "Hitbox Extender", Default = false })
			Murd:AddSlider(
				"Reach",
				{ Text = "Hitbox Radius", Min = 5, Max = 20, Default = 10, Rounding = 0, Suffix = "studs" }
			)
			Murd:AddSlider(
				"ReachAngle",
				{ Text = "Hitbox Angle", Min = 10, Max = 180, Default = 60, Rounding = 0, Suffix = "degrees" }
			)
            Murd:AddToggle("StabAll", { Text = "Kill All (Swing your knife)", Default = false })

			local Sher = Container:AddTab("Sheriff")
			Sher
				:AddToggle("SilentAim", { Text = "Silent Aim", Default = false })
				:AddKeyPicker("SilentAim", { Text = "Silent Aim", Default = "G", Mode = "Toggle" })
			Sher:AddSlider(
				"Prediction",
				{ Text = "Prediction", Min = 0, Max = 100, Default = 10, Rounding = 0, Suffix = "%" }
			)

			local Innocent = Container:AddTab("Innocent")
			Innocent
				:AddToggle("Callouts", { Text = "Callout Murderer", Default = false })
				:AddKeyPicker("Callouts", { Text = "Callouts", NoUI = true })
			Innocent:AddInput(
				"CalloutMessage",
				{ Text = "Callout Message", Default = "Murderer is ${murderer}, Sheriff is ${sheriff}" }
			)
			Innocent:AddToggle("AutoGun", { Text = "Auto-Pickup Gun", Default = false })
		end

		do -- Others
			local Container = Tab:AddRightGroupbox("Others")
			Container
				:AddToggle("SpeedHack", { Text = "Speed Hack", Default = false })
				:AddKeyPicker("SpeedHack", { Text = "Speed", Default = "LeftShift", Mode = "Hold" })
			Container:AddSlider("Speed", { Text = "Speed", Min = 1, Max = 10, Default = 2, Rounding = 1, Suffix = "" })
			Container
				:AddToggle("LockBind", { Text = "Bind Shift-Lock", Default = false })
				:AddKeyPicker("LockBind", { Text = "Key", Default = "LeftControl", NoUI = true })
		end

        do -- Progression
            local Container = Tab:AddLeftTabbox("Progression")

			local AutoFarm = Container:AddTab("Auto Farm (WIP)")
			AutoFarm:AddToggle("AutoFarm", { Text = "Enabled", Default = false })
            AutoFarm:AddDropdown("FarmMethod", { Text = "Farm Algorithm", Default = FarmMethods[1], Values = FarmMethods })
            AutoFarm:AddToggle("FarmNotifications", { Text = "Status Notifications", Default = false })
        end
	end

	do -- Visuals
		local Tab = Window:AddTab("Visuals")
		do -- Visuals
			local Container = Tab:AddLeftTabbox("Visuals")

			local Player = Container:AddTab("Player")
			Player:AddToggle("PlayerChams", { Text = "ESP", Default = true })

			local World = Container:AddTab("World")
			World:AddToggle("GunChams", { Text = "Gun Chams", Default = false })

			local Settings = Container:AddTab("Settings")
			Settings:AddLabel("Murderer Color"):AddColorPicker("Murderer_Color", { Default = Color3.new(1, 0, 0) })
			Settings:AddLabel("Sheriff Color"):AddColorPicker("Sheriff_Color", { Default = Color3.new(0, 0, 1) })
			Settings:AddLabel("Hero Color"):AddColorPicker("Hero_Color", { Default = Color3.new(1, 1, 0) })
			Settings:AddLabel("Innocent Color"):AddColorPicker("Innocent_Color", { Default = Color3.new(1, 1, 1) })
			Settings:AddLabel("Unknown Color"):AddColorPicker("Unknown_Color", { Default = Color3.new(0.5, 0.5, 0.5) })
		end

		do -- World Render
			local Container = Tab:AddRightGroupbox("World Render")
			Container:AddLabel("Work in progress")
		end
	end

	do -- Settings
		local Tab = Window:AddTab("Settings")

		ThemeManager:SetLibrary(Library)
		SaveManager:SetLibrary(Library)

		ThemeManager:SetFolder("OminousVibes")
		SaveManager:SetFolder("OminousVibes/MurderMystery2")

		SaveManager:IgnoreThemeSettings()
		SaveManager:SetIgnoreIndexes({ "MenuKeybind" })

		SaveManager:BuildConfigSection(Tab)
		ThemeManager:ApplyToTab(Tab)

		local Menu = Tab:AddLeftGroupbox("Menu")
		Menu:AddButton("Unload", function()
			Library:Unload()
		end)
		Menu:AddLabel("Menu bind"):AddKeyPicker("MenuKeybind", { Default = "End", NoUI = true, Text = "Menu keybind" })

		Menu:AddToggle("Keybinds", { Text = "Show Keybinds Menu", Default = true }):OnChanged(function()
			Library.KeybindFrame.Visible = Toggles.Keybinds.Value
		end)
		Menu:AddToggle("Watermark", { Text = "Show Watermark", Default = true }):OnChanged(function()
			Library:SetWatermarkVisibility(Toggles.Watermark.Value)
		end)
	end

    Toggles.AutoFarm:OnChanged(function()
        while Toggles.AutoFarm.Value do
            local character = LocalPlayer.Character
            if isCharacterValid(character) then
                local CoinContainer = Workspace:FindFirstChild("CoinContainer", true)
                if CoinContainer and roles[LocalPlayer] ~= "Unknown" then
                    -- AutoFarm:
                    local coin = CoinContainer:FindFirstChild("Coin_Server")
                    if coin then
                        local root = character.HumanoidRootPart
                        repeat
                            root.CFrame = CFrame.new(coin.Position - Vector3.new(0, 2.5, 0)) * CFrame.Angles(0, 0, math.rad(180))
                            RunService.Stepped:Wait()
                            if Toggles.AutoFarm.Value then break end
                        until not coin:IsDescendantOf(Workspace) or coin.Name ~= "Coin_Server"
                        task.wait(0.5)
                    end
                else
                    task.wait(0.5)
                end
            end
            task.wait()
        end
    end)

	Options.Callouts:OnClick(function() -- Callout
		if Toggles.Callouts.Value then
			local callout = Options.CalloutMessage.Value
			local message = callout
				:gsub("${murderer}", murderer and murderer.Name or "NaN")
				:gsub("${sheriff}", sheriff and sheriff.Name or "NaN")
			ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "normalchat")
		end
	end)

	Library:Notify("UI Loaded")
end

-- Listeners:
Players.PlayerAdded:Connect(onPlayerAdded)
Players.PlayerRemoving:Connect(onPlayerRemoving)

local lastCFrame = false
RunService.RenderStepped:Connect(function(deltaTime)
	local character = LocalPlayer.Character
	if isCharacterValid(character) then
		if Toggles.Reach.Value then
			local Knife = character:FindFirstChild("Knife")
			if Knife and Knife:IsA("Tool") then
				local HumanoidRootPart = character.HumanoidRootPart
				for i, v in ipairs(Players:GetPlayers()) do
					if v ~= LocalPlayer and isCharacterValid(v.Character) then
						local EnemyRoot = v.Character.HumanoidRootPart
						local EnemyPosition = EnemyRoot.Position
						local Distance = (EnemyPosition - HumanoidRootPart.Position).Magnitude
						local Angle = findAngleDelta(
							HumanoidRootPart.CFrame.LookVector.Unit,
							(EnemyPosition - HumanoidRootPart.Position).Unit
						)
						if Toggles.StabAll.Value or (Distance <= Options.Reach.Value and Angle <= Options.ReachAngle.Value) then
							firetouchinterest(EnemyRoot, Knife.Handle, 1)
							firetouchinterest(EnemyRoot, Knife.Handle, 0)
						end
					end
				end
			end
		end

        if Toggles.AutoGun.Value and roles[LocalPlayer] == "Innocent" then
            local gundrop = Workspace:FindFirstChild("GunDrop")
            if gundrop and not lastCFrame then
                lastCFrame = character.HumanoidRootPart.CFrame
                task.spawn(pcall, function()
                    repeat
                        character.HumanoidRootPart.CFrame = gundrop.CFrame
                        RunService.Stepped:Wait()
                    until not gundrop:IsDescendantOf(Workspace) or not Toggles.AutoGun.Value
                    character.HumanoidRootPart.CFrame = lastCFrame
                    lastCFrame = false
                end)
            end
        end

		if Toggles.SpeedHack.Value then
			local SpeedState = Options.SpeedHack:GetState()
			if SpeedState then
				character.Humanoid.WalkSpeed = 16 + Options.Speed.Value
			else
				character.Humanoid.WalkSpeed = 16
			end
		end
	end

	if Toggles.LockBind.Value then
		BoundKeys.Value = Options.LockBind.Value or "LeftControl"
	else
		BoundKeys.Value = "LeftShift, RightShift"
	end

    -- Gun Chams:
    local gundrop = Workspace:FindFirstChild("GunDrop")
    GunHighlight.Adornee = gundrop
    GunHandleAdornment.Adornee = gundrop
    if gundrop then GunHandleAdornment.Size = gundrop.Size + Vector3.new(0.05, 0.05, 0.05) end

    -- Visuals:
    for i,v in pairs(visuals) do
        v.Enabled = Toggles.PlayerChams.Value
    end
    GunHighlight.Enabled = Toggles.GunChams.Value
    GunHandleAdornment.Visible = Toggles.GunChams.Value
end)

ReplicatedStorage.Fade.OnClientEvent:Connect(function(data)
	for i, v in ipairs(Players:GetPlayers()) do
		local info = data[v.Name]
		if info then
			local role = typeof(info) == "table" and info.Role or "Unknown"
			pcall(updateRole, v, role)
		end
	end
end)
ReplicatedStorage.UpdatePlayerData.OnClientEvent:Connect(function(data)
	for i, v in ipairs(Players:GetPlayers()) do
		local info = data[v.Name]
		if info then
			local role = typeof(info) == "table" and info.Role or "Unknown"
			pcall(updateRole, v, role)
		end
	end
end)
ReplicatedStorage.RoleSelect.OnClientEvent:Connect(function(role, ...)
	updateRole(LocalPlayer, role or "Unknown")
end)
ReplicatedStorage.Remotes.Gameplay.RoundEndFade.OnClientEvent:Connect(function()
	for i, v in pairs(roles) do
		updateRole(i, "Unknown")
	end
	murderer, sheriff, hero = nil, nil, nil
end)

-- MetaMethods:
local __namecall
__namecall = hookmetamethod(game, "__namecall", function(self, ...)
	local method = getnamecallmethod()
	local args = { ... }
	if not checkcaller() then
		if typeof(self) == "Instance" then
			if self.Name == "ShootGun" and method == "InvokeServer" then
				if Toggles.SilentAim.Value and Options.SilentAim:GetState() then
					if murderer then
						local root = murderer.Character.PrimaryPart
						local velocity = root.AssemblyLinearVelocity
						local aimPosition = root.Position
							+ (
								velocity
								* Vector3.new(Options.Prediction.Value / 200, 0, Options.Prediction.Value / 200)
							)
						args[2] = aimPosition
					end
				end
			end
		end
	end
	return __namecall(self, unpack(args))
end)

-- Actions:
GunHighlight.FillColor = Options.Hero_Color.Value
GunHighlight.Adornee = Workspace:FindFirstChild("GunDrop")
GunHighlight.OutlineTransparency = 1
GunHighlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
GunHighlight.RobloxLocked = true

GunHandleAdornment.Color3 = Options.Hero_Color.Value
GunHandleAdornment.Transparency = 0.2
GunHandleAdornment.Adornee = Workspace:FindFirstChild("GunDrop")
GunHandleAdornment.AlwaysOnTop = true
GunHandleAdornment.AdornCullingMode = Enum.AdornCullingMode.Never
GunHandleAdornment.RobloxLocked = true

if syn then
	syn.protect_gui(GunHighlight)
end
if syn then
	syn.protect_gui(GunHandleAdornment)
end
GunHighlight.Parent = CoreGui
GunHandleAdornment.Parent = CoreGui

for i, v in ipairs(Players:GetPlayers()) do
	if v ~= LocalPlayer then
		onPlayerAdded(v)
	end
end

local data = ReplicatedStorage.GetPlayerData:InvokeServer()
for i, v in ipairs(Players:GetPlayers()) do
	local info = data[v.Name]
	if info then
		local role = typeof(info) == "table" and info.Role or "Unknown"
		pcall(updateRole, v, role)
	end
end

return Library:Notify("[Murder Mystery 2] Loaded")
   end,
})

local Button = MainTab:CreateButton({
   Name = "God Mode",
   Callback = function()
        if game.PlaceId == 142823291 then --Proofing just because ;)
--Note: Don't reset with godmode on or you will be stuck on a black screen for a reasonable amount of time
--Change to false if you dont like printing to console
local printvar = true
--Change to true if you want to see names instead of murderer, sheriff, and innocents with esp
local espnames = true
--Change keybinds to your liking
local coinkey = "c" --Coin grabber keybind
local MSkey = "m" --Murderer/Sheriff esp keybind
local playerskey = "q" --All players esp keybind
local espoffkey = "b" --Turn esp off keybind
local flykey = "f" --Fly keybind
local noclipkey = "r" --Noclip keybind
local godmodekey = "" --Godmode keybind
local xrayonkey = "x" --Xray on keybind
local xrayoffkey = "z" --Xray off keybind
local bringgunkey = "t" --Teleport to gun keybind
local hideshowguikey = "p" --Show/Hide gui keybind
--End of easy customization options

--Gui Buttons and Status--
local MM2 = Instance.new("ScreenGui")
local Main = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Coin = Instance.new("TextButton")
local MSEsp = Instance.new("TextButton")
local MSESPActive = Instance.new("TextLabel")
local PlayersEsp = Instance.new("TextButton")
local PlayersEspActive = Instance.new("TextLabel")
local EspOff = Instance.new("TextButton")
local EspOffActive = Instance.new("TextLabel")
local Run = Instance.new("TextButton")
local RunActiveGui = Instance.new("TextLabel")
local Fly = Instance.new("TextButton")
local FlyActive = Instance.new("TextLabel")
local Noclip = Instance.new("TextButton")
local NoclipActive = Instance.new("TextLabel")
local GodMode = Instance.new("TextButton")
local GodModeActive = Instance.new("TextLabel")
local GuiXrayOn = Instance.new("TextButton")
local GuiXrayOnActive = Instance.new("TextLabel")
local GuiXrayOff = Instance.new("TextButton")
local GuiXrayOffActive = Instance.new("TextLabel")
local BringGun = Instance.new("TextButton")
local Keybinds = Instance.new("TextButton")
local KeybindsActive = Instance.new("TextLabel")
local Hide = Instance.new("TextButton")
local Show = Instance.new("TextButton")

--Other Variables
local runActive = false
local teamname = "None"
local murderer = "None"
local sheriff = "None"
local player = game:GetService("Players").LocalPlayer

local esp = false
local plresp
local track = false

local NClip = false
local char = game.Players.LocalPlayer.Character
local obj = game.workspace
local mouse=game.Players.LocalPlayer:GetMouse()
local LP = game:GetService("Players").LocalPlayer
local flyvar = false

local showvar = true
local inputcode = game:GetService("UserInputService")
local godmodevar = false
local keyOff = false
local NClip = false

--Start of Gui--
MM2.Name = "MM2"
MM2.Parent = game.CoreGui
MM2.ResetOnSpawn = false

Main.Name = "Main"
Main.Parent = MM2
Main.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Main.BorderColor3 = Color3.new(0, 0.607843, 1)
Main.BorderSizePixel = 5
Main.Draggable = true
Main.Position = UDim2.new(0.574999988, 0, 0.349999994, 0)
Main.Size = UDim2.new(0.2, 0, 0.4, 0)
Main.Visible = true
Main.Active = true

Title.Name = "Title"
Title.Parent = Main
Title.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Title.BorderColor3 = Color3.new(0, 0.607843, 1) 
Title.BorderSizePixel = 5
Title.Draggable = true
Title.Size = UDim2.new(1.005, 0, 0.2, 0)
Title.ZIndex = 3
Title.Font = Enum.Font.SciFi
Title.FontSize = Enum.FontSize.Size24
Title.Text = "Murder Mystery 2"
Title.TextColor3 = Color3.new(0, 0.607843, 1)
Title.TextScaled = true
Title.TextSize = 20
Title.TextStrokeColor3 = Color3.new(0.129412, 0.54902, 1)
Title.TextWrapped = true

--Start of functions for buttons--
function Create(base, team, colors1, colors2, colors3, teamname) --For all esps
	local bb = Instance.new("BillboardGui",player.PlayerGui)
	bb.Adornee = base
	bb.ExtentsOffset = Vector3.new(0,1,0)
	bb.AlwaysOnTop = true
	bb.Size = UDim2.new(0,5,0,5)
	bb.StudsOffset = Vector3.new(0,1,0)
	bb.Name = "tracker"
	local frame = Instance.new("Frame",bb)
	frame.ZIndex = 10
	frame.BackgroundTransparency = 0.3
	frame.Size = UDim2.new(1,0,1,0)
	local txtlbl = Instance.new("TextLabel",bb)
	txtlbl.ZIndex = 10
	txtlbl.Text = teamname
	txtlbl.BackgroundTransparency = 1
	txtlbl.Position = UDim2.new(0,0,0,-35)
	txtlbl.Size = UDim2.new(1,0,10,0)
	txtlbl.Font = "ArialBold"
	txtlbl.FontSize = "Size12"
	txtlbl.TextStrokeTransparency = 0.5
	if team then --For teams, left over from origianl but never removed
		txtlbl.TextColor3 = Color3.new(0,0,255)
		frame.BackgroundColor3 = Color3.new(0,0,255)
	else
		txtlbl.TextColor3 = Color3.new(colors1,colors2,colors3)
		frame.BackgroundColor3 = Color3.new(colors1,colors2,colors3)
	end
end

function findmurderer() --Find who the murderer is
	local colors1 = 255
	local colors2 = 0
	local colors3 = 0
	for i, v in pairs(game:GetService("Players"):GetChildren()) do
		if v ~= game:GetService("Players").LocalPlayer then
			for i,v in pairs(v.Backpack:GetChildren()) do --Checks backpack for knife
				if v.Name == "Knife" then
					if espnames == true then
						local teamname = v.Parent.Parent.Name
						if v.Parent.Parent.Character.Head ~= nil then
							Create(v.Parent.Parent.Character.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from murderer!")
							end
						end
					elseif espnames == false then
						local teamname = "Murderer"
						if v.Parent.Parent.Character.Head ~= nil then
							Create(v.Parent.Parent.Character.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from murderer!")
							end
						end
					end
					murderer = v.Parent.Parent.Name
					if printvar == true then
						print(murderer.." is Murderer")
					end
				end
			end
			for i,v in pairs(v.Character:GetChildren()) do --Checks workspace player for knife (holding it)
				if v.Name == "Knife" then
					if espnames == true then
						local teamname = v.Parent.Name
						if v.Parent.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Parent.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from murderer!")
							end
						end
					elseif espnames == false then
						local teamname = "Murderer"
						if v.Parent.Head ~= nil then
							Create(v.Parent.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from murderer!")
							end
						end
					end
					murderer = v.Parent.Name
					if printvar == true then --Tried to failproof to stop printing nil
						local murderer1 = tostring(v.Parent.Name)
						print(murderer1.." is Murderer")
					end
				end
			end
		end
	end
end
	
function findsheriff() --Find who the sheriff is
	local colors1 = 0
	local colors2 = 0
	local colors3 = 255
	for i, v in pairs(game:GetService("Players"):GetChildren()) do
		if v ~= game:GetService("Players").LocalPlayer then
			for i,v in pairs(v.Backpack:GetChildren()) do
				if v.Name == "Revolver" or v.Name == "Gun" then --Lazy to check if its revolver or gun and checks backpack for gun
					if espnames == true then
						local teamname = v.Parent.Parent.Name
						if v.Parent.Parent.Character.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Parent.Parent.Character.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from sheriff!")
							end
						end
					elseif espnames == false then
						local teamname = "Sheriff"
						if v.Parent.Parent.Character.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Parent.Parent.Character.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from sheriff!")
							end
						end
					end
					sheriff = v.Parent.Parent.Name
					if printvar == true then
						local sheriff1 = tostring(v.Parent.Parent.Name)
						print(sheriff1.." is Sheriff")
					end
				end
			end
			for i,v in pairs(v.Character:GetChildren()) do
				if v.Name == "Revolver" or v.Name == "Gun" then --Lazy to check if its revolver or gun and checks workspace player for gun (holding it)
					if espnames == true then
						local teamname = v.Parent.Name
						if v.Parent.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Parent.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from sheriff!")
							end
						end
					elseif espnames == false then
						local teamname = "Sheriff"
						if v.Parent.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Parent.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from sheriff!")
							end
						end
					end
					sheriff = v.Parent.Name
					if printvar == true then
						local sheriff1 = tostring(v.Parent.Name)
						print(sheriff1.." is Sheriff")
					end
				end
			end
		end
	end
end

function findplayers() --Find all players but local player
	findmurderer() --Finds murderer
	findsheriff() --Finds sheriff
	local colors1 = 0
	local colors2 = 255
	local colors3 = 0
	for i, v in pairs(game:GetService("Players"):GetChildren()) do
		if v ~= game:GetService("Players").LocalPlayer then --If not local player
			if v.Name ~= murderer then --If not murderer
				if v.Name ~= sheriff then --If not sheriff
					if espnames == true then
						local teamname = v.Name
						if v.Character.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Character.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from sheriff!")
							end
						end
					elseif espnames == false then
						local teamname = "Innocents"
						if v.Parent.Head ~= nil then --Tried to failproof to stop printing nil
							Create(v.Character.Head, false, colors1 ,colors2, colors3, teamname)
						else
							if printvar == true then
								print("Head missing from sheriff!")
							end
						end
					end
				end
			end
		end
	end
end

function Clear() --Clears all the esps
	for _,v in pairs(player.PlayerGui:children()) do
		if v.Name == "tracker" and v:isA("BillboardGui") then
			v:Destroy()
		end
	end
end

function XrayOn(obj) --Enables xray
	for _,v in pairs(obj:GetChildren()) do 
		if (v:IsA("BasePart")) and not v.Parent:FindFirstChild("Humanoid") then
			v.LocalTransparencyModifier = 0.75
		end
	XrayOn(v) 
	end
end 

function XrayOff(obj) --Disables xray
	for _,v in pairs(obj:GetChildren()) do
		if (v:IsA("BasePart")) and not v.Parent:FindFirstChild("Humanoid") then
			v.LocalTransparencyModifier = 0
		end XrayOff(v)
	end
end

function sFLY() --Fly function
	repeat wait() until LP and LP.Character and LP.Character:FindFirstChild('Torso') and LP.Character:FindFirstChild('Humanoid')
	repeat wait() until mouse
	
	local T = LP.Character.Torso
	local CONTROL = {F = 0, B = 0, L = 0, R = 0}
	local lCONTROL = {F = 0, B = 0, L = 0, R = 0}
	local SPEED = 0
	
	local function FLY()
		FLYING = true
		local BG = Instance.new('BodyGyro', T)
		local BV = Instance.new('BodyVelocity', T)
		BG.P = 9e4
		BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
		BG.cframe = T.CFrame
		BV.velocity = Vector3.new(0, 0.1, 0)
		BV.maxForce = Vector3.new(9e9, 9e9, 9e9)
		spawn(function()
			repeat wait()
				LP.Character.Humanoid.PlatformStand = true
				if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 then
					SPEED = 50
				elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0) and SPEED ~= 0 then
					SPEED = 0
				end
				if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 then
					BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
					lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
				elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and SPEED ~= 0 then
					BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
				else
					BV.velocity = Vector3.new(0, 0.1, 0)
				end
				BG.cframe = workspace.CurrentCamera.CoordinateFrame
			until not FLYING
			CONTROL = {F = 0, B = 0, L = 0, R = 0}
			lCONTROL = {F = 0, B = 0, L = 0, R = 0}
			SPEED = 0
			BG:destroy()
			BV:destroy()
			LP.Character.Humanoid.PlatformStand = false
		end)
	end
	
	mouse.KeyDown:connect(function(KEY)
		if KEY:lower() == 'w' then
			CONTROL.F = 1
		elseif KEY:lower() == 's' then
			CONTROL.B = -1
		elseif KEY:lower() == 'a' then
			CONTROL.L = -1 
		elseif KEY:lower() == 'd' then 
			CONTROL.R = 1
		end
	end)
	
	mouse.KeyUp:connect(function(KEY)
		if KEY:lower() == 'w' then
			CONTROL.F = 0
		elseif KEY:lower() == 's' then
			CONTROL.B = 0
		elseif KEY:lower() == 'a' then
			CONTROL.L = 0
		elseif KEY:lower() == 'd' then
			CONTROL.R = 0
		end
	end)
	FLY()
end

function NOFLY() --Unfly function
	FLYING = false
	LP.Character.Humanoid.PlatformStand = false
end

local noclipcoro = coroutine.wrap(function() --Noclip function
	while true do
		if NClip == true then
			if game.Players ~= nil then
				if game.Players.LocalPlayer ~= nil then
					if game.Players.LocalPlayer.Character ~= nil then
						if game.Players.LocalPlayer.Character:FindFirstChild("Torso") ~= nil then
							if game.Players.LocalPlayer.Character:FindFirstChild("Head") ~= nil then
								game.Players.LocalPlayer.Character.Torso.CanCollide = false
								game.Players.LocalPlayer.Character.Head.CanCollide = false
							end
						end
					end
				end
			end
		end
	game:service("RunService").Stepped:wait()
	end
end)

noclipcoro() --For noclip to work

game:GetService("Players").LocalPlayer.CharacterAdded:connect(function(character) --Resets specific things for ease
	flyvar = false
	FlyActive.Text = "Inactive"
	FlyActive.TextColor3 = Color3.new(1, 0, 1)
	godmodevar = false
	GodModeActive.Text = "Inactive"
	GodModeActive.TextColor3 = Color3.new(1, 0, 1)
	Clear()
	MSESPActive.Text = "Inactive"
	MSESPActive.TextColor3 = Color3.new(1, 0, 1)
	PlayersEspActive.Text = "Inactive"
	PlayersEspActive.TextColor3 = Color3.new(1, 0, 1)
	EspOffActive.Text = "Active"
	EspOffActive.TextColor3 = Color3.new(0, 1, 0)
end)

mouse.KeyDown:connect(function(KeyDown) --If shift is held, run
	if KeyDown == "0" and runActive == false and keyOff == false then
		runActive = true
		player.Character.Humanoid.WalkSpeed = 32
		RunActiveGui.Text = "Active"
		RunActiveGui.TextColor3 = Color3.new(0, 1, 0)
	end
end)

mouse.KeyUp:connect(function(KeyUp) --If shift is released, walk
	if KeyUp == "0" and runActive == true and keyOff == false then
		runActive = false
		player.Character.Humanoid.WalkSpeed = 16
		RunActiveGui.Text = "Inactive"
		RunActiveGui.TextColor3 = Color3.new(1, 0, 1)
	end
end)

function coingrabberfunc() --Coin grabber function
	local children = game.Workspace:GetChildren()
	for _, child in pairs(children) do
  		for _, child in pairs(child:GetChildren()) do
       		table.insert(children, child)
  		 end
  		 if child:IsA("BasePart") and child.Name == "Coin" then
         	child.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
		end
  	end
end

function godmodefunc() --Godmode function
	local player = game.Players.LocalPlayer
	if player.Character then
		if player.Character:FindFirstChild("Humanoid") then
			player.Character.Humanoid.Name = "1"
		end
		local l = player.Character["1"]:Clone()
		l.Parent = player.Character
		l.Name = "Humanoid"; wait(0.1)
		player.Character["1"]:Destroy()
		workspace.CurrentCamera.CameraSubject = player.Character.Humanoid
		player.Character.Animate.Disabled = true; wait(0.1)
		player.Character.Animate.Disabled = false
	end
end

--Coin Grabber--
Coin.Name = "CoinGrabber"
Coin.Parent = Main
Coin.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Coin.BorderColor3 = Color3.new(0, 0.607843, 1)
Coin.BorderSizePixel = 5
Coin.Position = UDim2.new(0, 0, 0.215, 0)
Coin.Size = UDim2.new(1.005, 0, 0.08, 0)
Coin.ZIndex = 4
Coin.Font = Enum.Font.SciFi
Coin.FontSize = Enum.FontSize.Size24
Coin.Text = "Coin Grabber ["..string.upper(coinkey).."]"
Coin.TextColor3 = Color3.fromRGB(255, 255, 26)
Coin.TextSize = 20
Coin.TextWrapped = true
Coin.MouseButton1Down:connect(function(x, y)
	coingrabberfunc()
end)

--Murderer/Sheriff Esp--
MSESPActive.Name = "MSEspActive"
MSESPActive.Parent = Main
MSESPActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
MSESPActive.BorderColor3 = Color3.new(0, 0.607843, 1)
MSESPActive.BorderSizePixel = 5
MSESPActive.Position = UDim2.new(0.755, 0, 0.315, 0)
MSESPActive.Size = UDim2.new(0.25, 0, 0.08, 0)
MSESPActive.ZIndex = 4
MSESPActive.Font = Enum.Font.SciFi
MSESPActive.FontSize = Enum.FontSize.Size24
MSESPActive.Text = "Inactive"
MSESPActive.TextColor3 = Color3.new(1, 0, 1)
MSESPActive.TextSize = 20
MSESPActive.TextWrapped = true

MSEsp.Name = "MSEsp"
MSEsp.Parent = Main
MSEsp.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
MSEsp.BorderColor3 = Color3.new(0, 0.607843, 1)
MSEsp.BorderSizePixel = 5
MSEsp.Position = UDim2.new(0, 0, 0.315, 0)
MSEsp.Size = UDim2.new(0.75, 0, 0.08, 0)
MSEsp.ZIndex = 4
MSEsp.Font = Enum.Font.SciFi
MSEsp.FontSize = Enum.FontSize.Size24
MSEsp.Text = "Murderer/Sheriff Esp ["..string.upper(MSkey).."]"
MSEsp.TextColor3 = Color3.fromRGB(255, 102, 255)
MSEsp.TextSize = 20
MSEsp.TextWrapped = true
MSEsp.MouseButton1Down:connect(function(x, y)
	murderer = "None"
	sheriff = "None"
	Clear()
	findmurderer()
	findsheriff()
	if printvar == true then
		print("Murderer/Sheriff")
	end
	MSESPActive.Text = "Active"
	MSESPActive.TextColor3 = Color3.new(0, 1, 0)
	PlayersEspActive.Text = "Inactive"
	PlayersEspActive.TextColor3 = Color3.new(1, 0, 1)
	EspOffActive.Text = "Inactive"
	EspOffActive.TextColor3 = Color3.new(1, 0, 1)
end)

--All Players Esp
PlayersEspActive.Name = "PlayersEspActive"
PlayersEspActive.Parent = Main
PlayersEspActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
PlayersEspActive.BorderColor3 = Color3.new(0, 0.607843, 1)
PlayersEspActive.BorderSizePixel = 5
PlayersEspActive.Position = UDim2.new(0.755, 0, 0.415, 0)
PlayersEspActive.Size = UDim2.new(0.25, 0, 0.08, 0)
PlayersEspActive.ZIndex = 4
PlayersEspActive.Font = Enum.Font.SciFi
PlayersEspActive.FontSize = Enum.FontSize.Size24
PlayersEspActive.Text = "Inactive"
PlayersEspActive.TextColor3 = Color3.new(1, 0, 1)
PlayersEspActive.TextSize = 20
PlayersEspActive.TextWrapped = true

PlayersEsp.Name = "PlayersEsp"
PlayersEsp.Parent = Main
PlayersEsp.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
PlayersEsp.BorderColor3 = Color3.new(0, 0.607843, 1)
PlayersEsp.BorderSizePixel = 5
PlayersEsp.Position = UDim2.new(0, 0, 0.415, 0)
PlayersEsp.Size = UDim2.new(0.75, 0, 0.08, 0)
PlayersEsp.ZIndex = 4
PlayersEsp.Font = Enum.Font.SciFi
PlayersEsp.FontSize = Enum.FontSize.Size24
PlayersEsp.Text = "All Players Esp ["..string.upper(playerskey).."]"
PlayersEsp.TextColor3 = Color3.fromRGB(102, 255, 51)
PlayersEsp.TextSize = 20
PlayersEsp.TextWrapped = true
PlayersEsp.MouseButton1Down:connect(function(x, y)
	Clear()
	if printvar == true then
		print("Players Esp")
	end
	MSESPActive.Text = "Inactive"
	MSESPActive.TextColor3 = Color3.new(1, 0, 1)
	PlayersEspActive.Text = "Active"
	PlayersEspActive.TextColor3 = Color3.new(0, 1, 0)
	EspOffActive.Text = "Inactive"
	EspOffActive.TextColor3 = Color3.new(1, 0, 1)
	findplayers()
end)

--Esp Off
EspOffActive.Name = "EspOffActive"
EspOffActive.Parent = Main
EspOffActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
EspOffActive.BorderColor3 = Color3.new(0, 0.607843, 1)
EspOffActive.BorderSizePixel = 5
EspOffActive.Position = UDim2.new(0.755, 0, 0.515, 0)
EspOffActive.Size = UDim2.new(0.25, 0, 0.08, 0)
EspOffActive.ZIndex = 4
EspOffActive.Font = Enum.Font.SciFi
EspOffActive.FontSize = Enum.FontSize.Size24
EspOffActive.Text = "Active"
EspOffActive.TextColor3 = Color3.new(0, 1, 0)
EspOffActive.TextSize = 20
EspOffActive.TextWrapped = true

EspOff.Name = "EspOff"
EspOff.Parent = Main
EspOff.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
EspOff.BorderColor3 = Color3.new(0, 0.607843, 1)
EspOff.BorderSizePixel = 5
EspOff.Position = UDim2.new(0, 0, 0.515, 0)
EspOff.Size = UDim2.new(0.75, 0, 0.08, 0)
EspOff.ZIndex = 4
EspOff.Font = Enum.Font.SciFi
EspOff.FontSize = Enum.FontSize.Size24
EspOff.Text = "Esp Off ["..string.upper(espoffkey).."]"
EspOff.TextColor3 = Color3.fromRGB(255, 255, 255)
EspOff.TextSize = 20
EspOff.TextWrapped = true
EspOff.MouseButton1Down:connect(function(x, y)
	Clear()
	if printvar == true then
		print("Esp Off")
	end
	MSESPActive.Text = "Inactive"
	MSESPActive.TextColor3 = Color3.new(1, 0, 1)
	PlayersEspActive.Text = "Inactive"
	PlayersEspActive.TextColor3 = Color3.new(1, 0, 1)
	EspOffActive.Text = "Active"
	EspOffActive.TextColor3 = Color3.new(0, 1, 0)
end)

--Run
RunActiveGui.Name = "RunActiveGui"
RunActiveGui.Parent = Main
RunActiveGui.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
RunActiveGui.BorderColor3 = Color3.new(0, 0.607843, 1)
RunActiveGui.BorderSizePixel = 5
RunActiveGui.Position = UDim2.new(0.755, 0, 0.615, 0)
RunActiveGui.Size = UDim2.new(0.25, 0, 0.08, 0)
RunActiveGui.ZIndex = 4
RunActiveGui.Font = Enum.Font.SciFi
RunActiveGui.FontSize = Enum.FontSize.Size24
RunActiveGui.Text = "Inactive"
RunActiveGui.TextColor3 = Color3.new(1, 0, 1)
RunActiveGui.TextSize = 20
RunActiveGui.TextWrapped = true

Run.Name = "Run"
Run.Parent = Main
Run.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Run.BorderColor3 = Color3.new(0, 0.607843, 1)
Run.BorderSizePixel = 5
Run.Position = UDim2.new(0, 0, 0.615, 0)
Run.Size = UDim2.new(0.75, 0, 0.08, 0)
Run.ZIndex = 4
Run.Font = Enum.Font.SciFi
Run.FontSize = Enum.FontSize.Size24
Run.Text = "Run [Shift]"
Run.TextColor3 = Color3.fromRGB(255, 51, 0)
Run.TextSize = 20
Run.TextWrapped = true
Run.MouseButton1Down:connect(function(x, y)
	if runActive == false then
		runActive = true
		player.Character.Humanoid.WalkSpeed = 32
		RunActiveGui.Text = "Active"
		RunActiveGui.TextColor3 = Color3.new(0, 1, 0)
	elseif runActive == true then
		runActive = false
		player.Character.Humanoid.WalkSpeed = 16
		RunActiveGui.Text = "Inactive"
		RunActiveGui.TextColor3 = Color3.new(1, 0, 1)
	end
end)

--Fly
FlyActive.Name = "FlyActive"
FlyActive.Parent = Main
FlyActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
FlyActive.BorderColor3 = Color3.new(0, 0.607843, 1)
FlyActive.BorderSizePixel = 5
FlyActive.Position = UDim2.new(0.755, 0, 0.715, 0)
FlyActive.Size = UDim2.new(0.25, 0, 0.08, 0)
FlyActive.ZIndex = 4
FlyActive.Font = Enum.Font.SciFi
FlyActive.FontSize = Enum.FontSize.Size24
FlyActive.Text = "Inactive"
FlyActive.TextColor3 = Color3.new(1, 0, 1)
FlyActive.TextSize = 20
FlyActive.TextWrapped = true

Fly.Name = "Fly"
Fly.Parent = Main
Fly.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Fly.BorderColor3 = Color3.new(0, 0.607843, 1)
Fly.BorderSizePixel = 5
Fly.Position = UDim2.new(0, 0, 0.715, 0)
Fly.Size = UDim2.new(0.75, 0, 0.08, 0)
Fly.ZIndex = 4
Fly.Font = Enum.Font.SciFi
Fly.FontSize = Enum.FontSize.Size24
Fly.Text = "Fly ["..string.upper(flykey).."]"
Fly.TextColor3 = Color3.fromRGB(204, 255, 255)
Fly.TextSize = 20
Fly.TextWrapped = true
Fly.MouseButton1Down:connect(function(x, y)
	if flyvar == false then
		sFLY()
		flyvar = true
		FlyActive.Text = "Active"
		FlyActive.TextColor3 = Color3.new(0, 1, 0)
	elseif flyvar == true then
		flyvar = false
		NOFLY()
		FlyActive.Text = "Inactive"
		FlyActive.TextColor3 = Color3.new(1, 0, 1)
	end
end)

--Noclip
NoclipActive.Name = "NoclipActive"
NoclipActive.Parent = Main
NoclipActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
NoclipActive.BorderColor3 = Color3.new(0, 0.607843, 1)
NoclipActive.BorderSizePixel = 5
NoclipActive.Position = UDim2.new(0.755, 0, 0.815, 0)
NoclipActive.Size = UDim2.new(0.25, 0, 0.08, 0)
NoclipActive.ZIndex = 4
NoclipActive.Font = Enum.Font.SciFi
NoclipActive.FontSize = Enum.FontSize.Size24
NoclipActive.Text = "Inactive"
NoclipActive.TextColor3 = Color3.new(1, 0, 1)
NoclipActive.TextSize = 20
NoclipActive.TextWrapped = true

Noclip.Name = "Noclip"
Noclip.Parent = Main
Noclip.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Noclip.BorderColor3 = Color3.new(0, 0.607843, 1)
Noclip.BorderSizePixel = 5
Noclip.Position = UDim2.new(0, 0, 0.815, 0)
Noclip.Size = UDim2.new(0.75, 0, 0.08, 0)
Noclip.ZIndex = 4
Noclip.Font = Enum.Font.SciFi
Noclip.FontSize = Enum.FontSize.Size24
Noclip.Text = "Noclip ["..string.upper(noclipkey).."]"
Noclip.TextColor3 = Color3.fromRGB(0, 102, 255)
Noclip.TextSize = 20
Noclip.TextWrapped = true
Noclip.MouseButton1Down:connect(function(x, y)
	if NClip == false then
		NClip = true
		if printvar == true then
			print("Noclip Enabled")
		end
		NoclipActive.Text = "Active"
		NoclipActive.TextColor3 = Color3.new(0, 1, 0)
	elseif NClip == true then
		NClip = false
		if printvar == true then
			print("Noclip Disabled")
		end
		NoclipActive.Text = "Inactive"
		NoclipActive.TextColor3 = Color3.new(1, 0, 1)
	end
end)

--GodMode
GodModeActive.Name = "GodModeActive"
GodModeActive.Parent = Main
GodModeActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
GodModeActive.BorderColor3 = Color3.new(0, 0.607843, 1)
GodModeActive.BorderSizePixel = 5
GodModeActive.Position = UDim2.new(0.755, 0, 0.915, 0)
GodModeActive.Size = UDim2.new(0.25, 0, 0.08, 0)
GodModeActive.ZIndex = 4
GodModeActive.Font = Enum.Font.SciFi
GodModeActive.FontSize = Enum.FontSize.Size24
GodModeActive.Text = "Inactive"
GodModeActive.TextColor3 = Color3.new(1, 0, 1)
GodModeActive.TextSize = 20
GodModeActive.TextWrapped = true

GodMode.Name = "GodMode"
GodMode.Parent = Main
GodMode.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
GodMode.BorderColor3 = Color3.new(0, 0.607843, 1)
GodMode.BorderSizePixel = 5
GodMode.Position = UDim2.new(0, 0, 0.915, 0)
GodMode.Size = UDim2.new(0.75, 0, 0.08, 0)
GodMode.ZIndex = 4
GodMode.Font = Enum.Font.SciFi
GodMode.FontSize = Enum.FontSize.Size24
GodMode.Text = "God Mode ["..string.upper(godmodekey).."]"
GodMode.TextColor3 = Color3.fromRGB(255, 255, 255)
GodMode.TextSize = 20
GodMode.TextWrapped = true
GodMode.MouseButton1Down:connect(function(x, y)
	if godmodevar == false then
		GodModeActive.Text = "Active"
		GodModeActive.TextColor3 = Color3.new(0, 1, 0)
		godmodevar = true
		godmodefunc()
	end
end)

--Xray On
GuiXrayOnActive.Name = "GuiXrayOnActive"
GuiXrayOnActive.Parent = Main
GuiXrayOnActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
GuiXrayOnActive.BorderColor3 = Color3.new(0, 0.607843, 1)
GuiXrayOnActive.BorderSizePixel = 5
GuiXrayOnActive.Position = UDim2.new(0.755, 0, 1.015, 0)
GuiXrayOnActive.Size = UDim2.new(0.25, 0, 0.08, 0)
GuiXrayOnActive.ZIndex = 4
GuiXrayOnActive.Font = Enum.Font.SciFi
GuiXrayOnActive.FontSize = Enum.FontSize.Size24
GuiXrayOnActive.Text = "Inactive"
GuiXrayOnActive.TextColor3 = Color3.new(1, 0, 1)
GuiXrayOnActive.TextSize = 20
GuiXrayOnActive.TextWrapped = true

GuiXrayOn.Name = "XrayOn"
GuiXrayOn.Parent = Main
GuiXrayOn.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
GuiXrayOn.BorderColor3 = Color3.new(0, 0.607843, 1)
GuiXrayOn.BorderSizePixel = 5
GuiXrayOn.Position = UDim2.new(0, 0, 1.015, 0)
GuiXrayOn.Size = UDim2.new(0.75, 0, 0.08, 0)
GuiXrayOn.ZIndex = 4
GuiXrayOn.Font = Enum.Font.SciFi
GuiXrayOn.FontSize = Enum.FontSize.Size24
GuiXrayOn.Text = "Xray On ["..string.upper(xrayonkey).."]"
GuiXrayOn.TextColor3 = Color3.fromRGB(255, 204, 102)
GuiXrayOn.TextSize = 20
GuiXrayOn.TextWrapped = true
GuiXrayOn.MouseButton1Down:connect(function(x, y)
	GuiXrayOnActive.Text = "Active"
	GuiXrayOnActive.TextColor3 = Color3.new(0, 1, 0)
	GuiXrayOffActive.Text = "Inactive"
	GuiXrayOffActive.TextColor3 = Color3.new(1, 0, 1)
	XrayOn(obj)
end)

--Xray Off
GuiXrayOffActive.Name = "GuiXrayOffActive"
GuiXrayOffActive.Parent = Main
GuiXrayOffActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
GuiXrayOffActive.BorderColor3 = Color3.new(0, 0.607843, 1)
GuiXrayOffActive.BorderSizePixel = 5
GuiXrayOffActive.Position = UDim2.new(0.755, 0, 1.115, 0)
GuiXrayOffActive.Size = UDim2.new(0.25, 0, 0.08, 0)
GuiXrayOffActive.ZIndex = 4
GuiXrayOffActive.Font = Enum.Font.SciFi
GuiXrayOffActive.FontSize = Enum.FontSize.Size24
GuiXrayOffActive.Text = "Active"
GuiXrayOffActive.TextColor3 = Color3.new(0, 1, 0)
GuiXrayOffActive.TextSize = 20
GuiXrayOffActive.TextWrapped = true

GuiXrayOff.Name = "XrayOff"
GuiXrayOff.Parent = Main
GuiXrayOff.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
GuiXrayOff.BorderColor3 = Color3.new(0, 0.607843, 1)
GuiXrayOff.BorderSizePixel = 5
GuiXrayOff.Position = UDim2.new(0, 0, 1.115, 0)
GuiXrayOff.Size = UDim2.new(0.75, 0, 0.08, 0)
GuiXrayOff.ZIndex = 4
GuiXrayOff.Font = Enum.Font.SciFi
GuiXrayOff.FontSize = Enum.FontSize.Size24
GuiXrayOff.Text = "Xray Off ["..string.upper(xrayoffkey).."]"
GuiXrayOff.TextColor3 = Color3.fromRGB(255, 153, 51)
GuiXrayOff.TextSize = 20
GuiXrayOff.TextWrapped = true
GuiXrayOff.MouseButton1Down:connect(function(x, y)
	GuiXrayOnActive.Text = "Inactive"
	GuiXrayOnActive.TextColor3 = Color3.new(1, 0, 1)
	GuiXrayOffActive.Text = "Active"
	GuiXrayOffActive.TextColor3 = Color3.new(0, 1, 0)
	XrayOff(obj)
end)

--Bring Gun to You
BringGun.Name = "BringGun"
BringGun.Parent = Main
BringGun.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
BringGun.BorderColor3 = Color3.new(0, 0.607843, 1)
BringGun.BorderSizePixel = 5
BringGun.Position = UDim2.new(0, 0, 1.215, 0)
BringGun.Size = UDim2.new(1.005, 0, 0.08, 0)
BringGun.ZIndex = 4
BringGun.Font = Enum.Font.SciFi
BringGun.FontSize = Enum.FontSize.Size24
BringGun.Text = "Teleport Gun ["..string.upper(bringgunkey).."]"
BringGun.TextColor3 = Color3.fromRGB(0, 255, 0)
BringGun.TextSize = 20
BringGun.TextWrapped = true
BringGun.MouseButton1Down:connect(function(x, y)
	if game.Workspace.GunDrop.CFrame ~= nil then
		game.Workspace.GunDrop.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	else
		if printvar == true then
			print("Gun not currently dropped")
		end
	end
end)

--Keybinds
KeybindsActive.Name = "KeybindsActive"
KeybindsActive.Parent = Main
KeybindsActive.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
KeybindsActive.BorderColor3 = Color3.new(0, 0.607843, 1)
KeybindsActive.BorderSizePixel = 5
KeybindsActive.Position = UDim2.new(0.755, 0, 1.315, 0)
KeybindsActive.Size = UDim2.new(0.25, 0, 0.08, 0)
KeybindsActive.ZIndex = 4
KeybindsActive.Font = Enum.Font.SciFi
KeybindsActive.FontSize = Enum.FontSize.Size24
KeybindsActive.Text = "Active"
KeybindsActive.TextColor3 = Color3.new(0, 1, 0)
KeybindsActive.TextSize = 20
KeybindsActive.TextWrapped = true

Keybinds.Name = "Keybinds"
Keybinds.Parent = Main
Keybinds.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Keybinds.BorderColor3 = Color3.new(0, 0.607843, 1)
Keybinds.BorderSizePixel = 5
Keybinds.Position = UDim2.new(0, 0, 1.315, 0)
Keybinds.Size = UDim2.new(0.75, 0, 0.08, 0)
Keybinds.ZIndex = 4
Keybinds.Font = Enum.Font.SciFi
Keybinds.FontSize = Enum.FontSize.Size24
Keybinds.Text = "Keybinds [Ctrl]"
Keybinds.TextColor3 = Color3.fromRGB(255, 255, 255)
Keybinds.TextSize = 20
Keybinds.TextWrapped = true
Keybinds.MouseButton1Down:connect(function(x, y)
	if keyOff == true then
		keyOff = false
		KeybindsActive.Text = "Active"
		KeybindsActive.TextColor3 = Color3.new(0, 1, 0)
	elseif keyOff == false then
		keyOff = true
		KeybindsActive.Text = "Inactive"
		KeybindsActive.TextColor3 = Color3.new(1, 0, 1)
	end
end)

Show.Name = "Show"
Show.Parent = MM2
Show.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Show.BorderColor3 = Color3.new(0, 0.607843, 1)
Show.BorderSizePixel = 5
Show.Position = UDim2.new(0, 0, 0.85799998, 0)
Show.Size = UDim2.new(0.08, 0, 0.04, 0)
Show.ZIndex = 4
Show.Font = Enum.Font.SciFi
Show.FontSize = Enum.FontSize.Size24
Show.Text = "Show ["..string.upper(hideshowguikey).."]"
Show.TextColor3 = Color3.new(0, 0.333333, 1)
Show.TextSize = 20
Show.TextWrapped = true
Show.Visible = false

Hide.Name = "Hide"
Hide.Parent = Main
Hide.BackgroundColor3 = Color3.new(0.188235, 0.188235, 0.188235)
Hide.BorderColor3 = Color3.new(0, 0.607843, 1)
Hide.BorderSizePixel = 5
Hide.Position = UDim2.new(0, 0, 1.415, 0)
Hide.Size = UDim2.new(1.005, 0, 0.08, 0)
Hide.ZIndex = 4
Hide.Font = Enum.Font.SciFi
Hide.FontSize = Enum.FontSize.Size24
Hide.Text = "Hide ["..string.upper(hideshowguikey).."]"
Hide.TextColor3 = Color3.new(0, 0.333333, 1)
Hide.TextSize = 20
Hide.TextWrapped = true

Hide.MouseButton1Down:connect(function(x, y)
	if showvar == true then
		showvar = false
		Main.Visible = false
		Show.Visible = true
		if printvar == true then
			print("Hidden")
		end
	end
end)

Show.MouseButton1Down:connect(function(x, y)
	if showvar == false then
		showvar = true
		Show.Visible = false
		Main.Visible = true
		if printvar == true then
			print("Shown")
		end
	end
end)

inputcode.InputBegan:connect(function(input)
	if input.KeyCode == Enum.KeyCode.LeftControl then
		if keyOff == true then
			keyOff = false
			KeybindsActive.Text = "Active"
			KeybindsActive.TextColor3 = Color3.new(0, 1, 0)
		elseif keyOff == false then
			keyOff = true
			KeybindsActive.Text = "Inactive"
			KeybindsActive.TextColor3 = Color3.new(1, 0, 1)
		end
	end
end)

mouse.keyDown:connect(function(key)
	if keyOff == false then
		if key == coinkey then --Coin Grabber
			coingrabberfunc()
		elseif key == MSkey then --Murderer/Sheriff Esp On
			murderer = "None"
			sheriff = "None"
			Clear()
			findmurderer()
			findsheriff()
			if printvar == true then
				print("Murderer/Sheriff")
			end
			MSESPActive.Text = "Active"
			MSESPActive.TextColor3 = Color3.new(0, 1, 0)
			PlayersEspActive.Text = "Inactive"
			PlayersEspActive.TextColor3 = Color3.new(1, 0, 1)
			EspOffActive.Text = "Inactive"
			EspOffActive.TextColor3 = Color3.new(1, 0, 1)
		elseif key == playerskey then --Player Esp On
			Clear()
			MSESPActive.Text = "Inactive"
			MSESPActive.TextColor3 = Color3.new(1, 0, 1)
			PlayersEspActive.Text = "Active"
			PlayersEspActive.TextColor3 = Color3.new(0, 1, 0)
			EspOffActive.Text = "Inactive"
			EspOffActive.TextColor3 = Color3.new(1, 0, 1)
			findplayers()
			if printvar == true then
				print("Players")
			end
		elseif key == espoffkey then --Esp off
			Clear()
			if printvar == true then
				print("Esp Disabled")
			end
			MSESPActive.Text = "Inactive"
			MSESPActive.TextColor3 = Color3.new(1, 0, 1)
			PlayersEspActive.Text = "Inactive"
			PlayersEspActive.TextColor3 = Color3.new(1, 0, 1)
			EspOffActive.Text = "Active"
			EspOffActive.TextColor3 = Color3.new(0, 1, 0)
		elseif key == flykey then --Fly
			if flyvar == false then
				sFLY()
				flyvar = true
				FlyActive.Text = "Active"
				FlyActive.TextColor3 = Color3.new(0, 1, 0)
			elseif flyvar == true then
				flyvar = false
				NOFLY()
				FlyActive.Text = "Inactive"
				FlyActive.TextColor3 = Color3.new(1, 0, 1)
			end
		elseif key == noclipkey then --Noclip toggle
			if NClip == false then
				NClip = true
				if printvar == true then
					print("Noclip Enabled")
				end
				NoclipActive.Text = "Active"
				NoclipActive.TextColor3 = Color3.new(0, 1, 0)
			elseif NClip == true then
				NClip = false
				if printvar == true then
					print("Noclip Disabled")
				end
				NoclipActive.Text = "Inactive"
				NoclipActive.TextColor3 = Color3.new(1, 0, 1)
			end
		elseif key == godmodekey then --Godmode
			if godmodevar == false then
				godmodevar = true
				godmodefunc()
				GodModeActive.Text = "Active"
				GodModeActive.TextColor3 = Color3.new(0, 1, 0)
			end
		elseif key == xrayonkey then --Xray On
			GuiXrayOnActive.Text = "Active"
			GuiXrayOnActive.TextColor3 = Color3.new(0, 1, 0)
			GuiXrayOffActive.Text = "Inactive"
			GuiXrayOffActive.TextColor3 = Color3.new(1, 0, 1)
			XrayOn(obj)
		elseif key == xrayoffkey then --Xray Off
			GuiXrayOnActive.Text = "Inactive"
			GuiXrayOnActive.TextColor3 = Color3.new(1, 0, 1)
			GuiXrayOffActive.Text = "Active"
			GuiXrayOffActive.TextColor3 = Color3.new(0, 1, 0)
			XrayOff(obj)
		elseif key == bringgunkey then --Teleport Gun to You
			if game.Workspace.GunDrop.CFrame ~= nil then
				game.Workspace.GunDrop.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
			else
				if printvar == true then
					print("Gun not currently dropped")
				end
			end
		elseif key == hideshowguikey then --Show/Hide Gui
			if showvar == false then
				showvar = true
				Show.Visible = false
				Main.Visible = true
				if printvar == true then
					print("Shown")
				end
			elseif showvar == true then
				showvar = false
				Main.Visible = false
				Show.Visible = true
				if printvar == true then
					print("Hidden")
				end
			end
		end
	end
end)
end

local plrs = game:GetService("Players")
local TeamBased = true ; local teambasedswitch = "o"
local presskeytoaim = true; local aimkey = "e"
local raycast = false

local espupdatetime = 5; autoesp = false



local lockaim = true; local lockangle = 5



--function findwat(folder, what)
--	for i, smth in pairs(folder:GetChildren()) do
--		if string.find(string.lower(tostring(smth)), string.lower(what)) then
--			return smth
--		end
--	end
--end
--
--local plrs = findwat(game, "Players")




local Gui = Instance.new("ScreenGui")
local Move = Instance.new("Frame")
local Main = Instance.new("Frame")
local EspStatus = Instance.new("TextLabel")
local st1 = Instance.new("TextLabel")
local st1_2 = Instance.new("TextLabel")
local st1_3 = Instance.new("TextLabel")
local Name = Instance.new("TextLabel")
--Properties:
Gui.Name = "Gui"
Gui.Parent = plrs.LocalPlayer:WaitForChild("PlayerGui")

Move.Name = "Move"
Move.Parent = Gui
Move.BackgroundColor3 = Color3.new(0.545098, 0, 0)
Move.BackgroundTransparency = 1
Move.BorderSizePixel = 0
Move.Draggable = true
Move.Position = UDim2.new(0.005, 0, -0.15, 0)
Move.Size = UDim2.new(0.28141585, 0, 0.0320388414, 0)

Main.Name = "Main"
Main.Parent = Move
Main.BackgroundColor3 = Color3.new(1, 1, 1)
Main.Position = UDim2.new(0, 0, 0, 0)
Main.Size = UDim2.new(0, 0, 0, 0)
Main.Style = Enum.FrameStyle.RobloxSquare

EspStatus.Name = "EspStatus"
EspStatus.Parent = Main
EspStatus.BackgroundColor3 = Color3.new(1, 1, 1)
EspStatus.BackgroundTransparency = 1
EspStatus.Position = UDim2.new(0, 0, 0.300000012, 0)
EspStatus.Size = UDim2.new(1, 0, 0.162, 0)
EspStatus.Font = Enum.Font.ArialBold
EspStatus.Text = "Press O to change team based mode"
EspStatus.TextColor3 = Color3.new(0.6, 0.196078, 0.8)
EspStatus.TextScaled = true
EspStatus.TextWrapped = true

st1.Name = "st1"
st1.Parent = Main
st1.BackgroundColor3 = Color3.new(1, 1, 1)
st1.BackgroundTransparency = 1
st1.Position = UDim2.new(0.271787882, 0, 0, 0)
st1.Size = UDim2.new(0.728211343, 0, 0.161862016, 0)
st1.Font = Enum.Font.ArialBold
st1.Text = ""
st1.TextColor3 = Color3.new(0.0784314, 0.541176, 0)
st1.TextScaled = true
st1.TextSize = 14
st1.TextWrapped = true

-- Scripts:


local plrsforaim = {}

local lplr = game:GetService("Players").LocalPlayer
Move.Draggable = true
Gui.ResetOnSpawn = false
Gui.Name = "Chat"
Gui.DisplayOrder = 999

	Gui.Parent = plrs.LocalPlayer.PlayerGui


f = {}
local espforlder

f.addesp = function()
	--print("ESP ran")
	if espforlder then
	else
		espforlder = Instance.new("Folder")
		espforlder.Parent = game.Workspace.CurrentCamera
	end
	for i, v in pairs(espforlder:GetChildren()) do
		v:Destroy()
	end
	for _, plr in pairs(plrs:GetChildren()) do
		if plr.Character and plr.Character.Humanoid.Health > 0 and plr.Name ~= lplr.Name then
			if TeamBased == true then
				if plr.Team.Name ~= plrs.LocalPlayer.Team.Name  then
					local e = espforlder:FindFirstChild(plr.Name)
					if not e then
						--print("Added esp for team based")
						local bill = Instance.new("BillboardGui", espforlder)
						bill.Name = plr.Name
						bill.AlwaysOnTop = true
						bill.Size = UDim2.new(1,0,1,0)
						bill.Adornee = plr.Character.Head
						local Frame = Instance.new('Frame',bill)
						Frame.Active = true
						Frame.BackgroundColor3 = Color3.new(0.541176, 0.168627, 0.886275)
						Frame.BackgroundTransparency = 0
						Frame.BorderSizePixel = 0
						Frame.AnchorPoint = Vector2.new(.5, .5)
						Frame.Position = UDim2.new (0.5,0,0.5,0)
						Frame.Size = UDim2.new (1,0,1,0)
						Frame.Rotation = 0
						plr.Character.Humanoid.Died:Connect(function()
							bill:Destroy()
						end)
					end
				end
			else
				local e = espforlder:FindFirstChild(plr.Name)
				if not e then
					--print("Added esp")
					local bill = Instance.new("BillboardGui", espforlder)
					bill.Name = plr.Name
					bill.AlwaysOnTop = true
					bill.Size = UDim2.new(1,0,1,0)
					bill.Adornee = plr.Character.Head
					local Frame = Instance.new('Frame',bill)
					Frame.Active = true
					Frame.BackgroundColor3 = Color3.new(0.541176, 0.168627, 0.886275)
					Frame.BackgroundTransparency = 0
					Frame.BorderSizePixel = 0
					Frame.AnchorPoint = Vector2.new(.5, .5)
					Frame.Position = UDim2.new (0.5,0,0.5,0)
					Frame.Size = UDim2.new (1,0,1,0)
					Frame.Rotation = 0
					plr.Character.Humanoid.Died:Connect(function()
						bill:Destroy()
					end)
				end
			end
			
			
		end
	end
end
local cam = game.Workspace.CurrentCamera

local mouse = lplr:GetMouse()
local switch = false
local key = "k"
local aimatpart = nil
mouse.KeyDown:Connect(function(a)
	if a == "t" then
		print("worked1")
		f.addesp()
	elseif a == "u" then
		if raycast == true then
			raycast = false
		else
			raycast = true
		end
	elseif a == "l" then
		if autoesp == false then
			autoesp = true
		else
			autoesp = false
		end
	end
	if a == "j" then
		if mouse.Target then
			mouse.Target:Destroy()
		end
	end
	if a == key then
		if switch == false then
			switch = true
		else
			switch = false
			if aimatpart ~= nil then
				aimatpart = nil
			end
		end
	elseif a == teambasedswitch then
		if TeamBased == true then
			TeamBased = false
			teambasedstatus.Text = tostring(TeamBased)
		else
			TeamBased = true
			teambasedstatus.Text = tostring(TeamBased)
		end
	elseif a == aimkey then
		if not aimatpart then
			local maxangle = math.rad(20)
			for i, plr in pairs(plrs:GetChildren()) do
				if plr.Name ~= lplr.Name and plr.Character and plr.Character.Head and plr.Character.Humanoid and plr.Character.Humanoid.Health > 1 then
					if TeamBased == true then
						if plr.Team.Name ~= lplr.Team.Name then
							local an = checkfov(plr.Character.Head)
							if an < maxangle then
								maxangle = an
								aimatpart = plr.Character.Head
							end
						end
					else
						local an = checkfov(plr.Character.Head)
							if an < maxangle then
								maxangle = an
								aimatpart = plr.Character.Head
							end
							print(plr)
					end
					plr.Character.Humanoid.Died:Connect(function()
						if aimatpart.Parent == plr.Character or aimatpart == nil then
							aimatpart = nil
						end
					end)
				end
			end
		else
			aimatpart = nil
		end
	end
end)

function getfovxyz (p0, p1, deg)
	local x1, y1, z1 = p0:ToOrientation()
	local cf = CFrame.new(p0.p, p1.p)
	local x2, y2, z2 = cf:ToOrientation()
	--local d = math.deg
	if deg then
		--return Vector3.new(d(x1-x2), d(y1-y2), d(z1-z2))
	else
		return Vector3.new((x1-x2), (y1-y2), (z1-z2))
	end
end

function getaimbotplrs()
	plrsforaim = {}
	for i, plr in pairs(plrs:GetChildren()) do
		if plr.Character and plr.Character.Humanoid and plr.Character.Humanoid.Health > 0 and plr.Name ~= lplr.Name and plr.Character.Head then
			
			if TeamBased == true then
				if plr.Team.Name ~= lplr.Team.Name then
					local cf = CFrame.new(game.Workspace.CurrentCamera.CFrame.p, plr.Character.Head.CFrame.p)
					local r = Ray.new(cf, cf.LookVector * 10000)
					local ign = {}
					for i, v in pairs(plrs.LocalPlayer.Character:GetChildren()) do
						if v:IsA("BasePart") then
							table.insert(ign , v)
						end
					end
					local obj = game.Workspace:FindPartOnRayWithIgnoreList(r, ign)
					if obj.Parent == plr.Character and obj.Parent ~= lplr.Character then
						table.insert(plrsforaim, obj)
					end
				end
			else
				local cf = CFrame.new(game.Workspace.CurrentCamera.CFrame.p, plr.Character.Head.CFrame.p)
				local r = Ray.new(cf, cf.LookVector * 10000)
				local ign = {}
				for i, v in pairs(plrs.LocalPlayer.Character:GetChildren()) do
					if v:IsA("BasePart") then
						table.insert(ign , v)
					end
				end
				local obj = game.Workspace:FindPartOnRayWithIgnoreList(r, ign)
				if obj.Parent == plr.Character and obj.Parent ~= lplr.Character then
					table.insert(plrsforaim, obj)
				end
			end
			
			
		end
	end
end

function aimat(part)
	cam.CFrame = CFrame.new(cam.CFrame.p, part.CFrame.p)
end
function checkfov (part)
	local fov = getfovxyz(game.Workspace.CurrentCamera.CFrame, part.CFrame)
	local angle = math.abs(fov.X) + math.abs(fov.Y)
	return angle
end

game:GetService("RunService").RenderStepped:Connect(function()
	if aimatpart then
		aimat(aimatpart)
		if aimatpart.Parent == plrs.LocalPlayer.Character then
			aimatpart = nil
		end
	end
	
	
--	if switch == true then
--		local maxangle = 99999
--		
--		--print("Loop")
--		if true and raycast == false then
--			for i, plr in pairs(plrs:GetChildren()) do
--				if plr.Name ~= lplr.Name and plr.Character and plr.Character.Head and plr.Character.Humanoid and plr.Character.Humanoid.Health > 1 then
--					if TeamBased then
--						if plr.Team.Name ~= lplr.Team.Name or plr.Team.TeamColor ~= lplr.Team.TeamColor then
--							local an = checkfov(plr.Character.Head)
--							if an < maxangle then
--								maxangle = an
--								aimatpart = plr.Character.Head
--								if an < lockangle then
--									break
--								end
--							end
--						end
--					else
--						local an = checkfov(plr.Character.Head)
--							if an < maxangle then
--								maxangle = an
--								aimatpart = plr.Character.Head
--								if an < lockangle then
--									break
--								end
--							end
--					end
--					
--					
--					
--					
--				end
--			end
--		elseif raycast == true then
--			
--		end
		
		if raycast == true and switch == false and not aimatpart then
			getaimbotplrs()
			aimatpart = nil
			local maxangle = 999
			for i, v in ipairs(plrsforaim) do
				if v.Parent ~= lplr.Character then
					local an = checkfov(v)
					if an < maxangle and v ~= lplr.Character.Head then
						maxangle = an
						aimatpart = v
						print(v:GetFullName())
						v.Parent.Humanoid.Died:connect(function()
							aimatpart = nil
						end)
					end
				end
			end
		
	end
end)
delay(0, function()
	while wait(espupdatetime) do
		if autoesp == true then
			pcall(function()
			f.addesp()
			end)
		end
	end
end)
warn("loaded")
   end,
})

local Toggle = MainTab:CreateToggle({
   Name = "Fly E ",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        epeat wait() 
    until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
local mouse = game.Players.LocalPlayer:GetMouse() 
repeat wait() until mouse
local plr = game.Players.LocalPlayer 
local torso = plr.Character.Torso 
local flying = false
local deb = true 
local ctrl = {f = 0, b = 0, l = 0, r = 0} 
local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
local maxspeed = 50 
local speed = 0 
 
function Fly() 
local bg = Instance.new("BodyGyro", torso) 
bg.P = 9e4 
bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
bg.cframe = torso.CFrame 
local bv = Instance.new("BodyVelocity", torso) 
bv.velocity = Vector3.new(0,0.1,0) 
bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
repeat wait() 
plr.Character.Humanoid.PlatformStand = true 
if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then 
speed = speed+.5+(speed/maxspeed) 
if speed > maxspeed then 
speed = maxspeed 
end 
elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then 
speed = speed-1 
if speed < 0 then 
speed = 0 
end 
end 
if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then 
bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then 
bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
else 
bv.velocity = Vector3.new(0,0.1,0) 
end 
bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
until not flying 
ctrl = {f = 0, b = 0, l = 0, r = 0} 
lastctrl = {f = 0, b = 0, l = 0, r = 0} 
speed = 0 
bg:Destroy() 
bv:Destroy() 
plr.Character.Humanoid.PlatformStand = false 
end 
mouse.KeyDown:connect(function(key) 
if key:lower() == "e" then 
if flying then flying = false 
else 
flying = true 
Fly() 
end 
elseif key:lower() == "w" then 
ctrl.f = 1 
elseif key:lower() == "s" then 
ctrl.b = -1 
elseif key:lower() == "a" then 
ctrl.l = -1 
elseif key:lower() == "d" then 
ctrl.r = 1 
end 
end) 
mouse.KeyUp:connect(function(key) 
if key:lower() == "w" then 
ctrl.f = 0 
elseif key:lower() == "s" then 
ctrl.b = 0 
elseif key:lower() == "a" then 
ctrl.l = 0 
elseif key:lower() == "d" then 
ctrl.r = 0 
end 
end)
Fly()
   end,
})

local ScriptTab = Window:CreateTab("Scripts", nil) -- Title, Image

local Button = ScriptTab:CreateButton({
   Name = "Vynixu's MM2 Script",
   Callback = function()
        loadstring(game:GetObjects("rbxassetid://4001118261")[1].Source)()
   end,
})

local Button = ScriptTab:CreateButton({
   Name = "FE YEET GUI(Trollface Edition)",
   Callback = function()
        local lp = game:FindService("Players").LocalPlayer
 
local function gplr(String)
	local Found = {}
	local strl = String:lower()
	if strl == "all" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			table.insert(Found,v)
		end
	elseif strl == "others" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name ~= lp.Name then
				table.insert(Found,v)
			end
		end 
	elseif strl == "me" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name == lp.Name then
				table.insert(Found,v)
			end
		end 
	else
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name:lower():sub(1, #String) == String:lower() then
				table.insert(Found,v)
			end
		end 
	end
	return Found 
end
 
local function notif(str,dur)
	game:FindService("StarterGui"):SetCore("SendNotification", {
		Title = "yeet gui",
		Text = str,
		Icon = "rbxassetid://2005276185",
		Duration = dur or 3
	})
end
 
--// sds
 
local h = Instance.new("ScreenGui")
local Main = Instance.new("ImageLabel")
local Top = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local TextBox = Instance.new("TextBox")
local TextButton = Instance.new("TextButton")
 
h.Name = "h"
h.Parent = game:GetService("CoreGui")
h.ResetOnSpawn = false
 
Main.Name = "Main"
Main.Parent = h
Main.Active = true
Main.Draggable = true
Main.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Main.BorderSizePixel = 0
Main.Position = UDim2.new(0.174545452, 0, 0.459574461, 0)
Main.Size = UDim2.new(0, 454, 0, 218)
Main.Image = "rbxassetid://2005276185"
 
Top.Name = "Top"
Top.Parent = Main
Top.BackgroundColor3 = Color3.fromRGB(57, 57, 57)
Top.BorderSizePixel = 0
Top.Size = UDim2.new(0, 454, 0, 44)
 
Title.Name = "Title"
Title.Parent = Top
Title.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
Title.BorderSizePixel = 0
Title.Position = UDim2.new(0, 0, 0.295454562, 0)
Title.Size = UDim2.new(0, 454, 0, 30)
Title.Font = Enum.Font.SourceSans
Title.Text = "FE Yeet Gui (trollface edition)"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true
Title.TextSize = 14.000
Title.TextWrapped = true
 
TextBox.Parent = Main
TextBox.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
TextBox.BorderSizePixel = 0
TextBox.Position = UDim2.new(0.0704845786, 0, 0.270642221, 0)
TextBox.Size = UDim2.new(0, 388, 0, 62)
TextBox.Font = Enum.Font.SourceSans
TextBox.PlaceholderText = "Who do i destroy(can be shortened)"
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
TextBox.TextScaled = true
TextBox.TextSize = 14.000
TextBox.TextWrapped = true
 
TextButton.Parent = Main
TextButton.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.10352423, 0, 0.596330225, 0)
TextButton.Size = UDim2.new(0, 359, 0, 50)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "Cheese em'"
TextButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton.TextScaled = true
TextButton.TextSize = 14.000
TextButton.TextWrapped = true
 
TextButton.MouseButton1Click:Connect(function()
	local Target = gplr(TextBox.Text)
	if Target[1] then
		Target = Target[1]
 
		local Thrust = Instance.new('BodyThrust', lp.Character.HumanoidRootPart)
		Thrust.Force = Vector3.new(9999,9999,9999)
		Thrust.Name = "YeetForce"
		repeat
			lp.Character.HumanoidRootPart.CFrame = Target.Character.HumanoidRootPart.CFrame
			Thrust.Location = Target.Character.HumanoidRootPart.Position
			game:FindService("RunService").Heartbeat:wait()
		until not Target.Character:FindFirstChild("Head")
	else
		notif("Invalid player")
	end
end)
 
--//fsddfsdf
notif("Loaded successfully! Created by scuba#0001", 5)
   end,
})

local Toggle = MainTab:CreateToggle({
   Name = "X-Ray",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local XRay = game.Workspace.XRay
 
local UIS = game:GetService("UserInputService")
local Toggled = false
local Button = Player.PlayerGui:WaitForChild("MainFrame"):WaitForChild("ToggleButton")
local ValidKeyCode = {
    Enum.KeyCode.E
}
local ValidTransparency = {}
 
UIS.InputBegan:Connect(function(key, gameProcessedEvent)
    if not gameProcessedEvent then
        if not Toggled then
            for _, KEY in pairs(ValidKeyCode) do
                if key.KeyCode == KEY then
                    for partsIndex, parts in pairs(XRay:GetDescendants()) do
                        local success, err = pcall(function()
                            ValidTransparency["Part-"..parts.Name] = parts.Transparency
                            parts.Transparency = 0.5
                            Toggled = true
                        end)
                    end
                end
            end
        else
            for _, KEY in pairs(ValidKeyCode) do
                if key.KeyCode == KEY then
                    for partsIndex, parts in pairs(XRay:GetDescendants()) do
                        local success, err = pcall(function()
                            parts.Transparency = ValidTransparency["Part-"..parts.Name]
                            Toggled = false
                        end)
                    end
                end
            end
        end
    end
end)
 
Button.MouseButton1Click:Connect(function()
    if not Toggled then
        for _, KEY in pairs(ValidKeyCode) do
            for partsIndex, parts in pairs(XRay:GetDescendants()) do
                local success, err = pcall(function()
                    ValidTransparency["Part-"..parts.Name] = parts.Transparency
                    parts.Transparency = 0.5
                    Toggled = true
                end)
            end
        end
    else
        for _, KEY in pairs(ValidKeyCode) do
            for partsIndex, parts in pairs(XRay:GetDescendants()) do
                local success, err = pcall(function()
                    parts.Transparency = ValidTransparency["Part-"..parts.Name]
                    Toggled = false
                end)
            end
        end
    end
end)
   end,
})

local Button = MainTab:CreateButton({
   Name = "Get all Emotes",
   Callback = function()
        game.Players.LocalPlayer.Chatted:Connect(function(msg)
if msg == "/e zen" then 
game.ReplicatedStorage.PlayEmote:Fire("zen")
end
if msg == "/e sit" then 
game.ReplicatedStorage.PlayEmote:Fire("sit")
end
if msg == "/e dab" then 
game.ReplicatedStorage.PlayEmote:Fire("dab")
end
if msg == "/e zombie" then 
game.ReplicatedStorage.PlayEmote:Fire("zombie")
end
if msg == "/e floss" then 
game.ReplicatedStorage.PlayEmote:Fire("floss")
end
if msg == "/e ninja" then 
game.ReplicatedStorage.PlayEmote:Fire("ninja")
end
if msg == "/e headless" then 
game.ReplicatedStorage.PlayEmote:Fire("headless")
end
end)

   end,
})

local Button = MainTab:CreateButton({
   Name = "Crash Server",
   Callback = function()
        game.StarterGui:SetCore("SendNotification", {
    Title = "Subscribe To Mr Jim Ph";
    Text = "Subscribe For More Scripts"; -- what the text says (ofc)
    Duration = 60;
})
 
for _,s in 
pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
    if s:IsA("Motor6D") and s.Name ~= "Neck" then
        local fard = s.Parent
        s:Destroy()
        fard.CFrame = CFrame.new(9e9 * _,9e9* _,9e9*_)
        wait()
    end
end
   end,
})

local Toggle = MainTab:CreateToggle({
   Name = "silent aim",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        local localPlayer = game:GetService("Players").LocalPlayer
local mouse = localPlayer:GetMouse()
local teamCheck = true
 
local function getClosestPlayer()
    local closestPlayer = nil
    local shortestDistance = math.huge
 
    for i, v in pairs(game:GetService("Players"):GetPlayers()) do
        if v.Name ~= localPlayer.Name then
            if v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") and v.Character:FindFirstChild("Head") and teamCheck and v.Team ~= localPlayer.Team then
                local magnitude = (v.Character.HumanoidRootPart.Position - localPlayer.Character.HumanoidRootPart.Position).magnitude
 
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            elseif v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") and v.Character:FindFirstChild("Head") and not teamCheck then
                local magnitude = (v.Character.HumanoidRootPart.Position - localPlayer.Character.HumanoidRootPart.Position).magnitude
 
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end
    end
 
    return closestPlayer
end
 
game:GetService("UserInputService").InputBegan:Connect(function(input, onGui)
    if not onGui and input.KeyCode == Enum.KeyCode.T then
        teamCheck = not teamCheck
    end
end)
 
local mt = getrawmetatable(game)
local oldIndex = mt.__index
local oldNamecall = mt.__namecall
if setreadonly then setreadonly(mt, false) else make_writeable(mt, true) end
local nameCallMethod = getnamecallmethod or get_namecall_method
local newClose = newcclosure or function(f) return f end
 
mt.__index = newClose(function(t, k)
    if t == mouse and tostring(k) == "Hit" then
        if getClosestPlayer().Character and getClosestPlayer().Character:FindFirstChild("Head") then
            return getClosestPlayer().Character.Head.CFrame
        end
    end
 
    return oldIndex(t, k)
end)
 
mt.__namecall = newClose(function(...)
    local method = nameCallMethod()
    local args = {...}
 
    if tostring(method) == "FindPartOnRayWithIgnoreList" and getClosestPlayer() and getClosestPlayer().Character then
        return oldNamecall(args[1], args[2], {game:GetService("Workspace").IgnoreThese, game:GetService("Players").LocalPlayer.Character, game:GetService("Workspace").BuildStuff, game:GetService("Workspace").Map})
    end
 
    return oldNamecall(...)
end)
 
if setreadonly then setreadonly(mt, true) else make_writeable(mt, false) end
 
local oldFunc
 
oldFunc = hookfunction(workspace.FindPartOnRayWithIgnoreList, function(...)
	local args = {...}
 
	args[3] = {game:GetService("Workspace").IgnoreThese, game:GetService("Players").LocalPlayer.Character, game:GetService("Workspace").BuildStuff, game:GetService("Workspace").Map}
 
	return oldFunc(unpack(args))
end)
   end,
})

local PremiumTab = Window:CreateTab("Elite", nil) -- Title, Image

local Button = PremiumTab:CreateButton({
   Name = "Get All Items FAKE!!",
   Callback = function()
        ocal WeaponOwnRange = {
min=1,
max=5
}
local DataBase, PlayerData = getrenv()._G.Database, getrenv()._G.PlayerData
local newOwned = {}
for i,v in next, DataBase.Item do
newOwned[i] = math.random(WeaponOwnRange.min, WeaponOwnRange.max) -- newOwned[Weapon]: ItemCount
end
local PlayerWeapons = PlayerData.Weapons
game:GetService("RunService"):BindToRenderStep("InventoryUpdate", 0, function()
PlayerWeapons.Owned = newOwned
end)
game.Players.LocalPlayer.Character.Humanoid.Health = 0
   end,
})
