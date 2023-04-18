## IV. Build and Deployment
### One container image in all environments

An application is transformed into a container image running through two stages:

The codebase is the same across all deploys, although different versions may be active in each repository using different branches.  For example, a developer has its own feature branch deployed only on development.  

At the end, all feature/bugs branches will be targeting the main branch to create a unique container image to be promoted to different Lower level environments to Production stage.


* The *source build stage* is a transform which converts a code repo into an executable bundle known as a *build*.  Using a version of the code at a commit specified by the build process, the build stage fetches vendors dependencies and compiles binaries and assets. This will became a Release. Every release should always have a unique release ID, such as a timestamp of the release.  Releases are an append-only ledger and a release cannot be mutated once it is created.  Any change must create a new release.


The *building container image stage* creates a container image based on your artifact and build strategy definition. For example, Java Quarkus can run on an enterprise server, and Spring Boot application with an embedded web server.

* The *deployment stage* takes the build-produced container image and combines it with the current [config](./config) according to the target environment. This stage will create the deployment process on the container platform, aiming to have the application running.




