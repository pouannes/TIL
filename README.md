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

or when conda isn't configured for your shell:

`source activate [env]`

`conda deactivate`


### List all environments
`conda info --envs`

The current env has a little star


# Bash

## General stuff

### Count the number of files in a directory
`ls [dir] | wc -l`


# Docker
