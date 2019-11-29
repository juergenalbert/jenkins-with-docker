# jenkins-with-docker
Jenkins Docker Image able to call Docker CLI  

Installation steps:
```
docker build -t jenkins-docker .
```
```
sudo docker run --privileged --restart=unless-stopped --name jenkins-docker -d -p 5300:8080 -p 5301:50000 --group-add $(stat -c '%g' /var/run/docker.sock) -v /var/run/docker.sock:/var/run/docker.sock -v /host_path_to_jenkins_home:/var/jenkins_home -P jenkins-docker
```

