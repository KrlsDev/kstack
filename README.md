# rstack

Stack de plugins para agentes de código: el modo orquestador **krls-mode** con sus playbooks y el agente **worker-nuevo**, empaquetados como plugin portable ([Agent Plugins 1.0](https://agent-plugins.org/)).

Este repositorio es a la vez **plugin** y **marketplace**: la raíz es el plugin (con `plugin.json`) y `.github/plugin/marketplace.json` es el catálogo que lo lista.

## Contenido

| Componente | Ruta | Descripción |
|---|---|---|
| Skill `krls-mode-nuevo` | `skills/krls-mode-nuevo/` | Instrucciones del orquestador con playbooks para features, bugs y skills locales de setup (`verify`, `git`) |
| Agente Copilot `worker-nuevo` | `com.github.copilot/agents/worker-nuevo.agent.md` | Worker para escritura de código y exploración pesada |
| Agente OpenCode `worker-nuevo` | `agents/worker-nuevo.md` | El mismo worker en formato OpenCode (`mode: subagent`) |

## Instalación

### Android Studio y VS Code ("Plugin from Source")

Abre el diálogo de instalación de plugin desde fuente y teclea:

```
KrlsDev/rstack
```

### VS Code (marketplace)

Añade en Settings:

```json
"chat.plugins.marketplaces": ["KrlsDev/rstack"]
```

o en el chat de Copilot: `/plugin marketplace add KrlsDev/rstack` y luego `/plugin install krls-mode@rstack`.

### GitHub Copilot CLI

```
copilot plugin install KrlsDev/rstack
```

o vía marketplace: `copilot plugin marketplace add KrlsDev/rstack` + `copilot plugin install krls-mode@rstack`.

### OpenCode

Con GitHub CLI 2.90+:

```sh
gh skill install KrlsDev/rstack krls-mode-nuevo --agent opencode
mkdir -p ~/.config/opencode/agents
curl -fsSL https://raw.githubusercontent.com/KrlsDev/rstack/main/agents/worker-nuevo.md \
  -o ~/.config/opencode/agents/worker-nuevo.md
```

O manualmente: copia `skills/krls-mode-nuevo/` a `~/.config/opencode/skills/` (global) o `.opencode/skills/` (proyecto), y `agents/worker-nuevo.md` a `~/.config/opencode/agents/` o `.opencode/agents/`.

### Android Studio (solo skill, sin plugin)

```sh
gh skill install KrlsDev/rstack krls-mode-nuevo
```

Activa Agent Skills en Settings → GitHub Copilot → Chat → Agent (public preview).

## Estructura

```
plugin.json                      ← manifiesto del plugin (Agent Plugins 1.0); la raíz ES el plugin
skills/krls-mode-nuevo/          ← skill portable (SKILL.md + playbooks + evals)
com.github.copilot/
└── agents/worker-nuevo.agent.md ← agente específico de Copilot
agents/worker-nuevo.md           ← agente específico de OpenCode
.github/plugin/marketplace.json  ← catálogo del marketplace "rstack"
```

## Mantenimiento

- **Cambios en la skill**: edita solo `skills/krls-mode-nuevo/` (copia única) y sube `version` en `plugin.json` y `marketplace.json` a la vez.
- **Cambios en el worker**: el cuerpo (prompt) vive duplicado en `agents/worker-nuevo.md` (OpenCode) y `com.github.copilot/agents/worker-nuevo.agent.md` (Copilot) porque los formatos de agente no son portables; mantén los dos cuerpos sincronizados.
- El nombre del marketplace (`rstack`) es estable: los identificadores de plugin (`krls-mode@rstack`) dependen de él.
