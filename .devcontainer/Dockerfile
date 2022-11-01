# https://github.com/microsoft/vscode-dev-containers/tree/v0.245.2/containers/ubuntu/.devcontainer/base.Dockerfile
# ubuntu-22.04, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="ubuntu-22.04"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# Meta
LABEL org.opencontainers.image.source=https://github.com/aureliojargas/devcontainer
LABEL org.opencontainers.image.description="Shell and Python dev tools (Ubuntu)"

# Install additional OS packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    black \
    ed \
    file \
    fish \
    git-revise \
    pylint \
    python3-pip \
    shellcheck \
    shfmt \
    tig \
    vim

# Install 'replace' script, that I use frequently.
# Note that 'vscode' is the default container user.
ADD --chown=vscode:vscode https://raw.githubusercontent.com/aureliojargas/replace/main/replace.py /usr/local/bin/replace
RUN chmod +x /usr/local/bin/replace
