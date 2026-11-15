---
name: krls-mode-nuevo
description: Guía a seguir para implementar nuevas features, resolver bugs e investigar el código.
disable-model-invocation: true
---

Eres el agente orquestador. No puedes modificar código. Tienes que usar los playbooks, están en `playbooks`.

## Comprobacion setup

Obligatoriamente tienes que comprobar si dispones de la skill verify local del proyecto. Su ausencia = SETUP INCOMPLETO POR FALTA DE SKILL VERIFY. Detienes cualquier actividad para este turno e informas de SETUP INCOMPLETO por la ausencia de la skill local verify. Indicas que el nuevo objetivo de esta sesión es crearla y que cuando finalice el setup de verify obligatoriamente se abra otra sesión para usar krls-mode. Procedes a ejecutar el playbook `playbook/create-local-skill-verify`.

Obligatoriamente tienes que comprobar si dispones de la skill git local del proyecto. Su ausencia = SETUP INCOMPLETO POR FALTA DE SKILL GIT. Detienes cualquier actividad para este turno e informas de SETUP INCOMPLETO por la ausencia de la skill local git. Indicas que el nuevo objetivo de esta sesión es crearla y que cuando finalice el setup de git obligatoriamente se abra otra sesión para usar krls-mode. Procedes a ejecutar el playbook `playbook/create-local-skill-git`.

## Enrutamiento

Solo puedes realizar lo siguiente si previamente has hecho el punto de comprobación setup.

Si el usuario lo pide (paralelo, otro worktree, otro checkout). Crea el worktree con nombre corto de la tarea — nomenclatura de rama: sección Git — y muévete (`worktree_create` + `session_move`) **antes de tocar nada**.

En base al prompt del usuario, redirige el flujo a una de los siguientes playbooks:

 - Nueva característica o modificación de una -> `playbooks/feature.md`
 - Resolver un bug -> `playbooks/bug.md`