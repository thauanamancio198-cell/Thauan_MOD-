-- ts file was generated at discord.gg/25ms

local u1 = false
local u2 = false
local u3 = true
local u4 = false
local u5 = Color3.fromRGB(255, 50, 50)
local u6 = 100
local u7 = false
local u8 = 0.3
local u9 = true
local u10 = true
local u11 = false
local u12 = true
local u13 = false
local u14 = 500
local u15 = {}
local u16 = {}
local u17 = {}
local _Players = game:GetService('Players')
local _RunService = game:GetService('RunService')

game:GetService('UserInputService')

local _LocalPlayer = _Players.LocalPlayer
local _CurrentCamera = workspace.CurrentCamera
local _CoreGui = game:GetService('CoreGui')
local u23 = {}
local u24 = {}
local u25 = false
local _Circle = Drawing.new('Circle')

_Circle.Color = Color3.fromRGB(0, 255, 0)
_Circle.Thickness = 1
_Circle.Transparency = 0.5
_Circle.Filled = false
_Circle.Radius = u6
_Circle.Visible = u9
_Circle.Position = Vector2.new(_CurrentCamera.ViewportSize.X / 2, _CurrentCamera.ViewportSize.Y / 2)

local function u32(p27)
    if u23[p27] then
        local v28, v29, v30 = pairs(u23[p27])

        while true do
            local u31

            v30, u31 = v28(v29, v30)

            if v30 == nil then
                break
            end
            if u31 and u31.Remove then
                pcall(function()
                    u31:Remove()
                end)
            end
        end

        u23[p27] = nil
    end
end
local function u38(p33)
    u32(p33)

    if u15[p33] then
        releaseLockedPlayer(p33)
    end

    u16[p33] = nil
    u17[p33] = nil
    u15[p33] = nil

    if u24[p33] then
        local v34, v35, v36 = pairs(u24[p33])

        while true do
            local v37

            v36, v37 = v34(v35, v36)

            if v36 == nil then
                break
            end

            v37:Disconnect()
        end

        u24[p33] = nil
    end
end
local function u61()
    local v39, v40, v41 = pairs(u23)

    while true do
        local v42

        v41, v42 = v39(v40, v41)

        if v41 == nil then
            break
        end
        if not (v41 and v41.Parent) then
            u38(v41)
        end
    end

    if u3 then
        local v43 = not u25
        local v44, v45, v46 = pairs(u23)

        while true do
            local v47

            v46, v47 = v44(v45, v46)

            if v46 == nil then
                break
            end

            local v48

            if v46 then
                v48 = v46.Character
            else
                v48 = v46
            end

            local v49

            if v48 then
                v49 = v48:FindFirstChild('HumanoidRootPart')
            else
                v49 = v48
            end

            local v50

            if v48 then
                v50 = v48:FindFirstChild('Head')
            else
                v50 = v48
            end
            if v48 then
                v48 = v48:FindFirstChild('Humanoid')
            end
            if v49 and v50 then
                local v51 = (not u4 or v46.Team ~= _LocalPlayer.Team) and true or false
                local v52, v53 = _CurrentCamera:WorldToViewportPoint(v49.Position)

                if v53 and v51 then
                    local v54 = (_CurrentCamera:WorldToViewportPoint(v50.Position).Y - v52.Y) * 2
                    local v55 = v54 * 0.6

                    v47.box.PointA = Vector2.new(v52.X - v55 / 2, v52.Y - v54 / 2)
                    v47.box.PointB = Vector2.new(v52.X + v55 / 2, v52.Y - v54 / 2)
                    v47.box.PointC = Vector2.new(v52.X + v55 / 2, v52.Y + v54 / 2)
                    v47.box.PointD = Vector2.new(v52.X - v55 / 2, v52.Y + v54 / 2)
                    v47.box.Visible = v43
                    v47.name.Position = Vector2.new(v52.X, v52.Y - v54 / 2 - 15)
                    v47.name.Visible = v43

                    if v48 then
                        local v56 = math.floor(v48.Health) .. '/' .. math.floor(v48.MaxHealth)

                        if v47.health.Text ~= v56 then
                            v47.health.Text = v56
                        end

                        v47.health.Position = Vector2.new(v52.X, v52.Y + v54 / 2 + 5)
                        v47.health.Color = Color3.new(1 - v48.Health / v48.MaxHealth, v48.Health / v48.MaxHealth, 0)
                        v47.health.Visible = v43
                    else
                        v47.health.Visible = false
                    end
                elseif v47.box.Visible or (v47.name.Visible or v47.health.Visible) then
                    v47.box.Visible = false
                    v47.name.Visible = false
                    v47.health.Visible = false
                end
            elseif v47.box.Visible or (v47.name.Visible or v47.health.Visible) then
                v47.box.Visible = false
                v47.name.Visible = false
                v47.health.Visible = false
            end
        end
    else
        local v57, v58, v59 = pairs(u23)

        while true do
            local v60

            v59, v60 = v57(v58, v59)

            if v59 == nil then
                break
            end
            if v60.box.Visible or (v60.name.Visible or v60.health.Visible) then
                v60.box.Visible = false
                v60.name.Visible = false
                v60.health.Visible = false
            end
        end
    end
