# VSCodeChatModes

Colección de configuraciones para extender y personalizar los **Chat Modes** y las **Custom Instructions** en Visual Studio Code.

## 📖 Concepto

Los **Chat Modes** y **Custom Instructions** permiten adaptar el comportamiento de GitHub Copilot Chat en VS Code a distintos flujos de trabajo.

* **Chat Modes** → definen *personalidades* o *roles* para el chat.
* **Custom Instructions** → definen reglas y guías que influyen en las respuestas del chat de manera consistente.

## 🛠 Requisitos

* VS Code `1.101` o superior (con soporte para chat modes).
* Extensión **GitHub Copilot Chat** habilitada.

## 📂 Estructura del Repositorio

```
VSCodeChatModes/
├── references/                      
│   ├── Modes.json                       # Referencia de modos integrados y personalizados
│   ├── vscode_custom_instructions.json  # Referencia sobre instrucciones personalizadas
├── modes/                               # Ejemplos de .chatmode.md        
└── README.md
```

## 🚀 Instalación

Clona este repositorio en tu máquina:

```bash
git clone git@github.com:Pblo16/VSCodeChatModes.git
```

Configura VS Code para que reconozca la carpeta `modes/`.
Abre la configuración de VS Code y busca **`chat.modeFilesLocations`**.
Agrega la ruta a la carpeta `modes` del repositorio clonado:

* **Windows**

  ```json
  "chat.modeFilesLocations": [
    "C:/ruta/donde/clonaste/VSCodeChatModes/modes"
  ]
  ```

* **WSL**

  ```json
  "chat.modeFilesLocations": [
    "/mnt/c/ruta/donde/clonaste/VSCodeChatModes/modes"
  ]
  ```

* **Mac**

  ```json
  "chat.modeFilesLocations": [
    "/Users/tuusuario/VSCodeChatModes/modes"
  ]
  ```

Reinicia VS Code para que los cambios surtan efecto.

## ⚡ Chat Modes

VS Code incluye **3 modos integrados**:

* **Ask** → responder preguntas de código o diseño.
* **Edit** → realizar cambios de código en múltiples archivos.
* **Agent** → trabajar de forma más autónoma, ejecutando comandos y herramientas.

Además, puedes usar los ejemplos en [`/modes`](./modes/) como base para tus propios modos.

### Ejemplo de `.chatmode.md`

```markdown
---
description: Refactoriza código priorizando estructura y claridad.
tools: ['extensions', 'runCommands']
model: Claude Sonnet 4
---
# Refactor Mode
Refactoriza el código mejorando **estructura, claridad y mantenibilidad**, sin alterar su comportamiento.
```

## 🛠 Herramientas Disponibles en Chat Modes

Al crear un archivo `.chatmode.md` puedes habilitar diferentes **herramientas** en el `frontmatter` usando la clave `tools`.  
Estas herramientas permiten que el chat interactúe directamente con tu proyecto, tu entorno de desarrollo y la terminal.

Lista completa de herramientas soportadas:

```yaml
tools: [
  'extensions',
  'codebase',
  'usages',
  'vscodeAPI',
  'problems',
  'changes',
  'testFailure',
  'terminalSelection',
  'terminalLastCommand',
  'openSimpleBrowser',
  'fetch',
  'findTestFiles',
  'searchResults',
  'githubRepo',
  'runCommands',
  'runTasks',
  'editFiles',
  'runNotebooks',
  'search',
  'new'
]
```
---
🤖 Modelos conocidos disponibles para Copilot

GPT-4.1 

GPT-4o 

GPT-5

GPT-5 mini

o4-mini (Preview)

o3-mini 

GitHub Docs 

Claude Sonnet 4 

Claude Sonnet 3.5 

Claude Sonnet 3.7 

Grok Code Fast 1 (Preview)

Gemini 2.0

Gemini 2.5 Pro 

---


## 📝 Custom Instructions

Las **instrucciones personalizadas** permiten definir guías globales o específicas.

* `.github/copilot-instructions.md` → globales para todo el workspace.
* `*.instructions.md` → específicas por lenguaje, tarea o ruta.

### Ejemplo de `.instructions.md`

```markdown
---
applyTo: "**/*.ts,**/*.tsx"
---
# TypeScript & React Guidelines
- Usar functional components con hooks
- Preferir datos inmutables (`const`, `readonly`)
- Seguir las reglas de React hooks
```

También puedes configurarlas vía `settings.json`:

```json
"github.copilot.chat.pullRequestDescriptionGeneration.instructions": [
  { "text": "Always include a list of key changes." }
]
```

## 📌 Recursos

* [Documentación oficial de VS Code sobre Chat Modes](https://code.visualstudio.com/docs/copilot/copilot-chat)
* [Documentación de Custom Instructions](https://code.visualstudio.com/docs/copilot/copilot-instructions)

---
