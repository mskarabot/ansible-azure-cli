# Introduction 
This project builds container image with Ansible and Azure CLI installed on top of CentOS 7

# Example usage of the container image
```bash
podman run -it --rm --name ansible-azure-cli -v /mnt/c/adev/workspace:/workspace -w="/workspace/" docker.io/skmi/ansible-azure-cli:latest
```

