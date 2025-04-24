# MSESP
# **ATENÇÃO!**
> ESTE README.MD NÃO É OFICIAL!

# **📜 ESPLibrary - Documentação Completa**  
**Uma biblioteca avançada de ESP para Roblox**, criada por `mstudio45`.  

## **📌 Recursos**
✅ ESP para **objetos, NPCs e jogadores**  
✅ **Diferentes tipos de ESP** (Highlight, Billboard, Tracers, etc.)  
✅ **Atualizações em tempo real**  
✅ **Personalização completa**  
✅ **Modo Rainbow para cores animadas**  

---

## **📂 Importando a Biblioteca**
```lua
local ESPLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/Sc-Rhyan57/MSESP/refs/heads/main/source.lua"))()
```

---

# **🔹 Tipos de ESP**
A `ESPLibrary` suporta os seguintes tipos de ESP:  

| Tipo       | Função Associada         | Descrição |
|------------|--------------------------|------------|
| **Highlight**  | `ESP.Highlight(args)`  | Destaca objetos com contorno e preenchimento |
| **Billboard**  | `ESP.Billboard(args)`  | Mostra um texto acima do objeto |
| **Tracer**     | `ESP.Tracer(args)`     | Cria uma linha ligando a câmera ao objeto |
| **Arrow**      | `ESP.Arrow(args)`      | Adiciona uma seta apontando para o objeto |
| **Adornment**  | `ESP.Adornment(args)`  | Desenha um **box, esfera ou cilindro** no objeto |
| **Outline**    | `ESP.Outline(args)`    | Adiciona um contorno 3D ao objeto |

---

## **🔹 Criando um ESP**
Cada ESP possui configurações diferentes, mas todas seguem um padrão similar.

### **1️⃣ Criando um ESP Highlight**
```lua
local esp = ESPLibrary.ESP.Highlight({
    Name = "Porta",
    Model = workspace.Door,
    FillColor = Color3.fromRGB(255, 0, 0),
    OutlineColor = Color3.fromRGB(255, 255, 255),
    FillTransparency = 0.5,
    OutlineTransparency = 0.1
})
```

✅ **Funções para modificar o Highlight**  
```lua
esp.SetColor({
    FillColor = Color3.fromRGB(0, 255, 0), -- Verde
    OutlineColor = Color3.fromRGB(0, 0, 255) -- Azul
})
```
```lua
esp.SetText("Nova Porta")
```
```lua
esp.Destroy() -- Remove o ESP
```

---

### **2️⃣ Criando um ESP Billboard**
```lua
local esp = ESPLibrary.ESP.Billboard({
    Name = "NPC",
    Model = workspace.NPC,
    Color = Color3.fromRGB(255, 255, 0),
    TextSize = 18,
    StudsOffset = Vector3.new(0, 2, 0)
})
```

✅ **Funções para modificar o Billboard**  
```lua
esp.SetColor({ Color = Color3.fromRGB(0, 255, 255) }) -- Ciano
```
```lua
esp.SetText("Novo NPC")
```

---

### **3️⃣ Criando um ESP Tracer**
```lua
local esp = ESPLibrary.ESP.Tracer({
    Model = workspace.Part,
    Color = Color3.fromRGB(255, 0, 0),
    Thickness = 2,
    Transparency = 0.5,
    From = "Bottom"
})
```

✅ **Funções para modificar o Tracer**  
```lua
esp.SetColor({ Color = Color3.fromRGB(0, 255, 0) }) -- Verde
```

---

### **4️⃣ Criando um ESP Arrow**
```lua
local esp = ESPLibrary.ESP.Arrow({
    Model = workspace.Part,
    Color = Color3.fromRGB(255, 0, 255),
    CenterOffset = 300
})
```

✅ **Funções para modificar o Arrow**  
```lua
esp.SetColor({ Color = Color3.fromRGB(0, 255, 0) }) -- Verde
```

---

### **5️⃣ Criando um ESP Adornment**
```lua
local esp = ESPLibrary.ESP.Adornment({
    Name = "CaixaESP",
    Model = workspace.Part,
    Color = Color3.fromRGB(255, 0, 255),
    Type = "Box", -- Pode ser: "Box", "Sphere", "Cylinder"
    Transparency = 0.5
})
```

✅ **Funções para modificar o Adornment**  
```lua
esp.SetColor({ Color = Color3.fromRGB(0, 255, 0) }) -- Verde
```

---

### **6️⃣ Criando um ESP Outline**
```lua
local esp = ESPLibrary.ESP.Outline({
    Name = "OutlineESP",
    Model = workspace.Part,
    SurfaceColor = Color3.fromRGB(0, 255, 0),
    BorderColor = Color3.fromRGB(255, 255, 255),
    Thickness = 0.05,
    Transparency = 0.5
})
```

✅ **Funções para modificar o Outline**  
```lua
esp.SetColor({
    SurfaceColor = Color3.fromRGB(255, 0, 0),
    BorderColor = Color3.fromRGB(0, 0, 255)
})
```

---

# **⚙️ Configurações Extras**
### **🌈 Modo Rainbow (Mudança de cor automática)**
```lua
ESPLibrary.Rainbow.Enable()
```
Para desativar:
```lua
ESPLibrary.Rainbow.Disable()
```

---

# **🔄 Atualizando Todos os ESPs**
Caso queira **alterar a cor de todos os ESPs ativos**, você pode fazer:

```lua
function UpdateAllESPColors(newColor)
    for _, esp in pairs(ESPLibrary.ESP) do
        if typeof(esp) == "table" and esp.SetColor then
            esp.SetColor({ Color = newColor })
        end
    end
end

UpdateAllESPColors(Color3.fromRGB(0, 255, 255)) -- Define todos os ESPs para ciano
```

---

# **🗑️ Removendo ESPs**
### **Remover um ESP específico**
```lua
esp.Destroy()
```

### **Remover todos os ESPs**
```lua
ESPLibrary.ESP.Clear()
```

---

# **📜 Lista Completa de Funções**
| Função                        | Descrição |
|--------------------------------|------------|
| `ESP.Highlight(args)`          | Cria um Highlight no modelo |
| `ESP.Billboard(args)`          | Adiciona um Billboard (texto flutuante) |
| `ESP.Tracer(args)`             | Cria uma linha conectando a câmera ao objeto |
| `ESP.Arrow(args)`              | Adiciona uma seta indicando a direção do objeto |
| `ESP.Adornment(args)`          | Adiciona um Box, Esfera ou Cilindro ao redor do objeto |
| `ESP.Outline(args)`            | Cria um contorno ao redor do objeto |
| `ESP.Clear()`                  | Remove todos os ESPs ativos |
| `Rainbow.Enable()`             | Ativa o modo arco-íris para cores animadas |
| `Rainbow.Disable()`            | Desativa o modo arco-íris |
| `Highlight.SetColor({})`       | Atualiza as cores de um Highlight |
| `Billboard.SetColor({})`       | Atualiza as cores de um Billboard |
| `Tracer.SetColor({})`          | Atualiza as cores de um Tracer |
| `Arrow.SetColor({})`           | Atualiza as cores de um Arrow |
| `Adornment.SetColor({})`       | Atualiza as cores de um Adornment |
| `Outline.SetColor({})`         | Atualiza as cores de um Outline |
| `esp.Destroy()`                | Remove um ESP específico |

---

# **📢 Contribuição**
Se encontrar bugs ou quiser sugerir melhorias, abra uma **Issue** ou envie um **Pull Request** no GitHub!
