FROM ubuntu:20.04

LABEL maintainer="uihyeon.cha"
ARG DEBIAN_FRONTEND="noninteractive"
ENV TZ="Asia/Seoul"

RUN apt-get update

RUN apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

RUN echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list

RUN apt-get update
RUN apt-get install -y kubelet kubeadm kubectl

RUN apt-mark hold kubelet kubeadm kubectl
