-- ========== SAEKO HUB - OBSIDIAN TEMPLATE (AZUL CIANO) ==========
-- Versão: 1.0 - Apenas UI para teste
-- Nenhuma função de jogo incluída

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/deividcomsono/Obsidian/main/Library.lua"))()

-- ========== TEMA AZUL CIANO ==========
Library.Scheme.AccentColor = Color3.fromRGB(0, 180, 255)      -- Azul ciano vibrante
Library.Scheme.BackgroundColor = Color3.fromRGB(10, 12, 18)   -- Fundo escuro azulado
Library.Scheme.MainColor = Color3.fromRGB(18, 22, 30)         -- Principal azul escuro
Library.Scheme.OutlineColor = Color3.fromRGB(35, 45, 60)      -- Contorno azulado
Library.Scheme.FontColor = Color3.fromRGB(220, 235, 255)      -- Fonte branco-azulado

-- Cores adicionais
Library.Scheme.RedColor = Color3.fromRGB(255, 70, 70)
Library.Scheme.DarkColor = Color3.fromRGB(5, 7, 12)
Library.Scheme.WhiteColor = Color3.fromRGB(255, 255, 255)

-- ========== CRIAR JANELA PRINCIPAL ==========
local Window = Library:CreateWindow({
    Title = "Saeko Hub",
    SubTitle = "Obsidian Edition - Cyan Theme",
    Size = UDim2.fromOffset(520, 600),
    Center = true,
    Resizable = true,
    GlobalSearch = true,
})

-- ========== ABAS ==========
local MainTab = Window:CreateTab("Main")
local ElementsTab = Window:CreateTab("Elementos")
local ConfigTab = Window:CreateTab("Configurações")
local InfoTab = Window:CreateTab("Info")

-- ========== MAIN TAB ==========
local MainSection = MainTab:CreateSection("Informações")

MainSection:AddLabel("Bem-vindo ao Saeko Hub")
MainSection:AddLabel("Tema: Azul Ciano")
MainSection:AddLabel("Status: Teste UI")

MainSection:AddDivider({ Text = "Ações", Margin = 10 })

MainSection:AddButton({
    Text = "Abrir Notificação",
    Func = function()
        Library:Notify({
            Title = "Saeko Hub",
            Description = "Notificação de teste!",
            Duration = 3,
        })
    end,
})

MainSection:AddButton({
    Text = "Fechar UI",
    Func = function()
        Window:Hide()
    end,
})

MainSection:AddButton({
    Text = "Mostrar UI",
    Func = function()
        Window:Show()
    end,
})

-- ========== ELEMENTOS TAB ==========
-- Seção: Toggles
local ToggleSection = ElementsTab:CreateSection("Toggles (Interruptores)")

local toggle1 = ToggleSection:AddToggle("Toggle1", {
    Text = "Opção 1",
    Default = false,
    Callback = function(value)
        print("[Toggle 1] Valor:", value)
        Library:Notify("Opção 1: " .. (value and "ON" or "OFF"))
    end,
})

local toggle2 = ToggleSection:AddToggle("Toggle2", {
    Text = "Opção 2 (Risco)",
    Default = false,
    Risky = true,
    Callback = function(value)
        print("[Toggle 2] Valor:", value)
    end,
})

local toggle3 = ToggleSection:AddToggle("Toggle3", {
    Text = "Opção 3 (Desativado)",
    Default = true,
    Disabled = true,
    Callback = function(value)
        print("[Toggle 3] Valor:", value)
    end,
})

-- Seção: Sliders
local SliderSection = ElementsTab:CreateSection("Sliders (Controles Deslizantes)")

SliderSection:AddSlider("Slider1", {
    Text = "Velocidade",
    Default = 50,
    Min = 0,
    Max = 100,
    Rounding = 0,
    Suffix = "%",
    Callback = function(value)
        print("[Slider 1] Valor:", value)
    end,
})

SliderSection:AddSlider("Slider2", {
    Text = "Distância",
    Default = 15,
    Min = 5,
    Max = 50,
    Rounding = 1,
    Suffix = " studs",
    Callback = function(value)
        print("[Slider 2] Valor:", value)
    end,
})

SliderSection:AddSlider("Slider3", {
    Text = "Delay (segundos)",
    Default = 0.5,
    Min = 0.1,
    Max = 5,
    Rounding = 2,
    Suffix = "s",
    Callback = function(value)
        print("[Slider 3] Valor:", value)
    end,
})

-- Seção: Dropdowns
local DropdownSection = ElementsTab:CreateSection("Dropdowns (Menus Suspensos)")

local dropdown1 = DropdownSection:AddDropdown("Dropdown1", {
    Text = "Selecione um modo",
    Values = {"Normal", "Agressivo", "Seguro", "Raid"},
    Default = "Normal",
    Callback = function(value)
        print("[Dropdown 1] Selecionado:", value)
        Library:Notify("Modo: " .. value)
    end,
})

