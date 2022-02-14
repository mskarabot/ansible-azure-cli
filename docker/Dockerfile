#######################################################################################################################
# (C)2022 Mihael Skarabot, private
#
# Combination from:
# https://docs.microsoft.com/en-us/azure/developer/ansible/configure-in-docker-container?tabs=azure-cli
# https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=dnf
#######################################################################################################################

FROM centos:7

ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

RUN yum check-update; \
    yum install -y gcc libffi-devel python3 epel-release; \
    yum install -y python3-pip; \
    yum install -y wget; \
    yum clean all

RUN pip3 install --upgrade pip; \
    pip3 install --upgrade virtualenv; \
    pip3 install pywinrm[kerberos]; \
    pip3 install pywinrm; \
    pip3 install jmspath; \
    pip3 install requests; \
    python3 -m pip install ansible; \
    ansible-galaxy collection install azure.azcollection; \
    pip3 install -r ~/.ansible/collections/ansible_collections/azure/azcollection/requirements-azure.txt

RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc

RUN echo -e "[azure-cli] \nname=Azure CLI \nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli \nenabled=1 \ngpgcheck=1 \ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | tee /etc/yum.repos.d/azure-cli.repo

RUN yum install -y azure-cli