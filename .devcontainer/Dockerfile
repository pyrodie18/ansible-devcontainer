FROM geerlingguy/docker-ubuntu2204-ansible:latest

LABEL maintainer="Troy Ward"
# Install dependencies.
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    openssh-client \
    && rm -Rf /var/lib/apt/lists/* \
    && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
    && apt-get clean

COPY requirements.txt /tmp/requirements.txt
COPY ansible-requirements.yml /tmp/ansible-requirements.yml

# Install Ansible via Pip.
RUN pip3 install -r /tmp/requirements.txt
RUN ansible-galaxy install -r /tmp/ansible-requirements.yml
