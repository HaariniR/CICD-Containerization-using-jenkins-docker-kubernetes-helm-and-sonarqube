# CICD-Containerization-using-jenkins-docker-kubernetes-helm-and-sonarqube

Aim: The main objective of the project is to automate deployment of microservices.
This project involves automation of code build, analysis, building of docker image and deployment of the application on kubernetes cluster.

Servers involved: (These are run as AWS EC2 instances)
Jenkins server

Sonarqube server

Backend instances server - RabbitMQ, ElasticCache, Memcached are created as docker images.

Kubernetes server - created using KOPS

![image](https://user-images.githubusercontent.com/102613218/229347809-99327ea4-0358-4e53-9944-76927bb5aa76.png)

Step1:
This involves code build - fetching the code from github and building the artifact.

Step2:
This involves performing unit and integrated testing.

Step3: 
Code analysis and quality gates checking using sonarqube.

Step4: 
Next build the tomcat docker image using the artifact that is built in step 1

Step5: 
Using KOPS create a kubernetes cluster. Configure jenkins to be used with KOPS as a slave node.

Step 6: In slave node, install helm and create helm charts using the kubernetes files(deployment,service files)
All services will get deployed on the clusters created when helm install job is executed.

Everytime the kubernetes cluster will be deployed with the dynamically built docker image using the latest artifact

![image](https://user-images.githubusercontent.com/102613218/229348109-2726e73f-35bb-4469-965b-c1fb17e457e4.png)

Route53 configuration for kops
![image](https://user-images.githubusercontent.com/102613218/229348135-ea90deab-ed90-4971-9f55-e1fc3ec062ea.png)

S3 bucket for kops
![image](https://user-images.githubusercontent.com/102613218/229348147-3dee6245-3e27-4e68-a9b3-0cb4f75f4ba3.png)

KOPS configuration as slave node
![image](https://user-images.githubusercontent.com/102613218/229348204-e50ec097-7a86-4695-87d8-f2d4e07ef891.png)
![image](https://user-images.githubusercontent.com/102613218/229348239-31bede84-ae6a-4b58-97a8-2216f3e91639.png)
![image](https://user-images.githubusercontent.com/102613218/229348247-b60aaac6-ef8d-4f35-9d43-dde6e933cf7b.png)

Jenkins pipeline as a code
![image](https://user-images.githubusercontent.com/102613218/229348155-f7543c8b-1da3-485c-9746-032207542678.png)
![image](https://user-images.githubusercontent.com/102613218/229348159-d0f81411-bcd0-4f4c-99a4-67e2d15801eb.png)

Overview of the pipeline
![image](https://user-images.githubusercontent.com/102613218/229348121-a7691278-3987-432f-b836-713d7533847a.png)

Sonarqube quality gates passed
![image](https://user-images.githubusercontent.com/102613218/229348396-168f2329-16a7-4444-b6c3-8c54d98ab608.png)

Docker image built:
![image](https://user-images.githubusercontent.com/102613218/229348475-3b5d72a0-ba8e-4a25-a199-a5d20c2fdc7b.png)

These docker images were built automatically using jenkins
![image](https://user-images.githubusercontent.com/102613218/229348483-03f80e5e-bfd0-42b6-a8ed-ff1ce6584689.png)



Overview of helm charts
![image](https://user-images.githubusercontent.com/102613218/229348282-c149a8a3-fd61-4360-af66-06b41ea5b4bb.png)

Successful deployment of all services on kuernetes using helm install
![image](https://user-images.githubusercontent.com/102613218/229348328-14e478cc-84a1-4600-8fd2-458e5e006589.png)

