# Diagrama de procesos

Este diagrama es el ciclo de vida de un proceso. Para cada proceso del sistema, hay un ciclo de vida así. Comienza en estado nuevo, por donde pasa una sola vez en toda su vida, hasta que el planificador de procesos (parte del kernel) lo acepta y pasa a estado listo. A nivel lógico, todos los procesos están en un árbol de procesos, en la memoria interna. Este árbol de procesos es gestionado por el planificador de procesos. El objetivo del planificador de procesos es gestionar los procesos de forma concurrente. El planificador a su vez es una serie de rutinas, y a su vez una serie de procesos, y permiten la ejecución concurrente de todos los procesos.

**concurrente != simultáneo (o a la vez)**

Solo un proceso está ejecutándose de cada vez, en cada núcleo del procesador. Por tanto, no son simultáneos, sino que se va pasando de forma rápida de uno a otro, con lo que aparenta ser simultáneo.

Lo que distingue a un proceso de un programa es que el proceso es un programa vivo (ej. programa = imagen docker, proceso = contenedor docker). En Java, es un objeto de la clase Process, y para crearlo se utiliza la clase ProcessBuilder.

Un usuario da la órden de instanciar un ejecutable -> Se crea un proceso.

Estados de un proceso:
- Nuevo
- Listo
- En ejecución
- Bloqueado

Cuando está "listo", "en ejecución" o "bloqueado", está vivo. Cuando está terminado, se liberan todos los recursos, deja de estar referenciado en ningún sitio. Estado anterior al de ejecución: ESTADO LISTO. Nunca nuevo, ni otros.

Varias rutinas que quitan a un proceso de ejecución:
- Tiempo compartido: una forma de planificación de procesos. El planificador de procesos define una cantidad de tiempo (en milisegundos) llamada "cuanto" de ejecución, que es la cantidad de tiempo máximo que un proceso puede estar ocupando la CPU de forma ininterrumpida. Vuelve al final de la cola (FIFO) de su prioridad.

Para volver a estado de ejecución desde listo, hay que estar en cabeza de dicha cola.