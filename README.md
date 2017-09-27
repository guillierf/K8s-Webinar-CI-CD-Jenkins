# K8s-Webinar-CI-CD-Jenkins

Example taken from:

Kubernetes Webinar Series - Building CI CD Pipelines with Jenkins and Kubernetes

https://www.youtube.com/watch?v=288rTpd1SDE&t=1896s

# Lab Config
We are using the following components for this Lab:

Harbor (private registry) - configured with unsecure access mode - IP: 10.40.207.9

# Create Jenkins Jobs

Configure a new Jenkins jobs with the following parameters:

*Source Code Management: Git

Repository URL: https://github.com/guillierf/K8s-Webinar-CI-CD-Jenkins.git (clone this repository)

*Build Triggers: Poll SCM

schedule: * * * * *

*Build: Execute shell 1 (commands are in the file Jenkins/cmds.txt)

*Build: Execute shell 2 (commands are in the file Jenkins/cmds.txt)


# Run Deployment on Kubernetes Cluster

Run the following commands on your K8s cluster:

```
kubectl create deployment hellowhale --image 10.40.207.9/library/hellowhale
```

```
kubectl expose deployment hellowhale --port=80 --name=hellowhale-svc --type=NodePort
```

```
kubectl scale deployment hellowhale --replicas 10
```

# Automatically trigger the Jenkins jobs

from your mac:

```
git clone https://github.com/guillierf/K8s-Webinar-CI-CD-Jenkins.git
```
(replace the URL link with your own cloned repository)

```vi Build-Docker/hellowhale/html/index.html
```

modify Hello Kubernetes Fans! v<X> to modify Hello Kubernetes Fans! v<Y>

```
git add Build-Docker/hellowhale/html/index.html
```

```
git commit -m "update index.html"
```

```
$ git push
```

Check:
```
kubectl rollout history deployment hellowhale
```
