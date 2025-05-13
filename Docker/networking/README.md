##########This is a documentation for Docker netwoking concepts and commands:

1.Command to create and run a nginx docker container . Container name : login
docker run -d --name login  nginx:latest

2.login to the container:
docker exec it login /bin/bash

3.Install ping inside the container:
apt-get install iputils-ping -y

4.Check ping version
ping -V

5.Creating another conatiner - logout:
docker run -d --name login  nginx:latest

6.To check the running containers:
docker ps

7.to inspect ip address of a container:
docker inspect login 

8.Ping to logout container from login container , we can do it because we use default out of the box bridge networking.

9. to list all networks :
docker network ls
to delete: docker network rm <container-name>

PART 2 : Logically Isolate one container from other :

1. docker network create secure-network  --> creating a custom bridge network.

2. docker run -d --name finance --network secure-network nginx:latest -->Assigning this network to finance container.

3. inspect finance --> it will say secure-network - it will be isolated from others in terms of subnet .

PART 3 . trying to ping the finance container from login container 
ping <ip-of -finance> --> you will not able to communicate . 

PART -4 . Create a container with host network.
docker run -d --name host-demo --network host nginx:latest --> ip completely different - the networking is host networking.

