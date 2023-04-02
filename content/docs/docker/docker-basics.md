---
title: "Docker Basics"
date: 2023-04-02T16:55:47+01:00
draft: false
---

## Dockerfile
Text file containing the instructions for building a Docker image.

#### Common instructions
* FROM: specifies the base image to be used
* WORKDIR: sets the working directory for the next instructions (until changed)
* COPY: copy files from the host machine  to the image
* RUN: executes a command inside the image
* EXPOSE: opens the specified port from the container to the host machine
* CMD: specifies the default command to run when the container starts
* ENV: set an environment variable
* ARG: set build-time variables
* USER: set the user ID or username when running the container
* VOLUME: creates a mount point for a volume. The volume can be named or anonymous.
* ADD: copy files from the host machine to the image. By default it extracts tar.gz files to the specified destination.
* LABEL: adds meta data to the image.

# Example 

```bash
FROM ubuntu:latest
WORKDIR /app
COPY . /app
RUN apt-get update && apt-get install -y python3
EXPOSE 80
CMD ["python3", "app.py"]
ENV APP_ENV production
ARG APP_VERSION
USER appuser
VOLUME /data
ADD data.tar.gz /data/
LABEL version=$APP_VERSION
```
This Dockerfile specifies that the base image is ubuntu:latest, sets the working directory to /app, copies the contents of the current directory on the host machine to /app in the image, installs python3, exposes port 80, sets the default command to run python3 app.py, sets an environment variable APP_ENV to production, allows for a build-time variable APP_VERSION, sets the user to appuser, creates a mount point for a volume at /data, adds and extracts a data.tar.gz file to /data/ in the image, and adds a label with the key version and value of the build-time variable APP_VERSION.

