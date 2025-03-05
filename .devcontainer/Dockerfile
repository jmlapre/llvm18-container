FROM debian:trixie

COPY library-scripts/common-debian.sh /tmp/library-scripts/

RUN apt update \
    && bash /tmp/library-scripts/common-debian.sh \
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install clang-18 libclang-18-dev \
    && rm -rf /var/lib/apt/lists/*

USER vscode
