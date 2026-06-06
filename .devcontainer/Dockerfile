FROM eclipse-temurin:21-jdk-jammy

# Install bash, vim, git, openssh and other useful tools
RUN apt-get update && apt-get install -y --no-install-recommends \
    bash \
    vim \
    git \
    openssh-client \
    ca-certificates \
    curl && \
    rm -rf /var/lib/apt/lists/*

# Create working directory
RUN mkdir -p /code

# Set proper permissions for .ssh directory
RUN mkdir -p /root/.ssh && \
    chmod 700 /root/.ssh

WORKDIR /code

CMD ["bash"]