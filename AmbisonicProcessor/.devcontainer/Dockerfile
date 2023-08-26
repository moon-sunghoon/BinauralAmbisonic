FROM mcr.microsoft.com/devcontainers/cpp:0-debian-11

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

WORKDIR /myapp

RUN cd grpc \
    bazel build :all
# This command compiles your app using GCC, adjust for your source code

# This command runs your application, comment out this line to compile only
CMD ["./myapp"]

LABEL Name=devcontainer Version=0.0.1
