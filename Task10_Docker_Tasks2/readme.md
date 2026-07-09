# Docker Task - 2
 
## Project Overview
 
This project demonstrates how to create a Dockerized static website using **Docker**, **Docker Compose**, and **AWS EC2**. The website displays basic profile information and is served using the Nginx web server.
 
---
 
## Objective
 
- Create a static HTML webpage.
- Create a Dockerfile to containerize the application.
- Create a Docker Compose file to manage the container.
- Deploy the application on an AWS EC2 instance.
- Access the website using the EC2 Public IP.
 
---
 
## Tech Stack
 
- AWS EC2
- Docker
- Docker Compose
- Nginx
- HTML
- Git
- GitHub
 
---
 
## Project Structure
 
```
DevOps_Tasks/
│── Dockerfile
│── docker-compose.yml
│── index.html
└── README.md
```
 
---
 
## Dockerfile
 
```dockerfile
FROM nginx:latest
 
COPY index.html /usr/share/nginx/html/index.html
 
EXPOSE 80
```
 
### Description
 
- Uses the latest Nginx image.
- Copies the HTML file into the Nginx web directory.
- Exposes port 80 to serve the webpage.
 
---
 
## Docker Compose File
 
```yaml
version: '3.8'
 
services:
  profile:
    build: .
    container_name: docker-profile
    ports:
      - "80:80"
```
 
### Description
 
- Builds the Docker image from the Dockerfile.
- Creates a container named **docker-profile**.
- Maps EC2 Port 80 to Container Port 80.
 
---
 
## Deployment Steps
 
### 1. Clone Repository
 
```bash
git clone https://github.com/VigneshA1506/DevOps_Tasks.git
```
 
Switch to the required branch.
 
```bash
git checkout new_base
```
 
---
 
### 2. Navigate to Project
 
```bash
cd DevOps_Tasks
```
 
---
 
### 3. Verify Project Files
 
```bash
ls
```
 
Expected files:
 
```
Dockerfile
docker-compose.yml
index.html
README.md
```
 
---
 
### 4. Install Docker Compose
 
```bash
sudo curl -SL https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64 \
-o /usr/local/bin/docker-compose
 
sudo chmod +x /usr/local/bin/docker-compose
```
 
Verify:
 
```bash
docker-compose --version
```
 
---
 
### 5. Build and Run Application
 
```bash
DOCKER_BUILDKIT=0 docker-compose up -d
```
 
---
 
### 6. Verify Container
 
```bash
docker ps
```
 
Expected Output:
 
```
docker-profile   Up
```
 
---
 
### 7. Open Website
 
Open the browser:
 
```
http://<EC2-Public-IP>
```
 
The webpage displaying the profile details will be loaded.
 
---
 
## Docker Compose Commands
 
### Start
 
```bash
docker-compose up -d
```
 
### Stop
 
```bash
docker-compose stop
```
 
### Restart
 
```bash
docker-compose restart
```
 
### View Logs
 
```bash
docker-compose logs
```
 
### Remove Containers
 
```bash
docker-compose down
```
 
---
 
## Screenshots
 
Include the following screenshots:
 
- Project Structure
- Dockerfile
- Docker Compose File
- Docker Compose Build
- Running Containers (`docker ps`)
- Website Output
- GitHub Repository
 
---
 
## Project Outcome
 
Successfully:
 
- Created a static HTML website.
- Containerized the application using Docker.
- Managed the container using Docker Compose.
- Deployed the application on AWS EC2.
- Verified the application by accessing it through the EC2 Public IP.
 
---
 
## GitHub Repository
 
```
https://github.com/VigneshA1506/DevOps_Tasks
```
 
---
 
## Author
 
**Name:** Vignesh A
 
**Role:** Software Test Engineer
 
**Technologies:** AWS | Docker | Docker Compose | Git | GitHub | Nginx
AI Tools Directory - dealsbe.com
Find useful AI tools for content, code, design, research, and automation.
 