local dropdown2 = DropdownSection:AddDropdown("Dropdown2", {
    Text = "Selecione um alvo",
    Values = {"Inimigos", "Bosses", "Players", "Todos"},
    Default = "Inimigos",
    Callback = function(value)
        print("[Dropdown 2] Selecionado:", value)
    end,
})

-- Seção: Inputs
local InputSection = ElementsTab:CreateSection("Inputs (Campos de Texto)")

InputSection:AddInput("Input1", {
    Text = "Nome do jogador",
    Placeholder = "Digite um nome...",
    Callback = function(value)
        print("[Input 1] Valor:", value)
    end,
})

InputSection:AddInput("Input2", {
    Text = "ID do item",
    Placeholder = "Apenas números",
    Numeric = true,
    Callback = function(value)
        print("[Input 2] Valor:", value)
    end,
})

InputSection:AddInput("Input3", {
    Text = "Delay personalizado",
    Placeholder = "0.5",
    Numeric = true,
    Finished = true,
    Callback = function(value)
        print("[Input 3] Valor final:", value)
    end,
})

-- Seção: Botões
local ButtonSection = ElementsTab:CreateSection("Botões")

ButtonSection:AddButton({
    Text = "Botão Normal",
    Func = function()
        print("[Botão] Clicado!")
        Library:Notify("Botão clicado!")
    end,
})

ButtonSection:AddButton({
    Text = "Botão de Risco (Vermelho)",
    Risky = true,
    Func = function()
        print("[Botão de Risco] Ação perigosa!")
        Library:Notify("Ação de risco executada!")
    end,
})

ButtonSection:AddButton({
    Text = "Botão com Duplo Clique",
    DoubleClick = true,
    Func = function()
        print("[Botão] Confirmado!")
        Library:Notify("Ação confirmada!")
    end,
})

-- Seção: Labels
local LabelSection = ElementsTab:CreateSection("Labels (Textos Informativos)")

local dynamicLabel = LabelSection:AddLabel("Valor atual: Nenhum")

LabelSection:AddButton({
    Text = "Atualizar Label",
    Func = function()
        dynamicLabel:SetText("Valor atual: " .. tostring(os.time()))
    end,
})

-- ========== CONFIGURAÇÕES TAB ==========
local ConfigSection = ConfigTab:CreateSection("Configurações da UI")

ConfigSection:AddSlider("UIScale", {
    Text = "Escala da UI",
    Default = 100,
    Min = 50,
    Max = 150,
    Rounding = 0,
    Suffix = "%",
    Callback = function(value)
        Library:SetDPIScale(value)
    end,
})

ConfigSection:AddDivider()

ConfigSection:AddButton({
    Text = "Resetar Escala (100%)",
    Func = function()
        Library:SetDPIScale(100)
    end,
})

ConfigSection:AddButton({
    Text = "Recarregar Cores do Tema",
    Func = function()
        Library:UpdateColorsUsingRegistry()
        Library:Notify("Cores recarregadas!")
    end,
})

ConfigSection:AddDivider()

ConfigSection:AddButton({
    Text = "Descarregar Script (Unload)",
    Risky = true,
    Func = function()
        Library:Unload()
    end,
})

-- ========== INFO TAB ==========
local InfoSection = InfoTab:CreateSection("Sobre")

InfoSection:AddLabel("Saeko Hub")
InfoSection:AddLabel("Versão: 1.0 (Teste UI)")
InfoSection:AddLabel("UI Library: Obsidian")
InfoSection:AddLabel("Tema: Azul Ciano")
InfoSection:AddLabel("")

InfoSection:AddLabel("Elementos disponíveis:")
InfoSection:AddLabel("• Toggles (interruptores)")
InfoSection:AddLabel("• Sliders (controles)")
InfoSection:AddLabel("• Dropdowns (menus)")
InfoSection:AddLabel("• Inputs (campos)")
InfoSection:AddLabel("• Botões")
InfoSection:AddLabel("• Labels (textos)")

InfoSection:AddDivider({ Margin = 10 })

InfoSection:AddButton({
    Text = "GitHub da Obsidian",
    Func = function()
        setclipboard and setclipboard("https://github.com/deividcomsono/Obsidian")
        Library:Notify("Link copiado!")
    end,
})

-- ========== BOTÃO FLUTUANTE (AZUL CIANO) ==========
local FloatingButton = Library:AddDraggableButton("S", function()
    if Window.Frame.Visible then
        Window:Hide()
    else
        Window:Show()
    end
end)
FloatingButton:SetText("S")
FloatingButton.Button.BackgroundColor3 = Color3.fromRGB(0, 180, 255)

-- ========== NOTIFICAÇÃO INICIAL ==========
Library:Notify({
    Title = "Saeko Hub",
    Description = "UI carregada! Tema Azul Ciano",
    Duration = 3,
})

-- ========== MOSTRAR JANELA ==========
Window:Show()
