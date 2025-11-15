FROM kubasejdak/base:24.04

# Settings.
ARG ANSIBLE_VERSION=12.2.0

# Install python3.
RUN sudo apt update && \
    sudo apt install -y python-is-python3 python3 python3-pip python3-venv && \
    sudo -H pip config set global.break-system-packages true && \
    \
    # Install ansible and related tools.
    sudo -H pip install ansible==${ANSIBLE_VERSION} ansible-lint cryptography passlib && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
