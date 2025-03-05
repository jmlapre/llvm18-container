FROM debian:trixie

COPY library-scripts/common-debian.sh /tmp/library-scripts/

RUN apt update \
    && bash /tmp/library-scripts/common-debian.sh \
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install \
    build-essential \
    clang-18 \
    libclang-18-dev \
    libtool \
    python-is-python3 \
    python3-dev \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

USER vscode
