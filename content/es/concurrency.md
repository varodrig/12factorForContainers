## VIII. Concurrencia
### Escalar mediante el modelo de procesos

Todo programa de ordenador, al ejecutarse, se encuentra representado en memoria por uno o más procesos. Las aplicaciones web se pueden ejecutar de diferentes formas desde el punto de vista del modelo de procesos que usan. Por ejemplo, los procesos PHP se ejecutan como procesos pesados (o simplemente procesos), hijos del proceso Apache, creándolos bajo demanda a causa de la cantidad de peticiones si es necesario. Los procesos Java funcionan de forma distinta, la Máquina Virtual de Java (JVM) proporciona un conjunto de procesos que reservan al principio una gran cantidad de recursos del sistema (CPU y memoria), gestionando la concurrencia internamente mediante procesos ligeros (threads). En ambos casos, los procesos en ejecución son prácticamente transparentes para los desarrolladores de la aplicación.

![La escalabilidad está representada por el número de procesos en ejecución, mientras que la diversidad de carga de trabajo lo está por los tipos de procesos.](/images/process-types.png)

**En las aplicaciones "twelve-factor", los procesos son ciudadanos de primera clase.** Los procesos de las aplicaciones "twelve-factor" se inspiran en [el modelo de procesos de unix para ejecutar demonios](http://adam.heroku.com/past/2011/5/9/applying_the_unix_process_model_to_web_apps/). Usando este modelo, el desarrollador puede distribuir la ejecución de su aplicación para gestionar diversas cargas de trabajo asignando cada tipo de trabajo a un *tipo de proceso*. Por ejemplo, las peticiones HTTP se pueden procesar con un proceso y las tareas con mucha carga de trabajo con hilos.

Esto no exime a los procesos de gestionar su propia división interna mediante threads en la ejecución de la máquina virtual o mediante un modelo asíncrono o por eventos con herramientas como [EventMachine](http://rubyeventmachine.com/), [Twisted](http://twistedmatrix.com/trac/), o [Node.js](http://nodejs.org/). No obstante, una máquina virtual aislada tiene una capacidad de crecimiento limitada, así que la aplicación debe ser capaz de dividirse en multiples procesos que se puedan ejecutar en múltiples máquinas físicas.

El modelo de procesos muestra todo su potencial cuando llega el momento de escalar. La [naturaleza "share-nothing", divide horizontalmente los procesos de las aplicaciones "twelve-factor"](./processes) y se traduce en un aumento de la concurrencia como una operación simple y fiable. El conjunto de tipos de procesos y el número de procesos de cada tipo es conocido como *juego de procesos*.

Los procesos de las aplicaciones "twelve-factor" [nunca deberían ser demonios](http://dustin.github.com/2010/02/28/running-processes.html) ni escribir ficheros de tipo PID. En su lugar, se debería confiar en un gestor de procesos del sistema operativo (como [Upstart](http://upstart.ubuntu.com/), un gestor de procesos distribuido en una plataforma en la nube, o una herramienta como [Foreman](http://blog.daviddollar.org/2011/05/06/introducing-foreman.html) en desarrollo) para gestionar [los historiales](./logs), responder a procesos que terminen inesperadamente, y gestionar los reinicios y apagados provocados por los usuarios.