FROM ubuntu:24.04

# cf.) https://docs.astral.sh/uv/guides/integration/docker/#using-uv-temporarily
ENV UV_CACHE_DIR=/tmp \
    UV_NO_SYNC=1 \
    VIRTUAL_ENV="" \
    # avoid using virtual env.'s python
    UV_SYSTEM_PYTHON=1 \
    UV_PROJECT_ENVIRONMENT=/usr/local \
    PIP_BREAK_SYSTEM_PACKAGES=1

# install packages
RUN apt-get update && apt-get install -y \
    python3.12 \
    python3-pip \
    python3.12-venv \
    curl \
    git \
    ghostscript \
    libgl1-mesa-dev \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgomp1 \
    libgthread-2.0-0 \
    libgtk2.0-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    && rm -rf /var/lib/apt/lists/*

# Remove the EXTERNALLY-MANAGED file to allow pip installations
RUN rm -f /usr/lib/python*/EXTERNALLY-MANAGED

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

# install python packages globally (no venv)
COPY pyproject.toml uv.lock ./

# It's likely to be best practice to install those below separately:
#   - 1st command: external packages
#   - 2nd command: activate my python project
# 
# This improves build efficiency for caching into Docker Layer respectively.
RUN uv pip install --system -r pyproject.toml  
RUN uv pip install --system -e .

