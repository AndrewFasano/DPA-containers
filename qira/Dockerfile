FROM ubuntu:20.04

RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qq install -y \
    build-essential vim emacs nano git \
    gcc-multilib g++-multilib lib32z1 git curl python python-dev wget \
    pkg-config zlib1g-dev libglib2.0-dev libpixman-1-dev \
    libjpeg8-dev zlib1g-dev

RUN git clone https://github.com/geohot/qira.git /qira

WORKDIR /qira

# Install python2 pip - it's not in apt 
RUN wget https://bootstrap.pypa.io/pip/2.7/get-pip.py && python ./get-pip.py

# install python deps and make a fake venv (we installed dependnecies in container for all users)
RUN python -m pip install --upgrade -r requirements.txt && mkdir -p /qira/venv/bin && echo '' > /qira/venv/bin/activate

# Build qira's qemu fork - Note there's a bug in the main repo, so we build one that's available from a PR
#RUN git clone https://github.com/geohot/qemu.git --depth 1 --branch qira /qira/tracers/qemu/qemu # BUG: https://github.com/geohot/qira/issues/236
RUN git clone https://github.com/mephi42/qemu.git --depth 1 --branch qira /qira/tracers/qemu/qemu
RUN cd /qira/tracers/qemu/qemu && ./configure --target-list=i386-linux-user,x86_64-linux-user,arm-linux-user,ppc-linux-user,aarch64-linux-user,mips-linux-user,mipsel-linux-user --enable-tcg-interpreter --enable-debug-tcg --cpu=unknown --python=python && make -j $(nproc) -C /qira/tracers/qemu/qemu

# Link qira
RUN ln -sf /qira/qira /usr/local/bin/qira
