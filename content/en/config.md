## III. Config
### Store config in the environment

An app's *config* is everything that is likely to vary between [deploys](./build-release-run) (staging, production, developer environments, etc). Configurations are independently managed for each deploy.  This is a model that scales up smoothly as the app naturally expands into more deploys over its lifetime.

This includes:

* Resource handles to the database, Memcached, and other backing services.
* Credentials to external services such as Amazon S3 or Twitter
* Per-deploy values such as the canonical hostname for the deploy
* Routes and ports to connect to third party systems or any backend or services.

Apps sometimes store config as constants in the code.  This is a violation of twelve-factor, which requires **strict separation of config from code**.  Config varies substantially across deploys, code does not.

Config separated from the source code* 
Configurations should be separated from the source code and it will not be packaged with the application artifact. Configurations will be based on different environments such as the `development`, `test`, and `production` environments.

There are several ways of managing your configurations, env vars, files and secure files.
Which one is best?

- Configuration Files can be translated to easily to a container world using specific configuration files for containers such as Config Maps. These files will be reading from the container using different strategies later once you start building your container strategy.

- Env variables can be allocated in different deployment files that can be read at runtime by your container. 


