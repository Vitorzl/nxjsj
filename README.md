```lua
-- Script VitorTeste para Automação de Jogo

-- Função para coletar itens
function coletarItens()
    for _, item in pairs(workspace:GetChildren()) do
        if item:IsA("Part") and item.Name == "Fruta" then
            local sucesso, erro = pcall(function()
                item.Position = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
            end)
            if not sucesso then
                print("Erro ao coletar item: " .. erro)
            end
            wait(0.5) -- Aguarda um tempo para evitar sobrecarga
        end
    end
end

-- Função para atacar inimigos
function atacarInimigos()
    for _, inimigo in pairs(workspace:GetChildren()) do
        if inimigo:IsA("Model") and inimigo.Name == "Inimigo" then
            local jogador = game.Players.LocalPlayer
            local sucesso, erro = pcall(function()
                jogador.Character:FindFirstChild("Humanoid"):Attack(inimigo)
            end)
            if not sucesso then
                print("Erro ao atacar inimigo: " .. erro)
            end
            wait(1) -- Intervalo entre ataques
        end
    end
end

-- Função para teletransportar
function teletransportar(localizacao)
    local jogador = game.Players.LocalPlayer
    local sucesso, erro = pcall(function()
        jogador.Character.HumanoidRootPart.CFrame = localizacao
    end)
    if not sucesso then
        print("Erro ao teletransportar: " .. erro)
    end
end

-- Função principal para executar ações
function executarAcoes()
    while true do
        coletarItens()
        atacarInimigos()
        wait(2) -- Tempo de espera entre cada ciclo de ações
    end
end

-- Configurações do usuário
local configuracoes = {
    distanciaColeta = 10,
    intervaloAtaque = 1
}

-- Iniciar o script
executarAcoes()
```
