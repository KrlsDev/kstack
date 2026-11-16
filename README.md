Inspirado en [pstack](https://github.com/backnotprop/pstack) de [poteto](https://github.com/poteto): el mismo patrón de un modo orquestador que lee tu petición, elige el playbook adecuado y lanza subagentes para el trabajo pesado con verificación basada en evidencia.

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

## Instalación

### Visual Studio Code y Android Studio (misma forma en los dos)

Abre el diálogo **Plugins → Install Plugin from Source** (en VS Code: *Chat: Install Plugin from Source*) y teclea:

```
KrlsDev/rstack
```

### OpenCode

Necesita Node.js. Ejecuta el CLI de skills en el proyecto que va a usar la skill (`-g` para instalarla en todos tus proyectos):

```sh
# Última versión (sigue main)
npx skills add KrlsDev/rstack --skill '*' -a opencode

# Una versión fija (cada tag vX.Y.Z coincide con la versión del plugin)
npx skills add KrlsDev/rstack@v0.2.1 --skill '*' -a opencode
```

Instala la skill completa (con playbooks y evals) en `.agents/skills/`, que OpenCode descubre automáticamente. Sin fijar versión, `npx skills check` avisa de cambios en `main` y `npx skills update` los aplica.

El CLI no instala el agente `worker`: cópialo en `.opencode/agents/` del proyecto o en `~/.config/opencode/agents/` para todos tus proyectos:

```sh
mkdir -p .opencode/agents
curl -fsSL https://raw.githubusercontent.com/KrlsDev/rstack/main/agents/worker.md \
  -o .opencode/agents/worker.md
```

Después, pide a OpenCode que use la skill `renfecito-mode`.
