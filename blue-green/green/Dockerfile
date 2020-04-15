FROM nginx:1.17-alpine

# Dockerfile.jenkinsAgent
FROM debian:stretch-backports
# Install Docker in the image, which adds a docker group
RUN apt-get -y update && \
 apt-get -y install \
   apt-transport-https \
   ca-certificates \
   curl \
   gnupg \
   lsb-release \
   software-properties-common

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"

RUN apt-get -y update && \
 apt-get -y install \
   docker-ce \
   docker-ce-cli \
   containerd.io

RUN rm /usr/share/nginx/html/index.html


COPY index.html /usr/share/nginx/html
