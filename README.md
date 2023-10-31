game:GetService("StarterGui"):SetCore("SendNotification",{
    Title = "quracik",
    Text = "Made By quracik",
    Icon = "rbxassetid://57254792";
Duration = 5;
})
--// ANTI-KICK
local mt = getrawmetatable(game)
local ncallsa = mt.__namecall
	setreadonly(mt, false)
	mt.__namecall = newcclosure(function(...)
		local args = {...}
		if not checkcaller() and getnamecallmethod() == "Kick" then
			return nil
		end
		return ncallsa(...)
	end)
	setreadonly(mt, true)
--//
	
--// ANTI-BAN
	local mmt = getrawmetatable(game)

local oldnamecall = mmt.__namecall

setreadonly(mmt, false)

mmt.__namecall = newcclosure(function(self, ...)
   local method = tostring(getnamecallmethod())
   local Args = {...}
   if not checkcaller() and method == "FireServer" and tostring(self) == "Banned" then
       return nil
   end
   
   return oldnamecall(self, ...)
end)

setreadonly(mmt, true)
	
	local gmt = getrawmetatable(game);
setreadonly(gmt, false);
local old_index = gmt.__index;
gmt.__index = function(a, b)
    if tostring(a) == "BannedA" or tostring(a) == "BannedB" or tostring(a) == "BannedC" or tostring(a) == "BannedD" then
        if tostring(b) == "Value" then
            return false;
        end
    end
    return old_index(a, b);
end

local bgmt = getrawmetatable(game);
setreadonly(bgmt, false);
local bold_index = bgmt.__index;
bgmt.__index = function(a, b)
    if tostring(a) == "BCount" then
        if tostring(b) == "Value" then
            return 0;
        end
    end
    return bold_index(a, b);
end

for i,BN in pairs(game:GetService("Workspace").FE.Settings:GetChildren()) do
    if BN.Name == "BName" then
    BN:Destroy()
end
end
--//

--// ANTI-WALKSPEED AND ANTI-JUMPPOWER
for i,b in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
    if b.Name == " " then
    b:Destroy()
end
end

for i,lc2 in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
    if lc2:IsA("LocalScript") and string.match(lc2.Name, "1") or string.match(lc2.Name, "2") or string.match(lc2.Name, "3") or string.match(lc2.Name, "4") or string.match(lc2.Name, "5") or string.match(lc2.Name, "6") or string.match(lc2.Name, "7") or string.match(lc2.Name, "8") or string.match(lc2.Name, "9") then
       lc2:Destroy()
    end
end

for i,lc in pairs(game.Players.LocalPlayer.PlayerGui.Start:GetChildren()) do
    if lc:IsA("LocalScript") and string.match(lc.Name, "1") or string.match(lc.Name, "2") or string.match(lc.Name, "3") or string.match(lc.Name, "4") or string.match(lc.Name, "5") or string.match(lc.Name, "6") or string.match(lc.Name, "7") or string.match(lc.Name, "8") or string.match(lc.Name, "9") then
       lc:Destroy()
    end
end

for i,c in pairs(game.Players.LocalPlayer.PlayerGui.Start:GetChildren()) do
    if c.Name == "CheckPlayerW" then
    c:Destroy()
end
end

for i,z in pairs(game.StarterGui.Start:GetChildren()) do
    if z.Name == "CheckPlayerW" then
    z:Destroy()
end
end

for _, v in pairs(game.StarterPlayer.StarterCharacterScripts:GetDescendants()) do
if v.Name == " " then
v:Destroy()
end
end

game.Players.LocalPlayer.CharacterAdded:Connect(function()
wait(0.5)
for i,char in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
    if char.Name == " " then
       char:Destroy()
    end
    end
end)
--//

--// ANTI-LAG (REMOVES LAG FROM GUI)
for i,nolag in pairs(game.StarterGui.Start:GetChildren()) do
if nolag.Name == "Gradient" then
nolag:Destroy()
end
end
for i,nolaglp in pairs(game.Players.LocalPlayer.PlayerGui.Start:GetChildren()) do
if nolaglp.Name == "Gradient" then
nolaglp:Destroy()
end
end
--//

