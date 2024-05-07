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
# To push to nexus repo use the below command
```
curl -u username:password -O -L <NEXUS_URL> <NEXUS_PATH>/react.tar.gz
```
# This command navigates to correct directory path of the file Maven
```
cd micorserviceapp/demo-backend1
```
# To install jdk use the below command
```
sudo apt-get update && sudo apt-get install -y openjdk-11-jdk
```
# Maven install
```
sudo apt-get update && sudo apt-get install -y maven
```
