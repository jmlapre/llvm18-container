FROM debian:trixie-20250929-slim

LABEL maintainer="jmlapre@sandia.gov"

COPY library-scripts/common-debian.sh /tmp/library-scripts/

RUN apt-get update \
    && bash /tmp/library-scripts/common-debian.sh \
    && rm -rf /var/lib/apt/lists/*
    
RUN apt-get update \
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install \
    build-essential \
    clang-18 \
    clangd-18 \
    clang-tools-18 \
    libclang-18-dev \
    libtool \
    lld-18 \
    locate \
    python-is-python3 \
    python3-dev \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-18 100 \
    && update-alternatives --install /usr/bin/clang clang /usr/bin/clang-18 100 \
    && update-alternatives --install /usr/bin/clangd clangd /usr/bin/clangd-18 100 \
    && update-alternatives --install /usr/bin/scan-build scan-build /usr/bin/scan-build-18 100 \
    && update-alternatives --install /usr/bin/scan-view scan-view /usr/bin/scan-view-18 100 \
    && update-alternatives --install /usr/bin/lld lld /usr/bin/lld-18 100 \
    && update-alternatives --install /usr/bin/python-config python-config /usr/bin/python3-config 100

USER vscode
# It's too easy to forget this.  Add it to the Dockerfile.
ENV LDFLAGS="-fuse-ld=lld"
