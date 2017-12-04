Demo Steps
==========

docker run docker/whalesay cowsay hello bitsconf

docker run -it ubuntu bash

run couchbase
=============
docker run -d --name db -p 8091-8094:8091-8094 -p 11210:11210 couchbase
http://localhost:8091

dotnet new mvc

subl Dockerfile

docker build . -t docker-bitsconf-demo:latest

docker run -p 8080:80 docker-bitsconf-demo:latest

docker run -d -p 8080:80 docker-bitsconf-demo:latest

docker stop $(docker ps -a -q)


Create the repository in console.
---------------------------------
docker-bitsconf-demo

Login to ECS
------------
aws ecr get-login --no-include-email --region us-east-2

Tag image for upload
--------------------
docker tag docker-bitsconf-demo:latest 774656682386.dkr.ecr.us-east-1.amazonaws.com/docker-bitsconf-demo:latest

Upload image to ECR
-------------------
docker push 774656682386.dkr.ecr.us-east-1.amazonaws.com/docker-bitsconf-demo:latest

Create Cluster
--------------
aws ecs create-cluster --cluster-name fargate-cluster

Register Task Definition
------------------------------------
aws ecs register-task-definition --cli-input-json file://$HOME/personalGit/docker-bitsconf-demo/src/sample-taskdefinition.json

Create Service and Launch Containers
------------------------------------
aws ecs create-service --cluster fargate-cluster --service-name fargate-service --task-definition sample-fargate:4 --load-balancers targetGroupArn=arn:aws:elasticloadbalancing:us-east-1:774656682386:targetgroup/bitsconf-target-group/71c3ec2a618d16ec,containerName=bitsconf-demo,containerPort=80 --desired-count 2 --launch-type "FARGATE" --network-configuration "awsvpcConfiguration={subnets=[subnet-536acb7c,subnet-0500da58],securityGroups=[sg-6dd1b918],assignPublicIp=ENABLED}"

Demo Url
--------
http://bitsconf.jamiesnell.com/

