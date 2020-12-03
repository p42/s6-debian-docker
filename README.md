# project42/s6-debian

[![pipeline status](https://git.jordanclark.us/devops/s6-debian-docker/badges/master/pipeline.svg)](https://git.jordanclark.us/devops/s6-debian-docker/commits/master)

## Introduction
A docker image based on Debian Linux with the s6 process supervisor

### What is Debian Linux?

Debian Linux is composed entirely of free software, and packaged by a group of individuals participating in the Debian Project. Debian is community driven, developed openly and freely distributed in the spirit of the GNU Project.

### What is the s6-overlay?
The [s6-overlay project](https://github.com/just-containers/s6-overlay) is a series of init scripts and utilities to ease creating Docker images using s6 as a process supervisor.  The s6-overlay makes it easy to take advantages of s6 while still operate like other Docker images.  The s6 init system provides many helpful tools to initialize and manage processes as the Docker container starts.

### Tags

| Tag | Description |
|---|---|
| latest | The most current build.  Images based on latest may change often an possibly could break.  Test your images |
| 10, buster | Latest Debian 10, Buster series |
| 9, stretch | Latest Debian 9, Stretch series |
| 8, jessie | Latest Debian 8, Jessie series |
| 9.5 | Debian Linux 9.5 built on 2018-07-30 |
| 2.1.0.2 | Debian 10.6 with S6 Overlay v2.1.0.2 built on 2020-12-03 |
| 1.21.4.0 | Debian 9.5 with S6 Overlay v1.21.4.0 built on 2018-07-30 |
| 1.20.0.0 | Debian 9.1 with S6 Overlay v1.20.0.0 built on 2017-09-26 |

### Issues

I'm sure there are some but currently I'm unaware of current issues.  If you find an issue please let me know on [GitHub](https://github.com/p42/s6-debian-docker/issues)

### Prerequisites

A working docker daemon would be helpful to utilize this image.

## How to use this image

This image is meant to be used as a base to build custom docker images from.  It's value is that it takes the base Debian linux image and adds the s6 overlay.

### Usage

###### Running a quick Debian linux container

~~~
docker run --rm -ti project42/s6-debian:latest bash
~~~

This will present you with a shell on fresh container that will stop and remove itself when you exit the container.

###### Dockerfile that is based of of this image.

~~~
FROM project42/s6-debian:latest

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
    apt-get install -y cowsay && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/init"]
~~~

## Configuration

### Configuration Parameters
| Environment | Description |
| --- | --- |
| TZ | Sets the container Timezone; example: CST6CDT default: UTC |  

## Maintenance

### Shell Access

This image includes the bash shell and when running in detached mode can be connected to with:

~~~
docker exec -ti <container> bash
~~~


## References

Maintainer: [https://jordanclark.us](https://jordanclark.us)

Maintainer's git repo: [https://git.jordanclark.us/devops/s6-debian-docker](https://git.jordanclark.us/devops/s6-debian-docker)

Github Issues: [https://github.com/p42/s6-debian-docker/issues](https://github.com/p42/s6-debian-docker/issues)

Debian Linux: [https://www.debian.org](https://www.debian.org)

s6-overlay: [https://github.com/just-containers/s6-overlay](https://github.com/just-containers/s6-overlay)

s6 supervisor: [http://www.skarnet.org/software/s6/index.html](http://www.skarnet.org/software/s6/index.html)
