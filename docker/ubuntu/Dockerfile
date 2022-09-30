#######################################################################################################################
#
# Combination from:
# https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu
# https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt
#######################################################################################################################

FROM ubuntu:20.04

ENV LANGUAGE="C.UTF-8"
ENV LANG="C.UTF-8"
ENV DEBIAN_FRONTEND="noninteractive"
ENV LC_ALL="C.UTF-8"

# install Software Properties Common
RUN apt-get update; \
    apt-get upgrade --yes; \
    apt-get install --no-install-recommends --yes software-properties-common

# install ansible
RUN add-apt-repository --yes --update ppa:ansible/ansible; \
    apt-get install --no-install-recommends --yes ansible

# install step-by-step azure cli
RUN apt-get --yes install ca-certificates curl apt-transport-https lsb-release gnupg; \
    curl -sL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null; \
    AZ_REPO=$(lsb_release -cs); \
    echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | tee /etc/apt/sources.list.d/azure-cli.list; \
    apt-get update --yes; \
    apt-get install --no-install-recommends --yes azure-cli

# install pip3
RUN apt-get --yes --no-install-recommends install python3; \
    apt-get --yes --no-install-recommends install python3-pip

# install terraform
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor | tee /etc/apt/trusted.gpg.d/hashicorp.gpg > /dev/null; \
    HSH_REPO=$(lsb_release -cs); \
    echo "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $HSH_REPO main" | tee /etc/apt/sources.list.d/terraform.list; \
    apt-get update --yes; \
    apt-get install --yes --no-install-recommends terraform

# install helm
RUN curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/helm.gpg > /dev/null; \
    apt-get install apt-transport-https --yes; \
    echo "deb https://baltocdn.com/helm/stable/debian/ all main" | tee /etc/apt/sources.list.d/helm-stable-debian.list; \
    apt-get update --yes; \
    apt-get install --yes --no-install-recommends helm

# Install bash linter
RUN apt-get install --yes shellcheck

# Install robot framework linter
RUN pip install robotframework-robocop

# install robot framework
RUN pip install robotframework
