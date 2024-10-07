local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local workspace = game:GetService("Workspace")
local collectionService = game:GetService("CollectionService")

-- Função para coletar frutas
function collectFruits()
    for _, fruit in pairs(workspace:GetChildren()) do
        if fruit:IsA("Model") and collectionService:HasTag(fruit, "Fruit") then
            fruit:MoveTo(character.HumanoidRootPart.Position)
            wait(0.5) -- Espera um pouco antes de coletar a próxima fruta
        end
    end
end

-- Função para farmar inimigos
function farmEnemies()
    for _, enemy in pairs(workspace:GetChildren()) do
        if enemy:IsA("Model") and enemy:FindFirstChild("Humanoid") then
            character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
            wait(0.5) -- Aguarda para garantir que o ataque seja bem-sucedido
            -- Aqui você pode adicionar lógica para atacar o inimigo
        end
    end
end

-- Loop principal
while true do
    collectFruits()
    farmEnemies()
    wait(5) -- Espera um pouco antes de repetir
end
