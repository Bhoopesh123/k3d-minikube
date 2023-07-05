# k3d-minikube
Below Steps will help to create a k3d minikube cluster on a windows machine.

# 1. Install and configure Ubuntu:
Open powershell with Admin:  

    wsl --install

# 2. Install Ubuntu App from Microsoft Store:

# 3. Install docker on ubuntu:
Reference Documentation is as below:
https://docs.docker.com/engine/install/ubuntu/


Below Steps needs to be followed:

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

If we get any of the below error:

    E: Package 'docker-ce' has no installation candidate
    E: Unable to locate package docker-ce-cli
 
 follow the below steps to resolve it

    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    sudo apt-get update  
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin 

Follow the below steps to add your userid to docker group

    sudo usermod -aG docker ${USER}
    sudo chown root:docker /var/run/docker.sock

Exit the Ubuntu app machine and come back

# 4. Install k3d on Ubuntu:
Reference Documentation is as below:
https://k3d.io/v5.5.1/

Run the below commads:  

    wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
    curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

    k3d cluster create mycluster
    kubectl get nodes
    kubectl cluster-info

# 5. Install Brew:
Reference Documentation is as below:
https://linux.how2shout.com/install-brew-on-ubuntu-22-04-lts-jammy-linux/

    sudo apt update
    sudo apt install build-essential git
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    (echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/bhoopesh/.bashrc
    brew --help

# 6. Install Kubectl:
    brew install kubectl
    kubectl version --client
    
# 7. Run one test pod in default namespace
    kubectl run mycurlpod --image=curlimages/curl -i --tty -- sh

# 8. Install Helm:  
    brew install helm

# 9. Just in case if you want to delete the minikube k3d cluster completely
    k3d cluster delete mycluster
    k3d cluster delete -a

