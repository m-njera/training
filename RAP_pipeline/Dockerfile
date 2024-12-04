# Use the stevemayne/jupyter-sqlserver base image
FROM stevemayne/jupyter-sqlserver

# Set the user to root
USER root

# Install system dependencies and psycopg2 packages
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    gcc \
    python3-dev \
    libpq-dev \
    && pip install psycopg2 psycopg2-binary \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*
	