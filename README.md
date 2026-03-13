local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

local TradeRequest = ReplicatedStorage:WaitForChild("TradeRequest")
local TradeAccept = ReplicatedStorage:WaitForChild("TradeAccept")

local function getBestBrainrot(player)

	local base = workspace:FindFirstChild(player.Name.."_Base")
	if not base then return nil end

	local best = nil
	local bestValue = 0

	for _,brainrot in pairs(base:GetChildren()) do
		if brainrot:FindFirstChild("Value") then
			local value = brainrot.Value.Value
			
			if value > bestValue then
				bestValue = value
				best = brainrot
			end
		end
	end

	return best
end


TradeAccept.OnServerEvent:Connect(function(player, requester)

	local bestBrainrot = getBestBrainrot(player)

	if bestBrainrot then
		print("Brainrot escolhido:", bestBrainrot.Name)

		-- colocar item na troca
	end

end)
