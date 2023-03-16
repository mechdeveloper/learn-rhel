FROM mcr.microsoft.com/devcontainers/universal:2
ENV ANSIBLE_HOST_KEY_CHECKING=False
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install sshpass