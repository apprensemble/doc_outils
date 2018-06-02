# Exherbo

## ressources

https://exherbo.org/docs/install-guide.html

http://paludis.exherbo.org/clients/cave.html

https://wiki.gentoo.org/wiki/Paludis

https://exherbo.org/docs/eapi/exheres-for-smarties.html

l'irc : freenode : #exherbo et #paludis

## suivre la doc d'installation

https://exherbo.org/docs/install-guide.html

Tt fonctionne le guide est super. Mais cela n'offre qu'une install minimale.

## installation des outils via package manager

cave resolve -x x11-misc/dmenu

cave resolve -x app-crypt/gnupg

cave resolve -x repository/rust

cave resolve -x repository/net

cave resolve -x net-www/firefox

build-essential libreadline zlib1g libyaml libc6 libgdbm ncurses

### installation copyq

cave resolve -x sys-devel/cmake

cave resolve -x repository/kde

cave resolve -x x11-libs/qt

cave resolve -x x11-libs/qtbase #mettre sql sqlite dans options.conf

cave resolve -x x11-libs/qttools

cave resolve -x x11-libs/qtx11extras

cave resolve -x x11-libs/qtsvg

cave resolve -x x11-libs/qtscript

https://copyq.readthedocs.io/en/latest/build-source-code.html

## installation du reste des outils sans package manager

pip install py3status

### ajout vimplug
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

### install rvm
curl -sSL https://rvm.io/mpapis.asc | gpg --import -
\curl -sSL https://get.rvm.io | bash -s stable

### installer ruby 
rvm install ruby
rvm docs generate-ri
gem install neovim

### installer nodejs
cd ~/Outils/
wget https://nodejs.org/dist/v8.11.2/node-v8.11.2-linux-x64.tar.xz
tar -xJf node-v8.11.2-linux-x64.tar.xz
rm node-v8.11.2-linux-x64.tar.xz
# mettre dans .bashrc : 
export PATH=$PATH:$HOME/Outils/node-v8.11.2-linux-x64/bin
export EDITOR=vim

npm install -g neovim

## configuration dotfiles

cd ~/.config
ln -s ~/Outils/conf_linux/.config/i3
ln -s ~/Outils/conf_linux/.config/nvim

cd 
ln -s ~/Outils/conf_linux/.Xdefaults
ln -s ~/Outils/conf_linux/.Xresources
ln -s ~/Outils/conf_linux/.inputrc
ln -s ~/Outils/conf_linux/.tmux.conf


# A savoir

pb de d'ordre d'installation : ajouter build_options: -recommended_tests
ça m'est arrivé pour la glib

recompiler tout une categorie, par exemple x11-apps : cave resolve $(cave print-ids -m x11-apps/*::/ -f '%c/%p ')

reinstaller des drivers x11 : cave resolve -1 $(cave print-ids -m 'x11-drivers/*::installed' -f ' ')"

gdk-pixbuf : cannot recognize image file format. Dans ce cas installer shared-mime-info : https://github.com/Kozea/WeasyPrint/issues/182 

