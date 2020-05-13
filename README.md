# TIL

Random programming stuff I always forget and spend too much time looking up again

- [Python](#python)
  - [CLI](#cli)
    - [Execute python command directly on the CLI](#execute-python-command-directly-on-the-cli)
    - [Execute python module directly on the CLI](#execute-python-module-directly-on-the-cli)
  - [Conda](#conda)
    - [Install packages and related options](#install-packages-and-related-options)
    - [Create new environment](#create-new-environment)
    - [Switch to environments and back](#switch-to-environments-and-back)
    - [List all environments](#list-all-environments)
    - [Add a conda env to jupyter notebooks](#add-a-conda-env-to-jupyter-notebooks)
- [SSH](#ssh)
  - [General stuff](#general-stuff)
    - [Connect to an instance via .pem file](#connect-to-an-instance-via-pem-file)
    - [Create an SSH tunnel (for example for jupyter notebooks)](#create-an-ssh-tunnel-for-example-for-jupyter-notebooks)
    - [Copying files between local computer and instance](#copying-files-between-local-computer-and-instance)
- [Bash](#bash)
  - [General stuff](#general-stuff-1)
    - [Count the number of files in a directory](#count-the-number-of-files-in-a-directory)
    - [See volumes and use](#see-volumes-and-use)
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
    - [Get access to bash on a running container](#get-access-to-bash-on-a-running-container)
    - [Launch bash on a container id (like the last image before buid failure)](#launch-bash-on-a-container-id-like-the-last-image-before-buid-failure)
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

## CLI

### Execute python command directly on the CLI

`python -c [python code]`

### Execute python module directly on the CLI

`python -m [python module]`

The module will be looked for anywhere on the `sys.path`

## Conda

### Install packages and related options

`conda install [package]`

flags:

- `-y` for yes : agree to the confirmation
- `-q` for quiet : no progress bar
- `-n` or `--name` : install packages to a specific env
- `-c` or `--channel` : additionnal channels to search for packages, like conda-forge or pypi (or even pytorch, if you want to install torchvision for example)
- `--file` : read package versions from the given file (commonly something like `--file requirements.txt`)

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

### Add a conda env to jupyter notebooks

First make sure to have `ipykernel` installed:

`conda install -c anaconda ipykernel`

Then add the env:

`python -m ipykernel install --user --name=[env name]`

# SSH

## General stuff

### Connect to an instance via .pem file

`ssh -i [.pem file] [user]@[ip adress]`

flags:

- `-v` for verbose mode

### Create an SSH tunnel (for example for jupyter notebooks)

`ssh [user]@[ip address] -i [.pem file] -N -L localhost:[local port]:localhost:[remote port]`

For example to redirect a remote notebook (open through `jupyter notebook --no-browser --port 8887`):
`ssh -v [user]@[ip] -i [.pem file] -N -L localhost:8888:localhost:8887%`

### Copying files between local computer and instance

`scp -i [.pem file] [local file] [user]@[ip]:[remote path]`

To copy entire directories, add the `r` recursive option after the key.

# Bash

## General stuff

### Count the number of files in a directory

`ls [dir] | wc -l`

### See volumes and use

`df -H`

`-H` is to convert to bites or bytes, never remember which one (`-h` is for the other one).

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

### Get access to bash on a running container

`docker exec -t -i [container name] /bin/bash`

### Launch bash on a container id (like the last image before buid failure)

`docker run --rm -it [id_last_working_layer] bash -il`

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
