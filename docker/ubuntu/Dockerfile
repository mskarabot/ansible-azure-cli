#######################################################################################################################
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

# install terraform
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor | tee /etc/apt/trusted.gpg.d/hashicorp.gpg > /dev/null; \
    HSH_REPO=$(lsb_release -cs); \
    echo "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $HSH_REPO main" | tee /etc/apt/sources.list.d/terraform.list; \
    apt update --yes; \
    apt install --yes terraform

# install helm
RUN curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/helm.gpg > /dev/null; \
    apt-get install apt-transport-https --yes; \
    echo "deb https://baltocdn.com/helm/stable/debian/ all main" | tee /etc/apt/sources.list.d/helm-stable-debian.list; \
    apt update --yes; \
    apt install --yes helm
