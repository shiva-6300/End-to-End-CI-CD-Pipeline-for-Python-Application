1. Project Overview

This project demonstrates an End-to-End CI/CD Pipeline for a Python Flask E-Commerce Application.
The goal of this project is to automate the process of building, deploying, and updating a web application using DevOps tools.
The application is built using Python Flask and containerized with Docker. A CI/CD pipeline is implemented using Jenkins, which automatically pulls the latest code from GitHub, builds a Docker image, and deploys the application to an Amazon Web Services EC2 instance.
An Nginx reverse proxy is used to route incoming web traffic to the running Flask application container.
This project simulates a real-world DevOps deployment workflow, ensuring faster development cycles, automated deployments, and scalable infrastructure.

2. Technologies Used
The following tools and technologies were used to build and deploy this CI/CD pipeline:
1. Python Flask	   Backend web application framework
2. Docker	         Containerization of the Flask application
3. Jenkins         	CI/CD automation pipeline
4. GitHub	         Source code repository
5. Amazon            Web Services EC2	Cloud server hosting
6. Nginx	            Reverse proxy and web server
7. Linux (Ubuntu)	   Operating system for deployment

3. CI/CD Pipeline Flow
The CI/CD pipeline automates the deployment process whenever new code is pushed to the repository.
Workflow
1. Developer pushes code to the GitHub repository
2. A webhook triggers the Jenkins pipeline
3. Jenkins clones the latest source code from GitHub
4. Jenkins builds a Docker image for the Flask application using Docker
5. Jenkins stops the existing running container
6. Jenkins deploys a new container with the updated application
7. The application becomes accessible via Nginx reverse proxy on the AWS EC2 server


CI/CD Flow Diagram
Developer
   │
   │ Push Code
   ▼
GitHub Repository
   │
   │ Webhook Trigger
   ▼
Jenkins Pipeline
   │
   │ Build Docker Image
   ▼
Docker Container
   │
   │ Deploy to EC2
   ▼
Nginx Reverse Proxy
   │
   ▼
Flask E-Commerce Application

4. Architecture Diagram
The following diagram represents the architecture of the CI/CD pipeline used to build and deploy the Flask E-Commerce application.
        +-------------+
        |  Developer  |
        +-------------+
               │
               │ Push Code
               ▼
        +-------------+
        |   GitHub    |
        | Repository  |
        +-------------+
               │
               │ Webhook Trigger
               ▼
        +-------------+
        |   Jenkins   |
        | CI/CD Tool  |
        +-------------+
               │
               │ Build Docker Image
               ▼
        +-------------+
        |   Docker    |
        | Container   |
        +-------------+
               │
               │ Deploy Container
               ▼
      +----------------------+
      | AWS EC2 Instance     |
      +----------------------+
               │
               │ Reverse Proxy
               ▼
        +-------------+
        |    Nginx    |
        +-------------+
               │
               ▼
        +-------------------+
        | Flask E-Commerce  |
        | Application       |
        +-------------------+

This architecture shows how code changes flow from the developer to deployment using Jenkins, Docker, Nginx, and **Amazon Web Services EC2.

5. Setup Instructions
Follow the steps below to set up and run the CI/CD pipeline.
1. Launch EC2 Instance
Create an Ubuntu server on Amazon Web Services EC2 and connect using SSH.
ssh -i your-key.pem ubuntu@your-ec2-public-ip

2. Install Docker
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
Verify installation:
docker --version

4. Install Jenkins
sudo apt update
sudo apt install openjdk-21-jdk -y
Add Jenkins repository and install Jenkins.
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
Access Jenkins:
http://EC2-PUBLIC-IP:8080

4. Install Nginx
sudo apt install nginx -y
sudo systemctl start nginx
Configure Nginx as a reverse proxy for the Flask container.

5. Configure Jenkins Pipeline
Open Jenkins dashboard
Create New Pipeline Job
Connect your GitHub repository
Add Jenkinsfile for pipeline automation


6. Jenkins Pipeline
The Jenkins pipeline automates the entire deployment process from code commit to application deployment.
Pipeline Stages
Clone the repository from GitHub
Build Docker image
Stop the old running container
Deploy a new container with updated code
