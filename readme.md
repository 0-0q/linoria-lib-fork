Linoria UI lib fork
(https://github.com/violin-suzutsuki/LinoriaLib)
```lua
Library.EspPreview:SetBoxVisibility(flags["esp_box"])
Library.EspPreview:SetBoxOutline(flags["esp_boxcolor"], 0)
Library.EspPreview:SetBoxFill(flags["esp_boxfillcolor"], flags["esp_boxfillalpha"])
Library.EspPreview:SetNameVisibility(flags["esp_name"])
Library.EspPreview:SetNameColor(flags["esp_namecolor"])
Library.EspPreview:SetHpBarVisibility(flags["esp_hpbar"])
Library.EspPreview:SetHpTextVisibility(flags["esp_hptext"])
Library.EspPreview:SetDistanceVisibility(flags["esp_distance"])
Library.EspPreview:SetDistanceColor(flags["esp_distancecolor"])
Library.EspPreview:SetDistanceSuffix(flags["esp_distancemethod"] == "Metric" and "m" or "std")
Library.EspPreview:SetFlagsVisibility(false)
```
```lua
local CurveBox = Tab:AddLeftGroupbox({ Name = 'Curve Editor', CurveBox = true })
```
```lua
local points = CurveBox:GetPoints()
-- Returns: {
--   { Index = 1, X = 0.0, Y = 0.5 },
--   { Index = 2, X = 0.125, Y = 0.6 },
--   { Index = 3, X = 0.25, Y = 0.4 },
--   ...
--   { Index = 9, X = 1.0, Y = 0.5 }
-- }
```
