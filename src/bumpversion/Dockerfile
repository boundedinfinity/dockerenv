FROM boundedinfinity/python:3.7.0
LABEL maintainer="brad.babb@boundedinfinity.com"

RUN apk add --no-cache tini
RUN apk add --no-cache git

COPY requirements.txt /tmp
RUN pip install --disable-pip-version-check -r /tmp/requirements.txt

WORKDIR /src
