# Inception

## Docker

### What is Docker?
- Docker carves up a running Linux system into small containers, each of which is it's own sealed little world, with it's own programs, and it's own everything. All isolated from anything else. 
- These containers are designed to be portable so they can be shipped from one place to anotherand Docker does the work of getting these containers to and from your systems. 
- Docker also builds these containers for you.
- and it's a social platform to help you find and share containers with others who may have already built very similar work that you can build on top of. 

NOTE: And let's get it up front, that Docker is not virtual machines. There's only a single operating system running. That operating system is just carved up into isolated little spaces.

### What is a Container?
- A container is a self contained sealed unit of software.
- It has everything in it that is needed to run that code. I mean all of it, batteries included, operating system included.
- A container includes:
    - it has all of the code.
    - all of the configs.
    - contains all the processes within that container.
    - it has all of the networking to allow these containers to talk to the other containers they're supposed to be able to talk to, and nothing else.
    - It has all the dependencies that your system needs, bundled up in that container.
    - And it even includes just enough of the operating system to run your code.

### How does it works
So the way it works, it takes all the services that make up a Linux server. Networking, storage, code, interprocess communication, the whole works, and it makes a copy of that in the Linux Kernel for each container. So each container has its own little world that it can't see out of, and other containers can't see in. You might have one container on a system running Red Hat Linux, serving a database, through a virtual network to another container running Ubuntu Linux, running a web server that talks to that database, and that web server might also be talking to a caching server that runs in a SUSE Linux based container. The important part to understand is it doesn't matter which Linux each container is running on, it just has to be a Linux. And Docker is the program which manages all of this. Sets it up, monitors it, and tears it down when it's no longer needed.

### About Docker

- Docker is a client program, named Docker, it's a command you type at the terminal.
- It's also a server program that listens for messages from that command, and manages a running Linux system. 
- Docker has a program which builds containers from code. It takes your code along with its dependencies and bundles it up and then seals it into a container.
- And it's a service that distributes these containers across the internet and makes it so you can find other's work, and the right people can find your work. 
- It is also a company that makes all of these.


### Docker common commands

Here is a list of some common Docker commands:

- `docker build`: Build an image from a Dockerfile
- `docker run`: Run a container based on an image
- `docker start`: Start an existing container
- `docker stop`: Stop a running container
- `docker rm`: Remove a stopped container
- `docker exec`: Run a command inside a running container
- `docker pull`: Download an image from a registry
- `docker push`: Upload an image to a registry
- `docker images`: List all images on the local machine
- `docker ps`: List all running containers
- `docker logs`: View the logs for a container

- `docker inspect`: View detailed information about a container or image.
- `docker login`: Log in to a registry.
- `docker logout`: Log out from a registry.
- `docker tag`: Tag an image in the local repository.
- `docker save`: Save an image to a tar archive.
- `docker load`: Load an image from a tar archive.
- `docker system prune`: Remove unused data from the local system.
- `docker volume create`: Create a volume.
- `docker volume rm`: Remove one or more volumes.

These are just a few of the many Docker commands available. For a complete list, you can refer to the Docker documentation or use the docker command followed by `--help`.





### TOBEDELETEDLATER
- docker commit: turns a container into an image. 
- -d: for detached.


## NGINX - Configure a virtual host
- unlink the default config:
    - `ls -ltr /etc/nginx/sites-enabled/`
    - `unlink /etc/nginx/sites-enabled/default`
- `vim /etc/nginx/conf.d/binaryville.conf`
    ```conf
    server {
        listen 80;
        root /var/www/binaryville;
    }
    ```
- `nginx -t` - test new configuration
- `systemctl reload nginx` to reload the configuration
- `systemctl status nginx` to check nginx status
- `mkdir -p /var/www/binaryville`
- `echo "site coming soon." > /var/www/binaryville/index.html`