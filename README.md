# Jenkins and Nginx | <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c5/Nginx_logo.svg/1280px-Nginx_logo.svg.png" alt="servicenow" width="200" height="40" /> 
This project integrates Jenkins with Nginx, using Nginx as a reverse proxy to forward requests to the Jenkins server, ensuring improved security and scalability.

## What was changed?
- <b> docker-compose.yml </b>
  - added extra port mapping: - <i>"8080:8080"</i>
  - using already existing image: <i> jenkins-master:latest </i> (not building method)
- <b> jenkins.conf </b>
  - server_name -> <i> server_name jenkins; </i>
  - added <i> acces_log </i> and <i> error_log </i> for the helpful source in case of further troubles
  - proxy_pass -> http://jenkins-master-1:8080;
- <b> Dockerfile (./jenkins-master) </b>
  - deleted the one Jenkins setting -> <i> --handlerCountMax=300 </i>
  - maintainer -> Adam Wieczorek
- <b> Dockerfile (./jenkins-nginx) </b>
  - base image -> <i>nginx:latest</i>
  - package manager name -> <i>apt</i>
  - maintainer -> Adam Wieczorek

## Prerequisities
- run Notepad as Administrator, open file: <i>C:\Windows\System32\drivers\etc\hosts</i> + add line <i>127.0.0.1 jenkins</i> and save

## Sources
- [Nginx layers - base image](https://hub.docker.com/layers/library/nginx/stable-perl/images/sha256-567e80d2474f7d363aaf3bdae286fc5acd4070e1f5f6c92884f8443ae6b0d2d1)
- [Jenkins documentation](https://github.com/jenkinsci/docker/blob/master/README.md#usage)

## Make the app available - step by step
- clone the repo
- launch Docker Desktop
- go to project/jenkins-master
- run <i> docker build -t jenkins-master . </i>
- go to project/jenkins-nginx
- run <i> docker build -t jenkins-nginx . </i>
- go to project directory
- run <i> docker-compose -p jenkins up -d </i>
- visit browser in incognito tab and type http://jenkins
- follow the steps on the screen

## Screenshots
![containers](https://github.com/user-attachments/assets/6f1549e7-029c-4124-a1a5-aded0a1cbf42)
![images](https://github.com/user-attachments/assets/f5e8a543-f5e1-4023-a7cb-c84cfa1127d3)
![jenkins-logs](https://github.com/user-attachments/assets/90443051-6d16-478d-bfe1-b6ffe92557e7)
![jenkins-app-logs](https://github.com/user-attachments/assets/9dcb64e0-3a38-40c4-968f-6a5d36e2d03d)
![access-log](https://github.com/user-attachments/assets/6ba1458b-f14a-4b94-be70-e8977af1b920)
![jenkins-output](https://github.com/user-attachments/assets/7bd9994e-7e3a-4b3d-a89a-b3cf72282d20)
