FROM kubasejdak/base:24.04

# Settings.
ARG ANSIBLE_VERSION=10.2.0

ENV PIPX_HOME=/opt/pipx
ENV PIPX_BIN_DIR=${PIPX_HOME}/bin
ENV PATH=${PIPX_BIN_DIR}:${PATH}

# Install python3 and pipx.
RUN sudo apt update && \
    sudo apt install -y python3 python3-pip python3-venv python-is-python3 && \
    sudo -H pip config set global.break-system-packages true && \
    sudo mkdir -p -m 777 ${PIPX_HOME} && \
    sudo mkdir -p -m 777 ${PIPX_BIN_DIR} && \
    sudo -H pip install pipx && \
    \
    # Install ansible and related tools.
    pipx install --include-deps ansible==${ANSIBLE_VERSION} && \
    pipx inject --include-apps ansible ansible-lint && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
