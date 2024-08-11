<h2>Docker</h2>
Docker is a Containerization platform for packaging,deploying and running application as containers.

- docker is a container runtime engine.
- Docker Engine: It is a core part of docker, that handles the creation and management of containers.
- Dockerfile: It is a script that containing instructions to build a docker image.
- Docker Image: It is a read-only template that is used for creating containers, containing the application code and dependencies.
- Docker Hub: It is a cloud based repository that is used for finding and sharing the container images.
- Docker Registry: It is a storage distribution system for docker images, where you can store the images in both public and private modes.
- (The Docker daemon is simply as “Docker,” is a background service that manages Docker containers on a system.)

<h2>Containerization</h2>
containerizations is a lightweight form of virtulization that allow you to encapsulate an application and its dependencies into a self-contained unit called a "Container"
<h3>1)Container</h3>
A Docker container is a software package that contains everything needed to run an application, including the application's code and its dependencies.

- docker is tool which create container
- Docker container is a runtime instance of an image
- container is like virtual machine
- portable (easy to share one computer to another,code as well as dependencies)
- lightweight(easy to build,update,destroy).
<h3>what include in a container?</h3>

- - code
  - runtime
  - liberies
  - envionment
  - configs

<h3>What is Docker Image?</h3>
It is a executable file, comprised of multiple layers, used to execute code in a Docker container. 

- They are a set of instructions used to create docker containers.
- Docker Image is an executable package of software that includes everything needed to run an application
<h3>Docker image</h3>
Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

- Docker image =is actually excutable file(in file instruction to how container created )
- image is basically like static screenshot or static snapshot of what the code
- https://www.geeksforgeeks.org/what-is-docker-image/?ref=lbp
<h2>Dockerfile</h2>
- Docker can build images automatically by reading the instructions from a Dockerfile.
- A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.



https://docs.docker.com/reference/dockerfile/





 
https://docs.docker.com/get-started/docker_cheatsheet.pdf
<div>
<img width=500 height=300 src="https://www.google.com/imgres?q=docker%20cheatsheet&imgurl=https%3A%2F%2Fraw.githubusercontent.com%2Fsangam14%2Fdockercheatsheets%2Fmaster%2Fdockercheatsheet8.png&imgrefurl=https%3A%2F%2Fdockerlabs.collabnix.com%2Fdocker%2Fcheatsheet%2F&docid=7hB1JOR3fNsCmM&tbnid=g9CB8-d0fCaYcM&vet=12ahUKEwjgstvYwOOHAxVAUGwGHTkjLKkQM3oECBYQAA..i&w=1259&h=832&hcb=2&ved=2ahUKEwjgstvYwOOHAxVAUGwGHTkjLKkQM3oECBYQAA">
</div>

**A hypervisor** is software that allows multiple virtual machines (VMs) to run on a single physical computer
<h2>What is Docker Hub?</h2>
Docker Hub is a repository service and it is a cloud-based service where people push their Docker Container Images and also pull the Docker Container Images from the Docker Hub anytime or anywhere via the internet. 

- it makes it easy to find and reuse images,easy to share,push your image as private or public registry,where you can store docker image.
<h3>Why to use Docker?</h3>
Docker can be used to pack the application and its dependencies which makes it lightweight and easy to ship the code faster with more reliability. Docker make its very simple to run the application in the production environment docker container can be platform independent if the docker engine is installed in the machine.
