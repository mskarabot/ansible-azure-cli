#######################################################################################################################
# (C)2022 Mihael Skarabot, private
#
# Combination from:
# https://github.com/willhallonline/docker-ansible/blob/master/ansible-core/alpine315/Dockerfile
# 
#######################################################################################################################

FROM alpine:3.15

ENV ANSIBLE_VERSION "2.12.2"

# Install Ansible, Python3 and Pip3 on Alpine
RUN apk --no-cache add \
        sudo \
        python3\
        py3-pip \
        openssl \
        ca-certificates \
        sshpass \
        openssh-client \
        rsync \
        git && \
    apk --no-cache add --virtual build-dependencies \
        python3-dev \
        libffi-dev \
        musl-dev \
        gcc \
        cargo \
        openssl-dev \
        libressl-dev \
        build-base && \
    pip3 install --upgrade pip wheel && \
    pip3 install --upgrade cryptography cffi && \
    pip3 install ansible-core==${ANSIBLE_VERSION} ansible && \
    pip3 install mitogen ansible-lint jmespath && \
    pip3 install --upgrade pywinrm && \
    apk del build-dependencies && \
    rm -rf /var/cache/apk/* && \
    rm -rf /root/.cache/pip && \
    rm -rf /root/.cargo

# Create a localhost entry for Ansible
RUN mkdir /ansible && \
    mkdir -p /etc/ansible && \
    echo 'localhost' > /etc/ansible/hosts

# Install Azure CLI
RUN apk add gcc musl-dev python3-dev libffi-dev openssl-dev cargo make && \
    pip install azure-cli

WORKDIR /ansible

CMD [ "sh" ]