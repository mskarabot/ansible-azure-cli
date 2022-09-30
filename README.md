# Introduction

![Deploy Preview](https://github.com/mskarabot/ansible-azure-cli/actions/workflows/deploy-to-dockerhub.yml/badge.svg)
![Release to DockerHub](https://github.com/mskarabot/ansible-azure-cli/actions/workflows/release-to-dockerhub.yml/badge.svg)

This project builds container image with Ansible, Azure CLI and Azure Ansible Collection on top of Ubuntu 20.04.

## Get started

### Using container image from DockerHub

#### Pull image from DockerHub

```bash
docker pull docker.io/skmi/ansible-azure-cli:latest
```

#### Use image for as local run-time

```bash
docker run -it --rm --name ansible-azure-cli -v /mnt/c/adev/workspace:/workspace -w="/workspace/" docker.io/skmi/ansible-azure-cli:latest
```

### Manually build container image locally

#### Ubuntu

```bash
docker build docker/ubuntu -t ansible-azure-cli-ubuntu
```

## Changelog

For version history and release notes, please visit [here](CHANGELOG.md) or look at the git history for more detailed information.
