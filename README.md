# Docker container for RPI SaaS development

This docker container is intended to run Python 3.6 apps in a Raspberry PI 3. It is built from `resin/raspberrypi3-python:3.6`, and contains **Python 3.6.6**, **`numpy==1.14.3`**, **`pandas==0.23.4`** and **`scipy==1.1.0`**.

## Pull from Docker Hub

```
docker pull azogue/py36_base:rpi3
# or
docker pull azogue/py36_base:x64
```

## Use it as base container:

Start your Dockerfile with `FROM azogue/py36_base:rpi3`

```
FROM azogue/py36_base:rpi3

ADD ./requirements.txt .
RUN pip3 install -r requirements.txt
RUN ...

...
```

## Build

Get the repo with `git clone https://github.com/azogue/rpi_docker_base`, and `cd rpi_docker_base`.

You need **QEMU** to build the rpi3 container in a x64 platform. In macOS, install it with `brew install qemu`.
Then, copy the needed arm binary to the build dir: `cp /usr/local/bin/qemu-system-arm ./build`.

* For the 'rpi3' build:

```
export DOCKER_ID_USER=azogue
cd build
docker build -t $DOCKER_ID_USER/py36_base:rpi3 .
# Check
docker run -it --rm --name test_py36_base_rpi3 $DOCKER_ID_USER/py36_base:rpi3 /bin/sh
# And push
docker push $DOCKER_ID_USER/py36_base:rpi3
```

* For a 'x64' build:

```
export DOCKER_ID_USER=azogue
cd build_x64
docker build -t $DOCKER_ID_USER/py36_base:x64 .
# Check
docker run -it --rm --name test_py36_base_x64 $DOCKER_ID_USER/py36_base:x64 /bin/bash
# And push
docker push $DOCKER_ID_USER/py36_base:x64
```