end
local function u66(p62)
    if p62 ~= _LocalPlayer then
        local _Quad = Drawing.new('Quad')

        _Quad.Visible = false
        _Quad.Color = u5
        _Quad.Thickness = 1
        _Quad.Filled = false

        local _Text = Drawing.new('Text')

        _Text.Visible = false
        _Text.Color = u5
        _Text.Size = 13
        _Text.Center = true
        _Text.Outline = true
        _Text.Text = p62.Name

        local _Text2 = Drawing.new('Text')

        _Text2.Visible = false
        _Text2.Color = Color3.new(0, 1, 0)
        _Text2.Size = 13
        _Text2.Center = true
        _Text2.Outline = true
        u23[p62] = {
            box = _Quad,
            name = _Text,
            health = _Text2,
        }
    end
end
local function v68(p67)
    if p67 ~= _LocalPlayer then
        u24[p67] = {}

        u66(p67)
        table.insert(u24[p67], p67.CharacterAdded:Connect(function()
            u66(p67)
        end))
    end
end
local function u73(p69)
    local v70, v71 = _CurrentCamera:WorldToViewportPoint(p69)

    if not v71 then
        return false
    end

    local v72 = Vector2.new(_CurrentCamera.ViewportSize.X / 2, _CurrentCamera.ViewportSize.Y / 2)

    return (Vector2.new(v70.X, v70.Y) - v72).Magnitude <= u6
end
local function u79(p74)
    if u10 then
        if p74 and p74.Character and p74.Character:FindFirstChild('Head') then
            local _Position = _CurrentCamera.CFrame.Position
            local _Position2 = p74.Character.Head.Position
            local v77 = RaycastParams.new()

            v77.FilterDescendantsInstances = {
                _LocalPlayer.Character,
            }
            v77.FilterType = Enum.RaycastFilterType.Blacklist

            local v78 = workspace:Raycast(_Position, (_Position2 - _Position).Unit * (_Position2 - _Position).Magnitude, v77)

            if v78 then
                return v78.Instance:FindFirstAncestorOfClass('Model') ~= p74.Character
            else
                return false
            end
        else
            return true
        end
    else
        return false
    end
end
local function u89()
    local _huge = math.huge
    local v81 = _Players
    local v82, v83, v84 = pairs(v81:GetPlayers())
    local v85 = nil

    while true do
        local v86

        v84, v86 = v82(v83, v84)

        if v84 == nil then
            break
        end
        if v86 ~= _LocalPlayer and v86.Character and (v86.Character:FindFirstChild('HumanoidRootPart') and (not u2 or v86.Team ~= _LocalPlayer.Team)) then
            local _HumanoidRootPart = v86.Character.HumanoidRootPart
            local _Magnitude = (_HumanoidRootPart.Position - _CurrentCamera.CFrame.Position).Magnitude

            if u73(_HumanoidRootPart.Position) and (_Magnitude < _huge and not (u10 and u79(v86))) then
                v85 = v86
                _huge = _Magnitude
            end
        end
    end

    return v85
end
local function u94(p90)
    if p90 and p90.Character then
        local v91 = p90.Character:FindFirstChild('Head') or p90.Character.HumanoidRootPart

        if v91 then
            if u7 then
                local _CFrame = _CurrentCamera.CFrame
                local v93 = v91.Position + Vector3.new(0, 0.5, 0)

                _CurrentCamera.CFrame = _CFrame:Lerp(CFrame.lookAt(_CFrame.Position, v93), u8)
            else
                _CurrentCamera.CFrame = CFrame.lookAt(_CurrentCamera.CFrame.Position, v91.Position)
            end
        end
    else
        return
    end
