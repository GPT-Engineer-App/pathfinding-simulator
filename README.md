# pathfinding-simulator

local player = game.Players.LocalPlayer
local character = player.Character
local userInputService = game:GetService("UserInputService")
local pathfindingService = game:GetService("PathfindingService")

-- Set up your attack keys (1, 2, 3, 4)
local attackKeys = {"One", "Two", "Three", "Four"}

-- Function to handle key presses
local function onKeyPress(input)
    if input.UserInputType == Enum.UserInputType.Keyboard then
        local key = input.KeyCode.Name
        if table.find(attackKeys, key) then
            -- Simulate attack action (e.g., play animation, deal damage)
            -- Implement your attack logic here
        end
    end
end

-- Connect key press event
userInputService.InputBegan:Connect(onKeyPress)

-- Function to enable pathfinding
local function enablePathfinding(targetPosition)
    local path = pathfindingService:CreatePath({
        AgentRadius = 2, -- Adjust as needed
        AgentHeight = 5,
        AgentCanJump = true,
        AgentJumpHeight = 10,
        AgentMaxSlope = 45,
        })
    path:ComputeAsync(character.HumanoidRootPart.Position, targetPosition)
    path:MoveTo(character.HumanoidRootPart)
end

-- Example: When an enemy is detected (within 30 studs), call enablePathfinding
local enemyPosition = Vector3.new(100, 0, 200) -- Replace with actual enemy position
enablePathfinding(enemyPosition)


## Collaborate with GPT Engineer

This is a [gptengineer.app](https://gptengineer.app)-synced repository 🌟🤖

Changes made via gptengineer.app will be committed to this repo.

If you clone this repo and push changes, you will have them reflected in the GPT Engineer UI.

## Tech stack

This project is built with React and Chakra UI.

- Vite
- React
- Chakra UI

## Setup

```sh
git clone https://github.com/GPT-Engineer-App/pathfinding-simulator.git
cd pathfinding-simulator
npm i
```

```sh
npm run dev
```

This will run a dev server with auto reloading and an instant preview.

## Requirements

- Node.js & npm - [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating)
