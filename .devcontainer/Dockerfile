FROM rust:1.56.1-bullseye

ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install -y cmake clang golang lldb sudo time

ARG USER=code
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid=$USER_GID $USER \
    && useradd --uid=$USER_UID --gid=$USER_GID -m $USER \
    && echo "$USER ALL=(root) NOPASSWD:ALL" >/etc/sudoers.d/$USER \
    && chmod 0440 /etc/sudoers.d/$USER
USER $USER
ENV HOME=/home/$USER

RUN rustup component add clippy rustfmt
RUN mkdir /tmp/cargo-deny && cd /tmp/cargo-deny && \
    curl -vsL https://github.com/EmbarkStudios/cargo-deny/releases/download/0.11.0/cargo-deny-0.11.0-x86_64-unknown-linux-musl.tar.gz | tar zxf - && \
    sudo mv cargo-deny-0.11.0-x86_64-unknown-linux-musl/cargo-deny /usr/local/bin && \
    cd .. && rm -rf /tmp/cargo-deny