end
local function u101(p95, p96)
    if p95 and p95.Character then
        local v97, v98, v99 = ipairs(p95.Character:GetDescendants())

        while true do
            local v100

            v99, v100 = v97(v98, v99)

            if v99 == nil then
                break
            end
            if v100:IsA('BasePart') then
                if p96 < 1 then
                    if not u17[v100] then
                        u17[v100] = v100.Transparency
                    end

                    v100.Transparency = p96
                elseif u17[v100] then
                    v100.Transparency = u17[v100]
                    u17[v100] = nil
                end
            end
        end
    end
end
local function u104(p102)
    if p102 and p102.Character then
        local _HumanoidRootPart2 = p102.Character:FindFirstChild('HumanoidRootPart')

        if _HumanoidRootPart2 then
            if u16[p102] then
                _HumanoidRootPart2.CFrame = u16[p102]
            end

            _HumanoidRootPart2.Anchored = false

            u101(p102, 1)
        end

        u15[p102] = nil
        u16[p102] = nil
    end
end
local function u128()
    if not u11 or u25 then
        return
    end

    local _Position3 = _CurrentCamera.CFrame.Position
    local v106 = _Players
    local v107, v108, v109 = pairs(v106:GetPlayers())
    local v110 = {}

    while true do
        local v111

        v109, v111 = v107(v108, v109)

        if v109 == nil then
            break
        end
        if v111 ~= _LocalPlayer and v111.Character and (v111.Character:FindFirstChild('HumanoidRootPart') and (not u12 or v111.Team ~= _LocalPlayer.Team)) then
            local _Position4 = v111.Character.HumanoidRootPart.Position

            if (_Position4 - _Position3).Magnitude <= u14 and (u73(_Position4) and (u13 or not u79(v111))) then
                table.insert(v110, v111)
            end
        end
    end

    local v113, v114, v115 = pairs(u15)

    while true do
        local v116, _ = v113(v114, v115)

        if v116 == nil then
            local v117, v118, v119 = ipairs(v110)

            while true do
                local v120

                v119, v120 = v117(v118, v119)

                if v119 == nil then
                    break
                end
                if not u15[v120] then
                    u15[v120] = true
                    u16[v120] = v120.Character.HumanoidRootPart.CFrame

                    u101(v120, 0.5)

                    local _HumanoidRootPart3 = v120.Character.HumanoidRootPart
                    local v122 = _CurrentCamera.CFrame.Position + _CurrentCamera.CFrame.LookVector * 5

                    _HumanoidRootPart3.CFrame = CFrame.new(v122)
                    _HumanoidRootPart3.Anchored = true
                end
            end

            return
        end

        local v123, v124, v125 = ipairs(v110)

        v115 = v116

        local v126 = true

        while true do
            local v127

            v125, v127 = v123(v124, v125)

            if v125 == nil then
                break
            end
            if v127 == v116 then
                v126 = false

                break
            end
        end

        if v126 then
            u104(v116)
        end
    end
end

local _ScreenGui = Instance.new('ScreenGui')

_ScreenGui.Name = 'GHAimbotUI'
_ScreenGui.ResetOnSpawn = false
_ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local _Frame = Instance.new('Frame')

_Frame.Name = 'MainFrame'
_Frame.Parent = _ScreenGui
_Frame.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
_Frame.BackgroundTransparency = 0.2
_Frame.Size = UDim2.new(0, 250, 0, 350)
_Frame.Position = UDim2.new(0.5, -125, 0.5, -175)
_Frame.Visible = false
_Frame.Active = true
_Frame.Draggable = true

local _UICorner = Instance.new('UICorner')

_UICorner.CornerRadius = UDim.new(0, 8)
_UICorner.Parent = _Frame

local _ImageLabel = Instance.new('ImageLabel')

