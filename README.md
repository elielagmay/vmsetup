# Minimal VM setup with Dockerized development

## Specs
* VMWare Workstation 12 Player
* Xubuntu 16.04
* 4GB memory
* 32GB disk

## Install docker
```
sudo -i

apt install apt-transport-https ca-certificates curl

# Install and start Docker Engine
apt install docker-engine
usermod -aG docker <user>
newgrp docker
service docker start

# Install Docker Compose
curl -L https://github.com/docker/compose/releases/download/1.8.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

# Install Docker Machine (if needed)
curl -L https://github.com/docker/machine/releases/download/v0.7.0/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine
chmod +x /usr/local/bin/docker-machine

exit
```

## Generate SSH keys and upload to Github
```
ssh-keygen -t rsa -b 4096 -C "<user>@<domain>"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub
```

## Install git
```
sudo apt install git-core
```

## Clone repo
```
mkdir -p ~/projects
cd ~/projects
git clone <repo_url> <repo_dir>
```

## Configure git user
```
cd <repo_dir>
git config user.name "Elie Lagmay"
git config user.email ext.elagmay@riotgames.com
```
