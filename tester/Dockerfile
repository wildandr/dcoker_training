# Use the specified base image
FROM runpod/pytorch:2.4.0-py3.11-cuda12.4.1-devel-ubuntu22.04

# Run system updates and clean up
RUN apt-get update && apt-get upgrade -y && apt-get clean && rm -rf /var/lib/apt/lists/*

# Set the working directory to /
WORKDIR /

# Install Python dependencies
# Using '--no-cache-dir' with pip to avoid use of cache
RUN pip install --no-cache-dir xformers==0.0.22 \
    && pip install --no-cache-dir -r requirements_versions.txt