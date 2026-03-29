🚀 End-to-End CI/CD Pipeline for Python Flask Application

Automated build and deployment pipeline using Jenkins, Docker, AWS EC2, and Nginx — simulating a real-world DevOps workflow.


📌 Table of Contents

Project Overview
Architecture
Technologies Used
CI/CD Pipeline Flow
Jenkins Pipeline Stages
Setup Instructions
Docker Commands
Nginx Configuration
Future Improvements
Author


📖 Project Overview
This project demonstrates an End-to-End CI/CD pipeline for a Python Flask web application. The pipeline automatically builds and deploys the application whenever new code is pushed to the GitHub repository.
The application is:

Containerized using Docker
Deployed on an AWS EC2 instance
Served through Nginx as a reverse proxy


🏗️ Architecture
Developer
    │
    │  Push Code
    ▼
GitHub Repository
    │
    │  Webhook Trigger
    ▼
Jenkins Pipeline
    │
    │  Build Docker Image
    ▼
Docker Container
    │
    │  Deploy Container
    ▼
AWS EC2 Instance
    │
    │  Reverse Proxy
    ▼
Nginx Server
    │
    ▼
Flask Web Application

🛠️ Technologies Used
TechnologyPurposePython (Flask)Backend Web ApplicationDockerContainerizationJenkinsCI/CD AutomationGitHubSource Code RepositoryAWS EC2Cloud HostingNginxReverse ProxyLinux (Ubuntu)Deployment Server

🔄 CI/CD Pipeline Flow
The pipeline triggers automatically on every git push to the GitHub repository:

Developer pushes code to GitHub repository
GitHub webhook triggers Jenkins pipeline
Jenkins pulls the latest source code
Jenkins builds a new Docker image
Jenkins stops the old running container
Jenkins removes the old container
Jenkins runs the new container
Application is deployed on AWS EC2
Nginx routes incoming traffic to the Flask container
Updated application goes live ✅


🧩 Jenkins Pipeline Stages
Stage 1 → Clone GitHub Repository
Stage 2 → Build Docker Image
Stage 3 → Stop Running Container
Stage 4 → Remove Old Container
Stage 5 → Run New Container
Stage 6 → Deploy Application

⚙️ Setup Instructions
1. Connect to AWS EC2
bashssh -i your-key.pem ubuntu@your-ec2-public-ip
2. Install Docker
bashsudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
3. Install Jenkins
bashsudo apt install openjdk-21-jdk -y
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
Access Jenkins at:
http://<EC2-PUBLIC-IP>:8080
4. Install Nginx
bashsudo apt install nginx -y
sudo systemctl start nginx

🐳 Docker Commands
ActionCommandBuild Docker Imagedocker build -t flask-app .Run Docker Containerdocker run -d -p 5000:5000 flask-appList Running Containersdocker psStop a Containerdocker stop <container_id>

🌐 Nginx Configuration
Edit the default Nginx configuration:
bashsudo nano /etc/nginx/sites-available/default
Add the following reverse proxy configuration:
nginxserver {
    listen 80;

    location / {
        proxy_pass http://localhost:5000;
    }
}
Restart Nginx to apply changes:
bashsudo systemctl restart nginx

🔮 Future Improvements

 Deploy application using Kubernetes
 Use Terraform for AWS infrastructure provisioning
 Push Docker images to AWS ECR
 Implement Prometheus monitoring
 Create Grafana dashboards
 Add automated testing stage to the pipeline
 Implement Blue-Green Deployment strategy


👤 Author
Shiva — Aspiring DevOps Engineer
