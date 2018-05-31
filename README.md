apres l'installation d'ubuntu minimal.

# installation de l'ensemble des outils liés au package manager en une fois

sudo apt-get install gcc perl make ctags git tig neovim xinit i3 xsel copyq tmux python-pip python3-pip py3status curl rxvt-unicode-256color

# installation step by step

## Installation gcc perl make
sudo apt-get update && sudo apt-get install gcc perl make dkms

## montage cd addition invité
mkdir tmp && sudo mount /dev/cdrom tmp && cd tmp && sudo ./VBoxLinuxAdditions.run

## reboot puis installation ctags tig git
sudo apt-get install ctags tig git neovim

## installation i3
sudo apt-get install i3

## installation xinit et xsel
sudo apt-get install xinit xsel copyq

## install python-pip
sudo apt-get install python-pip python3-pip py3status curl tmux rxvt-unicode-256color

# installation des outils hors package manager

## pip3 install neovim && pip2 install neovim && gem install neovim 

## ajout vimplug
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
	
## lancer nvim puis :PlugInstall

## creer un lien .tmux.conf dans home, lancer tmux puis Ca+I


## ajout nodeJS
mkdir -p ~/Outils/
cd ~/Outils/
wget https://nodejs.org/dist/v8.11.2/node-v8.11.2-linux-x64.tar.xz
tar -xJf node-v8.11.2-linux-x64.tar.xz
rm node-v8.11.2-linux-x64.tar.xz
## mettre dans .bashrc : 
export PATH=$PATH:$HOME/Outils/node-v8.11.2-linux-x64/bin
export EDITOR=vim
set -o vi

## pus installer le module optionnel pour neovim
npm install -g neovim

## ajout sdkman
curl -s "https://get.sdkman.io" | bash

## dans un nouveau term installer java
sdk install java
 
## install rvm
curl -sSL https://rvm.io/mpapis.asc | gpg --import -
\curl -sSL https://get.rvm.io | bash -s stable

## installer ruby 
rvm install ruby
rvm docs generate-ri
gem install neovim

## install ansible
sudo apt-get install ansible
cd ~/Outils/

##git clone -b v2.4.3.0-1 --recursive https://github.com/ansible/ansible.git ansible_2.4.3
git clone --recursive https://github.com/ansible/ansible.git
git worktree add ../ansible_2.4.3 && cd ../ansible_2.4.3 && git checkout tags/v2.4.3.0-1 -b ansible_v2.4.3 && git worktree list

### utiliser la version ansible du worktree
source hacking/env-setup && ansible --version

# ressources
git@github.com:Grillon/conf_linux.git
