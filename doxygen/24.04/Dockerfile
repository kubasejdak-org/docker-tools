FROM kubasejdak/base:24.04

# Install doxygen and graphviz.
RUN sudo apt update && \
    sudo apt install -y doxygen graphviz && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
