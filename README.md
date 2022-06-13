My dotfiles

- First, you will need to connect to your droplet via SSH. For now, just open up your terminal app and type: ssh root@<IP-ADDRESS-OF-DROPLET> (substituting the IP-ADDRESS that you noted before).
  
- Before doing any kind of configuration on the droplet, let’s first create a user that you can use other than root. Type in adduser USER_NAME (substituting USER_NAME with the username of your choice).
  
- Now that we have created a new user, let’s make sure that we lock down sshd from allowing that user to connect with a password and continue to use the same SSH key to connect. First we will copy the key from the root user to the newly created user. Type: mkdir /home/USER_NAME/.ssh && cat ~/.ssh/authorized_keys >> /home/USER_NAME/.ssh/authorized_keys (remember to substitute USER_NAME with the username that you chose earlier).
  
- Next, we need to chown that directory that we just created so that the USER_NAME can write to it later. Execute this command: chown -R USER_NAME:USER_NAME /home/USER_NAME/.ssh

- Now we can add this new user to the sudoers file. This will allow this user to execute the sudo command. Replicate the line root ALL=(ALL:ALL) ALL, replacing root with your new username, and save the file. (If you’re in vim, you’ll need to save with :w! since the file is readonly.)
```
  vim /etc/sudoers
```

```
Basic setup on ubuntu

sudo apt-get update
sudo apt-get install tmux -y
tmux
sudo apt install zsh -y
echo "\# default" > .zshrc
echo $(zsh --version)
chsh -s /usr/bin/zsh
sign out and sign back in (maybe a new tmux?)

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
sudo apt-get install fonts-powerline -y

git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

git clone https://github.com/phouchens/dotz.git

cd dotz

. ./setup.sh

source .zshrc

sudo apt install curl -y
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
source ~/.zshrc

nvm --version
nvm install node
 sudo apt install lua5.3 -y

sudo apt install software-properties-common -y
sudo add-apt-repository ppa:neovim-ppa/stable -y
sudo add-apt-repository ppa:neovim-ppa/unstable -y
sudo apt-get update
sudo apt install neovim -y
mkdir .config
chmod 755 .config
cd .config
git clone https://github.com/phouchens/hVim.git nvim

git clone --depth 1 https://github.com/wbthomason/packer.nvim\
 ~/.loca:xl/share/nvim/site/pack/packer/start/packer.nvimzaaz
 Z
 sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
apt-cache policy docker-ce

sudo apt install docker-ce -y

sudo systemctl status docker

sudo usermod -aG docker ${USER}
su - ${USER}

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose



// minikube
sudo apt update
sudo apt install apt-transport-https
sudo apt upgrade

//use kvm
// note i couldnt get this to work right away... used the docker driver and it seemed to work
sudo apt -y install qemu-kvm libvirt-dev bridge-utils libvirt-daemon-system libvirt-daemon virtinst bridge-utils libosinfo-bin libguestfs-tools virt-top
sudo modprobe vhost_net
sudo lsmod | grep vhost
echo "vhost_net" | sudo tee -a /etc/modules

//You need to download the minikube binary. I will put the binary under /usr/local/bin directory since it is inside $PATH.
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
// https://help.ubuntu.com/community/KVM/Installation  


chmod +x kubectl
sudo mv kubectl  /usr/local/bin/
kubectl version -o json

//insgall docker machine kvm driver
curl -LO https://storage.googleapis.com/minikube/releases/latest/docker-machine-driver-kvm2
chmod +x docker-machine-driver-kvm2
sudo mv docker-machine-driver-kvm2 /usr/local/bin/

//starting minikube
//add user account to libvirt
sudo usermod -aG libvirt $USER
newgrp libvirt
virt-host-validate
//set kvm as driverZ
minikube config set driver kvm2
 minikube start 


 // kubens
 git clone https://github.com/ahmetb/kubectx
 chmod +x kubectx/kubens
 sudo mv kubectx/kubens /usr/local/bin
```
