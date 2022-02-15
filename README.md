![Deploy Preview](https://github.com/skmi/ansible-azure-cli/actions/workflows/deploy-to-dockerhub.yml/badge.svg)
![Release to DockerHub](https://github.com/skmi/ansible-azure-cli/actions/workflows/release-to-dockerhub.yml/badge.svg)

# Introduction 
This project builds container image with Ansible and Azure CLI installed on top of CentOS 7

# Get started
Manually building container image:
```bash
podman build docker -t ansible-azure-cli-local
```

# Example usage of the container image
```bash
podman run -it --rm --name ansible-azure-cli -v /mnt/c/adev/workspace:/workspace -w="/workspace/" docker.io/skmi/ansible-azure-cli:latest
```

# Change Log
Changes of this project are described in a formal change log found [here](CHANGELOG.md) 