FROM rust:1.56.1-bullseye
RUN --mount=type=cache,target=/var/lib/apt/lists \
    --mount=type=cache,target=/var/tmp \
  apt update && apt install -y cmake clang golang time