_ImageLabel.Name = 'DropShadow'
_ImageLabel.Parent = _Frame
_ImageLabel.BackgroundTransparency = 1
_ImageLabel.Size = UDim2.new(1, 6, 1, 6)
_ImageLabel.Position = UDim2.new(0, -3, 0, -3)
_ImageLabel.Image = 'rbxassetid://1316045217'
_ImageLabel.ImageColor3 = Color3.fromRGB(0, 0, 0)
_ImageLabel.ImageTransparency = 0.8
_ImageLabel.ScaleType = Enum.ScaleType.Slice
_ImageLabel.SliceCenter = Rect.new(10, 10, 118, 118)

local _TextLabel = Instance.new('TextLabel')

_TextLabel.Name = 'Header'
_TextLabel.Parent = _Frame
_TextLabel.Text = 'GH AIMBOT v4.2'
_TextLabel.Font = Enum.Font.GothamBold
_TextLabel.TextSize = 16
_TextLabel.TextColor3 = Color3.fromRGB(220, 220, 220)
_TextLabel.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
_TextLabel.Size = UDim2.new(1, 0, 0, 35)
_TextLabel.BorderSizePixel = 0

local _UICorner2 = Instance.new('UICorner')

_UICorner2.CornerRadius = UDim.new(0, 8)
_UICorner2.Parent = _TextLabel

local _Frame2 = Instance.new('Frame')

_Frame2.Name = 'TabButtons'
_Frame2.Parent = _Frame
_Frame2.BackgroundTransparency = 1
_Frame2.Size = UDim2.new(1, 0, 0, 30)
_Frame2.Position = UDim2.new(0, 0, 0, 35)

local function v141(p136, p137, p138)
    local _TextButton = Instance.new('TextButton')

    _TextButton.Name = p136
    _TextButton.Parent = _Frame2
    _TextButton.Text = p137
    _TextButton.Size = UDim2.new(0.5, 0, 1, 0)
    _TextButton.Position = UDim2.new(p138, 0, 0, 0)
    _TextButton.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    _TextButton.Font = Enum.Font.Gotham
    _TextButton.TextSize = 14
    _TextButton.TextColor3 = Color3.fromRGB(220, 220, 220)
    _TextButton.BorderSizePixel = 0
    _TextButton.AutoButtonColor = false

    local _UICorner3 = Instance.new('UICorner')

    _UICorner3.CornerRadius = UDim.new(0, 6)
    _UICorner3.Parent = _TextButton

    return _TextButton
end

local _AimbotTab = v141('AimbotTab', 'AIMBOT', 0)
local _TrollTab = v141('TrollTab', 'TROLL', 0.5)
local _Frame3 = Instance.new('Frame')

_Frame3.Name = 'AimbotFrame'
_Frame3.Parent = _Frame
_Frame3.BackgroundTransparency = 1
_Frame3.Size = UDim2.new(1, -10, 1, -75)
_Frame3.Position = UDim2.new(0, 5, 0, 70)
_Frame3.Visible = true

local _Frame4 = Instance.new('Frame')

_Frame4.Name = 'TrollFrame'
_Frame4.Parent = _Frame
_Frame4.BackgroundTransparency = 1
_Frame4.Size = UDim2.new(1, -10, 1, -75)
_Frame4.Position = UDim2.new(0, 5, 0, 70)
_Frame4.Visible = false

local function v154(p146, p147, p148, p149, p150)
    if not p150 then
        Color3.fromRGB(0, 255, 150)
    end

    local _TextButton2 = Instance.new('TextButton')

    _TextButton2.Name = p146
    _TextButton2.Parent = p147
    _TextButton2.Text = p149
    _TextButton2.Size = UDim2.new(1, 0, 0, 35)
    _TextButton2.Position = UDim2.new(0, 0, 0, p148)
    _TextButton2.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
    _TextButton2.Font = Enum.Font.Gotham
    _TextButton2.TextSize = 14
    _TextButton2.TextColor3 = Color3.fromRGB(220, 220, 220)
    _TextButton2.AutoButtonColor = false

    local _UICorner4 = Instance.new('UICorner')

    _UICorner4.CornerRadius = UDim.new(0, 6)
    _UICorner4.Parent = _TextButton2

    local _UIStroke = Instance.new('UIStroke')

    _UIStroke.Parent = _TextButton2
    _UIStroke.Color = Color3.fromRGB(60, 60, 65)
    _UIStroke.Thickness = 1

    _TextButton2.MouseEnter:Connect(function()
        _TextButton2.BackgroundColor3 = Color3.fromRGB(50, 50, 55)
    end)
    _TextButton2.MouseLeave:Connect(function()
        _TextButton2.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
    end)
    _TextButton2.MouseButton1Down:Connect(function()
        _TextButton2.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
    end)
    _TextButton2.MouseButton1Up:Connect(function()
        _TextButton2.BackgroundColor3 = Color3.fromRGB(50, 50, 55)
    end)

    return _TextButton2
