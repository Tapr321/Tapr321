-- Get the player's head position
local player = game.Players.LocalPlayer
local character = player.Character
local head = character:WaitForChild("Head")
local headPosition = head.Position

-- Calculate the direction to the player's head
local direction = (headPosition - workspace.CurrentCamera.CFrame.Position).Unit

-- Create a raycast to detect if there's an object in the way
local raycastParams = RaycastParams.new()
raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
raycastParams.FilterDescendantsInstances = {player.Character}

-- Perform the raycast
local raycastResult = workspace:Raycast(workspace.CurrentCamera.CFrame.Position, direction * 100, raycastParams)

-- Check if the raycast hit a part
if raycastResult then
    -- Check if the hit part is the player's head
    if raycastResult.Instance == head then
        -- Press the left mouse button to target the player's head
        mouse1press()
    end
end

