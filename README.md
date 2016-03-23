# YouTrack on Docker

This repository contains a Docker image of JetBrains [YouTrack 6.5](http://www.jetbrains.com/youtrack).

## Usage

First, pull the Docker image using the following command:

	docker pull barogi/youtrack

Next, create a container.

	docker run -d barogi/youtrack

YouTrack starts and listens on port 80 in the container.
To map it to the host's port 8000, use the following command to create the container instead:

	docker run --name="youtrack" -p 8000:80 -d barogi/youtrack

### Additional settings

YouTrack stores its data and backups at ```/root/teamsysdata``` and ```/root/teamsysdata-backup``` in the container. If you wish to re-use data, it is a good idea to set up a volume mapping for these two paths. For example:

	docker run --name="youtrack" -d \
	-v /path/on/host/teamsysdata:/root/teamsysdata \
	-v /path/on/host/teamsysdata-backup:/root/teamsysdata-backup \
	-p 8000:80 \
	barogi/youtrack
