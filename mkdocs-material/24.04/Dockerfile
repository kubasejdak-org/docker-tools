FROM kubasejdak/base:24.04

# Settings.
ARG MKDOCS_MATERIAL=9.5.44

# Install python3.
RUN sudo apt update && \
    sudo apt install -y python3 python3-pip python3-venv python-is-python3 && \
    sudo -H pip config set global.break-system-packages true && \
    \
    # Install ansible and related tools.
    sudo -H pip install ansible==${MKDOCS_MATERIAL} mkdocs-mermaid2-plugin && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
