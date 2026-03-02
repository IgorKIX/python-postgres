FROM mcr.microsoft.com/devcontainers/python:3.13

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    g++ \
    make \
    ripgrep \
    fd-find \
    unzip \
    curl \
    git \
    xclip \
    ca-certificates \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Install Node.js 20 LTS (includes npm)
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get update \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*

# Install Neovim
ARG NVIM_VERSION=v0.11.6
RUN curl -fsSL "https://github.com/neovim/neovim/releases/download/${NVIM_VERSION}/nvim-linux-x86_64.tar.gz" \
    | tar xz -C /opt \
    && ln -s /opt/nvim-linux-x86_64/bin/nvim /usr/local/bin/nvim

# Set Neovim as default editor
ENV EDITOR=nvim
ENV VISUAL=nvim

# Python tools
RUN pip install --no-cache-dir \
    psycopg2-binary \
    sqlalchemy \
    black \
    ruff \
    pytest