end

local _AimbotButton = v154('AimbotButton', _Frame3, 0, 'AIMBOT: OFF')

_AimbotButton.MouseButton1Click:Connect(function()
    u1 = not u1
    u2 = false
    _AimbotButton.Text = u1 and 'AIMBOT: ON' or 'AIMBOT: OFF'
    _AimbotButton.TextColor3 = u1 and Color3.fromRGB(0, 255, 150) or Color3.fromRGB(220, 220, 220)
end)

local _TeamCheckButton = v154('TeamCheckButton', _Frame3, 40, 'TEAM CHECK: OFF')

_TeamCheckButton.MouseButton1Click:Connect(function()
    u2 = not u2
    u1 = false
    _TeamCheckButton.Text = u2 and 'TEAM CHECK: ON' or 'TEAM CHECK: OFF'
    _TeamCheckButton.TextColor3 = u2 and Color3.fromRGB(0, 255, 150) or Color3.fromRGB(220, 220, 220)
end)

local _SmoothAimButton = v154('SmoothAimButton', _Frame3, 80, 'SMOOTH AIM: OFF')

_SmoothAimButton.MouseButton1Click:Connect(function()
    u7 = not u7
    _SmoothAimButton.Text = u7 and 'SMOOTH AIM: ON' or 'SMOOTH AIM: OFF'
    _SmoothAimButton.TextColor3 = u7 and Color3.fromRGB(0, 255, 150) or Color3.fromRGB(220, 220, 220)
end)

local _IgnoreWallsButton = v154('IgnoreWallsButton', _Frame3, 120, 'IGNORAR PAREDES: ON')

_IgnoreWallsButton.MouseButton1Click:Connect(function()
    u10 = not u10
    _IgnoreWallsButton.Text = u10 and 'IGNORAR PAREDES: ON' or 'IGNORAR PAREDES: OFF'
    _IgnoreWallsButton.TextColor3 = u10 and Color3.fromRGB(0, 255, 150) or Color3.fromRGB(220, 220, 220)
end)

local _ESPButton = v154('ESPButton', _Frame3, 160, 'ESP: ON')

_ESPButton.MouseButton1Click:Connect(function()
    u3 = not u3
    _ESPButton.Text = u3 and 'ESP: ON' or 'ESP: OFF'
    _ESPButton.TextColor3 = u3 and Color3.fromRGB(0, 255, 150) or Color3.fromRGB(220, 220, 220)

    u61()
end)

local _ESPTeamCheckButton = v154('ESPTeamCheckButton', _Frame3, 200, 'ESP TEAM CHECK: OFF')

_ESPTeamCheckButton.MouseButton1Click:Connect(function()
    u4 = not u4
    _ESPTeamCheckButton.Text = u4 and 'ESP TEAM CHECK: ON' or 'ESP TEAM CHECK: OFF'
    _ESPTeamCheckButton.TextColor3 = u4 and Color3.fromRGB(0, 255, 150) or Color3.fromRGB(220, 220, 220)
end)

local _Frame5 = Instance.new('Frame')

_Frame5.Name = 'FOVControls'
_Frame5.Parent = _Frame3
_Frame5.BackgroundTransparency = 1
_Frame5.Size = UDim2.new(1, 0, 0, 35)
_Frame5.Position = UDim2.new(0, 0, 0, 240)

local _TextLabel2 = Instance.new('TextLabel')

_TextLabel2.Name = 'FOVLabel'
_TextLabel2.Parent = _Frame5
_TextLabel2.Text = 'FOV SIZE: ' .. u6
_TextLabel2.Font = Enum.Font.Gotham
_TextLabel2.TextSize = 14
_TextLabel2.TextColor3 = Color3.fromRGB(220, 220, 220)
_TextLabel2.BackgroundTransparency = 1
_TextLabel2.Size = UDim2.new(0.6, 0, 1, 0)
_TextLabel2.Position = UDim2.new(0.05, 0, 0, 0)
_TextLabel2.TextXAlignment = Enum.TextXAlignment.Left

