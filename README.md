# k3d-minikube
k3d minikube cluster

# Install and configure Ubuntu:
# Open powershell with Admin:
wsl --install

# Install Ubuntu App 22.04.2 LTS:

# Install docker on ubuntu:
https://docs.docker.com/engine/install/ubuntu/
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

E: Package 'docker-ce' has no installation candidate
E: Unable to locate package docker-ce-cli
E: Unable to locate package containerd.io
E: Couldn't find any package by glob 'containerd.io'
E: Couldn't find any package by regex 'containerd.io'

https://stackoverflow.com/questions/71393595/installing-docker-in-ubuntu-from-repo-cant-find-a-repo
sudo apt-get install \
     ca-certificates \
     curl \
     gnupg \
     lsb-release

https://docs.docker.com/engine/install/ubuntu/

sudo usermod -aG docker ${USER}
sudo chown root:docker /var/run/docker.sock

exit the ubuntu machine and come back

# install k3d on ubuntu 22.04:
https://k3d.io/v5.5.1/

wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

k3d cluster create mycluster
kubectl get nodes
kubectl cluster-info

# Just in case if you want to delete the cluste
k3d cluster delete mycluster
k3d cluster delete -a


# Install Brew:
https://linux.how2shout.com/install-brew-on-ubuntu-22-04-lts-jammy-linux/

sudo apt update
sudo apt install build-essential git
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
(echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/bhoopesh/.bashrc
brew --help


# Install Kubectl:
brew install kubectl
kubectl version --client
kubectl run mycurlpod --image=curlimages/curl -i --tty -- sh

# Install Helm:
brew install helm



