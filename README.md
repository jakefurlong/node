# Run Jenkins in a Docker Container

Latest Jenkins image can be found here: https://hub.docker.com/r/jenkins/jenkins

`docker run -p 8080:8080 -p 50000:50000 --restart always jenkins/jenkins:lts-jdk11`

Use administrator password to log in to `http://localhost:8080`


```
b201c1fcd8a742ce860800e8b09ff282
This may also be found at: /var/jenkins_home/secrets/initialAdminPassword
```

- Install suggested plugins
- Wait for build to finish
- Create admin user
- Follow: https://tutorials.releaseworksacademy.com/learn/building-your-first-docker-image-with-jenkins-2-guide-for-developers
- 