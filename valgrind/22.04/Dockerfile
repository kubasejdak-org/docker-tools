FROM kubasejdak/base:22.04

# Install valgrind.
RUN sudo apt update && \
    sudo apt install -y valgrind && \
    \
    # Cleanup image.
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
