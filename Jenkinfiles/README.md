# Building a Tar File of React, Java, and Python for Nexus Repository
This repository contains scripts and instructions for building a tar file containing code written in React, Python, and Java, and pushing it to a Nexus repository for artifact management

# Prerequisites
Before you begin, ensure you have the following prerequisites:

• Git installed on your local machine.<br>
• npm installed for React development.<br>
• Python installed for Python development.<br>
• JDK (Java Development Kit) installed for Java development.<br>
• Access to a Nexus repository where you have permissions to deploy artifacts.<br>

# Usage
To use the script, follow the instructions below:

# clone the code by running below command
```
git clone https://github.com/kadagotiprudhvi/microserviceapp.git
```
# Navigate to the react Directory
```
cd microserviceapp/demo-frontend
```
# Install npm Dependencies for React
```
sudo apt-get update && sudo apt-get install -y npm
```
# Install React Dependencies
```
npm install
```
# Build React Application
```
npm run build
```
# Package the React Files for Nexus Repository:
```
tar -xzvf npm_build.tar.gz build
```
# Push to Nexus Repository of tar file
• Replace maven:12345 with your Nexus repository credentials and http://3.110.40.233:8081/repository/tar-repo/npm-snap:1.0.0.tar <br>
  with your Nexus repository URL and file path.
```
curl -v -u maven:12345 --upload-file npm_snap:1.0.0.tar "http://3.110.40.233:8081/repository/tar-repo/npm-snap:1.0.0.tar"
```

# Navigate to the Maven Directory
```
cd microserviceapp/demo-backend1
```
# Install JDK
```
sudo apt-get update && sudo apt-get install -y openjdk-11-jdk
```
# Download Maven Dependencies
```
sudo apt-get update && sudo apt-get install -y maven
```
# Pushing to Nexus Repository
To push to the Nexus repository, follow these steps:
• When cloning the git repository, the pom.xml file will be located in the demo-backend1 directory and needs to be configured.<br>
• When pushing to the Nexus repository, credentials need to be configured in the .m2/settings.xml file.
```
cd .m2
```
# In .m2/settings.xml, configure credentials for Maven deploy:
```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 https://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>maven-repo-snapshot</id>
      <username>maven</username>
      <password>12345</password>
    </server>
    <server>
      <id>maven-repo-release</id>
      <username>maven</username>
      <password>12345</password>
    </server>
  </servers>
</settings>
```
# To push Maven to Nexus repository, use the below command:
```
./ maven deploy
```

# Navigate to the Python Directory
```
cd microserviceapp/demo-backend2
```
# Install python
```
sudo apt-get update && sudo apt-get install -y python3
```
# Install pip
```
sudo apt-get update && sudo apt-get install -y python3-pip
```
# Run the pip command to download the dependencies
• Navigate to the directory containing requirements.txt:
```
cd microserviceapp/demo-backend2/sa
```
```
pip3 install -r requirements.txt
```
# Package the Python Files for Nexus Repository
```
tar -xzvf pythonfile:1.0.0.tar.gz demo-backend2
```

# Push to Nexus Repository of tar file
• Replace maven:12345 with your Nexus repository credentials and http://3.110.40.233:8081/repository/tar-repo/npm-snap:1.0.0.tar <br>
  with your Nexus repository URL and file path.
```
curl -v -u maven:12345 --upload-file pythonfile:1.0.0.tar.gz "http://3.110.40.233:8081/repository/tar-repo/pythonfile:1.0.0.tar.gz"
```


# Developing React, Python, and Java Projects Using Jenkins Pipeline with SSH 
This guide illustrates how to develop React, Python, and Java projects using a Jenkins pipeline with SSH.
# Prerequisites
Ensure you have the following prerequisites before starting:<br>
• Jenkins installed and configured.<br>
• SSH access to the target servers where the projects will be developed and deployed.<br>
• Git installed on the Jenkins server.<br>
• npm installed for React development.<br>
• Python installed for Python development.<br>
• JDK (Java Development Kit) installed for Java development.<br>
• Nexus repository where you have permissions to deploy artifacts.<br>

# React Deployment Jenkins Job Setup
# Download React Tar File from Nexus Repository
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP "curl -u jashu:12345 -O -L http://43.204.108.122:8081/repository/npm-repo/npmtar.1.1.7.tar"
```
# Unzip the file
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP "tar -xf npmtar.1.1.7.tar"
```
# After unzip copy the content of build, use the below command
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP "cd microserviceapp/demo-frontend/build/* /var/www/html"
```
# Install npm
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP "sudo apt-get update && sudo apt-get install -y npm"
```
# Install Ngnix
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP "sudo apt-get update && sudo apt-get install -y nginx"
```
# Start Nginx
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP "service nginx start"
```
• Ensure to configure your AWS deployment machine to allow traffic on port 80 (HTTP).


# Jenkins Job Setup for Java Deployment
# Downloading Java File from Nexus Repository
To download the Java file from the Nexus Repository, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Adress "curl -u jashu:12345 -O -L "http://43.204.108.122:8081/repository/maven-repo/com/sa/web/sentiment-analysis-web/mvn.1.1.0-SNAPSHOT/sentiment-analysis-web-mvn.1.1.0-20240503.080827-1.jar"
```
# Installing Java
To install Java, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address "sudo apt-get update && sudo apt-get install -y openjdk-11-jdk"
```
# Running the Java Application via SSH
To run the Java application through SSH, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address "java -jar /home/ubuntu/latest.jar --sa.logic.api.url=http://19.234.89.09:5000 &"
```

# Jenkins Job Setup for Python Deployment
# Downloading Python File from Nexus Repository
To download the Java file from the Nexus Repository, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address"curl -u jashu:12345 -O -L http://43.204.108.122:8081/repository/python-repo/pythonfile:1.0.0.tar.gz"
```
# Installing Python
To install Python, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address "sudo apt-get update && sudo apt-get install -y python3"
```
# Installing pip
To install pip, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address "sudo apt-get update && sudo apt-get install -y python3-pip"
```
# Running pip using the below command
To run pip, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address "pip install -r requirement.txt"
```
# Running the Python Application via SSH
To run the Python application through SSH, execute the following command:
```
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@IP Address "python3 sentiment_analysis.py"
```

# Jenkins Docker Pipeline

This `README.md` file provides instructions for building, tagging, pushing, and deploying a Docker image using a Jenkins pipeline.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Pipeline Stages](#pipeline-stages)
   - [Build and Docker Image Creation](#build-and-docker-image-creation)
   - [Docker Tagging](#docker-tagging)
   - [Docker Push](#docker-push)
   - [SSH and Docker Pull](#ssh-and-docker-pull)
4. [Configuration](#configuration)
5. [Running the Pipeline](#running-the-pipeline)
6. [References](#references)

## Introduction

This repository contains a Jenkins pipeline configuration for automating the Docker build, tag, push, and deployment process. It is designed to streamline the CI/CD process by integrating Docker with Jenkins.

## Prerequisites

- Jenkins installed and running.
- Docker installed on both the Jenkins server and the target server.
- SSH access to the target server with appropriate permissions.
- Docker Hub account or other Docker registry credentials for pushing the image.
- Configured Jenkins credentials for Docker Hub (if private repository) and SSH.

## Pipeline Stages

### Build and Docker Image Creation

This stage builds the Docker image from the `Dockerfile` located in the `demo-backend1` directory.

```groovy
stage("Build & making docker image") {
    steps {
        sh "cd demo-backend1 && docker build -t mvnimg:1.1.2 . -f Dockerfile"
    }
}
