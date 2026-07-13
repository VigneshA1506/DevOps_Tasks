# Docker Task 3 - Custom Nginx Image with Docker Compose
 
## Objective
 
Create a custom Docker image for Nginx, deploy it using Docker Compose with a bind mount at `/var/opt/nginx`, and push the custom image to Docker Hub.
 
---
 
## Project Structure
 
```
docker-task3/
│── Dockerfile
│── docker-compose.yml
│── index.html
└── README.md
```
 
---
 
## Prerequisites
 
- Amazon Linux 2023
- Docker Engine
- Docker Compose
- Docker Hub Account
 
---
 
## Step 1: Create Project Directory
 
```bash
mkdir docker-task3
cd docker-task3
```
 
---
 
## Step 2: Create index.html
 
```html
<!DOCTYPE html>
<html>
<head>
    <title>Custom Nginx</title>
</head>
<body>
    <h1>Welcome to Custom Nginx Docker Image</h1>
    <h2>Docker Task 3 - Created by Vignesh</h2>
</body>
</html>
```
 
---
 
## Step 3: Create Dockerfile
 
```dockerfile
FROM nginx:latest
 
COPY index.html /usr/share/nginx/html/index.html
 
EXPOSE 80
```
 
---
 
## Step 4: Build the Docker Image
 
```bash
docker build -t vickyamav/custom-nginx:v1 .
```
 
Verify the image:
 
```bash
docker images
```
 
---
 
## Step 5: Create Bind Mount Directory
 
Create the directory:
 
```bash
sudo mkdir -p /var/opt/nginx
```
 
Copy the HTML file:
 
```bash
sudo cp index.html /var/opt/nginx/
```
 
Verify:
 
```bash
ls -l /var/opt/nginx
```
 
---
 
## Step 6: Create docker-compose.yml
 
```yaml
services:
  nginx:
    image: vickyamav/custom-nginx:v1
    container_name: custom-nginx
    ports:
      - "80:80"
    volumes:
      - /var/opt/nginx:/usr/share/nginx/html
```
 
---
 
## Step 7: Start the Container
 
```bash
docker compose up -d
```
 
Verify:
 
```bash
docker ps
```
 
---
 
## Step 8: Test the Application
 
Using curl:
 
```bash
curl localhost
```
 
Or open the EC2 Public IP in your browser:
 
```
http://<EC2-Public-IP>
```
 
---
 
## Step 9: Push Image to Docker Hub
 
Login:
 
```bash
docker login
```
 
Push the image:
 
```bash
docker push vickyamav/custom-nginx:v1
```
 
---
 
## Docker Hub Repository
 
```
https://hub.docker.com/r/vickyamav/custom-nginx
```
 
---
 
# Explanation of Files
 
## Dockerfile
 
- Uses the official Nginx image.
- Copies the custom `index.html` into the default Nginx web directory.
- Exposes port 80.
 
## docker-compose.yml
 
- Deploys the custom Nginx image.
- Maps container port 80 to host port 80.
- Uses a bind mount:
 
```
Host:
/var/opt/nginx
 
↓
 
Container:
/usr/share/nginx/html
```
 
This allows changes made on the host machine to be reflected immediately inside the running container.
 
---
 
# Commands Used
 
```bash
mkdir docker-task3
 
cd docker-task3
 
docker build -t vickyamav/custom-nginx:v1 .
 
docker images
 
sudo mkdir -p /var/opt/nginx
 
sudo cp index.html /var/opt/nginx/
 
docker compose up -d
 
docker ps
 
curl localhost
 
docker login
 
docker push vickyamav/custom-nginx:v1
```
 
---
 
# Output
 
- Successfully built a custom Nginx Docker image.
- Successfully deployed using Docker Compose.
- Successfully configured a bind mount at `/var/opt/nginx`.
- Successfully accessed the web page through port 80.
- Successfully pushed the custom Docker image to Docker Hub.
 
---
 
## Author
 
**Name:** Vignesh A
 
**Docker Hub:** `vickyamav`