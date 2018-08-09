FROM python:3.6-alpine

RUN echo "http://dl-8.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
RUN apk --no-cache --update-cache add curl gcc libffi libffi-dev py-cffi openssl-dev g++ gfortran build-base wget freetype-dev libpng-dev openblas-dev
RUN ln -s /usr/include/locale.h /usr/include/xlocale.h

RUN pip install numpy==1.14.3
RUN pip install scipy==1.1.0
RUN pip install pandas==0.23.4
