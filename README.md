# Minimal VM setup with Dockerized development

## Specs
* VMWare Workstation 12 Player
* Xubuntu 16.04
* 4GB memory
* 32GB disk

## Install NVM and Node
```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.4/install.sh | bash && source ~/.bashrc
nvm install node
```

## Install Docker
```bash
sudo -i

apt install apt-transport-https ca-certificates curl

# Install and start Docker Engine
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
apt install docker-engine

# Ensure docker service is running
service docker start

# Setup user group
usermod -aG docker <user>
newgrp docker

# Install Docker Compose
curl -L https://github.com/docker/compose/releases/download/1.8.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

# Install Docker Machine (if needed)
curl -L https://github.com/docker/machine/releases/download/v0.7.0/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine
chmod +x /usr/local/bin/docker-machine

exit
```

## Install and configure Sublime

Install Sublime
```bash
wget https://download.sublimetext.com/sublime-text_build-3114_amd64.deb
sudo dpkg -i sublime-text_build-3114_amd64.deb
```

Install Sublime Packages using [Package Control](https://packagecontrol.io/installation)
* Spacegray Theme
* SublimeLinter
* SublimeLinter-flake8
* SublimeLinter-contrib-eslint
* Babel [**](https://github.com/babel/babel-sublime#setting-as-the-default-syntax)
* Stylus
* Dockerfile

To enable SublimeLinter, install the underlying linter packages

```bash
pip install flake8
npm install -g eslint
nvm which default  # <-- copy result to User/SublimeLinter.sublime-settings : user.paths.linux
```

Download and install Inconsolata
```bash
wget http://levien.com/type/myfonts/Inconsolata.otf
mkdir -p ~/.fonts
mv Inconsolata.otf ~/.fonts/Inconsolata.otf
sudo fc-cache -f
```

Update user preferences [using these settings](https://github.com/elielagmay/vmsetup/blob/master/Preferences.sublime-settings)

## Install Git
```bash
sudo apt install git-core
git config --global user.name "<name>"
git config --global user.email <you>@<domain>
```

## Generate SSH keys and upload to Github
```bash
ssh-keygen -t rsa -b 4096 -C "<user>@<domain>"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub
```

## Clone project
```bash
mkdir -p ~/projects
cd ~/projects
git clone <repo_url> <repo_dir>
```

## Set environment variables
```bash
sudo subl /etc/environment
```
