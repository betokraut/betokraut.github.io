
# Install & Configure on Ubuntu

## Install Docker Engine

_Additional details [Install using the repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)_

Install docker engine using the repository

Ensure **gnome-terminal** installed

```bash
sudo apt install gnome-terminal
```   

Set up the **Local Docker Repository**

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
```  

Add Docker’s official GPG key:

```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Set up the repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg]
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## Install Docker Desktop 

_Additional details [Install Docker Desktop on Ubuntu](https://docs.docker.com/desktop/install/ubuntu/)_	

```bash	
sudo apt-get install ./docker-desktop-4.10.0-amd64.deb
```

## Enable Kubernetes in Docker Desktop
_Additional details [Enable Kubernetes](https://docs.docker.com/desktop/kubernetes/#enable-kubernetes)_

```bash	
Settings > Kubernetes > enable
```
