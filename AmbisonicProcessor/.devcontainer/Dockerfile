ARG VARIANT=debian-11
FROM mcr.microsoft.com/vscode/devcontainers/cpp:0-${VARIANT}

# These commands copy your files into the specified directory in the image
# and set that as the working location
RUN apt-get update && apt-get upgrade -y \
  autoconf \
  automake \
  build-essential \
  cmake \
  curl \
  g++ \
  git \
  libtool \
  make \
  pkg-config \
  unzip \
  && apt-get clean

ENV GRPC_RELEASE_TAG v1.57.0

RUN echo "-- cloning grpc repo" && \
    git clone --recurse-submodules -b ${GRPC_RELEASE_TAG} --depth 1 --shallow-submodules https://github.com/grpc/grpc /var/local/git/grpc && \
    cd /var/local/git/grpc && \
    git submodule update --init --recursive

RUN echo "-- installing grpc" && \
    cd /var/local/git/grpc && \
    mkdir -p cmake/build && \
    cd cmake/build && \
    cmake ../.. -DgRPC_INSTALL=ON && \
    make &&\
    make install

# RUN cd grpc && \
#     bazel build :all
