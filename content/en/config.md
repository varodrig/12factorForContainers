## III. Config
### Store config in the environment

An app's *config* is everything that is likely to vary between [deploys](./codebase) (staging, production, developer environments, etc).  This includes:

* Resource handles to the database, Memcached, and other backing services.
* Credentials to external services such as Amazon S3 or Twitter
* Per-deploy values such as the canonical hostname for the deploy

Apps sometimes store config as constants in the code.  This is a violation of twelve-factor, which requires **strict separation of config from code**.  Config varies substantially across deploys, code does not.

A litmus test for whether an app has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials.

Note that this definition of "config" does **not** include internal application config, such as `config/routes.rb` in Rails, or how [code modules are connected](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/beans.html) in [Spring](http://spring.io/). This type of config does not vary between deploys, and so is best done in the code.

**The twelve-factor app stores config separated from the source code* 
Configurations should be separated from the source code and it will not be packaged with the application artifact. 
(often shortened to *env vars* or *env*). Env vars are easy to change between deploys without changing any code or configuration files.

Another aspect of config management is grouping. Sometimes apps batch config into named groups (often called "environments") named after specific deploys, such as the `development`, `test`, and `production` environments.

In a twelve-factor app, env vars are granular controls, each fully orthogonal to other env vars.  They are never grouped together as "environments", but instead are independently managed for each deploy.  This is a model that scales up smoothly as the app naturally expands into more deploys over its lifetime.
