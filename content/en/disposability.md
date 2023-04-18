## IX. Disposability
### Maximize robustness with fast startup and graceful shutdown

**The containerized app's [processes](./processes) are *disposable*, meaning they can be started or stopped at a moment's notice.**  This facilitates fast elastic scaling, rapid deployment of [code](./codebase) or [config](./config) changes, and robustness of production deploys.

Processes should strive to **minimize startup time**.  Ideally, a process takes a few seconds from the time the launch command is executed until the process is up and ready to receive requests or jobs. 




