FROM ubuntu:18.04

# Setup build directory and root user
WORKDIR /android-build
USER root

# Install dependencies
RUN apt-get -y update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
git-core \
gnupg \
flex \
bison \
gperf \
build-essential \
zip \
curl \
zlib1g-dev \
gcc-multilib \
g++-multilib \
libc6-dev-i386 \
lib32ncurses5-dev \
x11proto-core-dev \
libx11-dev \
lib32z-dev \
ccache \
libgl1-mesa-dev \
libxml2-utils \
xsltproc \
unzip \
openjdk-8-jdk \
python \
libssl-dev \
bc \
liblz4-tool \
python3 \
rsync \
    && apt-get purge -y --auto-remove \
    && apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH
ENV CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/lib/tools.jar
ENV _JAVA_OPTIONS="-Xmx4g"
