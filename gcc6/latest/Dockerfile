FROM gcc:6

ARG CMAKE_VERSION=3.11
ARG CMAKE_BUILD=1

# Install Cmake
RUN wget -q https://raw.githubusercontent.com/danquist/install-cmake/master/install-cmake.sh /; \
    chmod +x /install-cmake.sh; \
    /install-cmake.sh $CMAKE_VERSION $CMAKE_BUILD; \
    rm -f /install-cmake.sh

# Install clang and add to path
RUN apt update && apt install -y \
  xz-utils \
  build-essential \
  dos2unix \
  && rm -rf /var/lib/apt/lists/* \
  && curl -SL http://releases.llvm.org/7.0.0/clang+llvm-7.0.0-x86_64-linux-gnu-ubuntu-16.04.tar.xz \
  | tar -xJC . && \
  mv clang+llvm-7.0.0-x86_64-linux-gnu-ubuntu-16.04 clang-7
ENV PATH="/clang-7/bin:${PATH}"

# Install pip and gcovr
RUN mkdir ~\temp; \
    wget -q https://bootstrap.pypa.io/get-pip.py -P ~/temp; \
    python2.7 ~/temp/get-pip.py; \
    rm -rf ~/temp; \
    pip install gcovr
    