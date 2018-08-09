FROM resin/raspberrypi3-python:3.6
COPY ./qemu-system-arm /usr/bin/qemu-system-arm

RUN apt-get update -y
RUN apt-get upgrade
RUN apt-get install -qqy gcc libffi-dev g++ gfortran
RUN apt-get install -y libatlas-base-dev

RUN pip install numpy==1.14.3
RUN pip install scipy==1.1.0
RUN pip install pandas==0.23.4
CMD tail -f /dev/null
