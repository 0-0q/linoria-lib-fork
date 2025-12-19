Linoria UI lib fork
(https://github.com/violin-suzutsuki/LinoriaLib)

## ESP Preview System

### Creating an ESP Preview Tab
```lua
local Tab = Window:AddTab({ Name = 'ESP', EspPreview = true })
```
Set `EspPreview = true` to show the ESP preview window alongside your tab.

### ESP Box Control
```lua
-- Show/hide the ESP box
Library.EspPreview:SetBoxVisibility(true)

-- Set box fill color and transparency
Library.EspPreview:SetBoxFill(Color3.fromRGB(255, 0, 0), 0.5)

-- Set box outline color and transparency
Library.EspPreview:SetBoxOutline(Color3.fromRGB(255, 255, 255), 0)
```

### Chams (Character Model) Control
```lua
-- Set the fill color and transparency of body parts
Library.EspPreview:SetChamsFill(Color3.fromRGB(100, 150, 200), 0)

-- Set the outline color of body parts
Library.EspPreview:SetChamsOutline(Color3.fromRGB(0, 0, 0), 0)
```

### Name Label
```lua
-- Show/hide player name
Library.EspPreview:SetNameVisibility(true)

-- Change name color
Library.EspPreview:SetNameColor(Color3.fromRGB(255, 255, 255))
```

### HP Bar and Text
```lua
-- Show/hide HP bar
Library.EspPreview:SetHpBarVisibility(true)

-- Show/hide HP text ("<- Num.")
Library.EspPreview:SetHpTextVisibility(true)
```

### Distance Label
```lua
-- Show/hide distance text
Library.EspPreview:SetDistanceVisibility(true)
```

### Flags Label
```lua
-- Show/hide flags text ("-> Flags")
Library.EspPreview:SetFlagsVisibility(true)

-- Change flags text color (no transparency)
Library.EspPreview:SetFlagsColor(Color3.fromRGB(0, 255, 0))
```

## Curve Editor System

### Creating a Curve Box
```lua
-- Create curve editor on left side
local CurveBox = Tab:AddLeftGroupbox({ Name = 'Curve Editor', CurveBox = true })

-- Create curve editor on right side
local CurveBox = Tab:AddRightGroupbox({ Name = 'Aimbot Curve', CurveBox = true })
```

### Features
- **9 draggable points** aligned perfectly with grid lines (0 to 1)
- Points can only be dragged vertically (Y-axis)
- **Smooth pixel-based curve** connecting all points (160 pixels total)
- **8x8 grid** background for visual reference

### Getting Curve Data
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

-- Example: Use curve for aimbot smoothing
for i, point in ipairs(points) do
    print(string.format("Point %d: X=%.3f, Y=%.3f", point.Index, point.X, point.Y))
end
```

### Curve Point Data
- **X**: Horizontal position (0.0 to 1.0) - locked to grid lines
- **Y**: Vertical position (0.0 to 1.0) - draggable
  - 0.0 = top of grid
  - 0.5 = middle of grid
  - 1.0 = bottom of grid
- **Index**: Point number (1 to 9)

### Example Use Cases
```lua
-- Aimbot smooth curve based on distance
local function GetSmoothingValue(distance)
    local points = CurveBox:GetPoints()
    local normalizedDist = math.clamp(distance / maxDistance, 0, 1)
    
    -- Find which segment the distance falls into
    for i = 1, #points - 1 do
        local p1 = points[i]
        local p2 = points[i + 1]
        
        if normalizedDist >= p1.X and normalizedDist <= p2.X then
            -- Linear interpolation between points
            local t = (normalizedDist - p1.X) / (p2.X - p1.X)
            local smoothing = p1.Y + (p2.Y - p1.Y) * t
            return smoothing * maxSmoothing
        end
    end
    
    return 0
end

-- Apply to aimbot
local smoothing = GetSmoothingValue(targetDistance)
camera.CFrame = camera.CFrame:Lerp(targetCFrame, 1 / smoothing)
```

## UI Improvements

### Tab Buttons
- Tab buttons are now **wider** (+8px padding) for better readability

### Groupbox Titles
- All groupbox titles are now **centered** horizontally

## Notes

- All ESP preview elements use the library's accent color and theme system
- ESP preview automatically shows/hides when switching tabs
- Curve points have smooth dragging with real-time visual feedback
- All features are optimized for performance using RenderStepped updates
