# Use the latest Ubuntu image
FROM ubuntu:latest

# Install necessary packages and locale configurations
RUN apt-get update && apt-get install -y \
    locales \
    ansible \
    python3 \
    python3-pip \
    sshpass \
    git \
    curl \
    vim

# Generate the locale
RUN locale-gen en_US.UTF-8

# Set locale environment variables
ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

# Clean up to reduce image size
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Set the default shell to bash
SHELL ["/bin/bash", "-c"]

# Set the default command to run when the container starts
CMD ["bash"]
