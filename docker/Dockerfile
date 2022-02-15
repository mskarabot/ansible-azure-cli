#######################################################################################################################
# (C)2022 Mihael Skarabot, private
#
# Combination from:
# https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu
# https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt
#######################################################################################################################

FROM ubuntu:20.04

ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV DEBIAN_FRONTEND=noninteractive 

# install Software Properties Common
RUN apt update; \
    apt upgrade --yes; \
    apt install --yes software-properties-common

# install ansible
RUN add-apt-repository --yes --update ppa:ansible/ansible; \
    apt install --yes ansible; \
    ansible --version

# install step-by-step azure cli
RUN apt --yes install ca-certificates curl apt-transport-https lsb-release gnupg; \
    curl -sL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null; \
    AZ_REPO=$(lsb_release -cs); \
    echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | tee /etc/apt/sources.list.d/azure-cli.list; \
    apt update --yes; \
    apt install --yes azure-cli

# install pip3
RUN add-apt-repository --yes --update ppa:deadsnakes/ppa; \
    apt update; \
    apt --yes install python3-pip; \
    python3 --version; \
    pip3 --version

# install azure ansible collection
RUN pip3 install --upgrade pip; \
    pip3 install --upgrade virtualenv; \
    ansible-galaxy collection install azure.azcollection; \
    pip3 install -r ~/.ansible/collections/ansible_collections/azure/azcollection/requirements-azure.txt
