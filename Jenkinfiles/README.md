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
# This command navigates to correct directory path of the file
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
# Push to Nexus Repository
• Replace maven:12345 with your Nexus repository credentials and http://3.110.40.233:8081/repository/tar-repo/npm-snap:1.0.0.tar with your Nexus repository URL and 
  file path.
```
curl -v -u maven:12345 --upload-file npm_snap:1.0.0.tar "http://3.110.40.233:8081/repository/tar-repo/npm-snap:1.0.0.tar"
```
# Navigate to the Maven Directory
```
cd micorserviceapp/demo-backend1
```
# Install JDK
```
sudo apt-get update && sudo apt-get install -y openjdk-11-jdk
```
# Download Maven Dependencies
```
sudo apt-get update && sudo apt-get install -y maven
```
