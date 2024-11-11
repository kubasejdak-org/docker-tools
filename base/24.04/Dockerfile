FROM ubuntu:24.04
LABEL maintainer="Kuba Sejdak (kuba.sejdak@gmail.com)"

# Settings.
ARG USERNAME=ubuntu

ENV TZ=Europe/Warsaw

# Prepare APT for installing packages.
RUN ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo "APT::Install-Recommends \"false\";" >> /etc/apt/apt.conf && \
    echo "APT::Install-Suggests \"false\";" >> /etc/apt/apt.conf && \
    apt update && \
    apt upgrade -y && \
    apt install -y tzdata && \
    \
    # Set default user permissions.
    apt install -y sudo && \
    echo ${USERNAME} ALL=\(root\) NOPASSWD:ALL >> /etc/sudoers.d/${USERNAME} && \
    chmod 0440 /etc/sudoers.d/${USERNAME}

USER ${USERNAME}
WORKDIR /home/${USERNAME}
ENV HISTFILE=""
ENV LC_ALL=en_US.UTF-8
ENV USER=${USERNAME}

# Configure locales.
RUN sudo apt install -y locales && \
    sudo locale-gen en_US.UTF-8 && \
    \
    # Install git and SSH client.
    sudo apt install -y software-properties-common gnupg && \
    sudo add-apt-repository ppa:git-core/ppa && \
    sudo apt install -y git openssh-client && \
    sudo apt remove -y software-properties-common gnupg && \
    sudo git config --global --add safe.directory '*' && \
    \
    # Install additional packages.
    sudo apt install -y less bash-completion openssh-client file wget vim tree && \
    \
    # Create common project directories.
    sudo mkdir -p -m 777 /var/log/ks
