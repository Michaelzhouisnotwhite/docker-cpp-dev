FROM amd64/debian:12
WORKDIR /etc/apt/sources.list.d/

RUN echo "Types: deb" > debian.sources
RUN echo "URIs: http://mirrors4.tuna.tsinghua.edu.cn/debian" >> debian.sources
RUN echo "Suites: bookworm bookworm-updates bookworm-backports">> debian.sources
RUN echo "Components: main contrib non-free non-free-firmware ">> debian.sources
RUN echo "Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg ">> debian.sources
RUN echo "\n" >> debian.sources
RUN echo "# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释 ">> debian.sources
RUN echo "# Types: deb-src ">> debian.sources
RUN echo "# URIs: http://mirrors4.tuna.tsinghua.edu.cn/debian ">> debian.sources
RUN echo "# Suites: bookworm bookworm-updates bookworm-backports ">> debian.sources
RUN echo "# Components: main contrib non-free non-free-firmware ">> debian.sources
RUN echo "# Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg ">> debian.sources
RUN echo "\n">> debian.sources
RUN echo "# 以下安全更新软件源包含了官方源与镜像站配置，如有需要可自行修改注释切换 ">> debian.sources
RUN echo "Types: deb ">> debian.sources
RUN echo "URIs: http://mirrors4.tuna.tsinghua.edu.cn/debian-security ">> debian.sources
RUN echo "Suites: bookworm-security ">> debian.sources
RUN echo "Components: main contrib non-free non-free-firmware ">> debian.sources
RUN echo "Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg ">> debian.sources
RUN echo "\n" >> debian.sources
RUN echo "# Types: deb-src " >> debian.sources
RUN echo "# URIs: http://mirrors4.tuna.tsinghua.edu.cn/debian-security " >> debian.sources
RUN echo "# Suites: bookworm-security " >> debian.sources
RUN echo "# Components: main contrib non-free non-free-firmware " >> deblian.sources
RUN echo "# Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg" >> debian.sources
RUN cat debian.sources
WORKDIR /app
RUN apt-get update && apt upgrade -y
RUN apt install wget unzip git curl build-essential neovim pkg-config cmake clang llvm gdb zlib1g-dev net-tools iproute2 sudo iputils-ping -y

RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.5/zsh-in-docker.sh)" -- \
    -t robbyrussell

RUN wget -P /app https://github.com/clangd/clangd/releases/download/17.0.3/clangd-linux-17.0.3.zip \
    && unzip /app/clangd-linux-17.0.3.zip -d /app \
    && rm -rf clangd-linux-17.0.3.zip

RUN wget -P /app https://github.com/ninja-build/ninja/releases/download/v1.11.1/ninja-linux.zip \
    && unzip /app/ninja-linux.zip  -d /app \
    && cp /app/ninja /usr/bin \
    && rm -rf ninja-linux.zip 

RUN wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && rm packages-microsoft-prod.deb


RUN  apt-get update && \
    apt-get install -y dotnet-sdk-6.0

RUN  apt-get update && \
    apt-get install -y aspnetcore-runtime-6.0



ENV PATH=$PATH:/app
ENV PATH="$PATH:/app/clangd_17.0.3/bin"

WORKDIR /