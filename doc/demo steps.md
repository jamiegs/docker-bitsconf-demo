Demo Steps
==========
dotnet new mvc

docker run docker/whalesay cowsay hello bitsconf

docker run ubuntu bash

docker build . -t docker-bitsconf-demo

docker run -p 80 docker-bitsconf-demo
docker run -d -p 80 docker-bitsconf-demo

docker stop $(docker ps -a -q)


p-autocapture-web-ecs


aws ecs run-task --launch-type FARGATE --cluster fargate-test --task-definition nginx --network-configuration
"awsvpcConfiguration={subnets=[subnet-b563fcd3]}" 



