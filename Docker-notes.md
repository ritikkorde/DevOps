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
- The first entry in the file specifies the base image, which is a pre-made image containing all the dependencies you need for your application
- Then, there are commands you can send to the Dockerfile to install additional software, copy files, or run scripts.
<h3>Important Instructions used in Dockerfile</h3>

- The essential instructions of a Dockerfile are illustrated below How to create Dockerfile -
1) Open your preferred IDE (such as VS Code) and navigate to your project directory. Create a new file in your project directory (at the root level) and name it **Dockerfile** (only this name is excepted.no file extension)
<h3>2)FROM</h3>
This instruction sets the base image on which the new image is going to be built upon. It is usually the first instruction in a Dockerfile.

- <h4>FROM (imge></h4>
  
|   eg.           |
|-----------------|
| **FROM ubuntu:22**  |

<h3>3)WORKDIR</h3>

- In a Dockerfile, the WORKDIR instruction sets the working directory for any command that follows it in the Dockerfile.
- This means that any commands that are run in the container will be executed relative to the specified directory.
- <h4>WORKDIR(directory></h4>

|   eg.           |
|-----------------|
| **WORKDIR  /home/app**  |
This instruction tells Docker to set the working directory of the container to /app . Any subsequent commands in the Dockerfile, such as COPY, RUN, or CMD, will be executed in this directory.


<h3>4)COPY</h3>
Use the COPY instruction to copy local files from the host machine to the current working directory. 

- For example, to copy a file named package.json from the host machine’s current directory to the image’s /app directory, you would use the following command:

|   eg.           |
|-----------------|
| **COPY  package.json/app/**  |

|   eg.           |
|-----------------|
| **COPY  . .**  |
If you want to copy all the files from the host’s current directory to the container’s current directory, you can use the below command:
<h3>RUN</h3>
Use the “RUN” instruction to execute commands that will run during the image build process. The format of instruction is :
<h4>RUN (command_name></h4>

|   eg.           |
|-----------------|
| **RUN npm install**  |
 For example, to update the package manager and install a specific package, you would use the following command:
<h3>6)CMD</h3>
In a Dockerfile, the CMD instruction sets the command that will be executed when a container is run from the image. The format of the instruction is:
<h4>CMD ["executable","param1","param2",...]</h4>

|   eg.           |
|-----------------|
| **CMD ["npm", "start"]**  |
This instruction tells Docker to run the command npm start when a container is created from the image. This command will start the Node.js application that was installed in the container using the npm install command.
<h3>LABEL</h3>
This command provides meta-information for an image, like details of the maintainer, version, or description.

|   eg.           |
|-----------------|
| **LABEL maintainer="ritikkorde@gmail.com" |

this is content under Dockerile.

|   eg.           |
|-----------------|
| **FROM ubuntu:22 
| WORKDIR /home/app      
| COPY . .         
|RUN npm install
|CMD [ "npm", "start" ] |


https://docs.docker.com/reference/dockerfile/
https://medium.com/@anshita.bhasin/a-step-by-step-guide-to-create-dockerfile-9e3744d38d11

<h2>Build Docker Image</h2>
Once you have finished building your Dockerfile, you can build the image by running the below command from the Terminal :

- docker build -t (image_name> (-t for tag the image) Or (docker image build .)
- docker images (list of all docker images)
- docker rmi (image name> (delete an image) 
- docker login -u (usename> (to login docker deskstop to docker engine )
- push docker image .(before push image firstly you tag the image)
- docker tag imagename:tag username/imagename:tag (after that you can push image)
- docker push username/imagename:tag
- docker pull (image name > (pull an image from a docker hub)
- docker run --name (container_name> (image_name> (Create and run a container from an image, with a custom name)
- docker run -d (image name> (run container in background)
- docker inspect (container name> (to inspect container all details)
- docker exec -it (container name> shell(/bin/bash> (to open a shell inside the running container)
-  docker ps -a (list all containers)
-  docker start /stop (container name> (start or stop existing container)
- 
- 
- 

 
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
