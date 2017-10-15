# Docker Cleanup
This image will periodically clean up exited containers and remove images and volumes that aren't in use by a
running container. Based on [meltwater/docker-cleanup](https://github.com/meltwater/docker-cleanup) with some small fixes.

**WARNING: This script will remove all exited containers, data-only containers and unused images unless you
carefully exclude them. Take care if you mount /var/lib/docker into the container since that will clean
up all unused data volumes. If it's not compatible with your system or Docker version it may delete
all your volumes, even from under running containers.**

The default startup command for PS is:
```
docker run --name clean-up --restart=always -d -v /var/run/docker.sock:/var/run/docker.sock:rw -v /var/lib/docker:/var/lib/docker:rw -e CLEAN_PERIOD=3600 -e DELAY_TIME=900 pasientskyhosting/ps-docker-cleanup:1.8.0
```
