# Minimal VM setup with Dockerized development

## Specs
* VMWare Workstation 12 Player
* Xubuntu 16.04
* 4GB memory
* 32GB disk

## Install NVM and Node
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.4/install.sh | bash && source ~/.bashrc
nvm install node
```

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

## Install and configure sublime

Install Sublime
```
wget https://download.sublimetext.com/sublime-text_build-3114_amd64.deb
sudo dpkg -i sublime-text_build-3114_amd64.deb
```

Install Sublime Packages using [Package Control](https://packagecontrol.io/installation)
* Spacegray Theme
* SublimeLinter
* SublimeLinter-flake8
* SublimeLinter-contrib-eslint
* Babel
* Stylus
* Dockerfile

To enable SublimeLinter, install the underlying linter packages

```
npm install -g eslint
pip install flake8
```

Download and install Inconsolata
```
wget http://levien.com/type/myfonts/Inconsolata.otf
mkdir -p ~/.fonts
mv Inconsolata.otf ~/.fonts/Inconsolata.otf
sudo fc-cache -f
```

Update user preferences [using these settings](https://github.com/elielagmay/vmsetup/blob/master/Preferences.sublime-settings)

## Set environment variables
```
sudo subl /etc/environment
```
