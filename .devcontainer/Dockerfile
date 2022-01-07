FROM rust:1.56.1-bullseye
ARG USERNAME=code
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN apt update && apt install -y cmake clang golang sudo time
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
USER $USERNAME
RUN rustup component add clippy rustfmt
RUN cargo install cargo-deny

