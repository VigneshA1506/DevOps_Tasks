# Jenkins Task
 
## Task Description
 
Launch Jenkins on an AWS EC2 instance and explore creating projects and users.
 
---
 
# Tech Stack
 
- AWS EC2
- Amazon Linux 2023
- Jenkins
- Java 21 (Amazon Corretto)
 
---
 
# EC2 Configuration
 
| Property | Value |
|----------|-------|
| Cloud Provider | AWS |
| Service | EC2 |
| Instance Type | t3.small |
| Operating System | Amazon Linux 2023 |
| Region | eu-north-1 |
 
---
 
# Step 1: Connect to EC2
 
```bash
ssh -i <key.pem> ec2-user@<Public-IP>
```
 
---
 
# Step 2: Update the Server
 
```bash
sudo dnf update -y
```
 
---
 
# Step 3: Install Java
 
```bash
sudo dnf install java-21-amazon-corretto -y
```
 
Verify Java
 
```bash
java -version
```
 
Expected Output
 
```
openjdk version "21"
```
 
---
 
# Step 4: Add Jenkins Repository
 
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
 
Import Jenkins Key
 
```bash
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```
 
---
 
# Step 5: Install Jenkins
 
```bash
sudo dnf install jenkins -y
```
 
---
 
# Step 6: Enable Jenkins Service
 
```bash
sudo systemctl enable jenkins
```
 
---
 
# Step 7: Start Jenkins
 
```bash
sudo systemctl start jenkins
```
 
---
 
# Step 8: Check Jenkins Status
 
```bash
sudo systemctl status jenkins
```
 
Expected
 
```
Active: active (running)
```
 
Exit the screen
 
```
q
```
 
---
 
# Step 9: Open Port 8080
 
Edit the EC2 Security Group and add
 
| Type | Port | Source |
|------|------|--------|
| Custom TCP | 8080 | Anywhere (0.0.0.0/0) |
 
---
 
# Step 10: Access Jenkins
 
Open browser
 
```
http://<Public-IP>:8080
```
 
---
 
# Step 11: Get Initial Admin Password
 
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
 
Copy the password and paste it into Jenkins.
 
---
 
# Step 12: Install Suggested Plugins
 
Click
 
```
Install Suggested Plugins
```
 
Wait until installation completes.
 
---
 
# Step 13: Create Admin User
 
Fill
 
- Username
- Password
- Full Name
- Email
 
Click
 
```
Save and Continue
```
 
---
 
# Step 14: Create a Freestyle Project
 
Click
 
```
New Item
```
 
Project Name
 
```
First_Project
```
 
Select
 
```
Freestyle Project
```
 
Click
 
```
OK
```
 
---
 
# Step 15: Add Build Step
 
Go to
 
```
Build Steps
```
 
Click
 
```
Add Build Step
```
 
Select
 
```
Execute Shell
```
 
Add
 
```bash
echo "Welcome Vignesh"
 
date
 
hostname
 
whoami
 
pwd
```
 
Click
 
```
Save
```
 
---
 
# Step 16: Build the Project
 
Click
 
```
Build Now
```
 
Open Build #1
 
Click
 
```
Console Output
```
 
Expected Output
 
```
Welcome Vignesh
 
Mon Jul ...
 
ip-172-...
 
jenkins
 
/var/lib/jenkins/workspace/First_Project
```
 
---
 
# Jenkins Commands Used
 
Check Status
 
```bash
sudo systemctl status jenkins
```
 
Restart Jenkins
 
```bash
sudo systemctl restart jenkins
```
 
Stop Jenkins
 
```bash
sudo systemctl stop jenkins
```
 
Start Jenkins
 
```bash
sudo systemctl start jenkins
```
 
View Logs
 
```bash
sudo journalctl -u jenkins
```
 
Check Java Version
 
```bash
java -version
```
 
Get Initial Password
 
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
 
---
 
# Troubleshooting
 
## Problem
 
Built-In Node automatically goes offline.
 
### Reason
 
Amazon Linux 2023 creates a `/tmp` filesystem of approximately **955 MB**, while Jenkins requires **1 GiB** of free temporary space by default.
 
Error shown:
 
```
Disk space is below threshold of 1.00 GiB.
```
 
---
 
## Solution
 
Navigate to
 
```
Manage Jenkins
→ Nodes
→ Built-In Node
→ Configure
```
 
Enable
 
```
Disk Space Monitoring Thresholds
```
 
Set
 
```
Free Disk Space Threshold : 100 MiB
 
Free Disk Space Warning Threshold : 200 MiB
 
Free Temp Space Threshold : 100 MiB
 
Free Temp Space Warning Threshold : 200 MiB
```
 
Save the configuration.
 
Return to
 
```
Manage Jenkins
→ Nodes
→ Built-In Node
```
 
Click
 
```
Bring this node back online
```
 
---
 
# Learning Outcome
 
- Created an AWS EC2 instance.
- Installed Java 21.
- Installed Jenkins.
- Configured Jenkins service.
- Opened port 8080 using Security Groups.
- Accessed Jenkins through the browser.
- Retrieved the Jenkins admin password.
- Installed Jenkins plugins.
- Created a Freestyle Project.
- Executed shell commands in Jenkins.
- Viewed build history and console output.
- Learned Jenkins service management.
- Understood Jenkins Built-In Node and executors.
- Resolved the Jenkins Built-In Node offline issue caused by `/tmp` disk space monitoring.
 
---
 
# Author
 
**Vignesh A**