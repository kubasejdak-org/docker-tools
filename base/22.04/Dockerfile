FROM ubuntu:22.04
LABEL maintainer="Kuba Sejdak (kuba.sejdak@gmail.com)"

# Settings.
ARG USERNAME=builder
ARG USER_UID=1000
ARG USER_GID=${USER_UID}

# Prepare APT for installing packages.
RUN ln -snf /usr/share/zoneinfo/${CONTAINER_TIMEZONE} /etc/localtime && echo ${CONTAINER_TIMEZONE} > /etc/timezone && \
    echo "APT::Install-Recommends \"false\";" >> /etc/apt/apt.conf && \
    echo "APT::Install-Suggests \"false\";" >> /etc/apt/apt.conf && \
    apt update && \
    apt upgrade -y && \
    \
    # Create default user.
    groupadd --gid ${USER_GID} ${USERNAME} && \
    useradd --uid ${USER_UID} --gid ${USER_GID} -s /bin/bash -m ${USERNAME} && \
    apt install -y sudo && \
    echo ${USERNAME} ALL=\(root\) NOPASSWD:ALL >> /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/${USERNAME}

USER ${USERNAME}
WORKDIR /home/${USERNAME}
ENV HISTFILE ""

# Install git and SSH client.
RUN sudo apt install -y software-properties-common gnupg && \
    sudo add-apt-repository ppa:git-core/ppa && \
    sudo apt install -y git openssh-client && \
    git config --global --add safe.directory '*' && \
    \
    # Install additional packages.
    sudo apt install -y less bash-completion openssh-client file && \
    \
    # Create common project directories.
    sudo mkdir -p -m 777 /var/log/ks
