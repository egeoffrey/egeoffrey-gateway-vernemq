# egeoffrey-gateway-vernemq

This is an eGeoffrey gateway package.

## Description

Runs the eGeoffrey Gateway (VerneMQ) information.

## Install

To install this package, run the following command from within your eGeoffrey installation directory:
```
egeoffrey-cli install egeoffrey-gateway-vernemq
```
After the installation, remember to run also `egeoffrey-cli start` to ensure the Docker image of the package is effectively downloaded and started.
To validate the installation, go and visit the *'eGeoffrey Admin'* / *'Packages'* page of your eGeoffrey instance. All the modules, default configuration files and out-of-the-box contents if any will be automatically deployed and made available.
## Contribute

If you are the author of this package, simply clone the repository, apply any change you would need and run the following command from within this package's directory to commit your changes and automatically push them to Github:
```
egeoffrey-cli commit "<comment>"
```
After taking this action, remember you still need to build (see below) the package (e.g. the Docker image) to make it available for installation.

If you are a user willing to contribute to somebody's else package, submit your PR (Pull Request); the author will take care of validating your contributation, merging the new content and building a new version.

## Build

Building is required only if you are the author of the package. To build a Docker image and automatically push it to [Docker Hub](https://hub.docker.com/r/egeoffrey/egeoffrey-gateway-vernemq), run the following command from within this package's directory:
```
egeoffrey-cli build egeoffrey-gateway-vernemq
```
To function properly, when running in a Docker container, the following additional configuration settings has to be added to e.g. your docker-compose.yml file (when installing through egeoffrey-cli, this is not needed since done automatically upon installation):
```
environment:
- DOCKER_VERNEMQ_ACCEPT_EULA=yes
- DOCKER_VERNEMQ_ALLOW_ANONYMOUS=on
- DOCKER_VERNEMQ_PLUGINS__VMQ_ACL=off
- DOCKER_VERNEMQ_PLUGINS__VMQ_PASSWD=off
- DOCKER_VERNEMQ_PLUGINS__VMQ_DIVERSITY=off
- DOCKER_VERNEMQ_VMQ_DIVERSITY__HTTP_AUTH__file=/config/plugins/auth_http.lua
- AUTH_API_URL=http://192.168.0.26:5000/api/v1/auth/on_register_hook
- DOCKER_VERNEMQ_LISTENER__SSL__DEFAULT=0.0.0.0:8883
- DOCKER_VERNEMQ_LISTENER__SSL__CAFILE=/config/certs/ca.crt
- DOCKER_VERNEMQ_LISTENER__SSL__CERTFILE=/config/certs/server.crt
- DOCKER_VERNEMQ_LISTENER__SSL__KEYFILE=/config/certs/server.key
- DOCKER_VERNEMQ_PERSISTENT_CLIENT_EXPIRATION=7d
- DOCKER_VERNEMQ_MAX_INFLIGHT_MESSAGES=1
- DOCKER_VERNEMQ_MAX_ONLINE_MESSAGES=1000
- DOCKER_VERNEMQ_MAX_OFFLINE_MESSAGES=1000
- DOCKER_VERNEMQ_LOG__CONSOLE=both
ports:
- 443:8080
- 1883:1883
- 8883:8883
- 8888:8888
volumes:
- ./data/gateway_cloud/data:/vernemq/data
- ./data/gateway_cloud/logs:/vernemq/log
```

## Uninstall

To uninstall this package, run the following command from within your eGeoffrey installation directory:
```
egeoffrey-cli uninstall egeoffrey-gateway-vernemq
```
Remember to run also `egeoffrey-cli start` to ensure the changes are correctly applied.
## Tags

The following tags are associated to this package:
```
gateway
```

## Version

The version of this egeoffrey-gateway-vernemq is 1.0-1 on the master branch.