local _FOVIncreaseButton = v154('FOVIncreaseButton', _Frame5, 0, '+')

_FOVIncreaseButton.Size = UDim2.new(0.15, 0, 1, 0)
_FOVIncreaseButton.Position = UDim2.new(0.7, 0, 0, 0)

_FOVIncreaseButton.MouseButton1Click:Connect(function()
    u6 = math.min(300, u6 + 10)
    _TextLabel2.Text = 'FOV SIZE: ' .. u6
    _Circle.Radius = u6
end)

local _FOVDecreaseButton = v154('FOVDecreaseButton', _Frame5, 0, '-')

_FOVDecreaseButton.Size = UDim2.new(0.15, 0, 1, 0)
_FOVDecreaseButton.Position = UDim2.new(0.85, 0, 0, 0)

_FOVDecreaseButton.MouseButton1Click:Connect(function()
    u6 = math.max(10, u6 - 10)
    _TextLabel2.Text = 'FOV SIZE: ' .. u6
    _Circle.Radius = u6
end)

local _ProAimButton = v154('ProAimButton', _Frame4, 0, 'PRO AIM: OFF', Color3.fromRGB(255, 100, 100))

_ProAimButton.MouseButton1Click:Connect(function()
    u11 = not u11
    _ProAimButton.Text = u11 and 'PRO AIM: ON' or 'PRO AIM: OFF'
    _ProAimButton.TextColor3 = u11 and Color3.fromRGB(255, 100, 100) or Color3.fromRGB(220, 220, 220)
end)

local _ProAimTeamCheck = v154('ProAimTeamCheck', _Frame4, 40, 'TEAM CHECK: ON', Color3.fromRGB(255, 100, 100))

_ProAimTeamCheck.MouseButton1Click:Connect(function()
    u12 = not u12
    _ProAimTeamCheck.Text = u12 and 'TEAM CHECK: ON' or 'TEAM CHECK: OFF'
    _ProAimTeamCheck.TextColor3 = u12 and Color3.fromRGB(255, 100, 100) or Color3.fromRGB(220, 220, 220)
end)

local _ThroughWallsButton = v154('ThroughWallsButton', _Frame4, 80, 'ATRAV\u{c9}S DA PAREDE: OFF', Color3.fromRGB(255, 100, 100))

_ThroughWallsButton.MouseButton1Click:Connect(function()
    u13 = not u13
    _ThroughWallsButton.Text = u13 and 'ATRAV\u{c9}S DA PAREDE: ON' or 'ATRAV\u{c9}S DA PAREDE: OFF'
    _ThroughWallsButton.TextColor3 = u13 and Color3.fromRGB(255, 100, 100) or Color3.fromRGB(220, 220, 220)
end)

local _Frame6 = Instance.new('Frame')

_Frame6.Name = 'DistanceControls'
_Frame6.Parent = _Frame4
_Frame6.BackgroundTransparency = 1
_Frame6.Size = UDim2.new(1, 0, 0, 35)
_Frame6.Position = UDim2.new(0, 0, 0, 120)

local _TextLabel3 = Instance.new('TextLabel')

_TextLabel3.Name = 'DistanceLabel'
_TextLabel3.Parent = _Frame6
_TextLabel3.Text = 'DIST\u{c2}NCIA: ' .. u14
_TextLabel3.Font = Enum.Font.Gotham
_TextLabel3.TextSize = 14
_TextLabel3.TextColor3 = Color3.fromRGB(220, 220, 220)
_TextLabel3.BackgroundTransparency = 1
_TextLabel3.Size = UDim2.new(0.6, 0, 1, 0)
_TextLabel3.Position = UDim2.new(0.05, 0, 0, 0)
_TextLabel3.TextXAlignment = Enum.TextXAlignment.Left

local _DistanceIncreaseButton = v154('DistanceIncreaseButton', _Frame6, 0, '+', Color3.fromRGB(255, 100, 100))

_DistanceIncreaseButton.Size = UDim2.new(0.15, 0, 1, 0)
_DistanceIncreaseButton.Position = UDim2.new(0.7, 0, 0, 0)

_DistanceIncreaseButton.MouseButton1Click:Connect(function()
    u14 = math.min(5000, u14 + 50)
    _TextLabel3.Text = 'DIST\u{c2}NCIA: ' .. u14
end)

