FROM ubuntu:20.04

RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qq install -y \
    build-essential vim emacs nano \
    valgrind linux-tools-generic git
