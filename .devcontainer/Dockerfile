# Base image
FROM ubuntu:20.04

# Set non-interactive mode for installation
ENV DEBIAN_FRONTEND=noninteractive

# Install basic utilities
RUN apt-get update && apt-get install -y \
    sudo \
    curl \
    wget \
    git \
    vim \
    nano \
    unzip \
    software-properties-common \
    gnupg2 \
    lsb-release \
    ca-certificates \
    apt-transport-https \
    build-essential \
    python3 \
    python3-pip \
    python3-venv \
    python3-dev \
    python-is-python3 \
    openjdk-11-jdk \
    nodejs \
    npm \
    docker.io \
    jq \
    dbus \
    && apt-get clean

# Install Ansible
RUN apt-add-repository --yes --update ppa:ansible/ansible && \
    apt-get update && \
    apt-get install -y ansible

# Install Terraform
RUN wget https://releases.hashicorp.com/terraform/1.5.4/terraform_1.5.4_linux_amd64.zip && \
    unzip terraform_1.5.4_linux_amd64.zip && \
    mv terraform /usr/local/bin/ && \
    rm terraform_1.5.4_linux_amd64.zip

# Install AWS CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf awscliv2.zip aws

# Install GCP CLI
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \
    apt-get install -y apt-transport-https ca-certificates gnupg && \
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - && \
    apt-get update && apt-get install -y google-cloud-sdk

# Install Azure CLI
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash

# Set up Python environment
RUN pip install --upgrade pip && \
    pip install boto3 google-auth azure-cli

# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Add docker to the sudoers group (remove usermod for Docker to avoid error)
# RUN usermod -aG docker $USER

# Set the locale
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

# Set default shell to bash
CMD ["/bin/bash"]
