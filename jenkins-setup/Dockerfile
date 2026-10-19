FROM jenkins/jenkins:lts-jdk17

USER root

# Install prerequisites for adding a new repository
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# Add Docker's official GPG key and repository
RUN install -m 0755 -d /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc && \
    chmod a+r /etc/apt/keyrings/docker.asc && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list && \
    apt-get update

# Install the Docker CLI (not the full daemon)
RUN apt-get install -y --no-install-recommends docker-ce-cli

# Add the jenkins user to the docker group so it can access the socket
RUN groupadd -f docker && usermod -aG docker jenkins

USER jenkins