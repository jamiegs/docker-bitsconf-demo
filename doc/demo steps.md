 
Prep
====
aws-switch personal
docker container prune
docker image prune --all
docker pull couchbase:latest
docker pull ubuntu:latest
docker pull microsoft/aspnetcore:2.0
docker pull microsoft/dotnet:2.0-sdk
docker pull microsoft/dotnet:2.0-runtime

Demo Steps
==========


Running Simple container
=========================
docker run docker/whalesay cowsay hello bitsconf

Running Container with prompt
=============================
docker run -it ubuntu bash

run couchbase
=============
docker run -d --name db -p 8091-8094:8091-8094 -p 11210:11210 couchbase

http://localhost:8091

Creating your own image
=======================
dotnet new mvc --name docker-bitsconf-demo

csproj:

	<PropertyGroup>
		<PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
	</PropertyGroup>

subl Dockerfile

docker build . -t docker-bitsconf-demo:latest

docker images
docker run -p 8080:80 docker-bitsconf-demo:latest
docker ps

docker hub is like npm or nugt for docker containers
info on what an image is.
why are steps impressive

seperation of concerns slide
what is marvel? redefine how development wors
wording differences on python and dotnet at the same time
ham up java install, versaw doesn't have to isntall java anymore
waht are images, ubuntu, blah

ECS
===

Create the repository in console.
---------------------------------
docker-bitsconf-demo

Login to ECS
------------
aws ecr get-login --no-include-email --region us-east-1

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
subl bitsconf-task.json

aws ecs register-task-definition --cli-input-json file://$HOME/personalGit/docker-bitsconf-demo/src/bitsconf-task.json

Create Service and Launch Containers
------------------------------------
aws ecs create-service --cluster fargate-cluster --service-name fargate-service --task-definition sample-fargate:9 --load-balancers targetGroupArn=arn:aws:elasticloadbalancing:us-east-1:774656682386:targetgroup/bitsconf-target-group/71c3ec2a618d16ec,containerName=bitsconf-demo,containerPort=80 --desired-count 2 --launch-type "FARGATE" --network-configuration "awsvpcConfiguration={subnets=[subnet-536acb7c,subnet-0500da58],securityGroups=[sg-6dd1b918],assignPublicIp=ENABLED}"

Demo Url
--------
http://bitsconf.jamiesnell.com/

