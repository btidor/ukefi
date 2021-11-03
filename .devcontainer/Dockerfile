# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.205.0/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use hirsuite or bionic on local arm64/Apple Silicon): hirsute, focal, bionic
ARG VARIANT="hirsute"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

RUN apt update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt install -y -q build-essential autoconf shellcheck \
        git-buildpackage debhelper-compat
