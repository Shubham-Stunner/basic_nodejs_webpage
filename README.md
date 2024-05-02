Certainly! Here's the updated README file with Java installation before Jenkins:

---

# Node.js Application Deployment Guide

This guide will walk you through the steps to deploy a Node.js application using Docker and Jenkins on an AWS Ubuntu instance.

## Prerequisites

Before starting, ensure you have the following:

- AWS Ubuntu instance up and running.
- Access to the instance via SSH.
- Docker installed on the AWS Ubuntu instance.
- Java installed on the AWS Ubuntu instance.
- Jenkins installed on the AWS Ubuntu instance.

## Step 1: Install Java

Connect to your AWS Ubuntu instance via SSH and install Java using the following commands:

```bash
sudo apt update
sudo apt install default-jdk
```

Verify the Java installation:

```bash
java -version
```

## Step 2: Install Jenkins

Install Jenkins by adding its official repository to your system:

```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

Update your package index and install Jenkins:

```bash
sudo apt update
sudo apt install jenkins
```

Start the Jenkins service:

```bash
sudo systemctl start jenkins
```

Enable Jenkins to start on boot:

```bash
sudo systemctl enable jenkins
```

## Step 3: Install Docker

If Docker is not already installed, you can follow these steps to install it:

```bash
sudo apt update
sudo apt install docker.io
```

Start the Docker service:

```bash
sudo systemctl start docker
```

Enable Docker to start on boot:

```bash
sudo systemctl enable docker
```

Replace the placeholder stages with the corresponding stages from your Jenkinsfile.

## Step 5: Deploy the Node.js Application

Execute your Jenkins pipeline to deploy the Node.js application:

1. Navigate to your Jenkins dashboard.
2. Select your project/job.
3. Click on "Build Now" to trigger the pipeline.
4. Monitor the pipeline stages for any errors or failures.
5. Once the pipeline completes successfully, access your Node.js application at the AWS Ubuntu instance's public IP address and port 8081.

That's it! You have successfully deployed your Node.js application using Docker and Jenkins on an AWS Ubuntu instance.
