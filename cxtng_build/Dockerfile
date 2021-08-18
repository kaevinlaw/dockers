FROM ubuntu:18.04

# Setup build directory and root user
WORKDIR /cxtng
USER root

# Install dependencies
RUN apt-get -y update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
build-essential \
autoconf \
bison \
ca-certificates \
flex \
texinfo \
help2man \
gawk \
wget \
libtool \
libncurses5-dev \
python3 \
python3-dev \
python3-distutils \
    && apt-get purge -y --auto-remove \
    && apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/*

RUN ln -s -T /usr/bin/make /usr/bin/gmake && ln -s -T /bin/bash /usr/bin/bash && ln -s -T /bin/sed /usr/bin/sed && ln -s -T /bin/grep /usr/bin/grep

RUN adduser --disabled-password --gecos '' cxtng_builder
