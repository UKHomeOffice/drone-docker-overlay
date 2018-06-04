# Drone docker plugin overlay

[![Docker Stars](https://img.shields.io/docker/stars/ukhomeoffice/drone-docker.svg)](https://hub.docker.com/r/ukhomeoffice/drone-docker/)
[![Docker Pulls](https://img.shields.io/docker/pulls/ukhomeoffice/drone-docker.svg)](https://hub.docker.com/r/ukhomeoffice/drone-docker/)
[![Docker Automated build](https://img.shields.io/docker/automated/ukhomeoffice/drone-docker.svg)](https://hub.docker.com/r/ukhomeoffice/drone-docker/builds/)
[![ImageLayers Size](https://img.shields.io/imagelayers/image-size/ukhomeoffice/drone-docker/latest.svg)]()
[![ImageLayers Layers](https://img.shields.io/imagelayers/layers/ukhomeoffice/drone-docker/latest.svg)]()
[![GitHub license](https://img.shields.io/github/license/UKHomeOffice/drone-docker-overlay.svg)](https://github.com/UKHomeOffice/drone-docker-overlay/blob/master/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/UKHomeOffice/drone-docker-overlay.svg)](https://github.com/UKHomeOffice/drone-docker-overlay/issues)
[![GitHub forks](https://img.shields.io/github/forks/UKHomeOffice/drone-docker-overlay.svg)](https://github.com/UKHomeOffice/drone-docker-overlay/network)
[![GitHub stars](https://img.shields.io/github/stars/UKHomeOffice/drone-docker-overlay.svg)](https://github.com/UKHomeOffice/drone-docker-overlay/stargazers)

Overlay of hub.docker.com/r/plugins/docker that sets ukhomeoffice drone docker dind

The main reason this had to exist is because [drone looks for an exact string match of `plugins/docker`](https://github.com/drone/drone/blob/923de1c4f20ea596bd17d8e4c7fad1e5f192fa87/cmd/drone-server/server.go#L111) and tries to enable privileged which isn't allowed in ACP.
You can also work around it by specifying the full url and specifying the env var of the docker host, the same as I've done in the [Dockerfile](./Dockerfile) here

## Example Usage
```yaml
pipeline:
  build:
    image: ukhomeoffice/drone-docker
    repo: quay.io/ukhomeofficedigital/myimage
    secrets: [ docker_username, docker_password ]
    registry: quay.io
    force_tag: true
    tags:
      - ${DRONE_COMMIT_SHA}
      - ${DRONE_REPO_BRANCH}
    when:
      event: push
```
