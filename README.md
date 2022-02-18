![Deploy Preview](https://github.com/mskarabot/ansible-azure-cli/actions/workflows/deploy-to-dockerhub.yml/badge.svg)
![Release to DockerHub](https://github.com/mskarabot/ansible-azure-cli/actions/workflows/release-to-dockerhub.yml/badge.svg)

# Introduction 
This project builds container image with Ansible, Azure CLI and Azure Ansible Collection on top of Ubuntu 20.04.
Also dockerfile's for Alpine and CentOS are available, however, they are not built and deployed to DockerHub automatically.  

# Get started

> Note: 'podman' is like 'docker' but better

## Using container image from DockerHub

### Pull image from DockerHub:
```bash
podman pull docker.io/skmi/ansible-azure-cli:latest
```

### Use image for as local run-time:
```bash
podman run -it --rm --name ansible-azure-cli -v /mnt/c/adev/workspace:/workspace -w="/workspace/" docker.io/skmi/ansible-azure-cli:latest
```

## Manually build container image locally

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



# ChangeLog
For version history and release notes, please visit [here](CHANGELOG.md) or look at the git history for more detailed information.
