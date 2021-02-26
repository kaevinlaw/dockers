FROM ubuntu:18.04

# Setup build directory and root user
WORKDIR /scpp
USER root

# Install dependencies
RUN apt-get -y update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
ssh \
git \
repo \
    && apt-get purge -y --auto-remove \
    && apt-get clean && apt-get autoremove && rm -rf /var/lib/apt/lists/*

RUN adduser --disabled-password --gecos '' repo_user
