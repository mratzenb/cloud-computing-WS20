#Planned Architeture
This is the architecture we are planning to implement. **The actual implemented architecutre may differ from this one**.

The planned architecture looks something like this:
![Monolith - Architecture](./figs/Microservice-architecture.svg)

This means that the two backend services run in seperate docker conainers. The frontend part still works the same expect that the it will now be running in the same JVM instance as before.

The docker-containers will be running locally, so that the frontend has deal with the minimum amount of changes.

This architecture also supports Continous Integratino (CI) because each Microservice has its own repository as well as the frontend. For this Jenkins or Github CI will be used.