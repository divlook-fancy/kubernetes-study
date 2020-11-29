# kubeadm을 사용하여 쿠버네티스 설치하기

이 글은 Ubuntu에서 kubeadm을 사용하여 쿠버네티스를 설치하는 방법을 공부하며 정리한 내용입니다.

## 쿠버네티스 설치

```bash
$ sudo apt-get update

$ sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

$ cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF

$ sudo apt-get update
$ sudo apt-get install -y kubelet kubeadm kubectl

$ sudo apt-mark hold kubelet kubeadm kubectl
```

## 도커를 사용한 실습

```bash
$ git clone git@github.com:divlook/kubernetes-study.git
$ cd kubernetes-study/docs/install

# 이미지 build
$ docker build -t kubernetes-study/install .

# 컨테이너 생성
$ docker run -it --rm --name kubernetes-study.install kubernetes-study/install bash

# 컨테이너 내부에서 아래 명령어를 사용하여 설치 확인
$ kubeadm version
$ kubelet --version
$ kubectl version
```

## 참고 사이트

- https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/
- https://medium.com/finda-tech/overview-8d169b2a54ff