--// FUNCTIONS, VARIABLES AND SCRIPTS //--
function GetPlayer(String)
	local Foundplr = {}
	local strl = String:lower()
	if strl == "all" then
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			table.insert(Foundplr,v)
		end
	elseif strl == "others" then
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			if v.Name ~= game.Players.LocalPlayer.Name then
				table.insert(Foundplr,v)
			end
		end
	elseif strl == "me" then
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			if v.Name == game.Players.LocalPlayer.Name then
				table.insert(Foundplr,v)
			end
		end
	else
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			if v.DisplayName:lower():sub(1, #String) == String:lower() or v.Name:lower():sub(1, #String) == String:lower() then
				table.insert(Foundplr,v)
			end
		end
	end
	return Foundplr
end

local DistanceReach = 0

local Player = game.Players.LocalPlayer
local RootPart = Player.Character.HumanoidRootPart

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Reach Qura W Pyth", "Synapse")

    -- MAIN
    local Main1 = Window:NewTab("Reach Pc and Mobile (by Qura)")
    local Main1Section = Main1:NewSection("Reach Pc and Mobile")

local RunSteppedMobile
local DistanceReachMobile = 0

Main1Section:NewButton("Enable Reach", "Enables Reach", function()
    RunSteppedMobile = game:GetService("RunService").RenderStepped:Connect(function()
if game.Players.LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then
if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - game.Workspace.TPSSystem.TPS.Position).Magnitude <= DistanceReachMobile then
if game.Lighting[game.Players.LocalPlayer.Name].PreferredFoot.Value == 1 then
firetouchinterest(game.Players.LocalPlayer.Character["Right Leg"], game.Workspace.TPSSystem.TPS, 0)
			firetouchinterest(game.Players.LocalPlayer.Character["Right Leg"], game.Workspace.TPSSystem.TPS, 1)
elseif game.Lighting[game.Players.LocalPlayer.Name].PreferredFoot.Value == 2 then
firetouchinterest(game.Players.LocalPlayer.Character["Left Leg"], game.Workspace.TPSSystem.TPS, 0)
			firetouchinterest(game.Players.LocalPlayer.Character["Left Leg"], game.Workspace.TPSSystem.TPS, 1)

end
end
end
if game.Players.LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R15 then
if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - game.Workspace.TPSSystem.TPS.Position).Magnitude <= DistanceReach then
if game.Lighting[game.Players.LocalPlayer.Name].PreferredFoot.Value == 1 then
firetouchinterest(game.Players.LocalPlayer.Character["RightLowerLeg"], game.Workspace.TPSSystem.TPS, 0)
			firetouchinterest(game.Players.LocalPlayer.Character["RightLowerLeg"], game.Workspace.TPSSystem.TPS, 1)
elseif game.Lighting[game.Players.LocalPlayer.Name].PreferredFoot.Value == 2 then
firetouchinterest(game.Players.LocalPlayer.Character["LeftLowerLeg"], game.Workspace.TPSSystem.TPS, 0)
			firetouchinterest(game.Players.LocalPlayer.Character["LeftLowerLeg"], game.Workspace.TPSSystem.TPS, 1)
			end
			end
			end
			end)
end)

Main1Section:NewButton("Disable Reach", "Disable Reach", function()
    RunSteppedMobile:Disconnect()
end)

Main1Section:NewButton("Reach - 0", "Setting Size Of Reach", function()
    DistanceReachMobile = 0
end)

Main1Section:NewButton("Reach - 2", "Setting Size Of Reach", function()
    DistanceReachMobile = 2
end)

Main1Section:NewButton("Reach - 3", "Setting Size Of Reach", function()
    DistanceReachMobile = 3
end)

Main1Section:NewButton("Reach - 5", "Setting Size Of Reach", function()
    DistanceReachMobile = 5
end)

Main1Section:NewButton("Reach - 8", "Setting Size Of Reach", function()
    DistanceReachMobile = 8
end)

Main1Section:NewButton("Reach - 10", "Setting Size Of Reach", function()
    DistanceReachMobile = 10
end)

Main1Section:NewButton("Reach - 15", "Setting Size Of Reach", function()
    DistanceReachMobile = 15
end)

Main1Section:NewButton("Reach - 20", "Setting Size Of Reach", function()
    DistanceReachMobile = 20
end)

Main1Section:NewButton("Reach - 25", "Setting Size Of Reach", function()
    DistanceReachMobile = 25
end)

Main1Section:NewButton("Reach - 30", "Setting Size Of Reach", function()
    DistanceReachMobile = 30
end)

Main1Section:NewButton("Reach - 40", "Setting Size Of Reach", function()
    DistanceReachMobile = 40
end)

Main1Section:NewButton("Reach - 50", "Setting Size Of Reach", function()
    DistanceReachMobile = 50
end)

Main1Section:NewButton("Reach - 60", "Setting Size Of Reach", function()
    DistanceReachMobile = 60
end)

Main1Section:NewButton("Reach - 70", "Setting Size Of Reach", function()
    DistanceReachMobile = 70
end)

Main1Section:NewButton("Reach - 80", "Setting Size Of Reach", function()
    DistanceReachMobile = 80
end)

Main1Section:NewButton("Reach - 90", "Setting Size Of Reach", function()
    DistanceReachMobile = 90
end)

Main1Section:NewButton("Reach - 100", "Setting Size Of Reach", function()
    DistanceReachMobile = 100
end)
