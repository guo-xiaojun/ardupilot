FROM ubuntu:22.04

# 避免交互式提示
ENV DEBIAN_FRONTEND=noninteractive

# 更新系统
RUN apt-get update && apt-get upgrade -y

# 安装基础开发工具
RUN apt-get install -y \
    sudo \
    build-essential \
    cmake \
    ninja-build \
    git \
    wget \
    curl \
    vim \
    nano \
    htop \
    tree \
    software-properties-common \
    lsb-release \
    gnupg \
    ca-certificates

# 安装 Python 和相关包
RUN apt-get install -y \
    python3 \
    python3-pip \
    python3-dev \
    python3-numpy \
    python3-scipy \
    python3-matplotlib \
    python3-serial \
    python3-requests \
    python3-yaml \
    python3-empy \
    python3-toml \
    python3-future \
    python3-wheel \
    python3-setuptools \
    python3-pexpect

# 安装 ARM 交叉编译工具链
RUN apt-get install -y \
    gcc-arm-linux-gnueabihf \
    g++-arm-linux-gnueabihf \
    binutils-arm-linux-gnueabihf \
    libncurses5-dev

# 安装 SITL 仿真依赖
RUN apt-get install -y \
    libtool \
    autoconf \
    automake \
    libxml2-dev \
    libxslt1-dev \
    libgtk-3-dev \
    libglew-dev \
    libglfw3-dev \
    libeigen3-dev \
    libboost-all-dev \
    libprotobuf-dev \
    protobuf-compiler \
    libgrpc++-dev \
    libgrpc-dev

# 安装 GStreamer（用于视频流）
RUN apt-get install -y \
    libgstreamer1.0-dev \
    libgstreamer-plugins-base1.0-dev \
    gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-bad

# 安装 MAVProxy 依赖
# RUN pip3 install --break-system-packages \
RUN pip3 install \
    pymavlink \
    mavproxy \
    dronekit

# 清理缓存
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# 创建用户
RUN useradd -m -s /bin/bash ardupilot && \
    echo "ardupilot ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ardupilot && \
    chmod 0440 /etc/sudoers.d/ardupilot

# 设置工作目录用户
USER ardupilot

# 设置工作目录
WORKDIR /workspaces/ardupilot

# 默认命令
CMD ["bash"]
