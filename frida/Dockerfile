FROM ubuntu:20.04
RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qq install -y \
    vim emacs nano \
    build-essential curl git lib32stdc++-9-dev \
    libc6-dev-i386 nodejs npm python3-dev python3-pip

RUN pip3 install colorama prompt-toolkit pygments
RUN pip3 install frida-tools frida
RUN npm install frida

RUN mkdir -p /frida/examples/
COPY examples/ /frida/examples
WORKDIR /frida
