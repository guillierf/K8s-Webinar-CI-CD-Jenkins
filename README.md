# K8s-Webinar-CI-CD-Jenkins

Example taken from:
Kubernetes Webinar Series - Building CI CD Pipelines with Jenkins and Kubernetes
https://www.youtube.com/watch?v=288rTpd1SDE&t=1896s

# Note
We are using the following components for this Lab:
Harbor (private registry) - configured with unsecure access mode - IP: 10.40.207.9

# Procedure

Configure a new Jenkins jobs with the following parameters:

Source Code Management: Git

Repository URL: https://github.com/guillierf/K8s-Webinar-CI-CD-Jenkins.git (clone this repository)

Build Triggers: Poll SCM

schedule: * * * * *

Build: Execute shell 1 (commands are in the file Jenkins/cmd.txt)

Build: Execute shell 2 (commands are in the file Jenkins/cmd.txt)



