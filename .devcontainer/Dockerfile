FROM rust:slim-bullseye

ARG USERNAME=vscode
ARG USER_ID=1000
ARG USER_GID=$USER_ID

# Add a user other than root
RUN groupadd -g $USER_GID $USERNAME \
    && useradd -s /bin/bash -u $USER_ID -g $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Automatically install the latest version of packages available listed below
RUN apt-get update \
    && apt-get install -y curl git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
