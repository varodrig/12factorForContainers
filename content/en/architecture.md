## I. Architecture
### One business application per repository. 

An application is defined per its business role in the company. For example: Users, Reports, Authentication. There is always a one-to-one correlation between the codebase and the app.

Considerations:

* Front-end and backend should exists in a separated repository to take advantage of the [container technology](https://kubernetes.io/docs/concepts/containers/). 
* Multiple apps sharing the same code is a violation of twelve-factor. 


