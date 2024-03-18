# Jenkins
## What is Jenkins?
Jenkins is an open-source automation server that helps automate the process of building, testing, and deploying software. It allows you to set up pipelines to automatically build your code, run tests, and deploy applications to various environments. Jenkins is highly extensible and can be integrated with a wide range of tools and plugins to support continuous integration and continuous delivery (CI/CD) workflows.

## Continuous Integration (CI) : 
  Is the practice of frequently integrating code changes into a shared repository. Each integration is verified by automated build and test processes, allowing teams to detect and fix problems early.
## Continuous Delivery (CD) :
Is the practice of automatically building, testing, and preparing code changes for deployment to production. With continuous delivery, every change that passes automated tests can be deployed to a production-like environment, where it's ready to be released to customers at any time.
## Continuous Deployment (CD) :
Goes one step further by automatically deploying every change that passes through the pipeline to production, without human intervention. This practice is more common in environments where rapid and frequent releases are essential.

## Install Jenkins in ec2 machine use t2.large
First install java for jenkins in ubuntu in ec2
```bash
  sudo apt update
  sudo apt install fontconfig openjdk-17-jre
  java --version #Check Java Install or not
```
Install Jenkins longterm support for stable version
```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
## Start Jenkins
You can enable the Jenkins service to start at boot with the command:
```bash
sudo systemctl enable jenkins
```
You can start the Jenkins service with the command:
```bash
sudo systemctl start jenkins
```
You can check the status of the Jenkins service using the command:
```bash
sudo systemctl status jenkins
```
🔘 Go to Security group, edit inbound rules add custom TCP Select Port range 8080 & anywhere-IPv4 Save it.
🔘 Go to web browser and paste public-ip with port 8080.
🔘 For password:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
🔘 Select install plugin.
🔘 Fill the form & Save it.

## Also install docker and docker-compose on ec2 machine.
To install docker and docker-compose:
```bash
sudo apt update
sudo apt install docker.io docker-compose -y
```
You can enable the Docker service to start at boot with the command:
```bash
sudo systemctl enable docker
```
You can start the Docker service with the command:
```bash
sudo systemctl start docker
```
You can check the status of the Docker service using the command:
```bash
sudo systemctl status docker
```
## Add ubuntu and jenkins in docker group
```bash
sudo usermod -aG docker $USER
sudo usermod -aG docker jenkins
```
## Reboot the system 
```bash
sudo reboot
```













