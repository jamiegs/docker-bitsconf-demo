30 min presentation

https://docs.google.com/presentation/d/1eSf8KrV-Uy6NO6woc1Scnn9oHKQG6ugfTYr08WMXjdA/edit

Description: Nov 30th
Talk: December 5th

Learn what Docker and ECS are, why we're using them for Marvel, and how it can make your life better at Hudl and beyond.

https://www.youtube.com/watch?v=FdkNAjjO5yQ - docker for developers
https://www.youtube.com/watch?v=Q5POuMHxW-0 - introduction to docker - early
https://www.youtube.com/watch?v=Q5POuMHxW-0 - why we built docker
https://www.youtube.com/watch?v=3N3n9FzebAA - Docker Vs VM
https://www.youtube.com/watch?v=J88J_yox940&list=PLed9PY_Wq5pOBUw4XfoUMfom0WAu8WfpX  - Docker lightning talks
https://www.youtube.com/watch?v=4sBF5Dg8dQ4 - Why docker is perfect for microservices

Resources:
https://www.airpair.com/docker/posts/8-proven-real-world-ways-to-use-docker

Agenda
	
	- What is docker
		- Docker is just the most popular containerization software, there are others such as rkt.
		- build, ship, run
		- copy on write

		- typical memory footprint overhead of around 1.5 Mb, which is much better than a VM, which would be in hundreds of Mb

		- Benefits it provides
		- How to use it for your own projects	
		- Examples of use-cases

		- linux containers, running on linux are just running issolated. from other applications, not running in a VM
		- Windows and Mac run in lightweight VMs
		- everything is done through api, can program against.

		- snapshots, don't have to rebuild the full thing, able to zoom thorough builds if dependancies are installed first.
		- basic commands
			- ps
			- rm
			- stop
			- exec 
		- whole point is it provides all pieces required to run the application in the container images, don't need to worry about installing everything.
		- Differences
			- each vm is it's own OS, takes a whole OS boot. containers are just files running issolated from the rest of the OS, there's no boot process.
			- VMs take many seconds to minutes to boot, docker containers take ms to start
			- VMs reserve memory, disk, cpu. docker only uses what's needed, are able to set limits.
			- running multiple images doesn't create multiple copies of an image, only copy-on-write changes made during runtime are written to seperately.
			- base images are much easier to create in docker, and built automatically
			- dockerfiles are easier to create than vm images. with VMs you'd need to learn chef, ansible, or something similar.
		- reliable and consistant environment
		- a docker image is just a tarball + metadata, no magic
	- What is ECS
		- Benefits it provides
		- can use aws api and cli to interact with
		- has dedicated ecs-cli to simplify interaction
	- What is Fargate
		- https://cdn-images-1.medium.com/max/1600/1*GSVXxgrcREUoS_vRTbajpw.png
		- Deploy to fargate.
		- Fully managed servers
		- servers are dedicated to you
		- pricing
	- Show how it can be used for local couchbase, mongo, redis.

