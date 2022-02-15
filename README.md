![Deploy Preview](https://github.com/mskarabot/ansible-azure-cli/actions/workflows/deploy-to-dockerhub.yml/badge.svg)
![Release to DockerHub](https://github.com/mskarabot/ansible-azure-cli/actions/workflows/release-to-dockerhub.yml/badge.svg)

# Introduction 
This project builds container image with Ansible, Azure CLI and Azure Ansible Collection on top of Alpine Linux.

# Get started

## Manually build container image locally

> Note: 'podman' is like 'docker' but better

### Ubuntu
```bash
podman build docker/ubuntu -t ansible-azure-cli-ubuntu
```
### Alpine
```bash
podman build docker/alpine -t ansible-azure-cli-alpine
```



### CentOS
```bash
podman build docker/centos -t ansible-azure-cli-centos
```

## Example usage of the container image from DockerHub
```bash
podman run -it --rm --name ansible-azure-cli -v /mnt/c/adev/workspace:/workspace -w="/workspace/" docker.io/skmi/ansible-azure-cli:latest
```

# Change Log
Changes of this project are described in a formal change log found [here](CHANGELOG.md) 