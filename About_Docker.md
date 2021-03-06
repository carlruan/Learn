# [Docker Hub](https://hub.docker.com/)

# [Kubectl cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#zsh)

`docker container run `

## Cheatsheet for Docker CLII

![Complete Docker CLI](https://raw.githubusercontent.com/sangam14/dockercheatsheets/master/dockercheatsheet8.png)

Docker image  
`docker create [options] IMAGE -a, --attach # attach stdout/err -i, --interactive # attach stdin (interactive) -t, --tty # pseudo-tty --name NAME # name your image -p, --publish 5000:5000 # port map --expose 5432 # expose a port to linked containers -P, --publish-all # publish all ports --link container:alias # linking -v, --volume `pwd`:/app # mount (absolute paths needed) -e, --env NAME=hello # env vars `

Dockerfile

`FROM APP:TAG`  
all images must have a FROM.  
If you truly want to start with an empty container, use FROM scratch

`ENV`  
Optional environment variable that's used in later lines and set as envvar when container is running

`RUN`  
Cmd used to build. Can have many runs.

`EXPOSE [port num1] [port num2] ...`  
Expose these ports on the docker virtual network.
You still need to use -p or -P to open/forward these ports on host

`CMD ["cmd1", ["cmd2"], ...]`  
Required: run this command **when container is launched**.
Only one CMD allowed, so if there are multiple, last one wins

`WORKDIR [dir]`  
Change working directory.
Using WORKDIR is preferred to using 'RUN cd /some/path'

`COPY [Source dir] [Destination dir]`  
Copy files to dir.

## Use volumes

Volumes are the preferred mechanism for persisting data generated by and used by Docker containers.

## Compose template

`version:3.9`  
&emsp;`servicename: #a friendly name. this is also DNS name inside network`  
&emsp;&emsp;`image: # Optional if you use build:`

&emsp;&emsp;`command: # Optional, replace the default CMD specified by the image `  
&emsp;&emsp;`environment: # Optional, same as -e in docker run`  
&emsp;&emsp;`volumes: # Optional, same as -v in docker run`  
&emsp;`servicename2:`

`volumes: # Optional, same as docker volume create`

`networks: # Optional, same as docker network create`

## To start:

`docker-compose up`

## To stop

`docker-compose down`

## Enable swarm

`docker swarm init`

## Docker service

Create replicas
