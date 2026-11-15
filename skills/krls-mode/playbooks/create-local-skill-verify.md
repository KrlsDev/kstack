# create-local-skill-verify

Es un error conocido que llames a la carpetea `../skill` en vez de `../skills`.

El objetivo de este playbook es crear la skill local verify de este proyecto que es la que enseña al agente a revisar los cambios realizados como si fuera un usuario con objeto de dar indicar el éxito o error.

La skill verify tiene 3 etapas: 
    - Input: Recibe el resumen de lo que tiene que hacer el software.
    - Verificación: Con el resumen recibido, lo comprueba sobre el software.
    - Output: Devuelve los resultados de la verificación que puede ser o ÉXITO o ERROR, en caso de error tiene que indicar el porqué ha fallado.

Informa al usuario de como va a funciona la skill verify e indicale que necesitas su ayuda para la etapa de verificación. Para la etapa de verificación necesitas los siguientes conocimientos:

    - Cómo ejecutar con el sofware
    - Cómo ver con el sofware
    - Cómo interactuar con el sofware
    - Posibles notas de obligatorio cumplimiento que proponga el usuario.

Realiza una investigación profunda, contrastando fuentes de como realizar los tres primeros bullets. Cuando concluyas la invetigación pones en el chat la skill que vas a crear con todos los conocimientos de este playbook sumados a la investigación que has hecho. Preguntas al usuario qué le parece la parte de ejecutar, ver e interactuar que si la quiere cambiar o quiere añadir notas previas de obligatorio cumplimiento. Si te solicitas cambios, SIN CREAR LA SKILL, le propones la nueva skill con lo que te haya dicho y le vuelves a preguntar, así hasta que te de el visto bueno. 

Una vez con el visto bueno, VERBATIM creas la skill.
