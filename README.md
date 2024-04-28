# End to End DevSecOps Project `- Using Jenkins, CI/CD, Docker, Docker-Compose, Sonarqube, Owasp Dependency Check, Trivy`

## Introduction

In the ever-evolving landscape of software development, the integration of security practices into the development and deployment processes has become paramount. DevSecOps, an extension of DevOps, emphasizes the seamless integration of security into the software development lifecycle. This project serves as an exploration of various DevOps and DevSecOps tools, providing hands-on experience with their implementation.

## Tools Covered
```bash
- Linux: `The foundational operating system for hosting our DevOps and DevSecOps tools.`
- Git and GitHub: `Version control system and collaboration platform for managing code repositories.`
- Docker: `Containerization platform used for packaging applications and their dependencies into standardized units.`
- Docker-compose: `Tool for defining and running multi-container Docker applications.`
- Jenkins CI/CD: `Automation server for building, testing, and deploying software continuously.`
- SonarQube Scan: `Static code analysis tool for identifying and fixing code quality and security issues.`
- SonarQube Quality Gates: `Criteria set to ensure code quality and security standards are met before code is deployed.`
- Trivy: `Vulnerability scanner for container images, providing insights into security risks.`
```
## Project Overview

This project focuses on deploying a 3-tier application using Docker and implementing Continuous Integration/Continuous Deployment (CI/CD) pipelines with Jenkins. The emphasis is on incorporating DevSecOps practices throughout the development and deployment process. By following along with this project, you will gain practical experience with each of the covered tools and learn how to seamlessly integrate security into your DevOps workflow.

![Alt text](https://i.imgur.com/NxmCiA5.png)

## Pre-requisites to implement this project:

-  AWS EC2 instance (Ubuntu) with instance type t2.large and root volume 29GB.

-  Jenkins installed <br>
    - Reference: <b><a href="https://www.jenkins.io/doc/book/installing/linux/#long-term-support-release"><u> Jenkins installation </a></u></b>

-  Docker and docker-compose installled
```bash
    sudo apt-get update
    sudo apt-get install docker.io -y
    sudo apt-get install docker-compose -y
```

- Trivy installed <br>
    - Reference: <b> <a href="https://github.com/DevMadhup/Trivy_Installation_and_implementation/blob/main/README.md"><u>Trivy Installation</a></u></b>

- SonarQube Server installed
```bash
    docker run -itd --name sonarqube-server -p 9000:9000 sonarqube:lts-community
```
#
## Steps for Jenkins CI/CD:

1)  Access Jenkins UI and setup Jenkins

![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/1eec417e-95ab-4497-ad31-443ecd6b999e)

#

2)  Plugins Installation:

    - Go to <b><i><u>Manage Jenkins</u></i></b>, click on <b><i><u>Plugins</u></i></b> and install all the plugins listed below, we will require for other tools integration:

        - SonarQube Scanner (Version2.16.1)
        - Sonar Quality Gates (Version1.3.1)
        - OWASP Dependency-Check (Version5.4.3)
        - Docker (Version1.5)
#

3) Go to SonarQube Server and create token

    - Click on <b><i><u> Administration </u></i></b> tab, then <b><i><u> Security </u></i></b>, then <b><i><u> Users </u></i></b> and create Token.
    -  Create a webhook to notify Jenkins that Quality gates scanning is done. (We will need this step later)

        - Go to SonarQube Server, then <b><i><u> Administration </u></i></b>, then <b><i><u> Configuration </u></i></b> and click on <b><i><u> Webhook </u></i></b>, add webhook in below <b>Format</b>:
        > http://<jenkins_url>:8080/sonarqube-webhook/
        
        Example: 
        
        ```bash
            http://34.207.58.19:8080/sonarqube-webhook/
        ```

        ![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/b9ef2301-b8ff-46f4-a457-6345d5e2dab6)


        ![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/08a33164-f6a6-4c5d-8a34-7091cf8a5745)

#

4) Go to Jenkins UI <b><i><u> Manage Jenkins </u></i></b>, then <b><i><u> Credentials </u></i></b> and add SonarQube Credentials.

![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/f6db72ec-7d8c-4f4c-ae7a-55d99dd20ce9)

#

5) Now, It's time to integrate SonarQube Server with Jenkins, go to <b><i><u> Manage Jenkins </u></i></b>, then <b><i><u> System </u></i></b> and look for <b><i><u> SonarQube Servers </u></i></b> and add SonarQube.

![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/54849cb2-fe56-4acd-972d-3057a0eb3deb)

#

6) Go to <b><i><u> Manage Jenkins </u></i></b>, then <b><i><u> tools </u></i></b>, look for <b><i><u> SonarQube Scanner installations </u></i></b> and add SonarQube Scanner.

> Note: Add name as ```Sonar```

![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/1fe926f6-a844-42d4-bce4-62193dde6640)

7) Integrate OWASP with Jenkins, go to <b><i><u> Manage Jenkins </u></i></b>, then <b><i> tools </i></b>, look for <b><i><u>Dependency-Check installations</u></i></b> and add Dependency-Check.

> Note: Add name as ```dc```

![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/14516995-0c96-4110-bb96-97a37a9fe57d)

#

8) For trivy, we have already installed it, in pre-reuisites.

![image](https://github.com/DevMadhup/node-todo-cicd/assets/121779953/0fcd1620-bd64-4286-bc13-f6652d4527c6)
