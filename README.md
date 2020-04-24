# TIL
Random programming stuff I always forget and spend too much time looking up again

- [Python](#python)
  - [Conda](#conda)
    - [Create new environment](#create-new-environment)
    - [Switch to environments and back](#switch-to-environments-and-back)
    - [List all environments](#list-all-environments)
- [Bash](#bash)
  - [General stuff](#general-stuff)
    - [Count the number of files in a directory](#count-the-number-of-files-in-a-directory)
- [Docker](#docker)
  - [Docker CLI](#docker-cli)
    - [Start a container (and flags)](#start-a-container-and-flags)
    - [List containers](#list-containers)
    - [Stop a container](#stop-a-container)
    - [Remove a container](#remove-a-container)
    - [List available images (locally)](#list-available-images-locally)
    - [Remove an image](#remove-an-image)
    - [Download an image](#download-an-image)
    - [Append a command to a docker run](#append-a-command-to-a-docker-run)
    - [Execute a command on a running container](#execute-a-command-on-a-running-container)
    - [Run the container in the background mode (detach)](#run-the-container-in-the-background-mode-detach)
    - [Attach back a container](#attach-back-a-container)
    - [map stdin of host to docker container's](#map-stdin-of-host-to-docker-containers)
    - [Port mapping](#port-mapping)
    - [Data persistance / volume mapping](#data-persistance--volume-mapping)
    - [Inspect container (all details, including env variables)](#inspect-container-all-details-including-env-variables)
    - [View logs of container](#view-logs-of-container)
    - [Pass env variable](#pass-env-variable)
    - [Build an image](#build-an-image)
    - [Send image to docker hub](#send-image-to-docker-hub)
  - [Dockerfile and building an image](#dockerfile-and-building-an-image)
    - [Specify the base image](#specify-the-base-image)
    - [Run commands](#run-commands)
    - [Copy directory](#copy-directory)
    - [Specify command ran when the container is run](#specify-command-ran-when-the-container-is-run)


# Python

## Conda

### Create new environment

`conda create --name [myenv]`

Additionnal flags for `conda create`:
- `-y` to agree directly (no confirmation)
- `-n` in place of `--name`
- Just put the package after everything to install them
- `[package name]=[version]` to specify a version, e.g. `python=3.6` or `scipy=0.15.0`

### Switch to environments and back

`conda activate [env]`

or when conda isn't configured for your shell: `source activate [env]`

`conda deactivate`


### List all environments
`conda info --envs`

The current env has a little star


# Bash

## General stuff

### Count the number of files in a directory
`ls [dir] | wc -l`


# Docker

## Docker CLI

### Start a container (and flags)

`docker run [container name]`

Either locally, or if it's not found goes to docker hub

flags:
- Run a specific version of an image(a tag): `docker run [image name]:tag`. If no tag is provided, the tag `:latest` is used
- `-i` for interactive mode : link host stdin to container
- `-t` for terminal : attach to the terminal
- `-p` for port, e.g. `-p 80:5000` to link port 80 on host to port 5000 on container
- `-v` for volume : `-v [host dir]:[container dir]` to map the two directories and enable data persistance
- `-e` for env : `-e [ENV VARIABLE]:[value]` to pass env variable within the container 
- `--entrypoint [command]` : overwrite entry point
- `--network=` : specify on which network you want the docker. Default is `bridge`, other options are `--network=none` and `--network=host`

### List containers

`docker ps`

flags:
- `-a` to see all containers, running or not

### Stop a container

`docker stop [image id or name]`

### Remove a container

`docker rm [image name or id]`

### List available images (locally)

`docker images`

### Remove an image

`docker rmi [image name]`

### Download an image

`docker pull [image name]`

### Append a command to a docker run

`docker run [image] [command]`

e.g. `docker run ubuntu sleep 5`

### Execute a command on a running container

`docker exec [image name] [command]`

### Run the container in the background mode (detach)

`docker run -d [image name]`

### Attach back a container

`docker attach [image id]`

### map stdin of host to docker container's

`docker run -i [image name]`

### Port mapping

`docker run -p [local port]:[container port] [image name]`

e.g. `docker run -p 80:5000 [image name]`

### Data persistance / volume mapping

`docker run -v [host dir]:[container dir] [image name]`

e.g. `docker run -v /opt/datadir/:/var/lib/mysql mysql`

### Inspect container (all details, including env variables)

`docker inspect [image name]`

### View logs of container

`docker logs [image id or name]`

### Pass env variable

`docker run -e [VARIABLE_NAME]=[value] [image name]`

### Build an image

`docker build Dockerfile -t [account name]/[image name`

### Send image to docker hub

`docker push [account name]/[image name]`

## Dockerfile and building an image

### Specify the base image

`FROM [image name]`

### Run commands

`RUN [command]`

### Copy directory 

`COPY [image dir] [host dir]`

e.g. `COPY . /opt/source-code`

### Specify command ran when the container is run 

`ENTRYPOINT [command]`

If parameters are given after the the name of the image in the `docker run` command, those parameters will be given to the entry point command.
For example:
`ENTRYPOINT['sleep']` with `docker run [image name] 10` will run `sleep 10`.

You can combine an `ENTRYPOINT` and a `CMD` to have default values.
For example:
```
ENTRYPOINT['sleep']
CMD['5']
```
In that dockerfile the default command run is `sleep 5`, but if you override it as in the previous example, `CMD` will be overwritten and `sleep 10` will be run. 