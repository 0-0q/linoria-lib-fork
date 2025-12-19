Linoria UI lib fork
(https://github.com/violin-suzutsuki/LinoriaLib)

## ESP Preview System

### Esp preview
```lua
local Tab = Window:AddTab({ Name = 'ESP', EspPreview = true })
```

### ESP box
```lua
Library.EspPreview:SetBoxVisibility(true)

Library.EspPreview:SetBoxFill(Color3.fromRGB(255, 0, 0), 0.5)

Library.EspPreview:SetBoxOutline(Color3.fromRGB(255, 255, 255), 0)
```

### Chams
```lua
Library.EspPreview:SetChamsFill(Color3.fromRGB(100, 150, 200), 0)

Library.EspPreview:SetChamsOutline(Color3.fromRGB(0, 0, 0), 0)
```

### Name label
```lua
Library.EspPreview:SetNameVisibility(true)

Library.EspPreview:SetNameColor(Color3.fromRGB(255, 255, 255))
```

### HP bar and Text
```lua
Library.EspPreview:SetHpBarVisibility(true)

Library.EspPreview:SetHpTextVisibility(true)
```

### Distance label
```lua
Library.EspPreview:SetDistanceVisibility(true)
```

### Flags Label
```lua
-- Show/hide flags text ("-> Flags")
Library.EspPreview:SetFlagsVisibility(true)

-- Change flags text color (no transparency)
Library.EspPreview:SetFlagsColor(Color3.fromRGB(0, 255, 0))
```

## Curve editor

### Creating a Curve Box
```lua
-- Create curve editor on left side
local CurveBox = Tab:AddLeftGroupbox({ Name = 'Curve Editor', CurveBox = true })

-- Create curve editor on right side
local CurveBox = Tab:AddRightGroupbox({ Name = 'Aimbot Curve', CurveBox = true })
```

### Getting curve data
```lua
-- Get all point positions
local points = CurveBox:GetPoints()
-- Returns: {
--   { Index = 1, X = 0.0, Y = 0.5 },
--   { Index = 2, X = 0.125, Y = 0.6 },
--   { Index = 3, X = 0.25, Y = 0.4 },
--   ...
--   { Index = 9, X = 1.0, Y = 0.5 }
-- }
```
