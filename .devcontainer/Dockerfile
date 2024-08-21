FROM ubuntu:22.04

ENV DEBIAN_FRONTEND noninteractive
ENV LANG C.UTF-8
ENV TZ Asia/Tokyo
ENV NVIDIA_DRIVER_CAPABILITIES graphics

RUN apt-get update \
    && apt-get install -y \
    sudo \
    xxd \
    wget \
    curl \
    git \
    xz-utils \
    zip \
    unzip \
    ca-certificates \
    python3 \
    python3-pip \
    python3-venv \
    python3-dev \
    python3-opencv \
    --no-install-recommends 

# Clean Up
RUN	apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* 

# Install Python packages
ADD ./requirements.txt /tmp/requirements.txt
RUN python3 -m pip install --upgrade pip \
    && python3 -m pip install -r /tmp/requirements.txt \
    && rm -rf /tmp/requirements.txt