# Second stage: Create the final image
FROM alpine:latest

# Install Xmrig and other necessary packages
RUN apk --no-cache add \
    git \
    cmake \
    libuv-dev \
    openssl-dev \
    hwloc-dev \
    build-base

# Clone the Xmrig repository and build the software
RUN git clone https://github.com/xmrig/xmrig.git && \
    mkdir xmrig/build && \
    cd xmrig/build && \
    cmake .. && \
    make -j$(nproc)

# Build Xmrig with custom optimization flags
WORKDIR /xmrig
RUN cmake . \
    -DWITH_HWLOC=ON \
    -DWITH_ASM=ON \
    -DWITH_SSL=ON \
    -DWITH_TLS=OFF \
    -DWITH_HTTP=OFF \
    -DWITH_HWLOC=OFF \
    -DWITH_CCACHE=ON \
    -DCMAKE_C_COMPILER=gcc \
    -DARCH=native

RUN make

# Copy the updated config.json from the builder image
# Copy the original config.json to the builder image
COPY ../config/config.json /xmrig/build/config.json

# Create a custom script to start Xmrig
RUN echo -e '#!/bin/sh\n/xmrig/build/xmrig -c /xmrig/build/config.json' > /xmrig/start-xmrig.sh && \
    chmod +x /xmrig/start-xmrig.sh

# Set the entry point for the container
# ENTRYPOINT ["/xmrig/start-xmrig.sh"]
