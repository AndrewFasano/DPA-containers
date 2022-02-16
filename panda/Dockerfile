FROM pandare:latest

# Just install some packages: build-essentials for compiling
# and a few text editors

RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qq install -y \
    vim emacs nano
