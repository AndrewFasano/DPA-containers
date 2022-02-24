FROM ubuntu:20.04

# Support whole system x86_64 emulation and arm user mode emulation
ARG TARGET_LIST="x86_64-softmmu,arm-linux-user"

# Setup dependencies
RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qq install -y \
    build-essential \
    gcc g++ git cmake meson \
    vim emacs nano


RUN git clone -b stable-6.1 https://github.com/qemu/qemu.git

# Add source URIs and get qemu build deps
RUN sed -Ei 's/^# deb-src /deb-src /' /etc/apt/sources.list && apt-get update

# Install qemu dependencies. Apt has a different qemu verison but it works
RUN DEBIAN_FRONTEND=noninteractive apt -qq build-dep -y  qemu

# Configure and build QEMU
RUN mkdir /qemu/build && cd /qemu/build && \
    ../configure --enable-plugins \
                 --target-list="${TARGET_LIST}" &&  \
    make -j $(nproc)
