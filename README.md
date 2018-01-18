# Drone docker plugin overlay

[![Docker Stars](https://img.shields.io/docker/stars/ukhomeoffice/drone-docker.svg)]()
[![Docker Pulls](https://img.shields.io/docker/pulls/ukhomeoffice/drone-docker.svg)]()
[![Docker Automated build](https://img.shields.io/docker/automated/ukhomeoffice/drone-docker.svg)](https://hub.docker.com/r/ukhomeoffice/drone-docker/builds/)
[![ImageLayers Size](https://img.shields.io/imagelayers/image-size/ukhomeoffice/drone-docker/latest.svg)]()
[![ImageLayers Size](https://img.shields.io/imagelayers/image-size/ukhomeoffice/drone-docker/latest.svg)]()
[![ImageLayers Layers](https://img.shields.io/imagelayers/layers/ukhomeoffice/drone-docker/latest.svg)]()
[![license](https://img.shields.io/github/license/UKHomeOffice/drone-docker-overlay.svg)](https://github.com/UKHomeOffice/drone-docker-overlay/blob/master/LICENSE)

Overlay of hub.docker.com/r/plugins/docker that sets ukhomeoffice drone docker dind

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