# jenkins-with-docker
Jenkins Docker Image able to call Docker CLI  

Installation steps:
```
docker build -t jenkins-docker .
```
```
docker run --privileged --restart=unless-stopped --name jenkins-docker -d -p 5300:8080 -p 5301:50000 --group-add $(stat -c '%g' /var/run/docker.sock) -v /var/run/docker.sock:/var/run/docker.sock -v /[host_path_to_jenkins_home]:/var/jenkins_home -P jenkins-docker
```

Replace $(stat -c '%g' /var/run/docker.sock) with the groupid of docker user (synology: 0) if command is executed from other machine. 

Replace /[host_path_to_jenkins_home] with Jenkin's configuration directory.


Example for Synology devices:
```
docker run --privileged --restart=unless-stopped --name jenkins-docker -d -p 5300:8080 -p 5301:50000 --group-add 0 -v /var/run/docker.sock:/var/run/docker.sock -v /volume1/docker/jenkins:/var/jenkins_home -P jenkins-docker
```


