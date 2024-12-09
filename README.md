-- Serviços
local UserInputService = game:GetService("UserInputService")
local GuiService = game:GetService("GuiService")

-- Variável para controlar o estado do ESP Hack
local espHackAtivado = false

-- Criar janela
local janela = Instance.new("Frame")
janela.Size = UDim2.new(0, 200, 0, 100)
janela.BackgroundTransparency = 1
janela.Name = "ESP Hack"
janela.Parent = game.StarterGui.ScreenGui

-- Criar botão
local botao = Instance.new("TextButton")
botao.Size = UDim2.new(0, 50, 0, 30)
botao.Text = "Ativar"
botao.Parent = janela

-- Função para ativar/desativar ESP Hack
local function toggleEspHack()
 if espHackAtivado then
 espHackAtivado = false
 botao.Text = "Ativar"
 print("ESP Hack desativado")
 else
 espHackAtivado = true
 botao.Text = "Desativar"
 print("ESP Hack ativado")
 end
end

-- Conectar botão
botao.MouseButton1Click:Connect(toggleEspHack)

-- Função para abrir/fechar janela
local function toggleJanela()
 if janela:IsDescendantOf(game.StarterGui.ScreenGui) then
 janela.Parent = nil
 else
 janela.Parent = game.StarterGui.ScreenGui
 end
end

-- Registrar tecla Insert
UserInputService.InputBegan:Connect(function(input)
 if input.KeyCode == Enum.KeyCode.Insert then
 toggleJanela()
 end
end)
