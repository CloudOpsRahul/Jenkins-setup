## Now Let's start the Project
◼️Set EC2 Instance:

Instance Type - minimum t2.large & minimum Volume 10 GB.

◼️Install Openjdk 17-jre:

To run Jenkins, you need to have Java installed on your machine.
```bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre
```

◼️Install Jenkins:

Long Term Support Release
```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

◼️Now enable, start and verify the Jenkins service with below command:

```bash
sudo systemctl enable jenkins   
sudo systemctl start jenkins
sudo systemctl status jenkins
```

◼️Install Docker and docker-compose:
```bash
sudo apt-get install docker.io docker-compose -y
```

◼️Add Current User & jenkins into docker group:
```bash
sudo usermod -aG docker $USER
sudo usermod -aG docker jenkins
```
◼️Once reboot your instance:
```bash
sudo reboot
```
◼️Check current user & jenkins added in docker group:
```bash
sudo cat /etc/group
```

◼️Install SonarQube:

To start a Docker container running SonarQube Community Edition in the LTS (Long Term Support) version.
```bash
docker run -itd --name sonarqube-server -p 9000:9000 sonarqube:lts-community
```

◼️Install Trivy:
```bash
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```

◼️Now add the Ports shown below:

Go to Instance Security-> Security Groups-> Edit Inbound Rules-> Add Rules

For Jenkins: 8080, For SonarQube: 9000, For Docker: 8000

◼️Access Jenkins Server: With url as http://<publicIP>:8080

After acess jenkins-> Select suggested plugins.

After Installation you'll get path: /var/lib/jenkins/secrets/initialAdminPassword

Just copy that directory path and paste it in EC2 terminal using cat:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
◼️Copy the password and paste to jenkins. & Create your Jenkins account.

◼️Install SonarQube, OWASP, Docker plugins in Jenkins:
- Goto Dashboard-->Manage Jenkins-->Plugins
Plugins - SonarQube Scanner, Sonar Quality Gates, OWASP Dependency-Check, Docker.

◼️Access SonarQube Server: To access server just use http://<publicIP>:9000

Initially username and password will be ‘ admin’ , ’ admin’. Just change with a new password.

◼️Create users token in SonarQube server: Generate a token for authentication purposes. Click on Administration tab-> Security-> Users-> create Token name as jenkins.

Whatever token generated, just copy and paste to somewhere else. Once window is closed, you wont be able to see that again.

◼️Create a webhook in SonarQube server: Administration-> Configuration-> Webhook-> Create
 - In URL enter the jenkins url "ip:8080/sonarqube-webhook/"


◼️Now Add SonarQube Credentials to Jenkins:

Manage Jenkins-> Credentials-> Add SonarQube Credential

Kind -Secret Text

Scope- Global (Jenkins nodes..)

Secret- Token generated from sonarqube.

ID- Sonar

Description- Sonar

◼️Also Add DockerHub Credentials:

Kind- ‘Username with Password‘

Scope- Global (Jenkins nodes..)

Username- your DockerHub Username

Password- your DockerHub Password

ID- DockerHubCreds

Description- DockerHub Credentials.

◼️Add or Link SonarQube Server in Jenkins:

Manage Jenkins-> System-> SonarQube Servers-> SonarQube Installations-> Add SonarQube

Name : Sonar
Server URL:http://ipaddress:9000
Server authentication token: Sonar (Sonarqube server saved credentials).


















