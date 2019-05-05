### Image
 Images are defined by the Docker files and once built are immutable, they are a blueprint to the running application. 

### Container
A container is a running instance of a Docker image. 
In terms of coding the image is similar to a class and the container is an instance of the class that you've "newed" up.

### Dockerfile
A dockerfile is a file which describes how a Docker image is built.
The file without an extension is usually found in the project root directory

### Docker Compose
A Docker compose file is a basic way to orchestrate multiple images/containers. It is used to manage the lifecycle of a group of containers that make up a system. 
E.g. web app + database

### Host
The host is the underlying OS on which you will run Docker. Docker will utilise shared OS kernel resources to run your containers. 

### Container registry
A repository (public or private) to store container images. 
Common registries include Docker Hub, Quay, Azure container registry etc.