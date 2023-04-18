## II. Containerized Architecture
### One business application per repository. 

Your application will be transformed into a container image later in the build process. Ensuring your application follows the best design practices will ensure you are taking advantage of containers in terms of performance, scalability, etc.

A container image should be represented by ONLY one source code repository. And this source code repository should represent ONLY the content for the container image. 


Considerations:

* Front-end and backend should exist in a separated repository to take advantage of the [container technology](https://kubernetes.io/docs/concepts/containers/). 
* Multiple apps sharing the same code is a violation of the container-factor. 
 

Recommendations:

An application is defined per its business role in the company—for example, Users, Reports, and Authentication. There is always a one-to-one correlation between the codebase and the app. 

Microservices and containers:

Consider Micro-services architectures to define the smallest deployment unit for your application that can take advantage of containerization platforms.






