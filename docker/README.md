Run Microservices Atom Demo with Docker Compose and Docker Machine
==================================================

Docker Machine can create virtual machines to run Docker on. It
supports Virtual Box but also many other technologies including
several clouds. Docker Compose create all the Docker containers needed
fot the systems.

To run the demo:

- Install Maven, see https://maven.apache.org/download.cgi
- Install Virtual Box from https://www.virtualbox.org/wiki/Downloads
- Install Docker Compose, see
https://docs.docker.com/compose/#installation-and-set-up
- Install Docker, see https://docs.docker.com/installation/
- Install Docker Machine, see https://docs.docker.com/machine/#installation
- Go to directory `microservice-atom` and run `mvn package` there
- Execute `docker-machine create  --virtualbox-memory "4096" --driver
  virtualbox dev` . This will create a new environment called `dev`with Docker
  Machine. It will be virtual machine in Virtual Box with 4GB RAM.
- Execute `eval "$(docker-machine env dev)"` (Linux / Mac OS X). You
     might need to set your shell: `eval "$(docker-machine env --shell
     bash dev)"`. For Windows it's
    `docker-machine.exe env --shell powershell dev` (Windows,
    Powershell) /  `docker-machine.exe env --shell cmd dev` (Windows,
    cmd.exe). Now the docker tool will use the newly created virtual
    machine as environment.
- Change to the directory `docker` and run `docker-compose
   build`followed by `docker-compose up -d`. 


The result should be:

- Docker Compose builds the Docker images and runs them.
- Use `docker-machine ip dev` to find the IP adress of the virtual machine.
- You can access the order application at http://ipadresss:8080/ . 
- You can find the shipping application at http://ipadresss:8081/ .
- The invoicing application runs at http://ipadresss:8081/ .

- Use `docker-machine rm dev` to destroy the virtual machine.
