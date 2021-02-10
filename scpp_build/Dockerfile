FROM ubuntu:18.04

# Setup build directory and root user
WORKDIR /scpp
USER root

# Install dependencies
RUN apt-get -y update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
python3 \
python3-pip \
python3-distutils \
python3-setuptools \
software-properties-common \
gpg-agent \
ninja-build \
build-essential \
ccache \
git \
mtd-utils \
qemu-user-static \
rsync \
scons \
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
libfmt-dev

# Install pip and python packages
COPY kitware-archive-latest.asc /tmp/kitware-archive-latest.asc
RUN apt-key add /tmp/kitware-archive-latest.asc
RUN apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'
RUN apt-get update && apt install -y --no-install-recommends cmake \
    && apt-get purge -y --auto-remove \
    && apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/*
RUN rm /tmp/kitware-archive-latest.asc

RUN pip3 install polib virtualenv pipx conan
ENV PATH=$PATH:/scpp/repos/SnomArm/dev-host/bin/makedevs
