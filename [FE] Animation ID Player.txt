local playanother = false
local playing = false
local rtrnv;
local c;
local tbl3;
local v;
local anim;
local count;
local hhhh;
local asdf;
local s;
local animid;
local plr;
local char;
local cframe;
local torso;
local rs;
local ls;
local rh;
local lh;
local n;
local rj;
local rsc0;
local lsc0;
local rhc0;
local lhc0;
local rjc0;
local nc0;
local gc0;
local orsc0;
local olsc0;
local orhc0;
local olhc0;
local orjc0;
local onc0;
local count2;
local maxcount2;

local function getnext(tbl,number)
	c=100
	rtrnv=0
	for i,v in pairs(tbl) do
		if i>number and i-number<c then
			c=i-number
			rtrnv=i
		end
	end
	return(rtrnv)
end
local function wait2(tim)
	if tim<0.1 then
		game:GetService("RunService").Heartbeat:Wait()
	else
		for i=1,tim*40 do
			game:GetService("RunService").Heartbeat:Wait()
		end
	end
end
local function kftotbl(kf) -- Below this is literal pain..
	tbl3 = {}
	for i,v in pairs(kf:GetDescendants()) do
		if v:IsA("Pose") then
			tbl3[string.sub(v.Name,1,1)..string.sub(v.Name,#v.Name,#v.Name)] = v.CFrame
		end
	end
	return(tbl3)
end

local IDPlayer = Instance.new("ScreenGui")
local Frame = Instance.new("ImageLabel")
local TextLabel = Instance.new("TextLabel")
local AnimationID = Instance.new("ImageLabel")
local AnimationIDBox = Instance.new("TextBox")
local SoundID = Instance.new("ImageLabel")
local SoundIDBox = Instance.new("TextBox")
local PlayAnimation = Instance.new("ImageLabel")
local PlayButton = Instance.new("TextButton")

--Properties:

IDPlayer.Name = "IDPlayer"
IDPlayer.Parent = game:GetService("CoreGui")

Frame.Name = "Frame"
Frame.Parent = IDPlayer
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.BackgroundTransparency = 1.000
Frame.Active = true
Frame.Draggable = true
Frame.Position = UDim2.new(0.0248340052, 0, 0.4431988, 0)
Frame.Size = UDim2.new(0.216, 0, 0.293, 0)
Frame.Image = "rbxassetid://3570695787"
Frame.ImageColor3 = Color3.fromRGB(255, 0, 81)
Frame.ScaleType = Enum.ScaleType.Slice
Frame.SliceCenter = Rect.new(100, 100, 100, 100)
Frame.SliceScale = 0.120

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.115, 0, 0.046, 0)
TextLabel.Size = UDim2.new(0.787, 0, 0.179, 0)
TextLabel.Font = Enum.Font.Cartoon
TextLabel.Text = "Animation ID Player"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true

AnimationID.Name = "AnimationID"
AnimationID.Parent = Frame
AnimationID.Active = true
AnimationID.AnchorPoint = Vector2.new(0.5, 0.5)
AnimationID.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
AnimationID.BackgroundTransparency = 1.000
AnimationID.Position = UDim2.new(0.508173048, 0, 0.356446296, 0)
AnimationID.Selectable = true
AnimationID.Size = UDim2.new(0.786669195, 0, 0.191683754, 0)
AnimationID.Image = "rbxassetid://3570695787"
AnimationID.ScaleType = Enum.ScaleType.Slice
AnimationID.SliceCenter = Rect.new(100, 100, 100, 100)
AnimationID.SliceScale = 0.120

AnimationIDBox.Parent = AnimationID
AnimationIDBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
AnimationIDBox.BackgroundTransparency = 1.000
AnimationIDBox.BorderColor3 = Color3.fromRGB(0, 0, 0)
AnimationIDBox.BorderSizePixel = 0
AnimationIDBox.Position = UDim2.new(0.05, 0, 0, 0)
AnimationIDBox.Size = UDim2.new(0.911, 0, 1, 0)
AnimationIDBox.Font = Enum.Font.Cartoon
AnimationIDBox.PlaceholderText = "Animation ID Here"
AnimationIDBox.Text = ""
AnimationIDBox.TextColor3 = Color3.fromRGB(0, 0, 0)
AnimationIDBox.TextScaled = true
AnimationIDBox.TextSize = 14.000
AnimationIDBox.TextWrapped = true

SoundID.Name = "SoundID"
SoundID.Parent = Frame
SoundID.Active = true
SoundID.AnchorPoint = Vector2.new(0.5, 0.5)
SoundID.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SoundID.BackgroundTransparency = 1.000
SoundID.Position = UDim2.new(0.508173048, 0, 0.605001271, 0)
SoundID.Selectable = true
SoundID.Size = UDim2.new(0.786669195, 0, 0.191683769, 0)
SoundID.Image = "rbxassetid://3570695787"
SoundID.ScaleType = Enum.ScaleType.Slice
SoundID.SliceCenter = Rect.new(100, 100, 100, 100)
SoundID.SliceScale = 0.120

SoundIDBox.Parent = SoundID
SoundIDBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SoundIDBox.BackgroundTransparency = 1.000
SoundIDBox.BorderColor3 = Color3.fromRGB(0, 0, 0)
SoundIDBox.BorderSizePixel = 0
SoundIDBox.Position = UDim2.new(0.05, 0, 0, 0)
SoundIDBox.Size = UDim2.new(0.911, 0, 1, 0)
SoundIDBox.Font = Enum.Font.Cartoon
SoundIDBox.PlaceholderText = "Sound ID Here (Optional)"
SoundIDBox.Text = ""
SoundIDBox.TextColor3 = Color3.fromRGB(0, 0, 0)
SoundIDBox.TextScaled = true
SoundIDBox.TextSize = 14.000
SoundIDBox.TextWrapped = true

PlayAnimation.Name = "PlayAnimation"
PlayAnimation.Parent = Frame
PlayAnimation.Active = true
PlayAnimation.AnchorPoint = Vector2.new(0.5, 0.5)
PlayAnimation.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
PlayAnimation.BackgroundTransparency = 1.000
PlayAnimation.Position = UDim2.new(0.508172989, 0, 0.841664732, 0)
PlayAnimation.Selectable = true
PlayAnimation.Size = UDim2.new(0.786669135, 0, 0.192000017, 0)
PlayAnimation.Image = "rbxassetid://3570695787"
PlayAnimation.ImageColor3 = Color3.fromRGB(24, 24, 24)
PlayAnimation.ScaleType = Enum.ScaleType.Slice
PlayAnimation.SliceCenter = Rect.new(100, 100, 100, 100)
PlayAnimation.SliceScale = 0.120

PlayButton.Name = "PlayButton"
PlayButton.Parent = PlayAnimation
PlayButton.BackgroundColor3 = Color3.fromRGB(24, 24, 24)
PlayButton.BackgroundTransparency = 1.000
PlayButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
PlayButton.BorderSizePixel = 0
PlayButton.Position = UDim2.new(0.0424579717, 0, 0, 0)
PlayButton.Size = UDim2.new(0.917858839, 0, 1.00000012, 0)
PlayButton.Font = Enum.Font.Cartoon
PlayButton.Text = "Play Animation"
PlayButton.TextColor3 = Color3.fromRGB(255, 255, 255)
PlayButton.TextScaled = true
PlayButton.TextSize = 14.000
PlayButton.TextWrapped = true

PlayButton.MouseButton1Down:Connect(function()
	if AnimationIDBox.Text ~= "" then
		if playing == true then
			s:Destroy()
			playing = false
			playanother = true
		end
		wait()
		spawn(function()
			if playanother == true then
				playanother = false
			end
			playing = true
			s = Instance.new("Sound", game:GetService("Players").LocalPlayer.Character.Torso)
			if SoundIDBox.Text ~= "" then
				s.SoundId = "rbxassetid://"..SoundIDBox.Text
			end
			s.Looped = true
			s.Playing = true
			wait(.1) -- Do not change because changing it will break.
			animid="rbxassetid://".. AnimationIDBox.Text
			plr = game.Players.LocalPlayer
			char = game:GetService("Players").LocalPlayer.Character
			cframe = char.HumanoidRootPart.CFrame
			torso = game:GetService("Players").LocalPlayer.Character.Torso
			-----------------------------------------------------------
			rs = torso["Right Shoulder"] -- Just took this from another script(Faster).
			ls = torso["Left Shoulder"]
			rh = torso["Right Hip"]
			lh = torso["Left Hip"]
			n = torso["Neck"]
			rj = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart["RootJoint"]
			rsc0 = rs.C0
			lsc0 = ls.C0
			rhc0 = rh.C0
			lhc0 = lh.C0
			rjc0 = rj.C0
			nc0 = n.C0
			gc0 = CFrame.new()
			orsc0 = rs.C0
			olsc0 = ls.C0
			orhc0 = rh.C0
			olhc0 = lh.C0
			orjc0 = rj.C0
			onc0 = n.C0
			count2 = 100
			maxcount2=100
			-----------------------------------------------------------
			game:GetService("RunService").Heartbeat:Connect(function() -- Speed.
				if playanother == true then
					return nil
				else
					count2 = count2+1
					if count2<=maxcount2 then
						rs.Transform=rs.Transform:Lerp(rsc0,count2/maxcount2)
						ls.Transform=ls.Transform:Lerp(lsc0,count2/maxcount2)
						rh.Transform=rh.Transform:Lerp(rhc0,count2/maxcount2)
						lh.Transform=lh.Transform:Lerp(lhc0,count2/maxcount2)
						n.Transform=n.Transform:Lerp(nc0,count2/maxcount2)
						rj.Transform=rj.Transform:Lerp(rjc0,count2/maxcount2)
					end
				end
			end)
			-----------------------------------------------------------
			animid=game:GetObjects(animid)[1]
			anim={}
			for i,v in pairs(animid:GetChildren()) do
				if v:IsA("Keyframe") then
					anim[v.Time]=kftotbl(v)
				end
			end
			
			count = 0
			char=game:GetService("Players").LocalPlayer.Character
			hhhh=game:GetService("Players").LocalPlayer.Character.Humanoid.Animator
			hhhh.Parent = nil
			for _,v in pairs(char.Humanoid:GetPlayingAnimationTracks()) do
				v:Stop()
			end
			
			plr.CharacterRemoving:Connect(function()
				if playing == true then
					playing = false
				end
			end)
			
			while wait() do
				if playanother == true then
					break
				else
					for i,oasjdadlasdkadkldjkl in pairs(anim) do
						asdf=getnext(anim,count)
						v=anim[asdf]
						if v["Lg"] then
							lhc0 = v["Lg"]
						end
						if v["Rg"] then
							rhc0 = v["Rg"]
						end
						if v["Lm"] then
							lsc0 = v["Lm"]
						end
						if v["Rm"] then
							rsc0 = v["Rm"]
						end
						if v["To"] then
							rjc0 = v["To"]
						end
						if v["Hd"] then
							nc0 = v["Hd"]
						end
						count2=0
						maxcount2=asdf-count
						count=asdf
						wait(asdf-count)
						count2=maxcount2
						if v["Lg"] then
							char.Torso["Left Hip"].Transform = v["Lg"]
						end
						if v["Rg"] then
							char.Torso["Right Hip"].Transform = v["Rg"]
						end
						if v["Lm"] then
							char.Torso["Left Shoulder"].Transform = v["Lm"]
						end
						if v["Rm"] then
							char.Torso["Right Shoulder"].Transform = v["Rm"]
						end
						if v["To"] then
							char.HumanoidRootPart["RootJoint"].Transform = v["To"]
						end
						if v["Hd"] then
							char.Torso["Neck"].Transform = v["Hd"]
						end
					end
				end
			end
		end)
	end
end)