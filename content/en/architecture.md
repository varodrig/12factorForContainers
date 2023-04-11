## I. Containerized Architecture
### One business application per repository. 

A container image should be represented by ONLY one source code repository. And this source code repository should represent ONLY the content for the container image. 


Considerations:

* Front-end and backend should exist in a separated repository to take advantage of the [container technology](https://kubernetes.io/docs/concepts/containers/). 
* Multiple apps sharing the same code is a violation of the container-factor. 
 

Recommendations:
An application is defined per its business role in the company—for example, Users, Reports, and Authentication. There is always a one-to-one correlation between the codebase and the app. Consider Micro-services architectures to define the smallest deployment unit for your application that can take advantage of containerization platforms.






