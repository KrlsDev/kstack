# rstack

Stack de plugins para agentes de código: el modo orquestador **renfecito-mode** con sus playbooks y el agente **worker**, empaquetados como plugin portable ([Agent Plugins 1.0](https://agent-plugins.org/)).

Inspirado en [pstack](https://github.com/backnotprop/pstack) de [poteto](https://github.com/poteto): el mismo patrón de un modo orquestador que lee tu petición, elige el playbook adecuado y lanza subagentes para el trabajo pesado con verificación basada en evidencia.

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

## Uso

Al empezar una tarea, indica al agente que use la skill **renfecito-mode**. Eso es todo: la skill decide qué playbook aplicar según lo que le pidas.

```
usa renfecito-mode: añade un botón de ajustes en la pantalla principal
```

```
usa renfecito-mode: el login se cuelga si el token ha expirado, investiga y arréglalo
```

- Pide una **feature** → ejecuta el playbook de features: investiga y delega el cambio en un subagente `worker`.
- Reporta un **bug** → ejecuta el playbook de bugs: lanza workers para reproducir y localizar la causa, verifica las hipótesis con la skill local `verify` y luego delega la solución.
- El orquestador **no modifica código**: siempre trabaja a través de subagentes y exige verificación real (evidencia de comandos, no un build en verde) antes de dar nada por hecho.

En OpenCode también puedes invocarla directamente con `@renfecito-mode` al principio del prompt.
