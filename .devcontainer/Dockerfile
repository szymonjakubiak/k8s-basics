FROM mcr.microsoft.com/devcontainers/python:3.12

RUN apt-get update \
    && apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release

RUN mkdir -p /etc/apt/keyrings \
    && curl -sLS https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | tee /etc/apt/keyrings/microsoft.gpg > /dev/null \
    && chmod go+r /etc/apt/keyrings/microsoft.gpg

RUN AZ_DIST=$(lsb_release -cs) \
    && ARCH=$(dpkg --print-architecture) \
    && printf "Types: deb\nURIs: https://packages.microsoft.com/repos/azure-cli/\nSuites: %s\nComponents: main\nArchitectures: %s\nSigned-by: /etc/apt/keyrings/microsoft.gpg\n" "$AZ_DIST" "$ARCH" \
    | tee /etc/apt/sources.list.d/azure-cli.sources

RUN apt-get update \
    && apt-get install -y azure-cli

ARG USERNAME=vscode
USER ${USERNAME}
