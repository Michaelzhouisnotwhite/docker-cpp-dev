FROM amd64/fedora:40

WORKDIR /app
RUN dnf upgrade -y
RUN dnf install wget unzip git curl build-essential neovim pkg-config cmake clang llvm gdb zlib1g-dev net-tools iproute2 sudo iputils-ping -y

# RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.5/zsh-in-docker.sh)" -- \
#     -t robbyrussell

# RUN wget -P /app https://github.com/clangd/clangd/releases/download/17.0.3/clangd-linux-17.0.3.zip \
#     && unzip /app/clangd-linux-17.0.3.zip -d /app \
#     && rm -rf clangd-linux-17.0.3.zip

# RUN wget -P /app https://github.com/ninja-build/ninja/releases/download/v1.11.1/ninja-linux.zip \
#     && unzip /app/ninja-linux.zip  -d /app \
#     && cp /app/ninja /usr/bin \
#     && rm -rf ninja-linux.zip 

# RUN wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
#     && dpkg -i packages-microsoft-prod.deb \
#     && rm packages-microsoft-prod.deb


# RUN  apt-get update && \
#     apt-get install -y dotnet-sdk-6.0

# RUN  apt-get update && \
#     apt-get install -y aspnetcore-runtime-6.0



ENV PATH=$PATH:/app
ENV PATH="$PATH:/app/clangd_17.0.3/bin"

WORKDIR /