## Prerequsite

Docker 19.03 or greater

Docker-compose 1.26 or greater

## Legend

Docker compose with 3 applications (frontend + backend + DB).

### Instructions for running

1. Bootstrap the DB:

`docker-compose up -d db`

`docker-compose run --rm flaskapp /bin/bash -c "cd /opt/services/flaskapp/src && python -c  'import database; database.init_db()'"`

2. Boot up the cluster

`docker-compose up -d`

3. Browse to localhost:8080 to see the app in action.

## Questions

1. What is the difference between Docker Compose and dockerfile? Why do I need Docker Compose?  
A:  
	Docker compose is used to orchestrate several containers while Dockerfile is used  
	to build a Docker image. Actually Docker compose may use Dockerfile for  
	its build command in the docker-compose.yml.  
	Docker compose uses a declarative style where sequence of instructions does not matter.

2. How do I parameterize compose for different environments?  
A:  
	Each environment can use its own specific Docker compose file.  
	Several Docker compose files can be specified on the command line with -f switch.  

3. What types of entities are used in docker-compose and for what purpose?  
A:  
	Following entities can be used: configs, secrets, volumes, networks, services.   
	More details at: https://docs.docker.com/compose/compose-file/compose-file-v3/ 

4. `*` How to output application logs?  
A:  
	docker-compose logs [-options] Service  
	docker logs [-options] ContainerId  

4. `*` How to copy\upload a file from host machine to the container?  
A:  
	docker cp SomeFile ContainerName:/Path/SomeFile  

5. `*` How to save file changes made inside the container?  
A:  
	There are several ways: docker commit, persistent volumes, network storages like block SANs (e.g. iSCSI, etc.)  
	and network file systems like NAS (CIFS, NFS, etc.) or even fuse mounts (like sshfs, ftpfs, etc.).  

## Tasks

* Docker-compose has a bug - investigate it! What would you improve?

* Docker-compose with an environment file. Create 2 different environment files for docker-compose

* `*` Change the `docker-compose.yml` to run through dockerstack with code reuse (don't repeat yourself)

A:
	Will be done.