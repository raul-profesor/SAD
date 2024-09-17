## Aquí títol

```bash
#!/bin/bash

# Update the package database
sudo dnf update -y

# Uninstall any old versions of Docker
sudo dnf remove -y docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

# Set up the Docker repository
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# Install required packages for repository management
sudo dnf install -y dnf-plugins-core

# Install Docker Engine
sudo dnf install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Start Docker service
sudo systemctl start docker

# Enable Docker to start on boot
sudo systemctl enable docker

# Add your user to the 'docker' group to run docker without sudo (optional)
sudo usermod -aG docker $USER

# Install Docker Compose (standalone binary version, optional if using plugin)
DOCKER_COMPOSE_VERSION=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -oP '"tag_name": "\K(.*)(?=")')
sudo curl -L "https://github.com/docker/compose/releases/download/$DOCKER_COMPOSE_VERSION/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# Apply executable permissions to Docker Compose binary
sudo chmod +x /usr/local/bin/docker-compose

# Verify Docker Compose installation
docker-compose --version

# Enable Docker Compose plugin (if not using the standalone binary)
sudo ln -s /usr/libexec/docker/cli-plugins/docker-compose /usr/local/bin/docker-compose

# Restart the Docker service (important if usermod was used)
sudo systemctl restart docker

# Output the Docker and Docker Compose versions
echo "Docker version:"
docker --version

echo "Docker Compose version:"
docker-compose --version

echo "Docker and Docker Compose installation completed!"
```