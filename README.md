# rstack

Stack de plugins para agentes de código: el modo orquestador **renfecito-mode** con sus playbooks y el agente **worker**, empaquetados como plugin portable ([Agent Plugins 1.0](https://agent-plugins.org/)).

## Contenido

| Componente | Ruta | Descripción |
|---|---|---|
| Skill `renfecito-mode` | `skills/renfecito-mode/` | Instrucciones del orquestador con playbooks para features, bugs y skills locales de setup (`verify`, `git`) |
| Agente Copilot `worker` | `com.github.copilot/agents/worker.agent.md` | Worker para escritura de código y exploración pesada |
| Agente OpenCode `worker` | `agents/worker.md` | El mismo worker en formato OpenCode (`mode: subagent`) |

## Instalación

### Visual Studio Code y Android Studio (misma forma en los dos)

Abre el diálogo **Plugins → Install Plugin from Source** (en VS Code: *Chat: Install Plugin from Source*) y teclea:

```
KrlsDev/rstack
```

### OpenCode

Con GitHub CLI 2.90+:

```sh
gh skill install KrlsDev/rstack renfecito-mode --agent opencode
mkdir -p ~/.config/opencode/agents
curl -fsSL https://raw.githubusercontent.com/KrlsDev/rstack/main/agents/worker.md \
  -o ~/.config/opencode/agents/worker.md
```

O manualmente: copia `skills/renfecito-mode/` a `~/.config/opencode/skills/` (global) o `.opencode/skills/` (proyecto), y `agents/worker.md` a `~/.config/opencode/agents/` o `.opencode/agents/`.

## Actualizaciones

Cuando este repositorio se actualiza, quienes lo tengan instalado reciben los cambios así:

- **VS Code**: con el auto-update de extensiones activado se aplica solo; manualmente con *Chat: Update Plugins* o el icono de refrescar en Plugins. Los cambios se cargan en sesiones nuevas.
- **Android Studio**: comprobación manual desde la vista de plugins de Copilot (la acción de actualizar o reinstalando); los cambios se cargan en sesiones nuevas.
- **OpenCode**: `gh skill update --all` (o repetir el `gh skill install`), y volver a descargar el worker con el `curl` de arriba.

## Mantenimiento (para el autor)

- **Cambios en la skill**: edita solo `skills/renfecito-mode/` (copia única).
- **Cambios en el worker**: el cuerpo (prompt) vive duplicado en `agents/worker.md` (OpenCode) y `com.github.copilot/agents/worker.agent.md` (Copilot) porque los formatos de agente no son portables; mantén los dos cuerpos sincronizados.
- **Antes de cada push con cambios**: sube `version` en `plugin.json`. Es el mecanismo por el que los clientes detectan y aplican las actualizaciones a los usuarios.
