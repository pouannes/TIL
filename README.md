# TIL

Random programming stuff I always forget and spend too much time looking up again

- [CLI](#cli)
  - [Shortcuts](#shortcuts)
    - [Move cursor at the beginning of the line](#move-cursor-at-the-beginning-of-the-line)
    - [Move cursor at the end of the line](#move-cursor-at-the-end-of-the-line)
    - [Delete all characters from the cursor to the beginning of the line](#delete-all-characters-from-the-cursor-to-the-beginning-of-the-line)
    - [Delete all characters from the cursor the end of the line](#delete-all-characters-from-the-cursor-the-end-of-the-line)
    - [Delete the word to the left of the cursor](#delete-the-word-to-the-left-of-the-cursor)
    - [Redraw the screen at the prompt](#redraw-the-screen-at-the-prompt)
    - [Transpose a character at the cursor with a character to the left of the cursor](#transpose-a-character-at-the-cursor-with-a-character-to-the-left-of-the-cursor)
- [gcloud CLI](#gcloud-cli)
  - [General stuff](#general-stuff)
    - [Get current project id](#get-current-project-id)
    - [Change current project](#change-current-project)
- [Python](#python)
  - [CLI](#cli-1)
    - [Execute python command directly on the CLI](#execute-python-command-directly-on-the-cli)
    - [Execute python module directly on the CLI](#execute-python-module-directly-on-the-cli)
  - [Conda](#conda)
    - [Install packages and related options](#install-packages-and-related-options)
    - [Create new environment](#create-new-environment)
    - [Switch to environments and back](#switch-to-environments-and-back)
    - [List all environments](#list-all-environments)
    - [Add a conda env to jupyter notebooks](#add-a-conda-env-to-jupyter-notebooks)
- [SSH](#ssh)
  - [General stuff](#general-stuff-1)
    - [Connect to an instance via .pem file](#connect-to-an-instance-via-pem-file)
    - [Create an SSH tunnel (for example for jupyter notebooks)](#create-an-ssh-tunnel-for-example-for-jupyter-notebooks)
    - [Copying files between local computer and instance](#copying-files-between-local-computer-and-instance)
- [Bash](#bash)
  - [git](#git)
    - [list remotes](#list-remotes)
    - [remove existing remote](#remove-existing-remote)
    - [add origin remote](#add-origin-remote)
    - [Undo last commit (and preserve the changes done to the files)](#undo-last-commit-and-preserve-the-changes-done-to-the-files)
    - [Undo last commit (and DO NOT preserve the changes done to the files)](#undo-last-commit-and-do-not-preserve-the-changes-done-to-the-files)
  - [General stuff](#general-stuff-2)
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
    - [Remove all containers ever created still in memory](#remove-all-containers-ever-created-still-in-memory)
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
- [Kubernetes](#kubernetes)
  - [Concepts](#concepts)
    - [What is a k8s node?](#what-is-a-k8s-node)
    - [What is a k8s cluster?](#what-is-a-k8s-cluster)
    - [What is meant by Imperative vs Declarative deployments?](#what-is-meant-by-imperative-vs-declarative-deployments)
    - [Is it best to use Imperative or Declarative deployments?](#is-it-best-to-use-imperative-or-declarative-deployments)
    - [Objects](#objects)
      - [What are the k8s objects?](#what-are-the-k8s-objects)
      - [What is a Pod?](#what-is-a-pod)
      - [What is a Deployment?](#what-is-a-deployment)
      - [What is a Service?](#what-is-a-service)
      - [What is a NodePort service?](#what-is-a-nodeport-service)
      - [What is a ClusterIP Service?](#what-is-a-clusterip-service)
      - [What is a LoadBalancer Service?](#what-is-a-loadbalancer-service)
    - [Volumes (in a general sense)](#volumes-in-a-general-sense)
      - [What are volumes in k8s?](#what-are-volumes-in-k8s)
      - [What are persistent volumes in k8s?](#what-are-persistent-volumes-in-k8s)
      - [What are persistent volume claims?](#what-are-persistent-volume-claims)
  - [minikube](#minikube)
    - [Start a new minikube VM](#start-a-new-minikube-vm)
    - [Start a new minikube VM with a specific driver](#start-a-new-minikube-vm-with-a-specific-driver)
    - [Stop and delete a running minikube VM](#stop-and-delete-a-running-minikube-vm)
    - [Get ip where minikube VM is exposed](#get-ip-where-minikube-vm-is-exposed)
    - [Reconfigure the docker CLI to connect to docker-server inside minikube](#reconfigure-the-docker-cli-to-connect-to-docker-server-inside-minikube)
  - [kubectl](#kubectl)
    - [Apply a configuration file](#apply-a-configuration-file)
    - [See running objects of a given kind](#see-running-objects-of-a-given-kind)
    - [(imperatively) change a container version](#imperatively-change-a-container-version)
    - [Get the logs of a container](#get-the-logs-of-a-container)
    - [Exec a command inside a container](#exec-a-command-inside-a-container)

# CLI

## Shortcuts

### Move cursor at the beginning of the line

`ctrl + a`

### Move cursor at the end of the line

`ctrl + e`

### Delete all characters from the cursor to the beginning of the line

`ctrl + u`

### Delete all characters from the cursor the end of the line

`ctrl + k`

### Delete the word to the left of the cursor

`ctrl + w`

### Redraw the screen at the prompt

`ctrl + l`

### Transpose a character at the cursor with a character to the left of the cursor

`ctrl + t`

# gcloud CLI

## General stuff

### Get current project id

`gcloud config get-value project`

### Change current project

`gcloud config set project [project id]`

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

## git

### list remotes

`git remote -v`

### remove existing remote

`git remote rm [remote name]`

e.g. `git remote rm origin`

### add origin remote

`git remote add origin [remote link]`

### Undo last commit (and preserve the changes done to the files)

`git reset --soft HEAD~1`

`HEAD~1` means you want to reset the `HEAD` to one commit before in the log history.

### Undo last commit (and DO NOT preserve the changes done to the files)

`git reset --hard HEAD~1`

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

### Remove all containers ever created still in memory

`docker system prune`

### Download an image

`docker pull [image name]`

### Append a command to a docker run

`docker run [image] [command]`

e.g. `docker run ubuntu sleep 5`

### Execute a command on a running container

`docker exec [image name] [command]`

### Get access to bash on a running container

`docker exec -t -i [container name] /bin/bash`

You can also just put `-it` instead of `-i -t`, and `sh` instead of `/bin/bash`

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

# Kubernetes

## Concepts

### What is a k8s node?

A k8s node is a single VM instance that is running k8s and have different objects within it.

### What is a k8s cluster?

A k8s cluster is a set of k8s nodes. It's usually the level at which you work in k8s.

### What is meant by Imperative vs Declarative deployments?

There's two ways to interact with k8s:

- Imperatively: you use kubectl to directly tell k8s what you want, for example something like "create a pod with this container inside it"
- Declaratively: you use a config file detailing the way you want your k8s cluster to behave, and let the k8s engine figure out how to best reach the associated state and behaviour.

### Is it best to use Imperative or Declarative deployments?

Usually it's best to use declarative deployments: it's what makes k8s really powerful. You just tell k8s what you want and let it figure out how to do it.

However there's some actions that are way easier to do declaratively and in those cases you may use imperative deployments. For example, making existing pods update their containers image version is more straightforward to do in a declarative fashion

### Objects

#### What are the k8s objects?

In Kubernetes you mainly work through objects that you define with yaml configuration files. The k8s engine then works to respect what's defined in those config files as much as it can. For example if you want 8 workers containers, it will work to have 8 at all times; if one goes down it will try to boot one back up (though this is configurable behaviour).

These objects can have lots of different functions, like: running containers, setting up networking between the containers, accepting outside network requests, setting up requests, ...

#### What is a Pod?

A Pod is a k8s object that is used to run containers. Usually only one type of container is run per type of pod, although there can be exceptions. For example, if two containers are very tightly coupled it might make sense to make them run in the same pod.

#### What is a Deployment?

A Deployment is a k8s object that is used to make pods. Usually you don't create pods directly yourself; you create Deployments and specify the number and type of pods you want inside it.

#### What is a Service?

A Service is a type of k8s object used for networking between in a k8s cluster.

#### What is a NodePort service?

A NodePort Service is a k8s Service object that exposes a set of pods to the outside world. It's mainly used for devlopment purposes.

#### What is a ClusterIP Service?

A ClusterIP Service is a k8s Service object that exposes a set of pods to other objects in the cluster. It's used to set up networking between objects in a cluster, _not_ with the outside world.

#### What is a LoadBalancer Service?

It's a k8s Service object which is a legacy way of getting network traffic into a cluster.

### Volumes (in a general sense)

#### What are volumes in k8s?

In k8s you have to be careful when you speak about volumes: there's the generic "volume" meaning in CS which means some part of a disk filesystem, but k8s also has its own volume definition.

A Volume in k8s is a part of a container filesystem. So when you create a Volume inside a container, it will die with it.

#### What are persistent volumes in k8s?

Persistent volumes are k8s volumes created at the level of a pod. So different containers inside the same pod can access the same volume if needed, and if a container dies the volume persists. However, the persistent volume dies with the pod.

#### What are persistent volume claims?

Persistent volume claims are a k8s volumes created at the level of a cluster. Thus they aren't affected by the death of a specific pod. It's called a claim because you ask the k8s engine for the volume, which might or might not be already provisioned.

## minikube

### Start a new minikube VM

`minikube start`

### Start a new minikube VM with a specific driver

`minikube start -driver=[driver name]`

### Stop and delete a running minikube VM

`minikube delete`

### Get ip where minikube VM is exposed

`minikube ip`

### Reconfigure the docker CLI to connect to docker-server inside minikube

`eval $(minikube docker-env)`

Only works for current terminal window

## kubectl

### Apply a configuration file

`kubectl apply -f [file name]`

### See running objects of a given kind

`kubectl get [object kind]`

e.g. `kubectl get pods`

### (imperatively) change a container version

`kubectl set image [object type]/[object name] [container name]=[new image to use]`

e.g.

`kubectl set image deployment/client-deployment client=pouannes/image_name:latest`

### Get the logs of a container

`kubectl logs [pod name]`

### Exec a command inside a container

`kubectl exec [pod name]`
