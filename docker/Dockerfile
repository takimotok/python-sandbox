FROM ubuntu:24.04

ENV POETRY_VIRTUALENVS_CREATE=false \
    POETRY_VIRTUALENVS_IN_PROJECT=false


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

# Poetry
# -----
# install
RUN curl -sSL https://install.python-poetry.org | python3 -
ENV PATH="/root/.local/bin:$PATH"

# disable virtual env
# RUN poetry config virtualenvs.create false

# set working dir.
WORKDIR /app

# install python packages
COPY pyproject.toml ./
RUN poetry install --no-root

