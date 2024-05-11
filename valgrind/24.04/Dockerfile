FROM kubasejdak/base:24.04

# Settings.
ARG VALGRIND_VERSION=3.23.0
ARG VALGRIND_URL=https://sourceware.org/pub/valgrind/valgrind-${VALGRIND_VERSION}.tar.bz2

# Compile valgrind and install libc6-dbg.
RUN sudo apt install -y wget build-essential gcc && \
    wget --no-check-certificate ${VALGRIND_URL} && \
    tar -xf $(basename ${VALGRIND_URL}) && \
    cd valgrind-${VALGRIND_VERSION} && \
    ./configure && \
    make -j$(nproc) && \
    sudo make install && \
    cd - && \
    rm $(basename ${VALGRIND_URL}) && \
    rm -rf valgrind-${VALGRIND_VERSION} && \
    sudo apt install -y libc6-dbg && \
    \
    # Cleanup image.
    sudo apt remove -y wget build-essential gcc && \
    sudo apt autoremove -y && \
    sudo apt clean && \
    sudo rm -rf /var/lib/apt/lists/*
