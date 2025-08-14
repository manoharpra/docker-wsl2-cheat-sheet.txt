# docker-wsl2-cheat-sheet.txt

Docker WSL2 Quick Commands Cheat Sheet

1. Docker Installation & Setup
# Install Docker in WSL2 Ubuntu
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add current user to docker group (sudo-free usage)
sudo usermod -aG docker $USER
# Restart WSL terminal
exit

# Test Docker
docker run hello-world

2. Container Management
# Run interactive Ubuntu container
docker run -it ubuntu bash

# Exit container
exit

# List running containers
docker ps

# List all containers (running + stopped)
docker ps -a

# Start an existing container
docker start -ai <container_id>

# Stop a running container
docker stop <container_id>

# Remove container
docker rm <container_id>

3. Image Management
# Pull an image from Docker Hub
docker pull ubuntu

# List local images
docker images

# Remove an image
docker rmi <image_name_or_id>

# Build an image from Dockerfile
docker build -t myimage:tag .

4. Volumes & Data
# Create a volume
docker volume create myvolume

# List volumes
docker volume ls

# Mount volume in container
docker run -v myvolume:/data -it ubuntu bash

# Remove volume
docker volume rm myvolume

5. Networks
# List networks
docker network ls

# Create custom network
docker network create mynetwork

# Run container in custom network
docker run --network=mynetwork -it ubuntu bash

6. Docker Compose
# Check version
docker compose version

# Run docker-compose.yml
docker compose up

# Run in detached mode
docker compose up -d

# Stop services
docker compose down

7. System Cleanup
# Remove stopped containers
docker container prune

# Remove unused images
docker image prune -a

# Remove unused volumes
docker volume prune

# Remove unused networks
docker network prune

# Clean all at once
docker system prune -a

8. Useful Tips
Access container shell: docker exec -it <container_id> bash
Check logs: docker logs <container_id>
Monitor containers: docker stats
WSL path note: Prefer ~/ (Linux home) over /mnt/c/... for Docker operations to avoid file permission issues.

