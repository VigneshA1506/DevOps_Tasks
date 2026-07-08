# Docker on AWS EC2
 
## Project Overview
 
This project demonstrates the installation and usage of Docker on an AWS EC2 instance. The objective is to understand Docker fundamentals by working with Docker Images, Containers, Volumes, and Networks.
 
---
 
## Objective
 
- Install Docker on AWS EC2
- Explore Docker Images
- Create and manage Docker Containers
- Create and use Docker Volumes
- Create and manage Docker Networks
- Deploy an Nginx container and access it through a web browser
 
---
 
## Tech Stack
 
- AWS EC2
- Amazon Linux
- Docker
 
---
 
## Prerequisites
 
- AWS Account
- EC2 Instance (Amazon Linux 2 or Amazon Linux 2023)
- SSH Client (PuTTY)
- Security Group with:
  - SSH (22)
  - HTTP (80)
 
---
 
# Step 1: Connect to EC2
 
Connect to the EC2 instance using PuTTY.
 
---
 
# Step 2: Install Docker
 
Update the server
 
Amazon Linux 2023
 
```bash
sudo dnf update -y
sudo dnf install docker -y
```
 
Amazon Linux 2
 
```bash
sudo yum update -y
sudo amazon-linux-extras install docker -y
```
 
Start Docker
 
```bash
sudo systemctl start docker
```
 
Enable Docker
 
```bash
sudo systemctl enable docker
```
 
Verify Installation
 
```bash
docker --version
```
 
---
 
# Step 3: Configure Docker Permissions
 
```bash
sudo usermod -aG docker ec2-user
```
 
Reconnect to the server.
 
---
 
# Step 4: Docker Images
 
View images
 
```bash
docker images
```
 
Pull Ubuntu
 
```bash
docker pull ubuntu
```
 
Pull Nginx
 
```bash
docker pull nginx
```
 
List images again
 
```bash
docker images
```
 
---
 
# Step 5: Docker Containers
 
Run Hello World
 
```bash
docker run hello-world
```
 
Run Ubuntu Container
 
```bash
docker run -it ubuntu
```
 
List running containers
 
```bash
docker ps
```
 
List all containers
 
```bash
docker ps -a
```
 
Stop container
 
```bash
docker stop <container-id>
```
 
Start container
 
```bash
docker start <container-id>
```
 
Remove container
 
```bash
docker rm <container-id>
```
 
---
 
# Step 6: Deploy Nginx
 
Run Nginx
 
```bash
docker run -d -p 80:80 nginx
```
 
Verify
 
```bash
docker ps
```
 
Open browser
 
```
http://<EC2-Public-IP>
```
 
Expected Output
 
```
Welcome to nginx!
```
 
---
 
# Step 7: Docker Volumes
 
Create volume
 
```bash
docker volume create myvolume
```
 
List volumes
 
```bash
docker volume ls
```
 
Inspect volume
 
```bash
docker volume inspect myvolume
```
 
Run container with volume
 
```bash
docker run -it -v myvolume:/data ubuntu
```
 
Create file
 
```bash
echo "Docker Volume Demo" > /data/file.txt
```
 
Exit container
 
```bash
exit
```
 
Run another container using same volume
 
```bash
docker run -it -v myvolume:/data ubuntu
```
 
Verify
 
```bash
cat /data/file.txt
```
 
---
 
# Step 8: Docker Networks
 
List networks
 
```bash
docker network ls
```
 
Create network
 
```bash
docker network create mynetwork
```
 
Inspect network
 
```bash
docker network inspect mynetwork
```
 
Run container in custom network
 
```bash
docker run -it --network mynetwork ubuntu
```
 
---
 
# Step 9: Useful Docker Commands
 
```bash
docker --version
docker info
docker images
docker ps
docker ps -a
docker pull ubuntu
docker pull nginx
docker run hello-world
docker run -it ubuntu
docker run -d -p 80:80 nginx
docker logs <container-id>
docker exec -it <container-id> bash
docker stop <container-id>
docker start <container-id>
docker rm <container-id>
docker rmi <image-id>
docker volume ls
docker network ls
```
 
---
 
# Project Outcome
 
Successfully completed the following:
 
- Installed Docker on AWS EC2
- Explored Docker Images
- Created and managed Containers
- Created Docker Volumes
- Explored Docker Networks
- Deployed an Nginx web server
- Verified Docker installation and functionality
 
---
 
# Screenshots
 
Include the following screenshots:
 
- EC2 Instance Running
- Docker Version
- Docker Images
- Docker Containers
- Nginx Running in Browser
- Docker Volumes
- Docker Networks
- Docker Info
 
---
 
# Author
 
**Name:** Vignesh A
 
**Technology:** AWS EC2 | Docker