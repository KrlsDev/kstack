# Bug

Es objetivo de este playbook es investigar profundamente un bug y qué lo provoca. Para ello, entrarás en el siguiente bucle:

1. Lanzas 3 agentes workers para que investiguen y reproduzcan el bug. IMPORTANTE, dependiendo de lo que tenga en el verify tienes que deducir si los puedes lanzar secuencialmente o en paralelo.Indícales que, OBLIGATORIAMENTE, tienen que usar las herramientas del apartado de verificación de la skill local verify y que cuando hayan encontrado el bug y lo que lo provoca que te reporte EXITO y el porqué es provocado. Tienen 3 intentos, sino tienen que reportar error.
2. En caso de que no los 3 te devuelvan EXITO, vuelves a lanzar otros 3 hasta que los 3 te reporten EXITO. REPITE ESTE PASO LAS VECES NECESARIAS.
Siempre tienes que mostrar al usuario una tabla donde aparezca worker 1, worker 2... y los resutlados indicándole si se detiene su investigación por 3 'EXITO' o se sigue pq worker x ha fallado.
3. Una vez hayas recibido 3 'EXITO', junta las 3 hipótesis en una y usando las herramientas de la etapa de verificación de la skill verify, verifica su veracidad. Si no es cierto, vuelve al paso 1. Si sí que lo es, haz el resumen de como solventar el bug y lanza un worker para que lo solucione.