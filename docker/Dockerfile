FROM ubuntu:24.04

ENV UV_CACHE_DIR=/tmp


# install packages
RUN apt-get update && apt-get install -y \
    python3.12 \
    python3-pip \
    python3.12-venv \
    curl \
    git \
    ghostscript \
    && rm -rf /var/lib/apt/lists/*

# set python3.12 as default command
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.12 1
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.12 1

# uv
# -----
# install
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
ENV PATH="/root/.local/bin:$PATH"

# set working dir.
WORKDIR /app

# install python packages
RUN uv sync --locked --no-cache

