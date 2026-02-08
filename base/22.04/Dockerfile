FROM ubuntu:22.04
LABEL maintainer="Kuba Sejdak (kuba.sejdak@gmail.com)"

# Settings.
ARG USERNAME=ubuntu
ARG USER_UID=1000
ARG USER_GID=${USER_UID}

ENV TZ=Europe/Warsaw

# Prepare APT for installing packages.
RUN ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo "APT::Install-Recommends \"false\";" >> /etc/apt/apt.conf && \
    echo "APT::Install-Suggests \"false\";" >> /etc/apt/apt.conf && \
    apt update && \
    apt upgrade -y && \
    apt install -y tzdata && \
    \
    # Create default user.
    groupadd --gid ${USER_GID} ${USERNAME} && \
    useradd --uid ${USER_UID} --gid ${USER_GID} -s /bin/bash -m ${USERNAME} && \
    apt install -y sudo && \
    echo ${USERNAME} ALL=\(root\) NOPASSWD:ALL >> /etc/sudoers.d/${USERNAME} && \
    chmod 0440 /etc/sudoers.d/${USERNAME}

USER ${USERNAME}
WORKDIR /home/${USERNAME}
ENV HISTFILE=""
ENV LC_ALL=en_US.UTF-8
ENV PATH=/home/${USERNAME}/.local/bin:$PATH
ENV USER=${USERNAME}

# Configure locales.
RUN sudo apt install -y locales && \
    sudo locale-gen en_US.UTF-8 && \
    \
    # Install git and SSH client.
    sudo apt install -y git openssh-client && \
    sudo git config --system --add safe.directory '*' && \
    \
    # Install additional packages.
    sudo apt install -y bash-completion bc ca-certificates curl file less lsof openssh-client tmux tree vim wget jq && \
    \
    # Create common project directories.
    sudo mkdir -p -m 777 /var/log/ks
