# Feature

SIEMPRE que el usuario no te indique cuál es el resultado que se tendrá que verificar con el verify, solicítalo.

El objetivo de este playbook es desarrollar una nueva feature. No puedes modificar el código. Investiga todo lo necesario para desarrollar la nueva característica y ejecuta un subagente worker-nuevo para que haga el cambio. Le tienes que pasar un resumen de lo que tiene qué hacer, cómo hacerlo y el resultado esperado dado por el usuario.

## Entras en loop hasta que el diff sea el esperado

Recibes el output del worker:

- ERROR: Reformulas resumen solventando el error. 
- EXITO: 
    1. Compruebas diff:
        - Si no es lo esperado, solicitas los cambios al worker. 
        - Si es lo esperado, ejecutas verify para hacer la verificación final.

Cuando el verify tuyo devuelva éxito, ejecutas la skill local git y realizas lo que el usuario haya indicado ahí.