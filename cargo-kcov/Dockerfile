FROM ubuntu:20.04
# should be run using 
#   docker run -it --rm --security-opt seccomp=unconfined -v $(pwd):/data hpwxf/kcov
LABEL maintainer="hpwxf@haveneer.com"
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update \
    && apt install -y curl cmake g++ pkg-config jq python3 \
    && apt install -y libcurl4-openssl-dev libelf-dev libdw-dev binutils-dev libiberty-dev libssl-dev
ENV HOME /home/dev
RUN useradd -m -d $HOME dev
USER dev
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="$HOME/.cargo/bin:${PATH}"
RUN cd /tmp \ 
    && cargo install cargo-kcov \
    && cargo kcov --print-install-kcov-sh | sh \
    && rm -fr /tmp/kcov-*
WORKDIR /data
VOLUME ["/data"]
CMD cargo kcov