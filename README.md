# Build a New Docker Image using Jenkins

```
docker run -p 8080:8080 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name jenkins \
  jenkins/jenkins:lts
```

Use administrator password to log in to `http://localhost:8080`

*Your creds will be different*
```
7c9d7be51f61410f8352928df017649b

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword
```

- skip and login as admin user
- docker exec -it -u root jenkins bash


Install extras in Jenkins container

```
apt-get update && \
apt-get -y install apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common && \
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
   $(lsb_release -cs) \
   stable" && \
apt-get update && \
apt-get -y install docker-ce
```

Inside the container, give acces to /var/run/* 777

## Create a Pipeline
- New Item
- Pipeline
- Build Trigger: Poll SCM
- Schedule: `H/5 * * * *`
- Pipeline Script from SCM
- SCM = Git
- Provide Repo URL
- Branch = main
- Save
- Build now & wait