local _DistanceDecreaseButton = v154('DistanceDecreaseButton', _Frame6, 0, '-', Color3.fromRGB(255, 100, 100))

_DistanceDecreaseButton.Size = UDim2.new(0.15, 0, 1, 0)
_DistanceDecreaseButton.Position = UDim2.new(0.85, 0, 0, 0)

_DistanceDecreaseButton.MouseButton1Click:Connect(function()
    u14 = math.max(50, u14 - 50)
    _TextLabel3.Text = 'DIST\u{c2}NCIA: ' .. u14
end)

local _CreditsButton = v154('CreditsButton', _Frame4, 170, 'Discord(click pra copiar o link)', Color3.fromRGB(100, 100, 255))

_CreditsButton.MouseButton1Click:Connect(function()
    setclipboard('https://discord.gg/897RZRBMBZ')

    _CreditsButton.Text = 'DISCORD COPIADO!'

    task.wait(1)

    _CreditsButton.Text = '@Thauan Hub..'
end)
_AimbotTab.MouseButton1Click:Connect(function()
    _Frame3.Visible = true
    _Frame4.Visible = false
    _AimbotTab.BackgroundColor3 = Color3.fromRGB(50, 50, 55)
    _TrollTab.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
end)
_TrollTab.MouseButton1Click:Connect(function()
    _Frame3.Visible = false
    _Frame4.Visible = true
    _TrollTab.BackgroundColor3 = Color3.fromRGB(50, 50, 55)
    _AimbotTab.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
end)

local _OpenButton = v154('OpenButton', _ScreenGui, 0, 'GH AIMBOT')

_OpenButton.Size = UDim2.new(0, 150, 0, 35)
_OpenButton.Position = UDim2.new(0, 20, 0, 20)

_OpenButton.MouseButton1Click:Connect(function()
    u25 = not _Frame.Visible
    _Frame.Visible = not _Frame.Visible
end)

_ScreenGui.Parent = _CoreGui

local _ScreenGui2 = Instance.new('ScreenGui')

_ScreenGui2.Name = 'StartupNotification'
_ScreenGui2.Parent = _CoreGui

local _TextLabel4 = Instance.new('TextLabel')

_TextLabel4.Size = UDim2.new(0, 200, 0, 40)
_TextLabel4.Position = UDim2.new(0.5, -100, 0.1, 0)
_TextLabel4.Text = 'GH AIMBOT v4.2 CARREGADO'
_TextLabel4.TextColor3 = Color3.fromRGB(0, 255, 150)
_TextLabel4.BackgroundTransparency = 1
_TextLabel4.Font = Enum.Font.GothamBold
_TextLabel4.TextSize = 18
_TextLabel4.TextTransparency = 0.3
_TextLabel4.Parent = _ScreenGui2

game:GetService('Debris'):AddItem(_ScreenGui2, 3)

local v176 = _Players
local v177, v178, v179 = ipairs(_Players.GetPlayers(v176))
local u180 = u6
local u181 = _CurrentCamera
local u182 = _Circle
local u183 = _Players
local u184 = u2
local u185 = u1
local u186 = u61
local u187 = u38
local u188 = u25
local v189 = _LocalPlayer

while true do
    local v190

    v179, v190 = v177(v178, v179)

    if v179 == nil then
        break
    end
    if v190 ~= v189 then
        v68(v190)
    end
end

u183.PlayerAdded:Connect(v68)
u183.PlayerRemoving:Connect(function(p191)
    u187(p191)
end)
_RunService:BindToRenderStep('GH_Aimbot_Main', Enum.RenderPriority.Input.Value, function()
    u182.Position = Vector2.new(u181.ViewportSize.X / 2, u181.ViewportSize.Y / 2)
    u182.Radius = u180
    u182.Visible = u9

    u186()

    local v192 = (not u188 and (u185 or u184) and true or false) and u89()

    if v192 then
        u94(v192)
    end
    if not u188 then
        u128()
    end
end)
game:BindToClose(function()
    local v193 = u183
    local v194, v195, v196 = pairs(v193:GetPlayers())

    while true do
        local v197

        v196, v197 = v194(v195, v196)

        if v196 == nil then
            break
        end

        u187(v197)
    end

    u182:Remove()
    _RunService:UnbindFromRenderStep('GH_Aimbot_Main')
end)
