FROM ubuntu:18.04

# Setup build directory and root user
WORKDIR /scpp
USER root

# Install dependencies
RUN apt-get -y update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
python3 \
python3-pip \
python3-distutils \
python3-setuptools \
python3-venv \
python3-wheel \
python3-protobuf \
python3-jinja2 \
software-properties-common \
gpg-agent \
# For ninja 1.10.1
#ninja-build \
build-essential \
cpio \
ccache \
gdb \
git \
mtd-utils \
qemu-user-static \
rsync \
sharutils \
zip \
libqt4-dev \
wmctrl \
libopencore-amrnb-dev \
libboost-dev \
libasound2-dev \
libimlib2-dev \
libasyncns-dev \
libssl-dev \
libudev-dev \
recode \
libsqlite3-dev \
# protobuf-compiler \ needs more updated version
libfmt-dev \
    && apt-get purge -y --auto-remove \
    && apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/*

# Install pip and python packages
COPY kitware-archive-latest.asc /tmp/kitware-archive-latest.asc
#Use the one comes with SnomARM
#COPY makedevs /sbin/makedevs
COPY ninja /usr/bin/ninja
# For ninja 1.10.1
RUN apt-key add /tmp/kitware-archive-latest.asc
RUN apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'
RUN apt-get update && apt install -y --no-install-recommends cmake \
    && apt-get purge -y --auto-remove \
    && apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/*
RUN rm /tmp/kitware-archive-latest.asc

RUN pip3 install polib pipx conan SCons compdb
#RUN pip3 install polib virtualenv pipx conan SCons compdb
ENV PATH=$PATH:/scpp/repos/SnomARM/dev-host/bin
ENV CONAN_USER_HOME=/scpp
ENV CCACHE_DIR=/scpp/.ccache
