FROM kubasejdak/base:24.04

# Settings.
ARG MKDOCS_MATERIAL_VERSION=9.7.0

# Install python3.
RUN sudo apt update && \
    sudo apt install -y python-is-python3 python3 python3-pip python3-venv && \
    sudo -H pip config set global.break-system-packages true && \
    \
    # Install material for mkdocs and related tools.
    sudo -H pip install mkdocs-material[imaging]==${MKDOCS_MATERIAL_VERSION} \
    mkdocs-drawio \
    mkdocs-macros-plugin \
    mkdocs-mermaid2-plugin \
    mkdocs-redirects \
    mkdocs-rss-plugin \
    mike \
    mkdoxy && \
    sudo apt install -y doxygen libcairo2 python3-pyparsing python3-six && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
