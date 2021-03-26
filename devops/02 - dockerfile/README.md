## Prerequsite

* Docker 19.03 or greater

## Legend

A node.js application that outputs "Hello world!". 
There is a dockerfile and application code in example/app.js.
You need to optimize the Dockerfile by correcting or adding steps, rewrite the dockerfile to output `Hello ${ENV}`, where `${ENV}` is set via ENV in dockerfile and it is set to the ip address of the running container.

## Questions

1. What is Docker? Which technology is it based on?  
A:  
Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers.
Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.
Because all of the containers share the services of a single operating system kernel, they use fewer resources than virtual machines.  
https://en.wikipedia.org/wiki/Docker_(software)

2. Look at the Docker file – what would you change in it?  
A:  
	Use a LTS and specific tested version of the base image which is lighter, may be based on Alpine Linux.
	Reduce amount of layers and use multistage build.
	Add maintainer info and comments for each logical block.

3. How do I pass variables to the Docker file when building and running the container?  
A:  
	When building:  
		In the Dockerfile: 	ARG ArgVarName DefaultValue  
		Command line:		docker build --build-arg ArgVarName=Value  
	When running:  
		In the Dockerfile:      ENV EnvVarName DefaultValue  
		Command line:           docker run -e EnvVarName=Value  

## Tasks

* Dockerfile - Hello ${ENV}, where env is the ip address
A:
	When building the image we cannot determine an IP address.

* Multi-stage build – change the Dockerfile to make it multi-stage.
A:
	Dockerfile will be updated.
