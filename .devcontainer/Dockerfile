# Use an official Ubuntu as a base image
FROM ubuntu:latest

# Install necessary packages
RUN apt-get update && apt-get install -y \
    ansible \
    python3 \
    python3-pip \
    sshpass \
    git \
    curl \
    vim

# Clean up package lists to save space
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Set the default shell to bash
SHELL ["/bin/bash", "-c"]
