FROM ubuntu:latest

# Install necessary libraries
RUN apt-get update && apt-get install -y \
    build-essential \
    clang \
    curl \
    git \
    libftdi-dev \
    libusb-1.0-0-dev \
    pkg-config \
    python3 \
    python3-pip \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Install Rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/root/.cargo/bin:${PATH}"

# Install ice40storm FPGA compiler
RUN git clone https://github.com/cliffordwolf/icestorm.git icestorm \
    && cd icestorm \
    && make -j$(nproc) \
    && make install