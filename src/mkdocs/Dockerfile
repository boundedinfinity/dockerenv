FROM boundedinfinity/python:3.7.0
LABEL maintainer="brad.babb@boundedinfinity.com"

RUN apk add --no-cache tini
RUN apk add --no-cache git
RUN apk add --no-cache nodejs
RUN apk add --no-cache npm

RUN npm install --global yarn@1.10.1

COPY requirements.txt /tmp
RUN pip install --disable-pip-version-check -r /tmp/requirements.txt

ENV PORT 8000

WORKDIR /src
