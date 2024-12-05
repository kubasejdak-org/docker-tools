FROM kubasejdak/base:24.04

# Settings.
ARG MKDOCS_MATERIAL_VERSION=9.5.47

# Install python3.
RUN sudo apt update && \
    sudo apt install -y python3 python3-pip python3-venv python-is-python3 && \
    sudo -H pip config set global.break-system-packages true && \
    \
    # Install material fod mkdocs and related tools.
    sudo -H pip install mkdocs-material[imaging]==${MKDOCS_MATERIAL_VERSION} \
    mkdocs-mermaid2-plugin \
    mkdocs-redirects \
    mkdocs-rss-plugin \
    mike && \
    sudo apt install -y python3-pyparsing python3-six libcairo2 && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
