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
• When pushing to the Nexus repository, credentials need to be configured in the .m2 file.
```
cd .m2
```
# In .m2 file create a file for settings.xml for credentials while maven deploy
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
```
cd microserviceapp/demo-backend2/sa
```
```
pip3 install -r requirements.txt
```
# Package the React Files for Nexus Repository
```
tar -xzvf pythonfile:1.0.0.tar.gz demo-backend2
```
# Push to Nexus Repository of tar file
• Replace maven:12345 with your Nexus repository credentials and http://3.110.40.233:8081/repository/tar-repo/npm-snap:1.0.0.tar <br>
  with your Nexus repository URL and file path.
```
curl -v -u maven:12345 --upload-file pythonfile:1.0.0.tar.gz "http://3.110.40.233:8081/repository/tar-repo/pythonfile:1.0.0.tar.gz"
```
