## Haproxy / SSHD Dockerfile


This repository contains a fork of [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/haproxy/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

It was forked to use supervisord to start haproxy and sshd.


### Base Docker Image

* [dockerfile/ubuntu](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/llamashoes/haproxy-sshd/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull llamashoes/haproxy-sshd`

   (alternatively, you can build an image from Dockerfile: `docker build -t="llamashoes/haproxy-sshd" github.com/llamashoes/haproxy-sshd`)


### Usage

    docker run -d -p 80:80 -p 22 llamashoes/haproxy-sshd



#### Customizing Haproxy and log dir

    docker run -d -p 80:80 -p 22 -v <override-dir>:/haproxy-override llamashoes/haproxy-sshd

or

    docker run -d -p 80:80 -p 22 -v <override-dir>:/haproxy-override -v <log-dir>:/var/log llamashoes/haproxy-sshd

where `<override-dir>` is an absolute path of a directory that could contain:

  - `haproxy.cfg`: custom config file (replace `/dev/log` with `127.0.0.1`, and comment out `daemon`)
  - `errors/`: custom error responses

and `<log-dir>` is an absolute path for log files.

After few seconds, open `http://<host>` to see the haproxy stats page.
