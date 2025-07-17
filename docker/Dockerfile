FROM arm32v7/debian:bullseye

# Install build and runtime dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    gcc \
    libc6-dev \
    pkg-config \
    && apt-get clean

WORKDIR /app

COPY . .

# Build + Package
RUN mkdir build && cd build && \
    cmake .. -DCMAKE_SYSTEM_PROCESSOR=armhf -DCMAKE_INSTALL_PREFIX=/usr && \
    cmake --build . && \
    cpack -G DEB

# Debug: Show what's in the deb package
RUN dpkg-deb -c build/*.deb

# Install the generated package
RUN dpkg -i build/*.deb || apt-get -f install -y

# Final CMD
CMD ["/usr/bin/hello"]