## V. Scalability
### Scalable applications using fast startup and graceful shutdown

Applications should be able to scale up or down into different replicas. Considering the following design principles:


- streamlined startup:


**The containerized app's processes are *disposable*, meaning they can be started or stopped at a moment's notice.** 

Processes should strive to **minimize startup time**.  Ideally, a process takes a few seconds from the time the launch command is executed until the process is up and ready to receive requests or jobs. 

- graceful shutdown: 

Applications will not share in state between replicas as well as any temporary state that can be lost when stopping the application. If any state is required, data will be stored in a persistent or specific mechanism, such as user session.


